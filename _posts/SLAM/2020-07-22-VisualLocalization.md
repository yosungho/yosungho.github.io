---
title: 'Visual Localization이 실패하는 Case 정리'
<!-- categories:
  - SLAM -->
tags:
  - SLAM
description: >
  Visual Localization에서 해결해야 할 문제들은 어떤게 있을까?
sitemap :
  changefreq : weekly
  priority : 1.0
---

1. Strong illumination changes
[Toft, Stenborg, Hammarstrand, Brynte, Pollefeys, Sattler, Kahl,Semantic Match Consistency for Long-Term Visual Localization, ECCV 2018]
[Zhou, Sattler, Jacobs, Evaluating Local Features for Day-Night Matching. ECCV Workshops 2016]

2. Weakly Textured & Repetitive Scenes
[Taira, Okutomi, Sattler, Cimpoi, Pollefeys, Sivic, Pajdla, Torii, InLoc: Indoor Visual Localization with Dense Matching and View Synthesis. CVPR 2018]

3. Global Repetitions / Similarities
4. Strong Viewpoint Changes
[Taira, Okutomi, Sattler, Cimpoi, Pollefeys, Sivic, Pajdla, Torii, InLoc: Indoor Visual Localization with Dense Matching and View Synthesis. CVPR 2018]
[Schönberger, Pollefeys, Geiger, Sattler, Semantic Visual Localization, CVPR 2018]

5. Training data에 의존적 (e.g. LIFT가 rotation에 취약. 왜냐면 대부분 up-right 이미지에서 훈련되었기 때문)
6. Pose Regression도 CNN으로 잘 안됨. (e.g. PoseNet)
7. Many-to-Many Matches: 매칭 후보군이 많을 때 어떻게 할건데?
[1] “Efficient & Effective Prioritized Matching for Large-Scale Image-Based Localization”, Sattler et al., PAMI 2017
[2] “Learning Less is More - 6D Camera Localization via 3D Surface Regression”, Brachmann and Rother, CVPR’18
8. Large-Scale Localization
[“City-scale landmark identification on mobile devices”, Chen et al., in CVPR 2011]

그래서, 기술적 용어로 해결책을 생각해보자면...
1. Data Association을 잘하자
2. Pose Verification을 잘하자

Semantic Match Consistency
[Toft,Stenborg, Hammarstrand, Brynte, Pollefeys, Sattler, Kahl, Semantic Match Consistency for Long-Term Visual Localization, ECCV 2018]
Idea: Generate pose hypotheses per 2D-3D match, verify poses using all (visible) points and semantics
Schönberger, Pollefeys, Geiger, Sattler, Semantic Visual Localization, CVPR 2018]
