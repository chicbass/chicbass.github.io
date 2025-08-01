# AEM을 써야 하는 이유
- 전문지식이 없어도 관리할 수 있다.
- 많은 요소(컴퍼넌트, CF, XF 등)들의 재활용이 가능하다. (제일 큰 부분)
- 컴포넌트와 에셋들의 종속성이 있고 선택적으로 권한 부여가 되어 관리가 강력하다.
- 라이브카피로 다국어,글로벌 사이트(현지화)를 만들기 편하다.
- Adobe에서 기본적으로 제공하는 컴포넌트들이 꽤 있어서 커스터마이징 하기 편리하다.
- 높은 수준의 파일시스템과 메타 및 권한관리로 DAM으로 활용가능하다.



# 일반적인 구성
- author 1-2대 (stand-by)
- publish 2-3대 (이중화)
- dispacher 2대

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
  AEM 게시 서비스에 Apache 웹 서버 및 CDN을 통한 캐싱이 포함되어 있어 기본적으로 HTML 콘텐츠는 ~5분 동안 캐시됨.  

| 역할        | 설명                               |
  | --------- | -------------------------------- |
  | **캐싱**    | 페이지, 이미지 등을 저장해 빠른 응답 제공         |
  | **로드밸런싱** | 여러 Publish 서버로 요청 분배             |
  | **보안**    | Publish 직접 노출 방지, 허용된 요청만 전달     |
  | **정책 제어** | 캐시 무효화(Invalidation), 캐시 경로 설정 등 |

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

# 클래식UI
클래식 UI를 사용할 경우 JSP를 이용하여 AEM사이트를 만들 수 있음.
[바로가기](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/implementing/developing/introduction/website)

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

# AEM 노드 타입
| primary type      | 설명                      |
| ----------------- | ----------------------- |
| `nt:unstructured` | 구조가 자유로운 일반 컨텐츠 노드      |
| `sling:Folder`    | 구조용 폴더 (페이지가 아님!)       |
| `cq:Page`         | 페이지 루트 노드               |
| `cq:PageContent`  | 실제 페이지 컨텐츠 (메타데이터 포함)   |
| `nt:file`         | 파일 노드 (예: 이미지, pdf)     |
| `dam:Asset`       | DAM(자산) 파일 노드           |
| `nt:resource`     | 실제 바이너리 리소스 (예: 이미지 본문) |
| `rep:policy`      | 권한 정책 노드                |

# AEM Navigation 메뉴
| 메뉴                       | 핵심                      |
| ------------------------ | ----------------------- |
| **Projects**             | 작업, 팀, 리소스를 프로젝트 단위로 관리 |
| **Sites**                | 페이지 구조/콘텐츠 관리 (CMS 핵심)  |
| **Experience Fragments** | 재사용 가능한 콘텐츠 조각          |
| **Assets**               | 이미지·동영상 등 디지털 자산 중앙 관리  |
| **Forms**                | 온라인 폼, PDF 양식           |
| **Screens**              | 디지털 사이니지 콘텐츠            |
| **Personalization**      | 맞춤형 콘텐츠, A/B 테스트        |
| **Commerce**             | 전자상거래 기능 통합             |
| **Communities**          | 포럼, 리뷰, 커뮤니티 기능         |

# AEM TOOLS 메뉴
| 영역                 | 핵심 목적            |
| ------------------ | ---------------- |
| **General**        | 기본 구조/메타/구성 관리   |
| **Workflow**       | 프로세스 자동화         |
| **Operations**     | 시스템 관리·점검        |
| **Sites**          | 다국어/멀티사이트 관리     |
| **Assets**         | DAM + 메타데이터      |
| **Resources**      | 문서/개발 리소스        |
| **Deployment**     | 배포/복제/패키지 관리     |
| **Security**       | 사용자·권한·보안        |
| **Cloud Services** | Adobe/외부 클라우드 연동 |
| **Communities**    | UGC, 커뮤니티 기능     |
| **Commerce**       | 커머스 통합 기능        |
### General
| 메뉴                            | 설명                                             |
| ----------------------------- | ---------------------------------------------- |
| **CRXDE Lite**                | AEM 내부 리포지토리(JCR) 직접 탐색/편집하는 웹 IDE             |
| **Search Forms**              | 커스텀 검색 폼 정의 — 에셋/페이지/사용자 정의 검색                 |
| **Tagging**                   | 태그 정의·분류·관리 — 메타데이터 관리                         |
| **Templates**                 | (Static Templates) 전통 템플릿 관리                   |
| **Components**                | 재사용 가능한 컴포넌트 설정 — 에디터에 노출할 컴포넌트 관리             |
| **Configuration Browser**     | OSGi 구성(Config) 관리 UI                          |
| **Translation Configuration** | 번역 공급자(Adobe/외부) 연계 설정                         |
| **GraphQL Query Editor**      | GraphQL API 테스트·작성 도구 — Content Fragment 쿼리 확인 |
### Workflow
| 메뉴            | 설명                         |
| ------------- | -------------------------- |
| **Models**    | 워크플로우 프로세스 설계/편집           |
| **Instances** | 실행 중/완료된 워크플로우 인스턴스 모니터링   |
| **Launchers** | 특정 이벤트 발생 시 워크플로우 자동 실행 규칙 |
| **Archive**   | 완료된 워크플로우 기록 보관            |
| **Failures**  | 실패한 워크플로우 목록·재시도·오류 추적     |
### Operations
| 메뉴                  | 설명                                  |
| ------------------- | ----------------------------------- |
| **System Overview** | 서버/인스턴스 상태 개요 — 버전, 디스크, JVM, 번들 상태 |
| **Web Console**     | OSGi Felix 콘솔 바로가기 — 번들·구성 상세 관리    |
| **Testing**         | AEM 테스트 프레임워크 연계                    |
| **Configuration**   | 런타임 구성 설정 (OSGi Config 포함)          |
| **Backup**          | 리포지토리 백업 작업 관리                      |
| **Health Reports**  | 시스템 상태 리포트 — 성능·구성 점검               |
| **Diagnosis**       | 문제 진단 도구 — 로그·스레드 덤프 등              |
| **Maintenance**     | 유지보수 작업 스케줄링 — 예: 데이터 정리            |
| **Monitoring**      | 자원 사용량, 트래픽, 큐 상태 모니터링              |
| **Jobs**            | 비동기 작업(Job) 상태 모니터링/관리              |
### Sites
| 메뉴                        | 설명                                         |
| ------------------------- | ------------------------------------------ |
| **Blueprints**            | Multi Site Manager(다국어/멀티사이트) 마스터 블루프린트 관리 |
| **Launches**              | 컨텐츠 사전 배포/출시 관리 (Launch 복제본)               |
| **ContextHub**            | 사용자 컨텍스트 데이터 관리 (퍼스널라이제이션 세그먼트)            |
| **External Link Checker** | 외부 링크 유효성 검사 도구                            |
### Assets
| 메뉴                                 | 설명                          |
| ---------------------------------- | --------------------------- |
| **GraphQL**                        | Assets GraphQL API 관리       |
| **Content Fragment Models**        | Content Fragment 구조(스키마) 정의 |
| **Connected Assets Configuration** | 원격 DAM 연계 설정                |
| **Metadata Profiles**              | 에셋 메타데이터 자동 할당 프로필          |
| **Folder Metadata Schemas**        | 폴더별 메타데이터 스키마               |
| **Metadata Schemas**               | 전체 메타데이터 구조 관리              |
| **Desktop Tools for AEM**          | AEM Desktop App 설정          |
| **Insights Configuration**         | Adobe Analytics 연계 설정       |
| **Reports**                        | 에셋 사용량, 상태 등 보고서            |
### Resources
| 메뉴                      | 설명               |
| ----------------------- | ---------------- |
| **Documentation**       | AEM 공식 문서 바로가기   |
| **Developer Resources** | API 문서, 샘플 코드 링크 |
### Deployment
| 메뉴               | 설명                                          |
| ---------------- | ------------------------------------------- |
| **Replication**  | 작성 → 게시로 컨텐츠 배포 설정                          |
| **Distribution** | 콘텐츠 배포 경로(Author ↔ Publish ↔ Dispatcher) 설정 |
| **Packages**     | 패키지(.zip) 생성/배포/설치                          |
| **Topology**     | 작성/게시/Dispatcher 토폴로지 상태                    |
| **Offloading**   | 작업 오프로딩 설정 (예: 렌더링을 외부 노드로)                 |
### Security
| 메뉴                           | 설명                                   |
| ---------------------------- | ------------------------------------ |
| **Adobe IMS Configurations** | Adobe Identity Management Service 연계 |
| **Users**                    | 사용자 계정 관리                            |
| **Groups**                   | 사용자 그룹 관리                            |
| **Permissions**              | 권한(ACL) 설정                           |
| **OAuth Clients**            | OAuth 클라이언트 앱 등록                     |
| **SSL Configuration**        | SSL 인증서 구성                           |
| **Trust Store**              | 신뢰할 수 있는 인증서 저장소                     |

### Cloud Services
| 메뉴                                       | 설명                        |
| ---------------------------------------- | ------------------------- |
| **Legacy Cloud Services**                | 기존 Adobe 클라우드 서비스 연동      |
| **Translation Cloud Services**           | 번역 클라우드 서비스 설정            |
| **YouTube Publishing Configuration**     | 유튜브 게시 설정                 |
| **Scene7 Configuration**                 | Dynamic Media 연계          |
| **Adobe Stock**                          | Adobe Stock 연결            |
| **Adobe Launch Configurations**          | 태그 관리(AEM ↔ Adobe Launch) |
| **reCAPTCHA**                            | 구글 reCAPTCHA 설정           |
| **Adobe Fonts**                          | Adobe Fonts 연계            |
| **Facebook Social Login Configuration**  | 페이스북 소셜 로그인 설정            |
| **Twitter Social Login Configuration**   | 트위터 소셜 로그인 설정             |
| **Pinterest Social Login Configuration** | 핀터레스트 소셜 로그인 설정           |
| **AEM Brand Portal**                     | Brand Portal 연동           |

### Communities
| 메뉴                        | 설명                             |
| ------------------------- | ------------------------------ |
| **Storage Configuration** | UGC 저장소 설정 (예: MongoDB, TarMK) |
| **Component Guide**       | 커뮤니티 컴포넌트 예제                   |
| **Community Functions**   | 포럼/그룹 등 커뮤니티 기능                |
| **Group Templates**       | 사용자 그룹 템플릿                     |
| **Site Templates**        | 커뮤니티 사이트 템플릿                   |
| **Community Badges**      | 사용자 뱃지(포인트 시스템)                |

### Commerce
| 메뉴                   | 설명       |
| -------------------- | -------- |
| **Payment Methods**  | 결제 수단 설정 |
| **Shipping Methods** | 배송 옵션 설정 |

# AEM DAM을 쓰는 실질적인 이유
### (1) 자산의 중앙 관리
모든 이미지, 동영상, PDF 등을 한곳에서 관리 → 중복 제거, 파일 찾기 쉬움.  
전사 브랜드 관리(로고, 캠페인 이미지) 가능.
### (2) 메타데이터 관리
IPTC, EXIF, 사용자 정의 메타필드 저장.  
키워드, 태그, 권한 등으로 자산 검색이 빠르고 정확.
### (3) 렌디션(자동 리사이즈)
이미지 업로드 시 자동으로 썸네일/모바일용/웹용 등 여러 버전을 자동 생성.  
팀원이 각자 수동 리사이즈 안 해도 됨.
### (4) 워크플로우 연계
승인, 리뷰, 게시 같은 컨텐츠 흐름을 자동화.  
DAM에 올린 이미지가 자동으로 승인 요청 → 승인이 나면 페이지에 반영.
### (5) Experience Manager와 통합
DAM에 있는 이미지/비디오를 바로 페이지 편집기에서 Drag & Drop.  
Headless API(Content Fragment, GraphQL)와 연계해 멀티채널 제공.
### (6) 버전 관리
파일 수정 이력 추적 가능.  
잘못 올렸으면 이전 버전으로 복구 가능.
### (7) 브랜드 일관성
다국적, 다채널에 동일한 이미지/동영상을 배포 → 브랜드 가이드라인 유지.
### AEM DAM이 없다면?
파일 서버(Share Drive) 쓰거나 다른 DAM을 별도로 연동해야 함.  
메타데이터, 워크플로우, 페이지 편집기와 연결이 복잡.  
중복 업로드, 버전 관리 혼란, 승인 프로세스 누락 발생.
### 주요 사용 케이스
- 대기업 브랜드 포털 
- 글로벌 웹사이트 운영 (국가별 이미지 버전 관리)
- 대규모 마케팅 캠페인 (이미지/동영상 자산 공유)
- 여러 에디터가 동시에 협업할 때

# Adobe DAM(AEM Assets) 대표적인 글로벌 기업 사례
대기업의 글로벌 브랜드 관리, 옴니채널 콘텐츠 배포, 협업 효율화

### Coca-Cola
배경: 전 세계 수백 개 마케팅 캠페인을 각국 지사에서 따로 관리하다보니, 이미지/영상 중복 저장, 버전 혼란, 브랜드 가이드라인 불일치 문제가 심각했음.  
__AEM DAM 도입 후:__  
- 글로벌, 지역, 파트너사 모두 하나의 중앙 DAM에서 최신 자산 사용.  
- 마케팅팀은 승인된 이미지/영상만 사용 → 브랜드 일관성 확보.  
- Brand Portal로 파트너사에 쉽게 배포.

__효과:__
- 자산 재활용률 ↑ 
- 제작 비용 ↓ 
- 캠페인 런칭 시간 단축

### Under Armour
배경: 제품 이미지와 캠페인 콘텐츠가 여러 부서에 흩어져 있어 전자상거래 사이트, 앱, 광고 채널 간 자산 관리가 비효율적이었음.  
__AEM DAM 도입 후:__  
- 제품 사진, 영상, 소셜 광고 이미지를 통합 관리.  
- Experience Fragment로 전자상거래 페이지에 빠르게 연동.  
- 다양한 해상도로 자동 렌디션 생성 → 모바일/웹 최적화.  

__효과:__
- 채널별 맞춤 콘텐츠 배포 자동화
- 승인 워크플로우로 품질 통제
- 신규 제품 런칭 속도 대폭 단축

### Nissan
배경: 글로벌 자동차 브랜드로서 현지 딜러사에 최신 차량 이미지와 영상을 정확히 전달해야 하는데, 각국에서 재촬영하거나 수정본 사용 등 혼선이 많았음.  
__AEM DAM 도입 후:__  
- 중앙에서 승인된 차량 이미지와 스펙 시트 배포.  
- 각국 딜러사/광고대행사가 Brand Portal로 즉시 다운로드.  
- 현지 언어로 번역된 버전 자동 제공.

__효과:__
- 브랜드 통일성 유지
- 비승인 자료 유통 방지
- 현지 마케팅 소요 시간 단축

### Philips
배경: 제품 이미지, 사용설명서, 영상 등 디지털 자산이 부서별로 나뉘어 있고, 수많은 버전 관리 어려움.  
__AEM DAM 도입 후:__  
- 중앙 DAM에 마스터 파일만 저장.  
- 국가별 버전은 번역 워크플로우와 연결.  
- Experience Manager Sites와 연결해 웹사이트에 자동 노출.  

__효과:__
- 자산 찾는 시간 절감
- 일관된 브랜딩 유지
- 내부 승인/번역 비용 절감

### 공통 성공 요소
- 승인 & 메타데이터 표준화: 누구나 정확한 자산 검색 가능
- 자동 렌디션/포맷: 웹, 앱, SNS별 사이즈 자동 생성
- 워크플로우: 승인/번역/만료 자동화
- Brand Portal: 외부 협력사 배포 효율화