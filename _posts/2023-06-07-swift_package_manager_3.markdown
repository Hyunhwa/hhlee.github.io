---
layout: post
title: "[iOS] Swift Package Manager 도입하기 (3)"
date: 2023-06-07
tags: [iOS, Swift, SPM]
comments: true
categories: Swift
---

Swift Package Manager(이하 SwiftPM) 도입하기 3탄..!

Bitbucket에 Swift Package 비공개 저장소 생성하기 입니다.

이전 글을 따라 XCode에 Bitbucket 계정이 연동하셨다면 XCode로 저장소 생성이 가능합니다.
다만 저의 경우 여러가지 시도에도 불구하고(권한 문제로 추정됨) XCode에서 Bitbucket 저장소 생성이 불가하였습니다.

따라서 Bitbucket 사이트에서 비공개 저장소를 생성한 뒤 XCode에서 스위프트 패키지를 생성하여 연결(SourceTree를 통해)하는 작업을 공유합니다.

## Bitbucket 비공개 저장소 생성하기
비공개 저장소를 생성하기 위해서는 계정에 해당 Workspace 저장소 생성 권한이 있어야 합니다.
이 포스팅에서는 계정별로 할당된 개인 Workspace에서 저장소를 생성하도록 하겠습니다.

비트버킷 사이트 상단의 프로필 메뉴를 클릭하여 Workspace를 선택합니다.
(최근 워크스페이스에 표시되지 않는 경우, All workspaces를 클릭하여 리스트 내에서 선택)

사이트 상단 메뉴의 Create > Repository 를 선택합니다.

필수 입력 항목을 작성 후, **Access level : Private repository**를 선택하여 Create repository 버튼을 클릭합니다.

저장소 생성이 완료되면 다음과 같은 화면을 확인하실 수 있습니다.
(README, .gitignore 파일을 추가하지 않은 경우 다른 화면이 표시됩니다.)

## XCode에서 Swift Package 생성하기
**File > New > Package…** 를 클릭하여 새로운 패키지를 생성합니다.

패키지명을 작성 후 ‘**Create Git repository on my Mac**’ 을 체크하고 ‘Create’ 버튼을 클릭합니다.

다음과 같은 구조로 Package가 생성됩니다.


## Bitbucket 저장소에 Swift Package 업로드 하기
__XCode 기본 브런치는 main__입니다. __Bitbucket 기본 브런치는 master__죠.
따라서 __main 브런치의 Swift Package를 master 브런치에 덮어씌워야 합니다.__

생성 시점부터 하나의 브런치로 만들 수 있다면 좋겠지만 다음의 이유로 불가합니다.

현재로선 Bitbucket 사이트를 통해서만 저장소를 생성할 수 있습니다.
(XCode에서 동일한 브런치명으로 원격을 연결하는 방법도 브런치명 중복 오류 발생으로 불가합니다)

Bitbucket 원격 저장소를 복제하여 생성된 폴더에서 Swift Package를 생성하면 연동 시 정상동작하지 않습니다. 
(폴더 구조가 달라집니다)

따라서 덮어씌우기 작업을 위해 다음과 같이 main 브런치를 master에 재배치 하였습니다.

#### XCode에서 원격 연결 추가하기 
SourceControl Navigator를 클릭하여 Repositories > Remotes > Add Existing Remote… 클릭합니다.


Bitbucket의 저장소 URL을 등록 후 ‘Add’ 버튼을 클릭합니다.


#### SourceTree에서 브런치 재배치하기
XCode에서 생성한 Swift Package를 로컬 저장소로 추가합니다.


다음과 같이 아무런 main 브런치 상태에서 master 브런치를 선택하여 ‘재배치…’를 클릭합니다.


재배치 확인 알림창이 발생되면 ‘확인’ 버튼을 누릅니다. 


충돌이 발생된 .gitignore(or README.markdown) 파일을 수정하여 ‘커밋’합니다.


(no branch, rebasing main)에 새로운 브런치를 생성합니다.
(개발/테스트용 브런치인 ‘dev’로 생성하는 편을 추천드립니다.)


브런치 생성 후 ‘master’ 브런치로 상태를 변경하여 새로운 브런치와 병합합니다.


master 브런치의 내용을 푸시하면 Swift Package 저장소 생성이 완료됩니다.


## 마무리하며..
글 머리에서 언급하였듯 XCode에서 원격 연결 생성시 아래와 같은 오류가 발생됩니다.


때문에 돌고도는 방식으로 Swift Package 저장소를 생성하였습니다.
혹시 해결 방안을 알게되신다면 저에게도 공유해주세요 ‼️

다음 글은 Swift Package 업로드하기 입니다.
최대한 빨리 돌아올 수 있도록 노력해볼게요 😁
