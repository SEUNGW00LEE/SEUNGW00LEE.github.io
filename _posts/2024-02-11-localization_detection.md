---
layout: single
title: "[CS231n review] Lecture5 - Localization & Detection"
categories: [AI, Computer Vision, CS231n]
tag: [CS231n, Computer Vision, AI, CNNs]
typora-root-url: ../
use_math: true

---

<br><font color=gray>Stanford CS231n(2017)를 학습하며 정리 및 추가한 내용입니다.</font> <br>

<br>

# Localization & Detection



지금까지 배운 Classification은 아래의 Image를 '고양이'라고 labeling했습니다.

<img src="/images/2024-02-11-localization_detection/image-20240212000008718.png" alt="image-20240212000008718" style="zoom:50%;" />

이 Classification에 localization을 더하면 아래처럼, 고양이가 있는 부분을 박스로 표시할 수 있습니다.

<img src="/images/2024-02-11-localization_detection/image-20240212000117694.png" alt="image-20240212000117694" style="zoom:50%;" />

Object Detection이란 multiple object가 있을 때 여러 object를 찾아내는 것을 말합니다.

<img src="/images/2024-02-11-localization_detection/image-20240212000302931.png" alt="image-20240212000302931" style="zoom:50%;" />

아래의 사진처럼 object를 형상으로 따주는 것을 segementation이라고합니다.

<img src="/images/2024-02-11-localization_detection/image-20240212000403561.png" alt="image-20240212000403561" style="zoom:50%;" />

해당 강의에서는 segementation을 제외한 localization와 segementation에 대해 학습해 볼 것입니다.



Idea 1 : Localization as Regression



