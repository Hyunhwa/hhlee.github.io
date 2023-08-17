---
layout: post
title: "[iOS] Swift Package Manager 도입하기 (2)"
date: 2023-05-16
tags: [iOS, Swift, SPM]
comments: true
categories: Swift
---

Swift Package Manager(이하 SwiftPM) 도입하기 2탄!! 


XCode에 Bitbucket 계정 연동하기입니다.
 
XCode에서 비공개 저장소를 접근하기 위해서는 권한이 허용된 Bitbucket 계정의 연동이 필요합니다.

안타깝게도 XCode에 Bitbucket 계정을 연동하는 방법은 정보도 적고 이슈도 많은 것으로 보입니다.

(XCode에 Github 계정을 연동하는 방법에 대한 정보는 많은데.. 🥲)

이 글을 보시는 분들은 제가 이미 겪은 문제를 직면하지 않길 바랍니다.

## XCode에 Bitbucket 계정 등록하기
 
위에 언급한대로 XCode에서 Bitbucket 비공개 저장소를 생성 및 업데이트하기 위해서는 XCode에 Bitbucket 계정을 연동하는 작업이 선행되어야 합니다. 그리고 연동을 위해 __Bitbucket 앱 비밀번호__가 필요합니다.

#### Bitbucket 설정
Bitbucket 사이트 우측 상단의 프로필 이미지를 선택하여 ‘**Settings > Personal settings**’를 클릭합니다.

계정 설정 화면에 표시된 **Username**을 기억해주세요. 
‘**App passwords**’ 메뉴를 클릭합니다.
 
‘**Create app password**’ 버튼을 클릭합니다.


XCode에서 필요한 권한을 다음과 같이 체크해주세요. 

- **Account (XCode 계정 연동 권한) > Read** 

- Repositories (저장소 생성 및 업데이트 권한) > Read, Write, Admin 


 
생성된 앱 비밀번호가 새 창에 표시됩니다. 
**값을 복사하여 잘 간직해주세요. 이후 비밀번호를 다시 확인하실 수 없습니다.** 
(권한 변경이 필요한 경우, 삭제 후 새로 발급받아야 합니다.)


#### XCode 설정
**XCode > Settings.. > Acounts** 를 클릭하고 ‘+’ 버튼을 클릭하여 추가할 계정 유형 중 ‘**Bitbucket Cloud**’를 선택합니다.


Bitbucket 계정 등록 화면이 나옵니다.
여기에 입력하실 Account와 Password는 Bitbucket에서 로그인 시 입력하는 __이메일 계정정보와 비밀번호가 아닙니다!!__

- **Account** : Bitbucket > 프로필 설정 화면 > Username 

- **Password** : Bitbucket > App Password 


드디어 연동이 완료되었습니다. 
SSH를 사용하실 경우 아래와 같이 Key를 생성하여 연동하실 수 있습니다.


## 마무리하며..
XCode에서 Bitbucket에 비공개 저장소를 생성하는 권한 이슈가 여전히 남아있습니다. 

XCode에 Bitbucket 계정을 연동하는 과정에서 이중인증이 필요하다(세 번째 참고사이트 참조)는 이야기는 실제와 다른 것 같습니다. 시도해보았으나 사이트 접속만 한껏 번거로와졌습니다.. 😵‍💫

이 문제에 대해 자세한 내용은 다음 글에서 풀어보겠습니다. (언제라는 기약은.. 할 수 없지만.. 😅)

 

## 참고사이트
- [Configuring your Xcode project to use source control | Apple Developer Documentation](https://developer.apple.com/documentation/xcode/configuring-your-xcode-project-to-use-source-control) 

- [Create an App password | Bitbucket Cloud | Atlassian Support](https://support.atlassian.com/bitbucket-cloud/docs/create-an-app-password/)

- [Xcode Source Control Accounts](https://useyourloaf.com/blog/xcode-source-control-accounts/) 
