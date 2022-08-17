# nlp-sentimental_analysis

Sentimental Analysis with NLP

# 1. 프로젝트 개요
    
    자연어 처리와 감성 분석
    쇼핑몰 상품 후기에 대한 감성 분석
    말뭉치를 긍정과 부정으로 나누어 감성 예측 모델 구축
    


# 2. 모델

### 데이터셋
* Open Source 웹 크롤링 네이버 쇼핑 리뷰
    * https://bab2min.tistory.com/657
    * https://github.com/bab2min/corpus/tree/master/sentiment

* 데이터 정보
    * 네이버 쇼핑몰 후기
    * 약 200,000 개 : 의류, 잡화, 미용, 가전, 식품 등 다양한 분야 물건 포함


### 모델 Architecture
1. 데이터 전처리 - regex, labeling, 

2. Tokenization
    *  형태소 분석기 Mecab
3. Stop words
    *  불용어 stop_words 지정
    *  불용어 토큰 제거
4. Labeled words sort
    * 긍정/부정 단어 모으기 및 빈도 수 확인
5. Visualization
    * matplotlib, wordcloud

6. model - 모델 돌려서 학습해주는 함수
    * Sequential 
    * Hyper-parameters 
        1. epoch : 15
        2. criterion : binary_CrossEntropyLoss
        3. optimizer : rmsprop
        4. metrics : accuracy



# 3. 서비스 설명
쇼핑몰에서 상품에 대한 후기를 통해 감성을 분석을 진행.
후기들이 긍정인지 부정인지 판별 가능한 모델을 통해, 추후 상품에 대한 전반적인 평가 파악 가능.
