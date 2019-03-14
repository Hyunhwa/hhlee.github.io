---
layout: post
title: "Testlink 1.9 에서 사용자 역할 별 접근 권한"
date: 2019-03-12
tags: [testlink, 테스트링크]
comments: true
categories: Testlink
---

Testlink 는 웹 기반의 테스트 관리 도구이다. 테스트 명세와 계획, 리포팅, 요구사항 트래킹 기능을 가지고 있으며 각종 버그 트래킹 시스템들과 연동도 가능하다.

Testlink 는 다음과 같이 기본적으로 6가지 역할을 가지고 있으며, 각 역할마다 다른 접근 권한을 갖는다.

![]({{ site.url }}/_resource/testlink/total_user_list.png)


### 1. 게스트 (Guest) 

테스트 케이스와 프로젝트 매트릭스(보고서)를 열람할 권한을 갖는다.

![]({{ site.url }}/_resource/testlink/home_guest.png)

### 2. 테스트 실행자 (Tester)

게스트의 권한을 포함하여 그들에게 할당된 테스트만 실행할 수 있는 권한을 갖는다.

![]({{ site.url }}/_resource/testlink/home_tester.png)

### 3. 테스트 디자이너 (Test designer)

테스트 명세와 요구사항에 관한 모든 권한을 갖는다. (테스트 실행 권한 없음)

![]({{ site.url }}/_resource/testlink/home_test_designer.png)

### 4. 테스트 분석가 (Senior tester)

테스트 케이스를 실행할 수 있을 뿐만 아니라 검색, 생성, 편집 및 삭제할 수 있는 권한을 갖는다.

![]({{ site.url }}/_resource/testlink/home_senior_tester.png)

### 5. 리더 (Leader)

테스트 분석가의 권한을 포함하여 테스트 계획 관리, 테스터 배정, 마일스톤 생성, 키워드 관리 등의 권한을 갖는다.<br/>
(테스트 결과 마일스톤 메뉴는 표시되지 않고, 테스터는 배정할 테스트 항목 선택 시 메인으로 튕겨나갔다.)

리더(or 관리자)의 승인 없이 시스템의 모든 사용자는 테스트 계획 메뉴에 접근할 수 없다.

![]({{ site.url }}/_resource/testlink/home_leader.png)

### 6. 관리자 (Admin)

모든 기능에 대한 접근 권한이 허용된다.

시스템에 사용자를 추가하고 플러그인이나 각종 트래킹 시스템의 연동을 설정하는 권한을 유일하게 갖는다.

![]({{ site.url }}/_resource/testlink/home_admin.png)
