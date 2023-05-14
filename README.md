# 세뱃돈을 지켜줘! 청소년을 위한 종합 금융 서비스

- Member: 멋쟁이사자처럼 AI SCHOOL 8기 2조 금사빠
- Status: Complete
- Period: 23.04.24 ~ 23.05.10

## 1. 프로젝트 개요

유년 시절이나 청소년 시절 받은 세뱃돈을 부모님께서 관리해주신 경험이 있으신가요?

부모님께서는 경제 관념이 아직 확립되지 않은 청소년기에 목돈이 생기면 부적절한 소비 습관이 생기는 것을 우려해 세뱃돈을 맡아 관리를 해주셨습니다.

하지만 올바른 금융 교육과 경험을 통해 청소년기부터 스스로 목돈을 관리할 수는 없는 것일까요?

 한 조사에 따르면 우리나라는 정규 교육 과정 내에 `금융과 관련한 독립된 교과목이 부재`한 상황으로 청소년을 대상으로 한 금융 교육의 기반이 충분히 마련되어 있지 않은 것을 알 수 있습니다. 이로 인해 금융 이해력 지수 역시 타 국가에 비해 낮은 것으로 나타났습니다.

<p align="center"><img src="https://github.com/Daconic/ShinhanAI_project/assets/108817458/b0358430-caa0-401f-896a-3e433dc9934e"></p>

 이렇게 낮은 금융 이해력 지수는 자연스럽게 `성인 금융 문맹`으로 이어집니다. 제대로 된 금융 교육을 접하지 못한 아이들은 커서 금융 문맹으로 거듭나 이후 자산 관리에도 큰 어려움을 겪을 수 있습니다. 이렇듯 우리나라는 현재 `금융 교육 시스템의 도입이 시급함`을 알 수 있었습니다.

<p align="center"><img src="https://github.com/Daconic/ShinhanAI_project/assets/108817458/4d655278-95cf-49a4-bf00-a4f1c78c2051"></p>

그렇다면 적절한 금융 교육이란 어떤 것일까요?

 기획재정부에서 실시한 금융 이해력 실태 조사에 따르면 학생과 교사 모두 `체험형 교육 방식`을 선호하는 것으로 나타났습니다.

<p align="center"><img src="https://github.com/Daconic/ShinhanAI_project/assets/108817458/f659cc2b-53e7-4f11-9a85-3a7cab8a6bed" weight=600 height=300></p>

수업 시간에 교실에서 경제 수업을 듣는 것보다 실제로 자신이 금융을 경험하고 그 경험 속에서 개념을 이해하는 것을 선호하는 것입니다.

 이에 저희 조는 금융 교육부터 투자까지 다양한 금융 경험을 제공하고자 본 서비스를 기획하였습니다. 어린 나이부터 유년 시절 받은 세뱃돈을 이용하여 금융 교육을 한다면, 다음과 같은 효과를 기대해볼 수 있습니다.

  ✅ 부모 입장에서는 자녀에게 경제 관념을 기를 수 있는 기회 제공

  ✅ 은행은 잠재 고객 확보 및 부모 고객까지 공략 가능

## 2. 프로젝트 목차

1. **맞춤형 금융 교육 서비스**
    
    : 초등학생과 중고등학생으로 나누어 수준별 교육 제공
    
2. **청소년 자산 관리 및 주식 포트폴리오 추천**
    
    : 성향에 따른 자산 관리 방법 제안 및 주식 종목 추천
    
3. **청소년 맞춤 체크카드 추천 시스템**
    
    : 소비 패턴에 맞는 맞춤형 체크카드 추천
    

## 3. 데이터 소개

| 프로젝트명 | 출처 | 수집 방법 | 데이터 설명 |
| --- | --- | --- | --- |
| 금융 교육 서비스 | 한국경제신문 | 웹 스크래핑 | 금융 기초 지식과 관련된 퀴즈 |
| 청소년 자산 관리 및 주식 포트폴리오 추천 | KOSPI | Finance Data Reader 라이브러리 | KOSPI 상한가, 하한가, 종가, 시가, 변화량 |
|  | 네이버 증권 | 웹 스크래핑 | 네이버 증권 종목별 헤드라인 |
| 체크카드 추천 시스템 | 신한카드 | 웹 스크래핑 | 신한 체크카드명 및 혜택 |
|  | 직접 생성 | faker 라이브러리 | 사용자 연간 소비 데이터 |

## 4. 프로젝트 소개

> **4.1. 맞춤형 금융 교육 서비스**
> 
1. 금융 퀴즈
    - 한경에서 제공하는 금융 상식 퀴즈 스크래핑
        - GPT를 연동하여 ‘해설보기’ 버튼 클릭 시 해당 문제와 관련된 해설 출력
        - ChatGPT와 연동된 챗봇 시스템을 구현하여 질문을 입력하면 청소년의 눈높이로 해설 출력
    - Hugging face 형태소 분류를 통해 질문 유형 파악
        - 문제를 풀고 난 후 ‘결과보기’ 버튼 클릭 시 각 유형별 정답률 출력
        - 자신이 부족한 유형 판단 가능
    - streamlit 구현
       
        <p align="center"><img src="https://github.com/Daconic/ShinhanAI_project/assets/108817458/24a7e4a1-90b8-4787-ad1c-eae3b4346fe8"></p>
        
        <p align="center"><img src="https://github.com/Daconic/ShinhanAI_project/assets/108817458/3b9a7eea-4c07-4b69-866a-8545d9ca3470"></p>


> **4.2. 청소년 자산 관리 및 주식 포트폴리오 추천**
> 
1. 개인 설문을 통한 투자 성향 파악
    - 성향에 맞는 주식 포트폴리오를 추천
    - 설문 문항은 실제 신한은행에서 사용하는 투자자 정보 확인 설문을 참고하여 청소년기에 맞게 수정
    - 설문을 통해 개인 맞춤형 주식 포트폴리오가 출력되도록 구성

    ![Untitled (7)](https://github.com/Daconic/ShinhanAI_project/assets/108817458/cc096039-c9ab-4a14-84f2-58998ca03349)

2. 네이버 뉴스 헤드라인의 감정 분석값을 도출
    - 상위 30개 종목별 뉴스 헤드라인 크롤링 후 Finbert 금융 뉴스 감성 분석 모델로 점수 산출
    - 3가지 감정상태는 neutral: 0, positive: 1, negative: 2로 레이블 인코딩
    
    <p align="center"><img src="https://github.com/Daconic/ShinhanAI_project/assets/108817458/2e11b6f5-82f8-4a0a-9e1a-1e69941ed0c5"></p>
      
    <p align="center"><img src="https://github.com/Daconic/ShinhanAI_project/assets/108817458/222b0c78-49e6-4c85-b18a-7bcb57ee0f4b" weight=600 height=300></p>
    
    
    
3. 감성분석 값과 Finance-Data-Reader을 통해 생성된 시계열 변수들을 통해 주가 예측
    
    <p align="center"><img src="https://github.com/Daconic/ShinhanAI_project/assets/108817458/91997824-260c-407c-a1cc-e0c243629d5f7" weight=600 height=300></p>
    <p align="center"><img src="https://github.com/Daconic/ShinhanAI_project/assets/108817458/edc20552-656c-45e7-b162-bf5f074374ea" weight=600 height=300></p>

4. 예측된 값을 기반으로 상관계수, 공분산을 기준으로 포트폴리오를 나누고 Sharpe Ration를 통해 무위험 대비 수익률이 높은 포트폴리오를 추천
    - 상위 30 종목별 상관관계를 나타낸 히트맵
        
        <p align="center"><img src="https://github.com/Daconic/ShinhanAI_project/assets/108817458/e47079b9-589b-4296-9f45-05707ac3358f"></p>

    - 상관관계, 공분산이 0.5 이하인 각 쌍의 종목들
        
        <p align="center"><img src="https://github.com/Daconic/ShinhanAI_project/assets/108817458/28bf75da-22c0-4e2a-a620-0234cdd9b842"></p>
        
    - 출력된 결과값. 샤프 비율과 수익률, 변동성을 확인할 수 있음
        
        <p align="center"><img src="https://github.com/Daconic/ShinhanAI_project/assets/108817458/0cafb80f-f596-4cb6-9c37-38f0e4d62206" weight=600 height=300></p>


5. 네이버 종목 토론실 실시간 이용자 심리 분석
    - 네이버 종목 토론실 제목 및 내용 스크래핑
    - 텍스트 전처리
        - 정규표현식 적용하여 한글과 숫자 제외하고 제거
        - 토큰화
    - 감성 분석
        
        - Transformer의 감성 분석 파이프라인 모델 사용
       
        <p align="center"><img src="https://github.com/Daconic/ShinhanAI_project/assets/108817458/bda1ddf6-1563-4a70-b32d-34c83ed43ba7" weight=400 height=200></p>

    - streamlit 구현
        - 0.67 이상 긍정, 0.33~0.66 중립, 0.33 미만 부정
        <p align="center"><img src="https://github.com/Daconic/ShinhanAI_project/assets/108817458/a2c5ad05-5d96-41fd-a72f-2cf1754b599e" weight=600 height=300></p>

> **4.3. 청소년 맞춤 체크카드 추천 시스템**
> 
1. **카드 데이터 수집**
    
    현재 신한카드에만 약 90여종의 체크카드가 존재
    
    → 자신의 소비 습관에 알맞은 카드를 고르기 어려움
    
    → 청소년의 소비 패턴과 관심사를 고려하여 맞춤형 체크카드 추천
    
    1) selenium을 이용한 동적 크롤링
    
      : 신한 체크카드명 및 혜택 크롤링
    
    <p align="center"><img src="https://github.com/Daconic/ShinhanAI_project/assets/108817458/3b2e12b1-6235-473e-aa3b-eee5b72272f8" weight=400 height=200></p>
    
    2) 청소년에게 적합하지 않은 카드 제외
    
      : ‘삼성증권 CMA 신한 체크’, ‘신한카드 On 체크(한국유치원총연합회 교원증)’ 등 청소년에게 적합하지 않은 카드 제외
    
    → 총 51개의 카드 데이터 확보
    
2. **카드 정보 분석 및 군집화**
    
    1) 카드 혜택 one-hot-encoding
    
    - 카드 혜택을 교통, 뷰티, 영화, 카페 등으로 나눈 후 해당 혜택이 카드에 존재하면 1로, 존재하지 않으면 0으로 인코딩
    
    ![Untitled (5)](https://github.com/Daconic/ShinhanAI_project/assets/108817458/ab9eb91a-0e3c-492f-aa44-c848ef25728b)

    
    2) K-Means 군집화 수행
    
    3) 최적의 군집 개수 찾기
    
      : elbow method와 실루엣 계수 확인
    
    <p align="center"><img src="https://github.com/Daconic/ShinhanAI_project/assets/108817458/91eed884-30da-4491-9d65-2ae88863d0a1" weight=400 height=200></p>
    
    <p align="center"><img src="https://github.com/Daconic/ShinhanAI_project/assets/108817458/389efd6f-8706-40db-a0df-eaaad29c1e55" weight=400 height=200></p>
    
    - KElbowVisualizer 활용
        
        <p align="center"><img src="https://github.com/Daconic/ShinhanAI_project/assets/108817458/ef5f2a47-7fb1-40ba-b6fc-12581de1e3ca" weight=800 height=400></p>
        
3. **가상의 유저 데이터 생성**
    
    파이썬 faker 라이브러리 사용
    
    → 이름, ID, 관심사, 나이, 받고 싶은 혜택, 항목별 연간 총 비용 컬럼 생성
    
    ![Untitled (11)](https://github.com/Daconic/ShinhanAI_project/assets/108817458/81697ea4-ff7c-4502-a635-f8dc9997989e)

4. **모델링**
    
    1) LightGBM 알고리즘 사용
    
    2) RandomsearchCV를 사용하여 하이퍼파라미터 튜닝
    
5. **Test 데이터 생성 및 모델 적용**
    
    1) 파이썬 faker 라이브러리를 사용하여 test 데이터 생성
    
    ![Untitled (11)](https://github.com/Daconic/ShinhanAI_project/assets/108817458/56db92fe-f482-4248-9f86-c89766a769b5)

    
    2) 카드 군집 할당
    
    ![Untitled (12)](https://github.com/Daconic/ShinhanAI_project/assets/108817458/9305ffdd-1fef-4355-941e-a31d2bd8fc37)

    
    3) TF-IDF 및 코사인 유사도
    
    - 고객의 관심사, 받고 싶은 혜택과 카드 혜택 유사도 비교
    
    
    4) 모델 적용 결과
    
    - 사용자 지출 상위 3개 종목이 카드 혜택에 포함된 횟수 계산
    - 코사인 유사도와의 합을 구하여 총합이 큰 순서대로 나열
    
    ![Untitled (13)](https://github.com/Daconic/ShinhanAI_project/assets/108817458/ea5ae932-24d7-47be-825d-4b87d5be1789)

6. **결과 비교**
- 가상의 고객 연간 지출 데이터

![Untitled (15)](https://github.com/Daconic/ShinhanAI_project/assets/108817458/cfeb7af3-5155-433c-90b6-8e9343c25644)

- 추천된 카드 목록
![Untitled (14)](https://github.com/Daconic/ShinhanAI_project/assets/108817458/f7f3012c-99a5-4b80-a3e5-22d186d5f40d)

고객의 지출 데이터 중 지출 상위 3위 종목인 배달 및 카페(요식 업종), 도서에 대한 혜택이 있는 카드가 추천됨

## 5. 활용방안 제언 및 기대효과

> **5.1. 활용방안 제언**
> 
- 신한은행과 협력하여 기존 신한은행의 공식 캐릭터인 ‘쏠 및 ‘몰리’을 내세운 앱 서비스 개발
- 월간 모의투자 대회를 개최하여 우수 참여자 수상
- 오랜 기간동안 신한은행 체크카드 사용 및 신한은행을 통해 자산관리를 해 온 사용자에게 우대금리 적용

> **5.2. 기대효과**
> 
1. 금융 교육 서비스
    - 청소년에게 금융에 대한 이론적인 지식을 제공
    - 청소년은 자신의 취약 유형 파악 가능
2. 자산관리와 투자 포트폴리오 제안
    - 자신의 투자 성향 파악 가능
    - 투자 성향에 따른 자산 관리 및 포트폴리오 관리 가능
3. 체크카드 추천 서비스
    - 사용자 소비 패턴을 기반으로 맞춤형 체크카드 추천
    - 자신에게 알맞은 체크카드를 손쉽게 고를 수 있음
4. 실전 금융 경험
    - 실전 경험을 통해 금융에 대한 흥미 유발
    - 보다 많은 금융 경험을 얻을 수 있음
    - 투자에 대한 진입 장벽을 낮출 수 있음
5. 은행의 고객 확보
    - 잠재 고객 확보 및 부모 고객까지 공략 가능

## 6. 한계점

> **6.1. 맞춤형 금융 교육 서비스**
> 
1. 데이터 의존성
- `문제점`: 원천 소스가 막히거나 구조가 변경되면 매번 데이터를 수집해야하는 번거로움이 있음
- `해결방안`: 신한은행의 공식 캐릭터 ‘몰리’를 내세워 자체적인 퀴즈 콘텐츠 개발 및 신한은행 금융 교육 애니메이션 시리즈 ‘신한친구들 금융수사대’를 활용

> **6.2. 청소년 자산 관리 및 주식 포트폴리오 추천**
> 
- `문제점`: 감성분석 결과의 기간이 짧아 시계열 분석을 1년밖에 하지 못함
- `해결방안`: 내부적으로 생성한 신한 증권 리포트 데이터들을 5년치 또는 그 이상을 분석해 시계열 예측에 더하면 더 도움이 될 것으로 예상

> **6.3. 청소년 맞춤 체크카드 추천 시스템**
> 
1. 데이터 확보의 어려움
- `문제점`: 데이터를 구하기 어려워 가상의 데이터를 랜덤으로 생성하여 사용하다 보니 모델의 정확도가 현저히 낮아 어려움을 겪음
- `해결방안`: 실제 데이터를 적용하면 모델 성능이 더 나아질 것으로 예상
