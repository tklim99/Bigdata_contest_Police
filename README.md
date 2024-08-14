# Bigdata_contest_Police

# 지역 치안 안전 데이터 분석 경진대회
2023년 1월 20일부터 2월 15일에 시행한 충남,세종,대전 지역 교통사고 분석 및 예측 부문에 참가한 기록입니다.

대회 측 제공 데이터와 공공데이터를 활용하여 진행하였습니다.


https://www.bigdata-policing.kr/board/b_contest/view?idx=167&category=


# 지역 치안 안전 데이터 분석 경진대회
충남,세종,대전 지역 교통사고 분석 및 예측 

<br/>

## 1. 배경 & 목적

- 우리가 길을 걷거나, 운전할 때 교통사고가 발생하는 것을 종종 확인 할 수 있습니다. 교통사고는 그만큼 우리 주변에서 흔하게 일어나는 사고이며 목숨을 잃을 정도의 위험성을 가지고 있습니다. 또한 활용한 데이터의 3,849,381건 중 교통사고는 264,448건으로 전체 14.5% 가량 비중을 차지고 있으며, 적게 일어나는 사고가 아님을 알 수 있습니다. 
- 교통사고의 원인은 안전운전 불이행, 중앙선침범, 신호위반 등의 원인이 존재하는데 이전 교통사고의 데이터를 통해 교통사고가 자주 발생하는 구역에는 어떠한 원인이 존재하는지 분석할 필요가 있습니다.

<br/>

## 2. 주최/주관 & 팀원

- 주최/주관: 경찰대학교 치안정책연구소
- 팀원: 이시현, 이지훈, 임태경

<br/>

## 3. 프로젝트 기간

- 2023.01. ~ 2023.02. (3주)

<br/>

## 4. 프로젝트 소개

<img src='https://user-images.githubusercontent.com/75362328/212527918-e77fcc5e-2a2a-4d32-9c66-5ce9ad267a48.png' width='100%' height='80%'>

&nbsp;&nbsp;&nbsp;&nbsp; 길거리, 여행지, 공공장소와 같은 사람이 많은 장소에서 찍은 사진은 초상권 문제로 다양한 처리를 해주어야 한다. 포토샵을 통한 자르기, 모자이크, 블러 처리는 자연스럽지 못한 단점이 존재하기 때문에 딥러닝을 통해 ‘**배경에 있는 사람들을 같은 성별, 비슷한 나이대의 얼굴을 만들어서 바꾸어주는 서비스**’를 제안하였다.

&nbsp;&nbsp;&nbsp;&nbsp; Face Detection 분야의 Benchmark인 WiderFace, 아시아인 얼굴 데이터인 AFAD, AAFD 데이터 셋을 사용해 얼굴을 탐지해 주고자 하였다. 그 과정에서 얼굴과 나이가 모두 라벨링 되어 있는 데이터 셋이 없었기 때문에 **Gender, Age Pretrained Model을 사용**해서 WiderFace Annotation에 **Pseudo Label을 추가해 새로운 학습 데이터**를 만들어냈다. 

&nbsp;&nbsp;&nbsp;&nbsp; 얼굴 탐지에 있어서는 당시 **SOTA 모델인 RetinaFace** 구조에 **Gender Classification Head, Classification Head를 추가**하여 사용했다. 그렇게 함으로써 Backbone은 더 Robust 한 Feature를 추출하고 별도의 추가 Network 없이 Face Detection과 Gender/Age Classification을 end-to-end로 수행하게 하였다. 

&nbsp;&nbsp;&nbsp;&nbsp; 탐지된 성별과 나이대에 맞게 얼굴을 생성하는 과정에서는 **StyleGAN2-Ada 모델을 사용**하였다. StyleGAN은 Latent Space에서 선형적인 변환이 일어났을 때 Non-Linear Mapping을 사용하여 Disentanglement 하게 된다는 장점이 있어, 주어진 얼굴과 비슷한 속성을 가진 얼굴을 생성해야 하는 우리 프로젝트에서 적합하다고 판단하였다. 

&nbsp;&nbsp;&nbsp;&nbsp; 마지막으로 생성된 얼굴과 기존 얼굴을 바꾸어주는 **Face Swap 과정에서는 Simswap 모델을 사용**해 주었다. SimSwap은 Identity Extractor를 별도로 학습시켜 임의의 Source Image가 들어와도 Id Vector를 잘 추출해 합성된 Image와 Source Image가 닮도록 강제할 수 있다. 

&nbsp;&nbsp;&nbsp;&nbsp; 결과적으로 **Face Detection에서는 RetinaFace, Face Generation에서는 StyleGAN2-Ada, Face Swap에서는 SimSwap 모델**을 사용하였으며 진행 과정은 **웹 데모**를 만들어서 보여주었다. 이를 통해 제약이 없는 사진 촬영, 빠르고 자연스러운 보정, 초상권 침해 방지 등의 효과를 기대할 수 있을 것이다.

<br/>

## 5. 프로젝트 담당 역할

- StyleGAN2-Ada를 사용한 모델 학습 및 최적화
    - StyleGAN, StyleGAN2 구현 및 성능 비교
- DeepFaceLab, SimSwap, HifiFace, SmoothSwap 등 Face Synthesis, Face Swap 관련 모델 Inference 코드 제작

<br/>

