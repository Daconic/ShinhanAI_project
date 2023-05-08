import streamlit as st
import pandas as pd
import numpy as np

import requests
from bs4 import BeautifulSoup
import re

import FinanceDataReader as fdr


# 한페이지를 수집하는 함수
def get_one_page(item_code, page_no):
    url = f"https://finance.naver.com/item/board.naver?code={item_code}&page={page_no}"
    headers = {"user-agent":"Mozilla/5.0"}
    response = requests.get(url, headers=headers)

    table = pd.read_html(response.text)[1]
    cols = ["날짜", "제목", "글쓴이", "조회", "공감", "비공감"]
    table = table[cols]
    temp = table.dropna()
    return temp

# 여러 페이지를 수집하는 함수
def jongmok_toron(item_code, last_page):
    
    post_list = []
    for page_no in range(1, last_page + 1):

        df = get_one_page(item_code, page_no)
        post_list.append(df) 

    post_list = pd.concat(post_list, ignore_index=True)
    return post_list

# 내용 링크를 수집하는 함수
def jongmok_context(item_code, page_no):
    url = f'https://finance.naver.com/item/board.naver?code={item_code}&page={page_no}'
    headers = {"user-agent":"Mozilla/5.0"}
    response = requests.get(url, headers=headers)
    soup = BeautifulSoup(response.text, 'html.parser')
    base_url = 'https://finance.naver.com/'
    sub_url_list = [soup.select('td.title > a')[i]['href'] for i in range(len(soup.select('td.title > a')))]
    context_url_list = [base_url + i for i in sub_url_list]
    return context_url_list

# 원하는 페이지만큼 내용 링크를 수집하는 함수 만들기
def context_link(item_code, last_page):
    b=[]
    for i in range(1, last_page + 1):
        a = jongmok_context(item_code, i)
        b.append(a)
        context_list = pd.concat([pd.DataFrame(x) for x in b], ignore_index=True)
    return context_list

# 종목토론 목록과 내용링크를 포함한 데이터프레임 만들기
def 목록_내용링크(item_code, last_page):
    종목토론_목록 = jongmok_toron(item_code, last_page)
    종목토론_내용링크 = context_link(item_code, last_page)
    a = pd.concat([종목토론_목록, 종목토론_내용링크], axis=1, ignore_index=True)
    a.columns = ['날짜', '제목', '글쓴이', '조회', '공감', '비공감', '내용링크']
    return a


# 내용을 수집하는 함수
def 종목토론_내용(item_code, last_page):
    content = []
    df = 목록_내용링크(item_code, last_page)
    for i in df['내용링크']:
        headers = {"user-agent": "Mozilla/5.0"}
        response = requests.get(i, headers=headers)
        html = BeautifulSoup(response.text)
        a = html.select('#body')[0].text
        content.append(a)        
    return content

def 종목토론_목록_내용링크_내용(item_code, last_page):
    df = 목록_내용링크(item_code, last_page)
    df['내용'] = 종목토론_내용(item_code, last_page)
    return df

# 토큰화
from transformers import PreTrainedTokenizerFast

tokenizer = PreTrainedTokenizerFast.from_pretrained(
    "skt/kogpt2-base-v2",
    bos_token='</s>', 
    eos_token='</s>', 
    unk_token='<unk>',
    pad_token='<pad>', 
    mask_token='<mask>')
    
# 감성분석
from transformers import pipeline

classifier = pipeline("sentiment-analysis")

def 종목토론_제목_내용링크_내용_감성분석(item_code, last_page):
    df = 종목토론_목록_내용링크_내용(item_code, last_page)
    classifier = pipeline("sentiment-analysis")
    제목내용 = [df['제목'][i] + ' ' + df['내용'][i] for i in range(len(df))]

    # 정규표현식 적용
    제목내용_특수문자제거 = []
    for i in 제목내용:
        w = re.sub(r"[^가-힣\s\d]", "", i)
        제목내용_특수문자제거.append(w)

    # 토큰화
    제목내용_특수문자제거_토큰화 = []
    for i in 제목내용_특수문자제거:
        a = tokenizer.tokenize(i)
        제목내용_특수문자제거_토큰화.append(a)

    # 감성분석
    sentiment = []
    for i in 제목내용_특수문자제거_토큰화:
        a = classifier(i)
        sentiment.append(a)

    # 데이터프레임으로 만들기
    b = []
    for i in range(len(sentiment)):
        a = pd.DataFrame(sentiment[i], columns=['label', 'score'])
        b.append(a)
        sentiment_analysis = pd.concat(b, ignore_index=True)

    df['sentiment-analysis'] = sentiment_analysis['label']
    df['score'] = sentiment_analysis['score']

    return df

def 종목별_긍정점수(item_code, last_page):
    data = 종목토론_제목_내용링크_내용_감성분석(item_code, last_page)

    긍정점수 = []
    for i in range(len(data[['sentiment-analysis', 'score']])):
        if data['sentiment-analysis'][i] == 'POSITIVE':
            a = data['score'][i]
            긍정점수.append(a)
        else:
            a = 1 - data['score'][i]
            긍정점수.append(a)
    data['긍정점수'] = 긍정점수
    return data['긍정점수'].mean()


item_code = st.text_input('분석을 원하시는 종목의 코드를 입력하세요.')
last_page = 1
# last_page = st.number_input('스크래핑할 페이지 수를 입력하세요. (페이지 수가 많을수록 정확도는 향상되지만 오랜 시간이 소요됩니다)', min_value=0, step=1, format='%d')

score = round(float(종목별_긍정점수(item_code, last_page)), 3)

# 종목명 출력
krx = fdr.StockListing('KRX')
name = krx[krx['Code'] == item_code]['Name'].iloc[0]
    
print(f' 입력하신 종목은 {name}({item_code})입니다.')
print(f" 네이버 종목토론실에서 해당 종목의 실시간 긍정 점수는 {score}입니다.")
print(' 저희 서비스를 이용해주셔서 감사합니다.')
print('💡투자의 책임은 본인에게 있습니다.💡')


