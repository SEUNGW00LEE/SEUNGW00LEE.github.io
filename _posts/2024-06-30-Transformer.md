---
layout: single
title: "2.Transformer"
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



<img src="/images/2024-06-30-Transformer/image-20240630213906963.png" alt="image-20240630213906963" style="zoom:50%;" />



첫번째 encoder의 출력값인 r1과 r2는 두번째 encoder에 input으로 사용된다.



## Self-Attention

3가지의 벡터가 필요하다.

<img src="/images/2024-06-30-Transformer/image-20240630231504458.png" alt="image-20240630231504458" style="zoom:50%;" />

- Query : 현재 보고 있는 단어의 representation, 다른 단어들을 score하기 위한 기준
- Key : label, relevant word를 찾을 때 참고할 수 있는 폴더와 같은 역할
- Value : 실제 값



<img src="/images/2024-06-30-Transformer/image-20240630231714714.png" alt="image-20240630231714714" style="zoom:50%;" />



**Step 1**

$X_1$(1x4)과 $W^Q$(4x3)와 내적하여 $q_1$(1x3) ... 로 Queries, Keys, Values를 생성한다.

일반적으로 input dimension보다는 Queries, Keys, Values의 dimension을 적게잡는다.

<img src="/images/2024-06-30-Transformer/image-20240630232044902.png" alt="image-20240630232044902" style="zoom:50%;" />

**Step 2**

현재 보고 있는 토큰의 Query($q_1$)와 나머지 key value($k_1, k_2$)를 곱해준다.

<img src="/images/2024-06-30-Transformer/image-20240630232208475.png" alt="image-20240630232208475" style="zoom:50%;" />

**Step 3**

$\sqrt{d_k}$를 Score에 나눠준다.

**Step 4**

이 값을 Softmax를 처리한다.

해당 값은 현재 position의 단어가, 얼마나 중요한 역할을 하는가에 대한 지표

<img src="/images/2024-06-30-Transformer/image-20240630232448126.png" alt="image-20240630232448126" style="zoom:50%;" />

**Step 5**

파랑색의 $v_1$은 원래의 $v_1$에 softmax를 곱한 값이고, 

파랑색의 $v_2$은 원래의 $v_2$에 softmax를 곱한 값이다.

**Step 6**

z1 은 $v_1$과 $v_2$를 더한 값(가중 합이 된)이다.

이 값이 self attention의 output이다.



이를 Matrix calculation으로 보면

<img src="/images/2024-06-30-Transformer/image-20240630232834715.png" alt="image-20240630232834715" style="zoom:50%;" />

<img src="/images/2024-06-30-Transformer/image-20240630232842185.png" alt="image-20240630232842185" style="zoom:50%;" />











