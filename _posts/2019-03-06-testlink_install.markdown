---
layout: post
title: "Mac 에 Testlink 설치하기"
date: 2019-03-06
tags: [testlink, 테스트링크]
comments: true
categories: Testlink
---

[Testlink] 는 웹 기반의 테스트 관리 도구이다. 테스트 명세와 계획, 리포팅, 요구사항 트래킹 기능을 가지고 있으며 각종 버그 트래킹 시스템들과 연동도 가능하다.
오픈 소스 프로젝트 중 가장 많이 알려진 테스트 관리 도구이기도 하다.

Mac 환경에서 Testlink 를 설치하기 위한 방법은 세 가지가 있다.
1. 소스 다운로드 후 Mac에 서버 환경 구축
2. 소스 다운로드 후 Mac에 개발 환경 구축 (XAMPP 필요)<br/>
-> 도구 사용을 위해 개발 환경을 구축할 필요는 없다.
3. [Installer] 다운로드 후 VM(가상머신)에 서버 환경 구축<br/>
-> VM에 설치한 경우 다른 PC에서의 접근성이 문제가 된다.

따라서 1번 방법을 통해 설치하였다.

설치를 위해 다음과 같은 서버 환경이 필요하다. (기본적으로 Mac에는 Apache, php 가 내장되어있다.) 

|---|---|
| **OS** | Linux, Windows, Mac  |
| **DB** | MySQL 4.1.x 이상 (권장사양 5.x) <br/> Postgres 8.x 이상 <br/> μsoft SQL 2000, 2005 (1.9 버전에선 미지원) |
| **WAS** | Apache 1.3.x 또는 2.x 이상 <br/> IIS 3 이상 |
| **PHP** | 5.2 이상 (1.9.20 버전 기준 5.5 이상) |

### Apache 설정
브라우저 주소창에 `http://localhost`를 입력하였을 때 다음과 같이 **It works!**가 나타나면 Apache가 정상 작동 중이다.[^1]
![]({{ site.url }}/_resource/testlink/localhost.png)

Apache 는 **/etc/apache2** 경로에 설치되어있다. (**Finder** Command + Shift + G)
![]({{ site.url }}/_resource/testlink/apache2_location.png)

**httpd.conf** 파일을 열어 **'LoadModule php'** 를 찾아 주석을 풀어준다. (**#** 삭제)
![]({{ site.url }}/_resource/testlink/httpd_conf_php.png)

터미널을 열어 Apache 를 재시작한다.
```bash
sudo apachectl restart
```

Apache 웹서버의 루트 디렉토리가 될 폴더를 생성한다. ( **/User/{username}** 에 **Sites** 폴더 생성)
![]({{ site.url }}/_resource/testlink/insert_root_dir.png)

 **/User/{username}/Sites** 에 **{username}.conf** 파일을 생성하고 다음과 같이 내용을 작성한다.
```php
<Directory "/Users/{username}/Sites/">
    Options Indexes MultiViews FllowSymlinks
    AllowOverride All
    Require all granted
</Directory>
```

**/etc/apache2/httpd.conf** 파일을 열어 변경된 루트 디렉토리를 적용한다.
![]({{ site.url }}/_resource/testlink/httpd_conf_dir_root.png)

### MySql 설치
[MySql] 공식 사이트에서 **MySQL Comunity Edition** 을 설치한다. (자세한 설명은 다음 기회에..)

### Testlink 설치
[Github] 에서 Testlink 소스를 다운로드 받는다. <br/>
(2019.03.06 기준 sourceforge 사이트에 접근이 되지 않음)

**/User/{username}/Sites** 에 압축을 푼 뒤, 생성된 폴더명을 **testlink**로 변경한다.
![]({{ site.url }}/_resource/testlink/change_name_testlink.png)

**testlink** 내 **custom_config.inc.php.example** 파일을 복사하여 **custom_config.inc.php** 생성 뒤 다음과 같이 내용을 작성한다. 
```php
$tlCfg->log_path = '/Users/{username}/Sites/testlink/logs';
$g_repositoryPath = '/Users/{username}/Sites/testlink/upload_area';
```
터미널을 열어 **testlink** 내 모든 파일의 접근 권한을 변경한다. (모든 권한 허용)
```bash
sudo chmod 777 Sites/testlink/*
```
이제 브라우저에 `http://localhost/testlink/install` 입력하면 Testlink 설치를 위한 화면이 나타난다. [^2]

**New installation** 선택
![]({{ site.url }}/_resource/testlink/testlink_install_intro.png)

약관 동의 후 **continue** 선택 
![]({{ site.url }}/_resource/testlink/install_1_acceptance_of_license.png)

web/php 설정을 확인한다. (Database 는 Mysql / MSSql 중 하나만 설치되어 있으면 된다.)
![]({{ site.url }}/_resource/testlink/install_2_1_verification_of_system_and_configuration_requirements.png)

Testlink 내부 파일들의 접근 권한을 확인한다. (testlink 내 모든 파일 접근 권한이 허용되어있으면 OK)
- gui/templates_c
- logs
- upload_area 

![]({{ site.url }}/_resource/testlink/install_2_2_verification_of_system_and_configuration_requirements.png)

DB 설정을 위한 정보를 입력한다. (기본적으로 testlink 라는 테이블명으로 생성된다.)
![]({{ site.url }}/_resource/testlink/install_3_1_definition_of_db_access.png)

root 권한 계정과 Testlink 에 접근할 DB 계정 정보를 입력 후, **Process TestLink Setup!** 을 선택 

설치시 다음 권한이 필요하다.
- INDEX, CREATE, DELETE, DROP 

운영 시 Testlink 에 접근할 계정은 다음 권한을 갖고 있어야 한다.
- ALTER, SELECT, INSERT, UPDATE 

![]({{ site.url }}/_resource/testlink/install_3_2_definition_of_db_access.png)

다음과 같이 Testlink DB 가 생성되면 Testlink 설치가 완료된다. [^3]
![]({{ site.url }}/_resource/testlink/install_4_1_create_db.png)

Testlink 가 제공하는 메일 보내기 기능을 사용할 경우 추가 설정이 필요하다.

testlink 폴더 내부에 **config.inc.php** 파일에서 [SMTP] 설정 정보를 가져와[^4] **custom_config.inc.php** 에 붙여넣고, 메일 정보를 입력한다.

![]({{ site.url }}/_resource/testlink/install_4_2_create_db.png)

`http://localhost/testlink` 에 다음과 같이 관리자 화면이 나타나면 설치완료!![^5]
![]({{ site.url }}/_resource/testlink/testlink_intro.png)

<br/> 
### 참고자료
- [testlink_installation_manual.pdf]({{ site.url }}/_resource/testlink/testlink_installation_manual.pdf) [영문]
- [Testlink.pdf](https://www.swbank.kr/cmm/fms/FileDown.do?atchFileId=FILE_000000000005882&fileSn=0&AU=Y) [국문]
- [MAC OS上安装testlink](http://bungylovemickey.thpiano.com/?p=92) [중문]

[^1]: **It works!** 가 나타나지 않는 경우 터미널을 열어 Apache를 시작한다. ```sudo apachectl start #apache 시작```
[^2]: 페이지 에러가 발생된 경우 터미널에서 Apache를 재실행 한다.
[^3]: DB 연결 실패 화면이 표시된 경우 Mysql 이 실행되어있는지 확인한다. ```sudo mysql.server start #mysql 시작 ```
[^4]: **config.inc.php** 파일 내 **'[SMTP]'** 를 찾으면 구분선으로 구분된 영역을 찾을 수 있다. 
[^5]: 첫 진입 시 계정 정보는 ```admin```, ```admin``` 이다. 

[MySql]:https://www.mysql.com/downloads/
[Testlink]:http://testlink.org/
[Github]:https://github.com/TestLinkOpenSourceTRMS/testlink-code/tree/testlink_1_9/
[Installer]:https://bitnami.com/stack/testlink/installer
