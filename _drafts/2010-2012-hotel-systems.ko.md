---
title: "호텔 시스템"
excerpt: "2010-2012: 호텔 손실 방지(Loss Prevention) 업무 중 개발한 프로젝트"
project_type: Semi-Professional
date: 2010-01-01
lang: ko
permalink: /portfolio/2010-2012-hotel-systems/
header:
  teaser: /assets/images/hotelsystems/lpdatabase2.png
sidebar:
  - title: "상세 정보"
    image: /assets/images/hotelsystems/lpdatabase2.png
    text: "- 팀 규모: 1\n- 플랫폼: Windows\n- 기술: C#, WinForms, Microsoft Access Database"
  #- nav: portfolio
lpdatabase:
  - url: /assets/images/hotelsystems/employee_records.png
    image_path: assets/images/hotelsystems/thumbs/employee_records.png
  - url: /assets/images/hotelsystems/add_edit_employee.png
    image_path: assets/images/hotelsystems/thumbs/add_edit_employee.png
  - url: /assets/images/hotelsystems/lpdatabase1.png
    image_path: assets/images/hotelsystems/thumbs/lpdatabase1.png
  - url: /assets/images/hotelsystems/lpdatabase3.png
    image_path: assets/images/hotelsystems/thumbs/lpdatabase3.png
  - url: /assets/images/hotelsystems/report_log.png
    image_path: assets/images/hotelsystems/thumbs/report_log.png
  - url: /assets/images/hotelsystems/report_stats_chart.png
    image_path: assets/images/hotelsystems/thumbs/report_stats_chart.png
  - url: /assets/images/hotelsystems/report_stats_summary.png
    image_path: assets/images/hotelsystems/thumbs/report_stats_summary.png
  - url: /assets/images/hotelsystems/submit_report_info.png
    image_path: assets/images/hotelsystems/thumbs/submit_report_info.png

lftracker:
  - url: /assets/images/hotelsystems/lfhandler.png
    image_path: assets/images/hotelsystems/thumbs/lfhandler.png
  - url: /assets/images/hotelsystems/lfhandler2.png
    image_path: assets/images/hotelsystems/thumbs/lfhandler2.png
---

{% include video id="XUBedHznG0Y" provider="youtube" %}

### Loss Prevention 데이터베이스

목적: 사고 보고서를 기록하고 직원 기록과 연결하는 도구

하이라이트:

- Omni La Mansion Del Rio 및 Mokara Hotel and Spa에서 사용

LP Database는 기존 시스템의 품질 저하에 대한 문제의식과, 새 기능을 통해 업무 효율을 크게 높일 수 있다는 기대에서 시작되었습니다.

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/hotelsystems/lpdatabase_table_structure.png"/>

{% include gallery id="lpdatabase" %}

### 분실물(L&F) 트래커

사용 도구: Microsoft Excel/VBA

목적: 분실물, 고객 문의, 택배/수령 내역을 기록하는 도구

하이라이트:

- Omni La Mansion Del Rio, Mokara Hotel and Spa, Hyatt Hill Country Resort and Spa에서 사용
- 직원 Top 30 통계를 통해 하우스키핑의 분실물 제출 동기 부여
- VBA 폼으로 보호된 워크시트에만 데이터 입력하여 임의 수정 방지
- 사용자/직원 이름 동적 드롭다운으로 데이터 일관성 유지 및 관리 용이
- 폼 검증으로 필수 입력값 누락 방지

이 도구는 서로 연관된 3개의 문서를 하나로 통합하고 추가 기능을 더해 만든 결과물입니다. 기존 방식은 중복 입력과 폴더 탐색 시간 낭비가 컸고, 시간이 갈수록 관리가 어려워졌습니다. 통합 이후 효율이 크게 향상되었고, 부서장 관점의 통계 분석도 가능해졌습니다.

{% include gallery id="lftracker" %}
