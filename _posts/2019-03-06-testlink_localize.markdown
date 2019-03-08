---
layout: post
title: "Testlink 1.9 에서 테스트케이스 작성하기"
date: 2019-03-08
tags: [testlink, 테스트링크]
comments: true
categories: Testlink
---

Testlink 는 웹 기반의 테스트 관리 도구이다. 테스트 명세와 계획, 리포팅, 요구사항 트래킹 기능을 가지고 있으며 각종 버그 트래킹 시스템들과 연동도 가능하다.

이번 포스트에서는 Testlink 에 테스트케이스를 작성하는 방법을 소개한다.

1. 프로젝트 생성
2. 테스트 스위트 생성
3. 테스트 케이스 작성


### 1. 프로젝트 생성

관리자 페이지에서 첫 로그인을 성공하면 프로젝트를 생성하는 페이지가 나타난다.<br/>
(생성된 프로젝트가 하나도 없는 경우, 자동으로 프로젝트 생성 페이지로 이동한다.)

![]({{ site.url }}/_resource/testlink/no_project.png)

'생성' 버튼을 클릭하면, 다음과 같이 프로젝트 리스트가 표시된다.

![]({{ site.url }}/_resource/testlink/project_list.png)


### 2. 테스트 스위트 생성

상단의 **홈** 아이콘을 클릭한 뒤 **테스트 케이스 편집** 메뉴를 선택한다.

![]({{ site.url }}/_resource/testlink/testlink_home_no_plan.png)

테스트 프로젝트 영역 내 **설정** 아이콘을 클릭하면 **Test Suite Operations** 메뉴가 나타난다.

![]({{ site.url }}/_resource/testlink/testlink_no_test_suit.png)

**'+'** 아이콘을 선택하여 테스트 스위트를 작성한다.

![]({{ site.url }}/_resource/testlink/create_testsuite.png)

**저장** 버튼 클릭 시 다음과 같이 왼쪽 트리에 추가된 테스트 스위트를 확인할 수 있다.

![]({{ site.url }}/_resource/testlink/confirm_testsuite_created.png)


### 3. 테스트 케이스 작성

왼쪽 트리에서 테스트 스위트를 선택한다.<br/>
**설정** 아이콘을 클릭하면 **Test Suite Operations**[^1] 와 **Test Case Operations** 메뉴가 나타난다.

![]({{ site.url }}/_resource/testlink/testlink_no_test_case.png)

**Test Case Operations** 메뉴의 **'+'** 아이콘을 선택하여 테스트 케이스를 작성한다.

![]({{ site.url }}/_resource/testlink/create_testcase.png)

작성된 테스트 케이스 화면은 다음과 같다.

![]({{ site.url }}/_resource/testlink/testcase_no_step.png)

#### 단계별 테스트 추가

**step** 을 추가하기 위해 **Create Step** 버튼을 클릭한다.

단계별 테스트 액션과 테스트 결과를 입력 후 **Save & exit**  버튼을 클릭한다.
- **저장** - 작성 중인 step 을 저장 후, 추가 step 을 작성한다.
- **Save & exit** - 작성 중인 step 을 저장 후 테스트 케이스 화면으로 전환된다.

![]({{ site.url }}/_resource/testlink/create_step.png)

단계별 테스트가 작성된 테스트 케이스는 다음과 같다.

![]({{ site.url }}/_resource/testlink/confirm_testcase_created.png)

[^1]: **Test Suite Operations** 메뉴의 **'+'** 아이콘을 클릭하면 선택된 테스트 스위트의 하위 테스트 스위트 생성이 가능하다.
