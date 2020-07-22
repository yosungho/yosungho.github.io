---
title: 'OpenCV와 Eigen 어떻게 구분해서 쓸까?'
categories:
  - OpenSource
# tags: 
#     - SLAM
description: >
  OpenCV와 Eigen 어떻게 구분해서 쓸까?
sitemap :
  changefreq : weekly
  priority : 1.0
---

Eigen과 OpenCV 둘다 나름의 행렬 자료형을 가지고 있고 연산이 가능하다.
그래서 생각없이 코딩해서 섞어쓰다보면, 자료형 변환을 '기준 없이' 수시로 해주느라 코드만 복잡/더러워진다.

기본적으로 Eigen이 수치 연산 속도가 OpenCV대비 훨씬 빠르다.
그래서 기본적인 행렬 조작은 기본적으로 Eigen에서 하고, Computer Vision '알고리즘'이 필요할 때 OpenCV를 사용하는게 기본.
그런데 형변환을 오버헤드 없이 편하게 할 수 없을까?

아래 사이트에서 wrapping class를 만들었으니 참고해서 사용하면 된다.
https://computer-vision-talks.com/post/mapping-eigen-to-opencv/


추가로, openCV에서 제공하는 eigen2cv, cv2eigen함수는 다차원 행렬 (BGR이미지)는 지원을 안해서, cv::imread(Path, cv::IMREAD_GRAYSCALE)으로 grayscale의 이미지만 지원한다.
이 때, reshape기능을 사용하면 color도 변환 가능하다. 기본 아이디어는 color를 1차원 배열로 만들고 cv2eigen돌린 이후 다시 color로 변환.
https://stackoverflow.com/questions/54971083/how-to-use-cvmat-and-eigenmatrix-correctly-opencv-eigen