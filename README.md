# nlp-sentimental_analysis

Sentimental Analysis with NLP

# 1. 프로젝트 개요
    
    자연어 처리와 감성 분석
    


# 2. 모델

### 데이터셋
1. Open Source 네이버 쇼핑 리뷰

2. 웹 크롤링


### 모델 Architecture
1. Define Token
    *  Q_TKN, A_TKN, BOS, EOS, PAD, MASK, SENT, PAD

2. Define Chatbot Class
    *  len : 길이 함수
    *  getitem : 데이터 로더 함수
        1. 데이터 전처리 - regex
        2. Tokenization
            *  q_toked(문장 시작 토큰, 질문 데이터)
            *  a_toked(다음 문장 시작 토큰, 답변 데이터, 대화 종료 토큰)
        4. labeling - 답변지 생성 (질문 마스킹, embedded 답변 데이터, max_len 만큼 남은 길이 패딩)
        5. masking - labels 를 mask화 (0,0,0, …, 1,1,1, …, 0,0,0,…)
        6. Ids
            *  labels_id (9(MASK<unused0>),9,9,…, a1,a2,a3,…1(EOS</s>),3(PAD<pad>),3,3,…)
            *  token_ids (2(Q_TKN<usr>), q1,q2,q3,…,4(A_TKN<sys>),a1,a2,a3,…1(EOS</s>),3(PAD<pad>),3,3,…)

3. batch - batch 합쳐주는 함수

4. model - 모델 돌려서 학습해주는 함수
    *  Hyper-parameters 
        1. epoch : 10
        2. learning_rate : 3e-5
        3. Sneg : 1e18
        4. criterion : CrossEntropyLoss(다중분류함수)
        5. optimizer : Adam



# 3. 서비스 설명

### 디렉토리 구조
1. data : 추가될 데이터 저장하는 경로
4. `sa_model.py` : 가장 최신 데이터(csv) 불러와서 모델 학습 (후 pkl 파일로 생성)
5. `batch.py` : sa_model.py 실행 data 폴더 관리
6. `sa_modeling.ipynb`
