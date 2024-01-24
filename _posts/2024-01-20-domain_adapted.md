---
layout: single
title: "[Paper review] Domain adapted broiler density map estimation using negative-patch data augmentation"
categories: [AI, Paper Review]
tag: []
typora-root-url: ../
use_math: true


---

<br>

## Domain adapted broiler density map estimation using negative-patch data augmentation





### [Abstract]



인구 증가 및 소득 증가의 영향으로 닭고기의 수요와 소비량은 꾸준히 증가함.

생산의 효율성을 위해 자유방목보다 폐쇄형으로 사육이 선호됨.

그에 따라 닭 사육은 높은 밀도로 사육됨.

높은 밀도로 사육됨에 따라, 행동이 제한돼 체온, 스트레스, 공포가 증가.

이에 따른 닭 품질 저하.

따라서 축산업계에서는 동물 복지 등을 통해 축산 품질 향상을 도모함.





해결하기 위한 사육 밀도를 관리하기 위해 사육 환경을 지속적으로 모니터링할 필요가 있음. 같은 수의 육계더라도, 사육환경과 성장 상태에 따라 밀도가 달라질 수 있음.





육계를 자동적으로 관찰하기위해 이전 연구들

1. 사육 방법별 6가지 파라미터를 이용한 육계 행동 평가
2. 사육 밀도에 따른 페킨 오리의 성장 및 활동 모니터링
3. 육계 복지 평가를 돕기 위한 백색 육계의 행동 분류
4. 중심체 분할 기반 동적 모델링을 이용한 체중 예측



그러나 이 연구들은 수만 마리 육계같은 혼잡한 무리의 모니터링에는 문제가 있음

자동으로 관찰하기 위해서는 고밀도 무리를 효과적으로 선별할 수 있는 기술이 필요함

딥러닝을 통해 물체를 자동으로 감지하는 솔류션이 많은 분야에서 적용됨

