---
title: 'Neural Net을 훈련시킬 때 하는 흔한 실수들'
categories:
  - DL
# tags:
#     - SLAM
description: >
  common mistakes
sitemap :
  changefreq : weekly
  priority : 1.0
published: true
---
## Neural Net을 훈련시킬 때 하는 흔한 실수들
- batch_size를 1로하여 overfit을 해보지 않았다
- train / eval 모드를 toggle하지 않았다.
- .backward() 전에 .zero_grad()를 하지 않았다.
- loss값에 softmax의 출력을 그대로 넣었다.
- BatchNorm을 사용할 때 Linear/Conv2d에 bias=False를 하지 않았다.
- output layer에서 bias=True를 하지 않았다.
- .view()와 .permute()를 같은 것으로 생각한다.
