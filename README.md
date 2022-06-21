# AIFFEL X SOCAR PROJECT
- 모두의연구소 산하 인공지능 교육기관 AIFFEL과 카셰어링 기업 SOCAR가 협력하여 진행된 기업 연계 해커톤 프로젝트로서, [미시적 수요 분석과 모델링] 주제에 대해 SOCAR로부터 제공 받은 예약 데이터를 기반으로 프로젝트를 진행하였습니다. 
- 단, SOCAR 제공 데이터 EDA 및 시각화 자료는 저작권 및 보안 이슈 문제로 비식별화 처리 되었음을 참고 바랍니다.  


## 1. 프로젝트 소개
### 개요
- 주제 : **경기도 2030 인구의 쏘카 이용 특성에 따른
군집 별 대여시간 수요예측 분석**  
- 기간 : 2022.05.03(화)  ~ 2022.06.09(목)  
- 방식 : 팀 프로젝트  
- 구성원 

| 이름   |  구성   |                      역할                  |
| :----: | :----: |  :---------------------------------------: | 
| 박경빈   |  팀장   | 프로젝트 총괄, 외부 데이터 수집, EDA, 피처엔지니어링, PPT 작성, 분석보고서 작성, 모델링 구현, 마케팅 포인트 도출   | 
| 이한울  |  팀원   | 외부 데이터 수집, EDA, 피처엔지니어링, PPT 작성, 분석보고서 작성, 논문 탐색, 마케팅 포인트 도출, 포스터 작성    | 
| 김용범  |  팀원   | 외부 데이터 수집, EDA, 피처엔지니어링, 논문 탐색  | 
| 권준우  |  팀원   | 외부 데이터 수집, EDA, 분석 보고서 작성  | 

### 기술 스택 및 사용한 라이브러리
- Google Colaboratory, Pandas, Matplotlib, Seaborn, Scikit-learn,haversine,GCP
- jupyternotebook,datetime,scipy,optuna,catboost,lightgbm,xgboost,statsmodels 

### 문제정의
- 카셰어링은 지역, 이용자 연령 등 다양한 변수로  다른 특성을 보이며 다양한 외부요인에 의해 또다른 특성을 보임

- 경기도를 타겟으로 하여 수요 예측을 진행하기로함  



### 프로젝트 목표
- 군집화된 그룹에서의 차이점이 얼마나 영향을 미치는지 파악 후 비즈니스에 적용 가능한 개선 포인트 도출

- 이용건수가 아닌 실제 매출에 직접적으로 영향을 미치는 **총이용시간**을 **타겟변수로 설정**

![image](https://user-images.githubusercontent.com/59243727/172412508-57db2cdb-5eba-4934-9bc7-a46e2b338ae7.png)



### 프로세스

<img width="3194" alt="Untitled (2)" src="https://user-images.githubusercontent.com/96718939/174756583-afeb3629-ef42-4573-83a1-658c9f907623.png">


## 2. 프로젝트 내용

### 데이터 분석(EDA) 및 전처리
- 매출 지표 피쳐 생성
  ![image](https://user-images.githubusercontent.com/59243727/172420888-de9b1faa-2e18-44ac-bd58-a6a867864e06.png)

- 데이터 전처리 과정 
  - 타겟변수 생성
  - 이상치 제거
  - 기상 데이터는 feature로 채택하지 않음
 
- 군집화 

- 피쳐 엔지니어링 
  ![image](https://user-images.githubusercontent.com/59243727/172421634-6641b01a-6da3-49ee-8fb6-b80384dc0531.png)

  
## 3. Modeling
- 군집화
  - 범주형 변수는 One-hot Encoding 

- Hierarchical Clustering
   ![image](https://user-images.githubusercontent.com/59243727/172515611-9946f3b8-e54b-492f-9652-2abd14fb625a.png)

- Hierarchical Clustering 실루엣 계수 확인
  ![image](https://user-images.githubusercontent.com/59243727/172515678-222069f8-62a9-43f0-89f8-f6d966a70776.png)


- 군집화 K-means
  ![image](https://user-images.githubusercontent.com/59243727/172515339-7b830996-1c49-4205-9bb8-fafc3e6561c5.png)

- 군집화 K-means 실루엣 계수 확인
  ![image](https://user-images.githubusercontent.com/59243727/172515489-98e22694-d99e-49ac-abf5-3d1047446550.png)

  
- Modeling
   
  - OLS 
 
  - Linear Regression
 
  - CATBOOST + OPTUNA

  
- Validation
  - 평가결과(Score)
  
![img3](https://user-images.githubusercontent.com/59243727/172401665-67ae0f76-84d1-4ce9-8574-60d045605f70.png)

- Insight
  -  차량 대여를 시작하는 요일과 시간대에 따라 평균 이용 시간이 달라진다 것을 확인 했습니다.
  -  사회과학에서 통용되는 코헨의 기준 중 medium에 해당하는 0.13을 기준으로 했을 때, 여러 군집의 모델이 유의미한 모델이라고 할 수 있습니다.

  
## 4. 마케팅 포인트 제안
- **통근 수요**
    - 회사 밀집 지역에서 **야근-출근 시간대** 유휴차량 줄이는 전략 ⇒ 쿠폰, 할인 등

- **제조업 중심지**
    - 사업체와의 제휴를 통해 업무 이용 유도(쏘카 비즈니스)
    - 제조업 특성상 자차가 없으면 통근이 어려운 지역에 있으므로 대중교통 환승이 가능한 지역에 통근용 차량 배차
    ![image](https://user-images.githubusercontent.com/59243727/172405718-9052a118-988b-4088-8b00-182e2890aeb1.png)

- **이용 시간 리워드 시스템**
    - 쏘카 이용시간이 늘어날 때마다 게이지가 채워지는 리워드 시스템
    - 건당 총 이용시간을 늘려 매출 증진을 도모
    - 상/하반기 구분
    - 실제 앱에서 구현될 화면 보여주기
    ![image](https://user-images.githubusercontent.com/59243727/172406032-c271a46a-4fdf-484e-abda-fa5c226a4db0.png)


## 5. 프로젝트 회고
- 협업
  - 코로나 19 팬데믹이 내리막세를 보이는 관계로 프로젝트 기간동안 오프라인 진행이 가능했으며, 이에 따라 정기회의 및 상황에 따른 추가회의를 원활히 할 수 있었음   
  - 적시에 멘토링을 진행하여 어려운 상황을 타개하였음
 
- 데이터
  - 본 분석을 위해 제공받았던 데이터 외에 추가적인 데이터가 풍부하게 있었다면 이용 특성에 따른 군집화를 좀 더 세밀하게 진행할 수 있었다고 생감됨
  - 기상, 미세먼지 데이터의 상관관계가 낮게 나와 feature로 채택하지 않음

- 논문
  - 가설 설정, 분석 지역 특성 파악, 마케팅 전략 수립, 모델링을 위해 논문 탐색
