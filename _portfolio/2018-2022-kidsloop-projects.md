---
title: "KidsLoop Projects"
excerpt: "2018-2022: Educational Technology company"
project_type: Professional
classes: wide
header:
  teaser: /assets/images/kidsloop/kidsloop-logo.png
sidebar:
  - image: /assets/images/kidsloop/kidsloop-logo.png
    text: "<p><b>Nov 2018 - Jul 2022</b></p><p><b>Mid/Senior Software Engineer</b></p><p><b>Educational Technology</b> - for parents, teachers, and children</p>"
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

**Period:** Nov 2018 - Sep 2019<br />
**Platform:** Android & iOS<br />
**Role:** Unity Engineer<br />
**Engineers:** 2 backend, 2 frontend<br />
**Description:** a UI application for parents and teachers, developed from scratch

**Notable Contributions:**
- authentication and authorization
- virtual list views
- offline mode and syncing when back online
- asynchronous file loading and API calls + loading indicators

## Badanamu Apps

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/kidsloop/badanamu-game.png" style="width: 40%" class="align-right"/>

**Period:** Sep 2019 - Jan 2020<br />
**Platform:** Android & iOS<br />
**Role:** Unity Engineer<br />
**Description:** a suite of child learning applications that have been published on Google Play and Apple Store for many years

**Notable Contributions:**
- in-app purchasing
- update Unity versions
- integrate analytics
- bug fixing

## ESL Dashboard

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/kidsloop/esl-dashboard-progress.png" style="width: 40%" class="align-right"/>

**Period:** Jan 2020 - Jul 2020<br />
**Platform:** Android & iOS<br />
**Role:** Unity Engineer<br />
**Description:** a library for use in the Badanamu ESL learning application. It’s a dashboard that presents all kinds of learning statistics in categories such as reading, writing, listening, and speaking. I worked on this project with two other Unity developers and a couple backend developers.

**Notable Contributions:**
- native Android and iOS media plugins for taking pictures, choosing from a gallery, and image resizing/compression.
- speech recognition library utilizing Amazon Transcribe. I developed both the frontend and backend using .NET, and deployed it to AWS as a Docker container.
- asynchronous file loading and API calls + loading indicators
- incremental thumbnail loading

{% include gallery %}

## KidsLoop V2

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/kidsloop/online-learning-platform.png" style="width: 40%" class="align-right"/>

**Period:** Jul 2020 - Jul 2022<br />
**Platform:** Web<br />
**Role:** Backend Engineer (NodeJS/TypeScript)<br />
**Description:** an online learning platform for parents, teachers, and students

**Notable Contributions:** implement and manage the following repositories
- H5P Service: built on top of [H5P-Nodejs-library](https://github.com/Lumieducation/H5P-Nodejs-library); utilized Redis, MongoDB, express db, React, etc.
- Media Storage Service: stores audio, video, images, etc. recevied from H5P activities
- Media Storage React Hooks: a library used by certain client-side H5P activities to upload media such as audio recordings and screenshots
- xAPI Service: stores [xAPI events](https://docs.openedx.org/en/latest/developers/references/internal_data_formats/xapi_events.html) received from H5P activities
- xAPI Uploader: a library used by client-side H5P activities for uploading [user interaction events](https://h5p.org/events) to the xAPI Service
- Assessment Service: stores class results for students which is queried and presented in a frontend dashboard; reads from the xAPI service and Media Storage Service

I worked with many different technologies while developing these services such as Postgres, GraphQL, Redis, AWS (S3, Lambda, ECS, DynamoDB, RDS, IAM), Terraform, Postgres, and Docker. I was originally hired as a Unity Engineer, but when company priorities changed, they asked if I'd be interested in switching over to backend engineering. I'm always up for learning new things and expanding my software engineering skill set, so I accepted. My excitement for the opportunity also took over my personal/hobby development time, which was normally dedicated to Unity and C#. I had never really done any backend engineering or NodeJS/TypeScript development, so I went all-in on studying and practicing. I still prefer game development, but this was an enjoyable and enlightening experience.
