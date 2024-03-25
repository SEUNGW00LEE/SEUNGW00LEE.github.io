---
layout: single
title: "[기계학습의 이해]중고차 가격 예측 및 사이트 추천"
categories: [AI, Machine Learning]
tag: []
typora-root-url: ../
use_math: true



---

<br>

![Used Car Sales: Pre-owned car companies look at upstaging new car sales in  FY21, ET Auto](data:image/jpeg;base64,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)



[기계학습의 이해] 수업에서 **'중고차 가격 예측 및 사이트 추천'**를 진행하게 됐다.



## **수업소개**

**기계학습의이해 [UNDERSTANDING OF MACHINE LEARNING]**

![image-20240325211456870](/images/2024-03-25-car_project/image-20240325211456870.png)



## **프로젝트**



프로젝트는 총 4명으로 진행됐다. 

<img src="/images/2024-03-25-car_project/image-20240325212046781.png" alt="image-20240325212046781" style="zoom:50%;" />

주제부터 탐색하였는데 주제를 고르는 것이 상당히 어려웠다.

이미 있는 데이터(공공데이터 등)으로는 하고싶은 것이 생각이 나지않았다.

그러다 중고차의 수요가 날이 갈수록 커지고 현대차에서도 중고차 시장에 진입했다는 옛 뉴스가 기억이 났다.



## **중고차 가격 예측 및 사이트 추천**



![image-20240325211802489](/images/2024-03-25-car_project/image-20240325211802489.png)

제공되는 데이터는 존재하지않았지만 직접 사이트를 크롤링하여 데이터를 수집할 수 있다고 생각하여 주제를 선정했다.

그러나 중고차 가격이 구체적으로 어떻게 책정되는지는 판매자와 구매자 모두 알기 어렵다.

(중고차딜러의 안 좋은 이미지가 이 결과가 아닐까라는 생각이 든다.)

저희 조의 분석 목적은 국산 중고차의 차량 정보와 보험처리이력 등이 주어졌을 때, 중고차 거래 사이트 중 **어떤 사이트에 판매하면 가장 이득을 볼 수 있을지 계산하여 예측**하는 것으로 구체적인 주제를 선정했다.

예측 모델을 이용하면 중고차 판매자가 어떤 사이트에 판매해야 유리한지 판단할 수 있으며, 그 판매가는 얼마 정도가 될지 예측할 수 있다는 기대효과가 존재한다.

예측 대상이 되는 사이트는 [엔카](http://www.encar.com/dc/dc_carsearchlist.do?carType=kor), [KB차차차](https://www.kbchachacha.com/public/sellme/v2/main.kbc), [보배드림](https://www.bobaedream.co.kr/)으로 총 3개이다. 해당 사이트들을 고른 이유는 타 사이트에 비해 등록대수가 많아 학습시킬 데이터가 충분하기 때문이다.

| **사이트명**        | **전체 등록대수** |
| ------------------- | ----------------- |
| 엔카                | 163,204           |
| KB차차차            | 143,046           |
| 보배드림            | 49,476            |
| K Car               | 9,049             |
| 현대글로비스 오토벨 | 1,227             |



## **2. 데이터 소개**

1. 데이터 출처

   - 웹크롤링을 수행하여 3개 사이트의 국산차 데이터를 수집할 계획이다.
   - 보배드림 사이트 내에서 현재 거래되고 있는 국산차 데이터를 수집하였다.

2. 변수 설정

   - 차량 정보와 옵션을 모두 합치면 80개 이상의 변수를 찾을 수 있다.엔카, KB차차차, 보배드림 3개 사이트에서 공개하는 차량 정보에 차이가 존재한다.
   - 3개 사이트에서 공통적으로 수집할 수 있는 유의미한 변수를 정리하면 아래와 같다.
     - 기본 정보: 가격, 차종, 연식, 배기량, 주행거리, 색상, 변속기, 연료
     - 차량 옵션: 선루프, LED헤드램프, 어댑티드헤드램프, 가죽시트, 열선시트, 통풍시트, 후방센서, 스마트키, 네비게이션
     - 보험처리이력: 전손유무, 소유자 이전 횟수, 침수유무
     - 가격을 **예측변수**로, 이하 변수들을 **설명변수**로 하여 데이터를 수집하였다.
   - 차량 옵션의 유무는 중고차 판매가 변동에 큰 영향을 미치므로 설명변수로 추가했다.
     - 그랜져 기준, 하단 옵션이 추가될 때마다 판매가가 상승하는 것을 볼 수 있다.
     - 차량이 해당 옵션을 갖고 있으면 1, 아니면 0의 값을 갖도록 크롤링 하였다.
   - 보험처리이력은 구매자가 거래 시 많이 참고하는 지표이므로 설명변수로 추가하였다.
     - 차량이 전손유무, 침수유무가 있으면 1, 아니면 0의 값을 갖도록 크롤링 하였습니다.
     - 차량의 소유주 변경 횟수를 크롤링 하였다.

3. 데이터 설명

   - 데이터 크기

     - 1732 rows × 22 columns

   - 예측 변수

     - 중고차 판매가: 실제 구매자와 거래하는 중고차 판매 가격

   - 설명 변수

     💡 **연속형 변수** - 주행거리, 배기량 **범주형 변수** - 위 2개와 가격을 제외한 모든 변수

     - 기본 정보

       - 브랜드: 자동차 제조 회사명

         | GM대우       | KG모빌리티     | 기아       | 대우     |
         | ------------ | -------------- | ---------- | -------- |
         | **르노삼성** | **르노코리아** | **쉐보레** | **쌍용** |
         | **제네시스** | **현대**       |            |          |

       - 차종: 자동차의 모델명

       - 연식: 자동차가 제작된 해

       - 배기량: 엔진이 한 번 돌아갈 때 소비되는 가스의 양, 엔진의 주요 성능지표

       - 주행거리: 실제로 자동차를 운행한 거리

       - 색상: 자동차의 색상

         | 검정색     | 갈색       | 기타       | 노란색     |
         | ---------- | ---------- | ---------- | ---------- |
         | **녹색**   | **분홍색** | **빨간색** | **주황색** |
         | **자주색** | **파란색** | **회색**   | **흰색**   |

       - 변속기: 동력원의 동력을 속도나 환경에 맞추어 필요한 회전력으로 바꾸는 장치

       - 연료: 자동차가 운행될 수 있도록 에너지를 방출하는 물질

         | 가솔린   | 디젤     | LPG                | 가솔린 하이브리드 |
         | -------- | -------- | ------------------ | ----------------- |
         | **전기** | **수소** | **가솔린/LPG겸용** | **기타**          |

     - 차량 옵션

       | 선루프               | LED헤드램프            | 어댑티드헤드램프 | 가죽시트     |
       | -------------------- | ---------------------- | ---------------- | ------------ |
       | **열선시트(앞좌석)** | **통풍시트**           | **후방센서**     | **스마트키** |
       | **네비게이션(순정)** | **네비게이션(비순정)** |                  |              |

     - 보험처리이력

       - 전손유무: 차량의 파손 정도가 매우 심하여 ‘전손처리’된 이력의 유무
       - 소유자 이전 횟수: 차량의 실 소유주가 변경된 횟수
       - 침수유무: 차량이 침수 피해를 입어 파손된 이력의 유무



## **3. 데이터 전처리 과정**

>  💡 전처리 단계: 웹사이트 →  크롤링을 통한 데이터 수집 → 데이터 전처리



<img src="/images/2024-03-25-car_project/image-20240325212331380.png" alt="image-20240325212331380" style="zoom:50%;" />

<img src="/images/2024-03-25-car_project/image-20240325212347281.png" alt="image-20240325212347281" style="zoom:50%;" />



- 예측 변수

  - ‘가격’ 열에서 결측치가 존재하는 행을 제거하였다.
  - ‘가격’ 열에서 ’판매완료’, ’상담’으로 기록된 행을 제거하였다.
  - ‘가격’ 변수는 수치형 변수이므로 숫자형 데이터로 변환하였다.

- 설명 변수

  - ‘연식’ 변수의 서식을 YYYY.MM으로 변환하였다.
  - ‘배기량’ 변수는 수치형 변수이므로 숫자형 데이터로 변환하였다.
  - ‘주행거리’ 변수는 수치형 변수이므로 숫자형 데이터로 변환하였다.
  - ‘색상’ 변수 중 유사한 색끼리는 묶어 주었다.
    - 흰색: 흰색, 진주색, 진주투톤
    - 회색: 회색, 진회색, 은색
    - 파란색: 파란색, 청색, 청옥색, 하늘색, 남색, 은하늘색, 진청색
    - 검정색: 검정색, 검정투톤
    - 노란색: 노란색, 베이지색, 금색, 연금색
    - 자주색: 자주색, 보라색
  - 범주형 변수 중 색상, 변속기, 연료 변수에 레이블 인코딩을 수행하였다.
  - ‘차종’ 열을 첫 공백을 기준으로 ‘브랜드’와 ‘차종’ 열로 분할하였다.

- 결측치 처리

  - 보배드림 사이트에 판매글을 게시한 중고차 딜러가 해당 차량에 옵션이 없을 경우 아예 기재하지 않는 경우가 있기 때문에, 차량 옵션 변수 중 결측치가 존재하면 0으로 대체하였다.

  - 모든 열에 대해 결측치가 없는 것을 확인하였다. (데이터 완결성)

    

- 이상치 확인

  - 아래 변수를 Boxplot으로 시각화한 결과 이상치를 발견하여 수정하였습니다.

    - 가격에 대한 Boxplot<br>

      <img src="/images/2024-03-25-car_project/image-20240325212823496.png" alt="image-20240325212823496" style="zoom:50%;" />

    - 주행거리에 대한 Boxplot<br>

      <img src="/images/2024-03-25-car_project/image-20240325212840612.png" alt="image-20240325212840612" style="zoom:50%;" />

  - **가격 30,000,000만원  →  3,000만원**

    [2021 현대 팰리세이드(19~22년) 3.8 가솔린 2WD 프레스티지 중고차](https://www.bobaedream.co.kr/mycar/mycar_view?no=2221734&gubun=K)

  - **가격 630,000만원  →  630만원**

    [2015 현대 포터2 슈퍼캡 내장탑차  초장축 디럭스 중고차](https://www.bobaedream.co.kr/mycar/mycar_view?no=2222647&gubun=K)

  - **주행거리 2,322,500km  →  232,000km**

    [2010 현대 제네시스 쿠페(08~11년) 3.8 GT RW 중고차](https://www.bobaedream.co.kr/mycar/mycar_view?no=2222198&gubun=K)



## **4. 데이터 시각화**

<img src="/images/2024-03-25-car_project/image-20240325213155510.png" alt="image-20240325213155510" style="zoom:50%;" />

<img src="/images/2024-03-25-car_project/image-20240325213218196.png" alt="image-20240325213218196" style="zoom:50%;" />

<img src="/images/2024-03-25-car_project/image-20240325213325433.png" alt="image-20240325213325433" style="zoom:50%;" />



### **추후 업데이트 예정입니다.**



1. 엔카, KB차차차 웹크롤링을 통한 데이터 수집
2. 기계학습 모델 데이터 학습



---

[코드 저장소](https://github.com/SEUNGW00LEE/ML_Team2)

[회의 기록(노션)](https://galvanized-cacao-0d0.notion.site/929c70c458f84da3b3e5ad8af49f8e84?pvs=4)

