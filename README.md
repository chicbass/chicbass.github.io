# AEM을 써야 하는 이유
- 전문지식이 없어도 관리할 수 있다.
- 많은 요소(컴퍼넌트, CF, XF 등)들의 재활용이 가능하다. (제일 큰 부분)
- 컴포넌트와 에셋들의 종속성이 있고 선택적으로 권한 부여가 되어 관리가 강력하다.
- 라이브카피로 다국어,글로벌 사이트를 만들기 편하다.
- Adobe에서 기본적으로 제공하는 컴포넌트들이 꽤 있어서 커스터마이징 하기 편리하다.



# 일반적인 구성
- author 1-2대 (stand-by)
- publish 2-3대 (이중화)
- dispacher 2대

## 자주쓰는 메뉴
- Package Manager
- CRXDE
- General
- Assets
- Sites
- Deployment
- Project 거의 안씀.

# Author
- open properties
- publish page > author 서버에서 publish 서버로 보내줌
- edit template
- view in published

# AEM
- AEM 6의 AEM 플랫폼은 Apache Jackrabbit Oak을 기반
- Apache Jackrabbit : Java로 만들어진 오픈소스 콘텐츠 저장소(Content Repository)
- Oak은 JSR-283(JCR 2.0) 사양을 구현
- Java Specification Requests
- SR 283: Content Repository for JavaTM Technology API Version 2.0
- Oak JCR은 AEM이 사용하는 저장소(Repository) 구현체이다.
- JCR : Java Content Repository
# Platform
- Oracle Java™ SE 11,8 JDK - 64비트
- Oracle Java™ 17 및 21은 AEM 6.5 LTS에서 지원
- Maven 필요
# Repository
- MongoDB Enterprise 4.2~7.0 지원
- Oracle 데이터베이스 12c,19c,IBM® DB2® 10.5 제한된 지원
- Microsoft® SQL Server 2016,2022  지원
- AEM6에서 사용할 수 있는 노드 스토리지 구현은 Tar 스토리지와 MongoDB 스토리지
- TarMK : Tar + MicroKernel
- MongoMK : MongoDB + MicroKernel
- TarMK는 성능을 위해 설계된 반면, MongoMK는 확장성을 위해 사용된다
- AEM Author 및 Publish 인스턴스 모두에 대해 모든 배포 시나리오에서 고객이 사용하는 기본 지속성 기술로 TarMK를 강력히 권장
- AEM에서 MongoDB를 사용해야 하는 경우
  - 하루에 1000명 이상의 고유 사용자
  - 100명 이상의 동시 사용자
  - 대량의 페이지 편집
  - 대규모 롤아웃 또는 활성화.
# Search
- Apache Lucene 지원
- Apache Solr 지원
# WAS
- JBoss® EAP 7.4(JBoss® Application Server 포함) 지원
- Quickstart 기본 제공 서블릿 엔진(Jetty 9.4) 지원
- Tomcat 8/8.5
- Oracle WebLogic 12.1.3/12.2
- JBoss® EAP 6.3.0/6.4.0
# OS
- Linux®, Red Hat® Debian SUSE® 우분투배포 기반  지원
# Dispatcher : 캐싱 및 로드 밸런싱 구성 요소
- Experience Manager 6.5를 사용하려면 Dispatcher 버전 4.3.2 이상이 필요
- Apache httpd 2.4.x
- Microsoft® IIS 10(Internet Information Server)
- Dispatcher은 Windows 운영 체제용 Apache 2.4.x에서 사용할 수 없습니다.
- Dispatcher 없이 AEM을 실행하려면 다른 애플리케이션에서 SSL 종료 및 로드 밸런싱을 수행해야 합니다.
세션이 만들어지는 AEM 인스턴스(고정 연결이라고 함)에 대한 친화성을 가져야 하므로 필요합니다.
그 이유는 콘텐츠에 대한 업데이트가 최소한의 지연을 보이도록 하기 위해서입니다.
# Browser
- Google Chrome (Evergreen) 지원
- Microsoft® Edge(에버그린) 지원
- Mozilla Firefox (Evergreen) 지원
- macOS의 Apple Safari(Evergreen) 지원
- iOS 12.x의 Apple Safari 지원
- macOS의 Apple Safari 11.x 지원안됨
- iOS 11.x의 Apple Safari 지원안됨
- Microsoft® Internet Explorer 11 지원안됨
# RAM
- SSD 스토리지용 1:10
- 하드 디스크 스토리지용 1:3
  SSD 배포의 경우 2TB 데이터베이스에 200GB의 RAM이 필요
# AEM 제공 수준
- WAS: AEM은 독립 실행형 모드(통합 Jetty 웹 서버 포함)
- FrameWork : Sling
- 콘텐츠 저장소:  JCR(Java™ Content Repository)
- cq-quickstart-6.5.0.jar: 실행해야 하는 모든 내용이 포함된 독립 실행형 실행 파일 jar.
- cq-quickstart-6.5.0.war: 타사 응용 프로그램 서버에 배포할 war 파일입니다.
# CRXDE Lite
AEM에 기본 포함된 웹 기반 JCR 편집기
# OSGi(Open Service Gateway Initiative)
Java 애플리케이션을 모듈 단위로 관리할 수 있게 해주는 표준 프레임워크.
OSGi는 Java 코드를 ‘번들(Bundle)’이라는 작은 단위로 나누고, 런타임에서 동적으로 설치/업데이트/제거할 수 있도록 관리해 주는 시스템.
- Apache Felix → AEM 기본 OSGi 컨테이너.
# GraphQL
클라이언트가 원하는 데이터만 정확히 요청할 수 있게 해주는 쿼리 언어 기반의 API 기술이다!
# 렌디션
원본 파일(주로 이미지, 영상 등)에서 자동으로 생성된 파생 버전(썸네일, 리사이즈 이미지, 압축 파일 등)을 의미한다.

# Coral UI
AEM의 관리 콘솔(Authoring UI)을 구성하는 Adobe의 전용 UI 컴포넌트 라이브러리입니다.

# POJO
Plain Old Java Object의 약자입니다.

# Blueprint
다국어/다지사 사이트 관리 기능과 연결됩니다.

# 사이트 구조
~/code/  
|--- aem-guides-wknd/  
|--- all/  
|--- core/ 			:  java 소스 (백엔드)  
|--- ui.apps/		: 컴퍼넌트  
|--- ui.apps.structure/	: 템플릿  
|--- ui.config/		: 환경변수 셋팅  
|--- ui.content/		: DAM, 사이트  
|--- ui.frontend/		: CSS, javascript  
|--- ui.tests /  
|--- it.tests/  
|--- dispatcher/  
|--- pom.xml  
|--- README.md  
|--- .gitignore
