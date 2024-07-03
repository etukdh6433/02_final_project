# 02_final_project

# 최종프로젝트 코드를 모아두는 레포지토리입니다.
## 진행할 프로젝트 주제 
1) 네이버 시리즈온 영화 데이터의 기록 분석 및 평점 예측
2) 영화 리뷰칸에서 순수 영화 리뷰만 뽑아내기

### 1) 네이버 시리즈온 영화 데이터의 기록 분석
  1. 네이버 시리즈온 영화 데이터 수집
  2. 데이터 기초 분석 및 전처리 작업
  3. 목표 가설 설정 및 검증 EDA 수행
### 2) 데이터의 각종 feature를 통한 rating 예측 및 feature 중요도 파악
  1. rating을 예측하기 위한 XGBoost / LightGBM / RandomForest 모델 설계 및 파라미터 최적화
  2. feature 중요도 확인
  3. rating에 영향을 많이 주는 요소를 통한 인사이트 제시

### 3) 영화 리뷰칸에서 순수 영화 리뷰만 뽑아내기
  1. 네이버 시리즈온 영화리뷰 댓글 수집
  2. 수집한 데이터중 19000개의 데이터에 대해 0,1 라벨링 작업 (0 : 영화 내용 및 후기와 관련없는 댓글, 1 : 영화 내용 및 후기에 관련된 댓글)
  3. AutoTokenizer로 수집한 데이터에 대해 토크나이징 및 어텐션마스크 처리
  4. ElectraForSequenceClassification 모델 설계 및 배치단위 fine-tuning
  5. test 검증 및 라벨링 진행하지 않은 댓글에 대해 실제 적용

  ###### 3-1) 0으로 분류된 댓글에서 잦은 빈도로 등장한 단어들을 통해 네이버 시리즈온의 전체적인 불만사항의 트렌드를 유추
  1. 학습된 모델을 전체 댓글에 대해 분류를 진행
  2. 얻은 결과물을 토크나이징하여 주로 등장했던 토큰들을 추적
  3. 실제 사람이 라벨링했던 데이터에 대해 2.번의 작업을 마찬가지로 수행
  4. 두 결과물을 분석하여 모델의 성능을 간접적으로 확인하고, 네이버 시리즈온의 주된 불만사항을 수집
