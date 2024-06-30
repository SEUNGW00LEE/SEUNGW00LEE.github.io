---
layout: single
title: "2. Transformer"
categories: [AI, Paper Review]
tag: []
typora-root-url: ../
use_math: true




---

## Transformer



Transformer은 Attention을 이용해 한번의 하나의 토큰 씩 하는 것이 아닌 한꺼번에 정보를 처리한다.

<img src="/images/2024-06-30-Transformer/image-20240630192102249.png" alt="image-20240630192102249" style="zoom:25%;" />



Encoding component : Encoding의 스택

Decoding component : Decoding의 스택(Encodig 스택 수와 같다.)

Encoding block vs Decoding block = Unmasked vs Masked

<img src="/images/2024-06-30-Transformer/image-20240630192156060.png" alt="image-20240630192156060" style="zoom:25%;" />



Transformer의 Encoder의 특징은 각각의 Encoder은 전부 동일한 구조를 가진다.

다만, 가중치를 공유하는 것은 아니다.

<img src="/images/2024-06-30-Transformer/image-20240630192713643.png" alt="image-20240630192713643" style="zoom:25%;" />

Encoder은Self Attention과 Feed Forward Neural Network로 구성되어 있다.

Decoder은 Encoder-Decoder Attention 레이어가 추가되어 있다.

<img src="/images/2024-06-30-Transformer/image-20240630193046123.png" alt="image-20240630193046123" style="zoom:25%;" />

Encoder Block이 왼쪽, Decoder Block이 오른쪽이다.

Self Attention은 Single head attention이 아닌 Multi head attention이다.



Input Embedding : bottom-most encoder, 제일 첫번째 인코더의 input으로만 사용.

embedding algorithm을 통해 input embedding 수행(512 차원)

그 위의 encoder들은 바로 아래에 있는 encoder의 output을 input으로 받는다.(사이즈는 유지된다.)

<img src="/images/2024-06-30-Transformer/image-20240630194154205.png" alt="image-20240630194154205" style="zoom:50%;" />

Positional Encoding : Input Embedding에 더하여(512차원의 벡터를 만듬/concat처럼 1024 차원이 되지 않음) 각각의 단어의 순서를 고려한다.

Positional Encoding을 왜하는가.

- 트랜스포머의 한번에 모든 sequence를 받기 때문에, 단어가 가진 위치정보를 고려하지 못하는 단점을 보완하는 장치이다.

$$
PE_{(pos,2i)} = sin(pos/10000^{2i/d_{model}})\\
PE_{(pos,2i+1)} = cos(pos/10000^{2i/d_{model}})
$$

1. 해당하는 encoding의 size는 동일해야한다.

2. 총 100개의 토큰들에 대해 512개 차원의 positional encoding을 해보면, L2 norm의 distribution은 평균 256, 표준편차 1.35가 나온다.

   -> 위치 정보를 반영한다.



Imbedding된 단어들은 이제 Encoder의 2개의 Layer를 지나간다.

<img src="/images/2024-06-30-Transformer/image-20240630202013414.png" alt="image-20240630202013414" style="zoom:50%;" />

위의 4차원 벡터들이 self-attention layer을 지나면 4차원의 벡터가 들어가는데, self-attention layer은 dependency가 있고, Feed-Forward는 dependency가 없다.













