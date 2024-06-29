---
layout: single
title: "Attention, Transformer에 대하여"
categories: [AI, Paper Review]
tag: []
typora-root-url: ../
use_math: true



---

**<img src="/images/2024-06-28-Atttention/image-20240628025940178.png" alt="image-20240628025940178"/>**

> ***Attention is what I want***



## RNN



**Transformer를 알기 전, RNN부터 알아야한다.**

**"RNN은 연속적인(시계열) 데이터에 잘 동작하는 네트워크 구조이다.""**

**CNN은 이미지 구역별로 같은 weight를 공유한다면,**

**RNN은 시간 별로 같은 weight를 공유한다.**

**즉, 과거와 현재는 같은 weight를 공유한다.**

> First Order system : 현재 시간의 상태가 이전 시간의 상태와 관련이 있다고 가정



**Word embedding : 단어를 숫자로 바꾸자**

**저는 학생 입니다.**

-> **[1,0,0], [0,1,0], [0,0,1]**

-> **X1, X2, X3**

**이를 Neural Network에 순차적으로 넣어보자 (RNN의 접근법)**

**RNN의 동작 방식 (Recurrent Neural Network)**

**<img src="/images/2024-06-28-Atttention/image-20240628181213342.png" alt="image-20240628181213342" style="zoom:50%;" />**

### **RNN의 수식**

- **화살표를 지날 때 FC 통과한다고 생각하면 된다.**

**<img src="/images/2024-06-28-Atttention/image-20240628181416186.png" alt="image-20240628181416186" style="zoom:50%;" />**

**$W_x, W_h, W_y, b, b_y$는 시간에 따라 다르지 않다.**

**<img src="/images/2024-06-28-Atttention/image-20240628181909067.png" alt="image-20240628181909067" style="zoom:50%;" />**

**이와 같이 $h$는 이전의 정보를 가진다.**

**<img src="/images/2024-06-28-Atttention/image-20240628182054796.png" alt="image-20240628182054796" style="zoom:50%;" />**

**** 

**다음에 어떤 알파벳(one-hot encoded)이 나와야 할까? => 다중 분류네!**

**<img src="/images/2024-06-28-Atttention/image-20240628183547905.png" alt="image-20240628183547905" style="zoom:50%;" />**



**=> *ŷ* 을 softmax 통과시켜서 cross-entropy 계산**
**=> ELLO 네개 글자에 대해 cross-entropy 더해주면 되겠다**

**근데 O가 나오게 하기 위해 H가 gradient 에 미치는 영향력?**

**멀수록 잊혀진다!(back propagation) 또, 갈수록 흐려진다!(forward propagation) <- tanh 때문**

**이 둘 모두 RNN의 구조적 한계이다.**

 ## **RNN의 유형**



**<img src="/images/2024-06-28-Atttention/image-20240629233135329.png" alt="image-20240629233135329" style="zoom:50%;" />**

## **seq2seq**

- **각각의 cell은 plain RNN에서 발전된 형태인 LSTM이나 GRU를 주로 사용한다.**
- **encoder, decoder 두 파트로 구성된다.**
- **encoder의 마지막 h를 decoder의 첫 h로 사용한다.**
- **학습 시엔 teacher forcing, test 땐 출력 나온 것을 입력으로 사용한다.**

**<img src="/images/2024-06-28-Atttention/image-20240629233216235.png" alt="image-20240629233216235" style="zoom:50%;" />**

### **seq2seq의 문제점**

- **멀수록 잊혀진다는 문제를 해결하지 못했다.**
- **context vector에 마지막 단어의 정보가 가장 많이 담긴다.**
  - **즉 마지막 단어를 가장 열심히 본다.**



- **plain RNN이 번역기로 잘 안쓰이는 이유**
  - **무조건 나중의 정보가 중요하게 처리하기 때문**
- **LSTM, GRU가 있다지만 근본적인 해결책이 될 수 없다.**
- **이를 해결한 것이 트랜스포머**
  - **Attention is all you need**
  - **핵심 아이디어 : 무엇을 중요하게 봐야하는지 학습하자**
- **발전 방향 : RNN -> RNN + Attention -> 트랜스포머**
  - **RNN + Attention의 구조적인 한계 : 흐려지는 정보에 Attention한다.**
  - **EX ) '쓰다'라는 단어의 뜻을 이해할려면 멀리 있는 선행 단어를 봐야 알 수 있는데, 흐려진채로 들어가니 의미를 잘 못 담는 문제 발생 -> bidirection RNN을 써야한다.**
- **트랜스포머는 attention을 적극활용, self-attention을 통해 RNN (구조)을 완전히 버렸다.**
  - **Decoder가 마지막 단어만 열심히 보는 문제 (갈수록 흐려진다.) <- attention으로 해결**
  - **RNN의 vanishing gradient (멀수록 잊혀진다) <- self-attention으로 해결**
  - **흐려지는 정보에 attention**





**Attention 시점마다 context vector가 변한다.**

**Attention의 방식은 dot product이다.**

**hidden state 간의 weight sum.**

 **벡터에 행렬을 곱하는 것은 곧 선형변환.**





