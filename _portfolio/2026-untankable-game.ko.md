---
title: "UnTANKable"
excerpt: "<i class='fab fa-fw fa-github'>2026: 타임어택 아케이드 탱크 슈팅 게임</i>"
project_type: Professional
date: 2026-01-01
lang: ko
permalink: /portfolio/2026-untankable-game/

header:
  teaser: /assets/images/untankable/untankable00.jpg
sidebar:
  - title: "상세 정보"
    image: /assets/images/untankable/untankable00.jpg
    text: "- 회사: Sevenline Labs\n- 팀 규모: 1\n- 플랫폼: Web 및 PC\n- 기술: Unity 6.3\n- 기간: 4.5개월"
  #- nav: portfolio
gallery:
  - url: /assets/images/untankable/untankable01.jpg
    image_path: assets/images/untankable/untankable01.jpg
  - url: /assets/images/untankable/untankable02.jpg
    image_path: assets/images/untankable/untankable02.jpg
  - url: /assets/images/untankable/untankable03.jpg
    image_path: assets/images/untankable/untankable03.jpg
  - url: /assets/images/untankable/untankable04.jpg
    image_path: assets/images/untankable/untankable04.jpg
  - url: /assets/images/untankable/untankable05.jpg
    image_path: assets/images/untankable/untankable05.jpg
  - url: /assets/images/untankable/untankable06.jpg
    image_path: assets/images/untankable/untankable06.jpg
  - url: /assets/images/untankable/untankable07.jpg
    image_path: assets/images/untankable/untankable07.jpg
  - url: /assets/images/untankable/untankable08.jpg
    image_path: assets/images/untankable/untankable08.jpg
  - url: /assets/images/untankable/untankable09.jpg
    image_path: assets/images/untankable/untankable09.jpg
  - url: /assets/images/untankable/untankable10.png
    image_path: assets/images/untankable/untankable10.png
  - url: /assets/images/untankable/untankable11.png
    image_path: assets/images/untankable/untankable11.png
  - url: /assets/images/untankable/untankable12.png
    image_path: assets/images/untankable/untankable12.png
  - url: /assets/images/untankable/untankable13.png
    image_path: assets/images/untankable/untankable13.png
  - url: /assets/images/untankable/untankable14.png
    image_path: assets/images/untankable/untankable14.png
  - url: /assets/images/untankable/untankable15.png
    image_path: assets/images/untankable/untankable15.png
  - url: /assets/images/untankable/untankable16.png
    image_path: assets/images/untankable/untankable16.png
  - url: /assets/images/untankable/untankable17.png
    image_path: assets/images/untankable/untankable17.png
  - url: /assets/images/untankable/untankable18.png
    image_path: assets/images/untankable/untankable18.png
---

UnTANKable은 싱글플레이 타임어택 아레나 탱크 슈팅 게임입니다. 모든 적 전차와 포탑을 최대한 빠르게 파괴해 각 스테이지를 클리어하고, 기록 단축을 위해 스테이지를 반복 플레이할 수 있습니다. 24개의 전차 부품을 수집하고 성장시키며, 공격력, 조작, 생존력 중심으로 빌드를 조정하세요.

Sevenline Labs에서 근무하며 1인 개발자로 이 게임을 개발했습니다.
- Steam, Epic Games Store, Itch.io에 출시되었습니다.
- Leaderboards, Cloud Save, Cloud Code, Economy, Remote Config, Analytics 등 Unity 클라우드 서비스를 활용합니다.
- Unity Authentication과 함께 Google, Steam, Epic Games 로그인을 사용합니다.
- 적 전차 내비게이션에 [Environment Query System(EQS)을](https://iiii4.tistory.com/193) 구현했습니다.
- 적 전차의 공격, 후퇴, 아군 치료 등의 의사 결정에 [Utility AI를](https://shaggydev.com/2023/04/19/utility-ai/) 구현했습니다.
- 전차 부품 업그레이드, 판매, 골드 보상, 리더보드 점수 제출 등 서버 권한이 필요한 게임 로직에 Cloud Code를 활용합니다.
- 중앙 게임플레이 이벤트를 통한 이벤트 기반 디커플링을 구현했습니다.
- 모의 백엔드와 UGS 백엔드를 교체할 수 있도록 서비스를 추상화했습니다.
- 적 전차 아키타입과 능력 시스템을 데이터 기반으로 설계했습니다.

## 주요 기능
- 각 30개 스테이지로 구성된 2개 챕터: 초원 및 던전 테마
- 포탑별 2종 무기 구성: 강력한 주무기와 더 빠른 보조 무기
- 포탑 유형에 따른 8가지 탄환 특성: 탄도, 기본 포탄, 산탄, 반사, 기관총, 관통, 미니 미사일, 유도
- 수집 가능한 전차 부품 24종: 포탑 8개, 차체 8개, 궤도 8개
- 골드를 사용한 전차 부품 성장 및 업그레이드
- 희귀도 시스템: 일반 부품 9개, 고급 부품 9개, 희귀 부품 6개
- 파괴 가능한 벽을 제거하는 지뢰 능력
- 모든 전투 행동이 공유하는 AP 자원과 비전투 시간 기반 자동 회복
- 특화된 전투 역할을 가진 적 전차 아키타입 9종
- 전술적 맵 상호작용: 폭발물, 위험 요소, 다양한 엄폐물 로직
- 리더보드
- 전차 색상 커스터마이즈
- 부분적인 게임패드 지원
- ForTem API를 이용한 전차 부품 NFT 민팅 및 리딤

[Steam 페이지](https://store.steampowered.com/app/4713920/UnTANKable/){: .btn .btn--info}

[Epic Games Store 페이지](https://store.epicgames.com/p/untankable-a34ce1){: .btn .btn--info}

{% include video id="iTgX6OUqFO4" provider="youtube" %}

{% include video id="XsQu62IOARc" provider="youtube" %}

{% include video id="ec8XFQrfFYg" provider="youtube" %}

{% include video id="9KXDLsb8_kE" provider="youtube" %}

{% include video id="bmLRN6h3QxY" provider="youtube" %}

{% include video id="ZPu4YDNUELE" provider="youtube" %}

{% include gallery %}