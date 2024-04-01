---
layout: single
title: "[R-Library]Statgarten-datatoys"
categories: [Data Science]
tag: [R]
typora-root-url: ../
use_math: true




---

<br>

# [R-Library]Statgarten-datatoys

<img src="https://github.com/SEUNGW00LEE/datatoys/raw/main/man/figures/logo.png" alt="img" style="zoom:50%;" />



데이터 사이언스를 처음 접하는 입문자를 위해 공공데이터 등을 통해 데이터를 가공하여 데이터셋을 제공하는 R 라이브러리인 **'datatoys'**를 제작하는 프로젝트에 참여했다. 



나는 

**(1)** 공공데이터포탈, 통계청, 서울열린데이터광장 등등에서 데이터 분석 하기 좋은 데이터를 선별한 후, **(2)** 데이터셋을 입문자들도 손쉽게 분석할 수 있도록 전처리를 일정 부분 진행하였다.

> 데이터 전처리에는
>
> (i) column 이름을 간결하게 변경하고
>
> (ii) 필요없는 column을 제거하고
>
> (iii) 결측치를 채워주거나, 결측치가 있는 행을 제거하고
>
> (iv)  여러 성질이 하나의 column에 합쳐진 column을 분리하고
>
> (v) row마다 다른 단위인 데이터들을 같은 단위로 통일시켜주는 등등의 과정이 포함됐다.

**(3)** 해당 데이터셋을 R 언어를 활용하는 예시코드를 제시했다.



**(예시)**

---

> datatoys - seoulCulture

<img src="/images/2024-04-01-statgarten_datatoys/image-20240401152643628.png" alt="image-20240401152643628" style="zoom: 33%;" />

위 스크린샷은 leaflet 라이브러리를 함께 활용하여 **datatoys**의 **seoulCulture**을 지도에 나타낸 예시코드이다.

> datatoys-imdependenceMov

<img src="/images/2024-04-01-statgarten_datatoys/image-20240401155329098.png" alt="image-20240401155329098" style="zoom:50%;" />

위 사진은 3.1절을 맞이하여, 독립운동관련 문서 데이터를 통하여, **datatoys**의 **impedenceMov**를 워드클라우드를 생성한 예시코드이다. 예시코드에서 보는 것과 같이, '하여', '하고', '것입니다','것이다', '우리' 와 같은 단어가 반복적으로 나타나는 것을 관찰 할 수 있다.

---

위는 간략한 코드로 시각화 및 워드클라우드를 진행한 예시코드들의 예시이다.

---

또한 국가통계포털의 [통계청,「인구총조사」, 2021, 2023.01.16, 인구,가구 및 주택 – 읍면동(연도 끝자리 0,5), 시군구(그 외 연도)](https://kosis.kr/statHtml/statHtml.do?orgId=101&tblId=DT_1IN1503&conn_path=I2) 등의 데이터를 활용해 데이터셋을 만들었다.

[ggplot2](http://aispiration.com/R-ecology-lesson/kr/05-visualization-ggplot2.html)과 [gganimal](https://gganimate.com/)를 통해 데이터 시각화도 진행했다.

모든 연도를 합치고, 평균 등의 데이터를 삭제하여 활용하기 좋은 데이터셋을 만들었다.

<br>

> datatoys - population

**데이터 전처리**

- 데이터를 모두 dataframe으로 저장한다.
- column '행정구역별' 에 value를 채워준다.
- df_4의 column 값만 달라서 df_1,df_2,df_3과 동일하게 변경한다.
- df_4 data 값 변경한다.(이전 data : 행정구역별(읍면동) 변경 후 data : 행정구역별)
- 4개로 나뉜 dataframe을 하나로 결합한다.
- 이 데이터의 column 값을 명시적으로 바꿔주고, 첫번째 행을 삭제한다.(column과 내용 중복).
- 이 데이터를 R dataframe으로 저장한다.

**데이터 시각화**

> **ggplot2, gganimate를 통해 Data Visualization**

- 각 연도, 행정구역별 총인구 히스토그램 (ggplot) -> 연도별 행정구역 총인구 히스토그램 애니메이션(gganimate)

![total_population](https://user-images.githubusercontent.com/86904141/214488927-89211470-8c21-4421-bc45-7fb22f12e4f8.gif)

- 위의 그래프를 coord_flip을 통해 전환하고, 년도별 더 많은 인구를 가진 지역이 위로 올라오도록 설정 & 가독성을 높이기위해 지역별로 묶어 비슷한 색깔을 지정

![total_population_color_ver](https://user-images.githubusercontent.com/86904141/214770781-d29bea28-b888-4f80-926c-2b7c5a8dc95d.gif)

- 서울시 각 연도별, 연령대별 인구 변화 히스토그램 (ggplot) -> 연도별 서울시 연령대별 히스토그램 애니메이션 (gganimate)

![seoul_populationpyramid](https://user-images.githubusercontent.com/86904141/215535686-811b6ce2-05b9-42e4-9fb0-2058ec50a84c.gif)





---

이러한 라이브러리 및 예시코드는 [datatoys 웹사이트](https://www.statgarten.com/datatoys/index.html)에 배포했다.

관련 코드는 [statgarten GitHub](https://github.com/statgarten/datatoys)에 게시되어있다.

---

아래는 datatoys에 대한 간략한 설명 및 라이브러리에 수록된 데이터 셋이다.



## **Overview**

Let’s play with data! We prepared toy data for data newbies. This package contains some datasets provided by the [Public Data Portal](https://data.go.kr/) in Republic of Korea. It makes you can play with data for fun like children! Install the package, and **start your adventure!**



 여기 시작하는 사람들을 위한 재밌는 데이터가 있습니다. 이 패키지에는 공공데이터포털, 통계청 등에서 제공하는 재밌는 데이터셋이 포함되어 있습니다. 우리 삶에 닿아 있는 데이터를 다루다 보면 데이터 분석에 재미를 느끼게 될거에요. 패키지를 설치하고 모험을 시작해 보세요!



## **Installation**

```R
# install.packages("remotes")
# Due to the large size of the file, you may get a download error. If so, set the options below.
# options(timeout = 9999999)
remotes::install_github("statgarten/datatoys")
```



## **A list of datasets**

| 번호 | 데이터셋              | 출처                   | 설명                                             |
| ---- | --------------------- | ---------------------- | ------------------------------------------------ |
| 1    | accident              | 도로교통공단           | 사망교통사고 정보                                |
| 2    | accom                 | 행정안전부             | 관광숙박업 정보                                  |
| 3    | airport               | 국토교통부             | 전세계 공항정보                                  |
| 4    | animalHospital        | 행정안전부             | 동물병원 정보                                    |
| 5    | aniPollution          | 행정안전부             | 가축분뇨수집운반업, 배출시설관리업 정보          |
| 6    | artmuseum (Artmuseum) | 서울특별시             | 서울시립미술관 소장품 정보                       |
| 7    | bathHouse             | 행정안전부             | 목욕장업 정보                                    |
| 8    | bike                  | 서울특별시             | 자전거편의시설                                   |
| 9    | birthRate             | 통계청                 | 시도/인구동태건수 및 동태율(출생,사망,혼인,이혼) |
| 10   | bloodTest             | 국민건강보험공단       | 2014-15 혈액검사 데이터                          |
| 11   | budget2023            | 기획재정부             | 연도별 세출 및 지출 예산현황                     |
| 12   | busStation            | 국토교통부             | 전국 버스 정류장 위치정보                        |
| 13   | busyMetro             | 서울교통공사           | 지하철혼잡도정보                                 |
| 14   | carInspection         | 한국교통안전공단       | 자동차검사소 정보                                |
| 15   | cheerUp               | 서울특별시             | 사회적 약자를 위한 위로의 글                     |
| 16   | childAbuse            | 보건복지부             | 아동학대 신고정보                                |
| 17   | cinema                | 서울특별시             | 영화관상영관인허가정보                           |
| 18   | coolCenter            | 서울특별시             | 무더위쉼터 현황                                  |
| 19   | crime                 | 경찰청                 | 범죄 발생 지역별 통계                            |
| 20   | crimePlace            | 경찰청                 | 범죄 발생 장소별 통계                            |
| 21   | departure             | 통계청                 | 내국인 출국 연령별                               |
| 22   | drunkdrive            | 경찰청                 | 음주운전 적발 기록 현황                          |
| 23   | earthShelter          | 서울특별시             | 지진실내구호소 현황                              |
| 24   | economyPeople         | 통계청                 | 경제활동인구조사                                 |
| 25   | election2020          | 중앙선거관리위원회     | 국회의원선거 개표결과 정보                       |
| 26   | elevator              | 한국승강기안전공단     | 국내 승강기 보유 현황                            |
| 27   | entrance              | 통계청                 | 외래객 입국-연령별/국적별                        |
| 28   | farmGIS               | 행전안전부             | 가축사육업 로컬데이터                            |
| 29   | fire                  | 소방청                 | 화재통계                                         |
| 30   | fireStation           | 소방청                 | 전국 소방서 정보                                 |
| 31   | foodBank              | 한국사회복지협의회     | 2021 전국푸드뱅크 기부자 통계                    |
| 32   | foodNutrients         | 식품의약품안전처       | 식품영양성분 데이터베이스                        |
| 33   | gasStation            | 산업통상자원부         | 전국 주유소 등록현황                             |
| 34   | globalBusiness        | 대한무역투자진흥공사   | 해외진출기업 정보                                |
| 35   | gyeonggiER            | 경기도                 | 응급의료기관 및 응급의료지원센터 현황            |
| 36   | hatching              | 행정안전부             | 부화업 정보                                      |
| 37   | hospitalInfo          | 건강보험심사평가원     | 병의원 기본정보                                  |
| 38   | housingPrice          | 국토교통부             | 2021 공동주택 공시가격 정보                      |
| 39   | iceMarket             | 행정안전부             | 식용얼음판매업 정보                              |
| 40   | imdependenceMov       | 공공데이터포털         | 독립운동정보 원문정보                            |
| 41   | jobMating             | 행정안전부             | 직업소개소 정보                                  |
| 42   | karaoke               | 행정안전부             | 단란주점 영업 정보                               |
| 43   | Kcalendar             | 한국천문연구원         | 특일 정보                                        |
| 44   | legalDong             | 국토교통부             | 법정동 정보                                      |
| 45   | liquor                | 보건복지부             | 주류관련 통계                                    |
| 46   | medicalCheckup        | 국민건강보험           | 일반건강검진결과                                 |
| 47   | medicine              | 건강보험심사평가원     | 의약품 주성분 정보                               |
| 48   | nationalPension       | 국민연금공단           | 국민연금사업장 정보                              |
| 49   | necessariesPrice      | 한국소비자원           | 생필품가격 정보                                  |
| 50   | odaIndex              | 한국국제협력단         | 협력국 개발지표 및 ODA 지원 실적                 |
| 51   | odaKR                 | 한국국제협력단         | 소득수준별 ODA 실적통계                          |
| 52   | odaNews               | 한국국제협력단         | 국가별 개발협력동향정보                          |
| 53   | olleWheelchair        | 제주데이터허브         | 무장애여행정보 제주올레길코스                    |
| 54   | openData              | 공공데이터활용지원센터 | 공공데이터포털 목록개방현황                      |
| 55   | optician              | 행정안전부             | 안경업 정보                                      |
| 56   | pcRoom                | 행정안전부             | 인터넷컴퓨터게임시설제공업 정보                  |
| 57   | petNames              | 마포구                 | 반려동물 이름 통계                               |
| 58   | pharmacyInfo          | 건강보험심사평가원     | 약국 기본정보                                    |
| 59   | policeBox             | 경찰청                 | 전국치안센터주소현황                             |
| 60   | pollution             | 국립환경과학원         | 축산오염원조사정보                               |
| 61   | population            | 통계청                 | 인구총조사                                       |
| 62   | postnatal             | 행정안전부             | 산후조리업 정보                                  |
| 63   | postOffice            | 서울특별시             | 우체국 정보                                      |
| 64   | pwd                   | 통계청                 | 장애인현황                                       |
| 65   | restaurant            | 경기도                 | 맛집 정보                                        |
| 66   | scholarship           | 한국장학재단           | 2020년도 장학금 수혜현황                         |
| 67   | seoulCarpark          | 서울특별시             | 공영주차장 안내 정보                             |
| 68   | seoulCCTV             | 서울특별시             | 안심이 CCTV 연계 현황                            |
| 69   | seoulCivic            | 서울특별시             | 2022년 서울 시민생활 데이터                      |
| 70   | seoulCulture          | 서울특별시             | 문화공간정보                                     |
| 71   | seoulER               | 서울특별시             | 응급실 위치 정보                                 |
| 72   | seoulFestival         | 서울특별시             | 문화행사 정보                                    |
| 73   | seoulGraute           | 서울특별시             | 대학원 통계                                      |
| 74   | seoulLibrary          | 서울특별시             | 공공도서관 현황정보                              |
| 75   | seoulRestroom         | 서울특별시             | 공중화장실 위치정보                              |
| 76   | seoulStatue           | 서울특별시             | 동상 현황                                        |
| 77   | singingRoom           | 행정안전부             | 노래연습장업 정보                                |
| 78   | socialCenter          | 서울특별시             | 사회복지시설 정보                                |
| 79   | tuition               | 한국장학재단           | 장학금 정보                                      |
| 80   | warmingCenter         | 서울특별시             | 한파쉼터현황                                     |
| 81   | weather2020           | 농림축산식품부         | 농업 종관기상 데이터                             |