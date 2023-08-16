---
layout: post
title: "[iOS] Swift Package Manager 도입하기 (1)"
date: 2023-05-18
tags: [iOS, Swift, SPM, SwiftPackageManager]
comments: true
categories: Swift
---

저희 팀에서 Swift 공용 프레임워크를 개발하자는 의견이 있었습니다.

iOS용으로 개발된 프레임워크가 있었지만 Objective-C로 개발되어있었고 노후화된 상태였죠.

때문에 Swift Package Manager(이하 SwiftPM)을 도입하기로 하였습니다. 

이 글은 도입하게된 이유와 간단한 사용 방법에 대한 포스팅입니다.


## SwiftPM?

XCode11(Swift 3.0 이상)부터 내장되어 애플에서 제공하는 공식 종속성 관리 도구입니다. Swift, Objective-C, Objecitve-C++, C, C++ 언어를 지원하며 소스 파일, 바이너리 및 리소스를 번들로 묶어 관리합니다. 

## SwiftPM을 도입하려는 이유?

:one:  CocoaPods의 기술적 한계

현재 저희 회사에서 iOS 종속성 관리를 위해 CocoaPods을 사용합니다. 그러나 범용성과 익숙함을 제외한다면 CocoaPods은 이점이 크지 않은 도구이기도 합니다. XCode 버전 업데이트 때마다 발생되는 호환성 문제와 Ruby 언어로 작성된 프로그램(즉, Mac Ruby 버전의 영향을 받음)으로 종속성이 변경된 순간마다 ‘터미널’ 앱에 명령어를 입력하는 불편함을 감수해야 합니다. 

이런 불편함을 감수하더라도 결정적으로 XCode14 부터 리소스 번들을 종속성으로 추가할 경우 서명이  필요하게 됨에 따라 Fastlane을 이용한 전체 배포가 불가한 문제는 현재 해결할 방안이 없었습니다. 

공용 플레이어 개발 계획을 갖고 있는 우리 팀에게 리소스 번들을 종속성으로 추가하지 못하는 점은 개발상 큰 제약이 될 수 있어 이에 대한 방안이 필요했습니다.

:two:  애플 공식 종속성 관리 도구

Swift 5.3 버전(XCode12)부터 SwiftPM을 통해 리소스 번들을 추가하는 것이 가능해졌습니다. 그리고 추가된 리소스 번들에 별도의 서명이 필요하지 않습니다. 언제 지원이 종료될지 걱정하지 않아도 됩니다. 애플에서 공식적으로 제공되는 도구니까요 :thumbsup: 

:three:  개발의 편의성

XCode 하나로 종속성을 관리할 수 있다는 점은 많은 편의성을 가져다주었습니다. 종속성의 추가/업데이트/삭제가 한 두번의 버튼 클릭으로 가능해졌고, Swift Package를 Private 저장소로 생성하여 공유하는 것 또한 CocoaPods spec을 올리는 작업보다 단순합니다.(시간 단축 또한 덤!!)

## SwiftPM 사용법

그럼 SwiftPM을 사용하여 종속성을 관리하면 얼마나 편리해지는지 사용법에 대해 알아보겠습니다.

### Swift Package 추가

프로젝트 구조(Navigator 영역)에서 프로젝트 파일을 선택 후 ‘Package Dependencies’를 클릭합니다.

하단의 '+' 버튼을 누른 뒤 검색필드에 Git 저장소 URL을 입력합니다.

검색어에 대한 저장소 검색 결과화면에서 추가하고자 하는 종속성을 선택하고 ‘Add Package’ 버튼을 클릭합니다.

성공적으로 패키지가 추가됨을 확인할 수 있습니다. (추가 후 로딩에 시간 소요가 있습니다)

### Swift Package 삭제

패키지 목록에서 삭제할 패키지를 선택 후 '-' 버튼을 클릭합니다. (쉽죠?)

### Swift Package 업데이트

‘File > Packages > Update to Lastet Package Versions'를 클릭합니다.

## 마무리하며..

Cocoapods에 비해 종속성 관리가 많이 편해졌죠? 

Private한 저장소를 생성하고 공유하는 작업도 이후 공유할 예정입니다. 

2탄을 기대해주세요.

 

## 참고사이트
- [(공식)애플문서-스위프트 패키지]:https://developer.apple.com/documentation/xcode/swift-packages

- [GitHub - apple/swift-package-manager]:https://github.com/apple/swift-package-manager

- [Swift 5.3 released!]:https://www.swift.org/blog/swift-5.3-released/

- [Swift Package Manager 적용기]:https://tech.kakao.com/2022/06/02/swift-package-manager/
