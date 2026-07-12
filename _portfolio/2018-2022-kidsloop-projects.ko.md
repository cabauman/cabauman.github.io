---
title: "KidsLoop 프로젝트"
excerpt: "2018-2022: 교육 기술 회사"
project_type: Professional
classes: wide
date: 2018-11-01
lang: ko
permalink: /portfolio/2018-2022-kidsloop-projects/
header:
  teaser: /assets/images/kidsloop/kidsloop-logo.png
sidebar:
  - image: /assets/images/kidsloop/kidsloop-logo.png
    text: "<p><b>2018년 11월 - 2022년 7월</b></p><p><b>미드/시니어 소프트웨어 엔지니어</b></p><p><b>교육 기술</b> - 학부모, 교사, 아동 대상</p>"
gallery:
  - url: /assets/images/kidsloop/esl-dashboard-summary.png
    image_path: assets/images/kidsloop/esl-dashboard-summary.png
  - url: /assets/images/kidsloop/esl-dashboard-reading-analysis.png
    image_path: assets/images/kidsloop/esl-dashboard-reading-analysis.png
  - url: /assets/images/kidsloop/esl-dashboard-writing-analysis.png
    image_path: assets/images/kidsloop/esl-dashboard-writing-analysis.png
  - url: /assets/images/kidsloop/esl-dashboard-listening-analysis.png
    image_path: assets/images/kidsloop/esl-dashboard-listening-analysis.png
  - url: /assets/images/kidsloop/esl-dashboard-speaking-analysis.png
    image_path: assets/images/kidsloop/esl-dashboard-speaking-analysis.png
---

## KidsLoop V1

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/kidsloop/kidsloop-app.png" class="align-right"/>

**기간:** 2018년 11월 - 2019년 9월<br />
**플랫폼:** Android & iOS<br />
**역할:** Unity 엔지니어<br />
**엔지니어 구성:** 백엔드 2, 프론트엔드 2<br />
**설명:** 학부모와 교사를 위한 UI 애플리케이션을 처음부터 개발

**주요 기여:**
- 인증/인가
- 가상 리스트 뷰
- 오프라인 모드 및 재접속 시 동기화
- 비동기 파일 로딩 및 API 호출 + 로딩 인디케이터

## Badanamu 앱

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/kidsloop/badanamu-game.png" style="width: 40%" class="align-right"/>

**기간:** 2019년 9월 - 2020년 1월<br />
**플랫폼:** Android & iOS<br />
**역할:** Unity 엔지니어<br />
**설명:** 오랜 기간 Google Play와 Apple Store에 서비스된 아동 학습 앱 제품군

**주요 기여:**
- 인앱 결제
- Unity 버전 업그레이드
- 분석 도구(analytics) 연동
- 버그 수정

## ESL 대시보드

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/kidsloop/esl-dashboard-progress.png" style="width: 40%" class="align-right"/>

**기간:** 2020년 1월 - 2020년 7월<br />
**플랫폼:** Android & iOS<br />
**역할:** Unity 엔지니어<br />
**설명:** Badanamu ESL 학습 앱에서 사용하는 라이브러리. 읽기, 쓰기, 듣기, 말하기 등 학습 통계를 대시보드 형태로 제공했습니다. Unity 개발자 2명, 백엔드 개발자 몇 명과 함께 작업했습니다.

**주요 기여:**
- 사진 촬영/갤러리 선택/이미지 리사이즈·압축을 위한 Android/iOS 네이티브 미디어 플러그인 개발
- Amazon Transcribe 기반 음성 인식 라이브러리 개발 (프론트엔드/백엔드 모두 .NET으로 구현 후 AWS Docker 컨테이너로 배포)
- 비동기 파일 로딩 및 API 호출 + 로딩 인디케이터
- 썸네일 점진 로딩

{% include gallery %}

## KidsLoop V2

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/kidsloop/online-learning-platform.png" style="width: 40%" class="align-right"/>

**기간:** 2020년 7월 - 2022년 7월<br />
**플랫폼:** Web<br />
**역할:** 백엔드 엔지니어 (NodeJS/TypeScript)<br />
**설명:** 학부모, 교사, 학생을 위한 온라인 학습 플랫폼

**주요 기여:** 아래 저장소들을 구현 및 운영
- H5P Service: [H5P-Nodejs-library](https://github.com/Lumieducation/H5P-Nodejs-library) 기반으로 구축; Redis, MongoDB, express db, React 등 활용
- Media Storage Service: H5P 액티비티에서 전달되는 오디오/비디오/이미지 등 미디어 저장
- Media Storage React Hooks: 일부 클라이언트 H5P 액티비티에서 오디오 녹음/스크린샷 등 미디어 업로드에 사용하는 라이브러리
- xAPI Service: H5P 액티비티에서 수신한 [xAPI 이벤트](https://docs.openedx.org/en/latest/developers/references/internal_data_formats/xapi_events.html) 저장
- xAPI Uploader: 클라이언트 H5P 액티비티가 [사용자 상호작용 이벤트](https://h5p.org/events)를 xAPI Service로 업로드할 때 사용하는 라이브러리
- Assessment Service: 학생 성적 데이터를 저장하고 대시보드에서 조회 가능하도록 제공; xAPI Service와 Media Storage Service 데이터를 함께 사용

이 서비스들을 개발하면서 Postgres, GraphQL, Redis, AWS (S3, Lambda, ECS, DynamoDB, RDS, IAM), Terraform, Docker 등 다양한 기술을 다뤘습니다. 처음에는 Unity 엔지니어로 입사했지만 회사 우선순위가 바뀌며 백엔드로 전환 제안을 받았고, 새로운 영역을 배우는 것을 좋아해 수락했습니다. 그 시기에는 개인적으로 하던 Unity/C# 중심의 취미 개발 시간까지 백엔드 학습과 실습에 집중할 만큼 몰입했습니다. 여전히 게임 개발을 가장 선호하지만, 매우 의미 있고 시야를 넓혀 준 경험이었습니다.
