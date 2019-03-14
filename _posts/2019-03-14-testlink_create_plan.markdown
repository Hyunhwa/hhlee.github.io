---
layout: post
title: "Testlink 1.9 에서 테스트 계획하기"
date: 2019-03-14
tags: [testlink, 테스트링크]
comments: true
categories: Testlink
---

Testlink 는 웹 기반의 테스트 관리 도구이다. 테스트 명세와 계획, 리포팅, 요구사항 트래킹 기능을 가지고 있으며 각종 버그 트래킹 시스템들과 연동도 가능하다.

이번 포스트에서는 Testlink 에 테스트 계획을 생성 및 할당하는 방법을 소개한다. <br/>
<u>리더 권한 이상을 필요</u>로 한다. (테스트 결과 관리자 권한으로만 테스터 배정이 가능했다.)


1. 테스트 계획 생성
2. 테스트 빌드 버전 생성
3. 테스트 케이스 할당
4. 테스트를 수행할 테스터 배정

<br/>
### 1. 테스트 계획 생성

**홈** 화면 우측 상단의 **테스트 계획 관리**를 선택한다.

![]({{ site.url }}/_resource/testlink/home_no_test_plan.png)

생성된 테스트 계획이 없는 경우 아래와 같은 화면이 나타난다. (**생성** 버튼 클릭)

![]({{ site.url }}/_resource/testlink/test_plan_list_no_data.png)

테스트 계획을 작성 후 **생성** 버튼 클릭한다.<br/>
- **사용함** 자신의 홈에 테스트 계획 메뉴 표시 여부
- **public** 자신보다 낮은 권한을 가진 사용자의 홈에 테스트 계획 메뉴 표시 여부

![]({{ site.url }}/_resource/testlink/create_test_plan.png)

**테스트 계획** 이 생성되면 테스트 계획 리스트 화면으로 이동한다.<br/>
생성 화면에서 테스트 계획 **사용함**을 선택하지 않은 경우, 이 화면에서 전구를 켜서 테스트 계획을 활성화하는게 가능하다.

![]({{ site.url }}/_resource/testlink/test_plan_list.png)

<br/>
### 2. 테스트 빌드 버전 생성

테스트 계획을 활성화하면 아래와 같이 **홈**화면 우측에 테스트 계획 관리 메뉴가 표시된다. <br/>
**홈** 화면 우측에 생성된 메뉴에서 **빌드 / 릴리즈** 메뉴를 선택한다.

![]({{ site.url }}/_resource/testlink/home_has_test_plan.png)

생성된 테스트 빌드 버전이 없는 경우 아래와 같은 화면이 나타난다. (**생성** 버튼 클릭)

![]({{ site.url }}/_resource/testlink/build_version_list_no_data.png)

테스트 빌드 버전을 입력 후 **생성** 버튼을 클릭한다.

![]({{ site.url }}/_resource/testlink/create_testplan_build_version.png)

테스트 빌드 버전을 작성하면 테스트 빌드 리스트 화면으로 이동한다.

![]({{ site.url }}/_resource/testlink/testplan_build_version_list.png)

<br/>
### 3. 테스트 케이스 할당

**홈** 화면에서 **테스트 케이스 추가 / 삭제** 메뉴를 선택한다.

![]({{ site.url }}/_resource/testlink/home_add_testcases_to_testplan.png)

왼쪽 하단의 트리 구조에서 테스트할 **테스트 스위트**나 **테스트 케이스**를 선택한다.

![]({{ site.url }}/_resource/testlink/add_test_case_in_testplan.png)

테스트 항목을 모두 선택 후 **선택한 것들 추가** 버튼을 클릭한다.[^1]<br/>

![]({{ site.url }}/_resource/testlink/diselect_test_case_in_testplan.png)

테스트 항목이 선택 완료된 경우 다음과 같이 화면에 표시된다.

![]({{ site.url }}/_resource/testlink/select_test_case_in_testplan.png)

<br/>
### 4. 테스트를 수행할 테스터 배정

**홈** 화면에서 **실행할 테스터 지정** 메뉴를 선택한다.

![]({{ site.url }}/_resource/testlink/home_accept_users.png)

왼쪽 하단의 트리 구조에서 테스터를 배정할 **테스트 스위트**나 **테스트 케이스**를 선택한다.

![]({{ site.url }}/_resource/testlink/add_tester_in_testplan.png)

테스트 항목과 테스터를 선택 후 **Apply Assign** 버튼과 **Save Assignments** 버튼을 클릭한다.

![]({{ site.url }}/_resource/testlink/diselect_senior_tester_in_testplan.png)

로그인 테스트에 두 명의 테스터가 할당되었다.

![]({{ site.url }}/_resource/testlink/select_senior_tester_in_testplan.png)

[^1]: 이 단계에서도 테스터 배정이 가능하다. smtp 정보가 설정되어있다면 테스터에게 메일로 알려주는 것도 가능하다
