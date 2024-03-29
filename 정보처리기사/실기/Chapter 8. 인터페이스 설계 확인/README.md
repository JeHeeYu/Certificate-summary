# 인터페이스 설계 확인 과목 정리 내용

# 외부 및 내부 모듈 연계를 위한 인터페이스 기능 식별(:star::star::star:)

## 1. 외부, 내부 모듈 연계 방법(EAI, ESB 연계 방법)
- 기업 시스템이나 공공 서비스를 위한 시스템에서 **인터페이스를 위해 외부 및 내부 모듈을 연계**하는 대표적인 방법은 **EAI 방식과 ESB 방식**이 있음

### 1-1. EAI(Enterprise Application Intergration) 방식
- EAI는 기업에서 운영되는 **서로 다른 플랫폼 및 애플리케이션 간의 정보를 전달, 연계, 통합이 가능하도록 해주는 솔루션**임
- EAI를 사용함으로써 **각 비즈니스 간 통합 및 연계성을 증대시켜 효율성을 높여**줄 수 있으며 **각 시스템 간의 확장성을 높여**줄 수 있음

#### EAI 구축 유형
|구축 유형|설명|
|:---:|:---|
|<b>포인트 투 포인트</b><br>(Point-to-Point)|가장 기초적인 애플리케이션 통합방법으로 1:1 단순 통합방법|
|<b>허브 앤 스포크</b><br>(Hub & Spoke)|- 단일한 접점의 허브 시스템을 통하여 데이터를 전송하는 중앙 집중식 방식<br>- 허브 장애 시 전체 장애 발생|
|<b>메시지 버스</b><br>(Message Bus)|- 애플리케이션 사이 미들웨어(버스)를 두어 연계하는 미들웨어 통합 방식<br>- 뛰어난 확장성과 대용량 데이터 처리 가능|
|<b>하이브리드</b><br>(Hybrid)|- 그룹 내부는 허브 앤 스포크 방식을 사용하고, 그룹 간에는 메시지 버스 방식을 사용하는 통합 방식<br>- 그룹 내부 환경에 맞는 작업 가능|

### 1-2. ESB(Enterprise Service Bus) 방식
- ESB는 기업에서 운영되는 **서로 다른 플랫폼 및 애플리케이션들 간을 하나의 시스템으로 관리 운영할 수 있도록 서비스 중심의 통합을 지향하는 아키텍처**임
- ESB는 버스를 중심으로 각각 프로토콜이 호환될 수 있도록 애플리케이션의 통합을 느슨한 결합 방식으로 지원함


<br>


---


<br>


# 외부 및 내부 모듈 간 인터페이스 데이터 표준 확인(:star::star:)

## 1. 인터페이스 데이터 표준 확인
- 인터페이스 데이터 표준 확인은 **상호 연계하고자 하는 시스템 간 인터페이스 되어야 할 범위의 데이터 형식과 표준을 정의하는 활동**임
- 인터페이스 데이터 전송 시 인터페이스 **데이터 형태가 동일한 경우는 그대로 전송, 동일하지 않은 경우는 변환하여 전송**
- 송수신 시스템 간의 인터페이스 데이터를 표준화하기 위해서는 송수신 데이터 중 공통의 영역을 추출하여 정의하는 경우, 한쪽의 데이터를 변환하는 경우가 있음

![image](https://user-images.githubusercontent.com/87363461/232176117-41f83a86-d9cb-4d25-ad17-f507d8207942.png)

<br>

## 2. 송수신 시스템 간 인터페이스 데이터 표준 확인 절차

### 2-1. 식별된 데이터 인터페이스를 통해 인터페이스 데이터 표준 확인

#### 1. 데이터 인터페이스 입출력 의미 파악
- 식별된 데이터 인터페이스의 입력값, 출력값이 의미하는 내용 파악
- 각 출력값이 의미하는 바와 데이터의 특성 등 참고할만한 사항을 구체적으로 작성

<br>

---

<br>

# 인터페이스 기능 구현(:star::star::star:)

## 1. 인터페이스 기능 구현

### 1-1. JSON(JavaScript Object Notation)

#### 1. JSON의 개념
- JSON은 속성-값(Attribute-Value Pair) 쌍 또는 "키-값 쌍"으로 이루어진 데이터 오브젝트를 전달하기 위해 텍스트를 사용하는 **개방형 표준 포맷임**

#### 2. JSON의 특징
- AJAX에서 많이 사용되고, XML을 대체하는 주요 데이터 포맷
- 언어 독립형 데이터 포맷으로 다양한 데이터 프로그래밍 언어에서 사용됨
- 사람이 읽고 쓰기에 용이하며, 기계가 분석하고 생성하기에 용이함

#### 3. JSON 표현 자료형
|자료형|사례|
|:---:|:---|
|<b>숫자</b><br>(Number)|- 기본 자료형의 수는 정수, 실수(고정소수점), 실수(부동소수점)로 표현<br>- 74, 3.14, 3.4e + 4|
|<b>문자열</b><br>(String)|- 항상 큰 따옴표로 묶어야 하며, 그 안에는 유니코드 문자들이 나열<br>- "ABC", "1234"|
|<b>배열</b><br>(Array)|- 배열은 대괄호로 표시, 배열의 각 요소는 기본 자료형이거나 배열, 객체임<br>- 각 요소들은 쉼표로 구별되고 각 요소가 나타나는 순서에 의미가 있음<br>- [10, {"V":20}, [30, "마흔"]|
|<b>객체</b><br>(Object)|- 객체는 이름/값 쌍의 집합으로 중괄호 사용<br>- 이름이 문자열이기 때뭉네 반드시 따옴표표를 하며 값은 기본 자료형<br>- 각 쌍들은 쉼표로 구별되고 각 쌍이 나오는 순서는 의미가 없음<br>- {"name2:" : 40", "name3": "값3", "name" : true}|

#### 4. jSON 문법

|구분|설명|
|:---:|:---|
|<b>구조</b>|- name/value 쌍으로 구성<br>- '{'로 시작하고 '}'로 끝남<br>- 배열은 대괄호 []로 나타냄|
|<b>내용</b>|- { 내용 ... }|
|<b>도구</b>|- Parser : JSON text 파일을 해석하고 자바 오브젝트로 변환<br>- Render : 자바를 text로 표현<br>- Serializer : POJO를 JSON 표현으로 직렬화<br>- Mapper : POJO와 SJON을 매핑<br>- Validator : JSON 스키마를 이용해서 파일 내용 유효성 체크|


#### 5. JSON 장단점
|장점|단점|
|:---|:---|
|- XML보다 가볍고 빠름<br>- 자료 종류에 큰 제한이 없음<br>- XML은 모두 String, JSON은 String, Number, Array 등 다양함<br>- Javascript 코드 안에서 JSON 객체에 접근이 쉬움|- 태그가 없어서 가독성이 떨어짐<br>- DTD같은 것이 없어 데이터 형식이 틀렸을 경우 체크 어려움|

### 1-2. XML(Extensible Markup Language)

#### 1. XML의 개념
- XML은 **HTML의 단점을 보완한 인터넷 언어**로, SGML의 복잡한 단점을 개선한 특수한 목적을 갖는 마크업 언어임

#### 2. XML의 특징
- XML은 **송수신 시스템 간 데이터 연계의 편의성을 위해서 전송되는 데이터 구조를 동일한 형태로 정의**함
- 인간과 기계가 모두 이해할 수 있는 텍스트 형태로 마크업 포맷을 정의하기 위한 메타언어임
- 사용자가 직접 문서의 태그를 정의할 수 있으며, **다른 사용자가 정의한 태그를 사용할 수 있음**


### 1-3. AJAX(Asynchronous Javascript ANd XML)

#### 1. AJAX의 개념
- AJAX는 자바스크립트를 사용하여 **웹 서버와 클라이언트 간 비동기적으로 XML 데이터를 교환하고 조작하기 위한 웹 기술**임
- 브라우저가 가지고 있는 XMLHttpRequest 객체를 이용해서 전체 페이지를 새로 로드하지 않고 필요한 일부 페이지의 데이터만을 로드하는 기법
- HTML만으로는 어려운 다양한 작업을 웹 페이지에서 구현해서 이용자가 웹 페이지와 자유롭게 상호 작용할 수 있도록 구현하는 기법

#### 2. AJAX의 주요 기술

|주요 기술|설명|
|:---:|:---|
|<b>XMLHttpRequest</b><br>|- 웹 브라우저와 웹 서버 간에 메서드가 데이터를 전송하는 객체 폼의 API<br>- 비동기 통신을 담당하는 자바스크립트 객체|
|<b>Javascript</b><br>|- 객체 기반의 스크립트 언어<br>- 웹 브라우저 내에서 주로 사용하며, 다른 응용 프로그램의 내장 객체에도 접근할 수 있는 기능 소유|
|<b>XML</b><br>(Extensible Markup<br>Language)|- HTML의 단점을 보완한 인터넷 언어로, SGML의 단점을 개선한 특수한 목적을 갖는 마크업 언어|
|<b>DOM</b><br>(Document<br>Object Model)|- XML 문서를 트리 구조의 형태로 접근할 수 있게 해주는 API<br>- 플랫폼/언어 중립적으로 구조화된 문서를 표현하는 객체 지향 모델|
|<b>XSLT</b><br>(Extensible<br>Stylesheet Language<br>Transformations)|- XML 문서를 다른 XML 문서로 변환하는 데 사용하는 XML 기반 언어<br>- W3C에서 제정한 표준으로 XML 변환 언어를 사용하여 XML 문서로 바꿔주며, 탐색하기 위해 XPath 사용|
|<b>HTML</b><br>(HyperText<br>Markup Language)|- 인터넷 웹(WWW) 문서를 표현하는 표준화된 마크업 언어|
|<b>CSS</b><br>(Cascading Style<br>Sheets)|- 마크업 언어가 실제 표시되는 방법을 기술하는 언어<br>- 운영체제나 사용 프로그램과 관계없이 글자 크기, 간격, 색상 등을 자유롭게 선택할 수 있는 스타일 시트|

#### 3. AJAX의 동작 원리

1. 사용자에 의한 이벤트 발생
2. 요청 이벤트가 발생하면 이벤트 핸들러에 의해 자바스크립트 호출
3. 자바스크립트는 XMLHttpRequest 객체를 사용하여 서버로 요청, 이때 웹 브라우저는 요청을 보내고 나서 서버의 답을 기다릴 필요 없이 다른 작업 처리 가능
4. 서버는 전달받은 XMLHttpRequest 객체를 가지고 AJAX 요청 처리
5. 서버는 처리한 결과를 HTML, XML, JSON의 형태의 데이터로 웹 브라우저에 전달
6. 서버로 전달받은 데이터를 가지고 웹 페이지의 일부분만을 갱신하는 자바스크립트 호출
7. 결과적으로 웹 페이지의 일부분만이 다시 로딩 되어서 표시

![image](https://user-images.githubusercontent.com/87363461/232177172-6f0e3843-d3e0-4c21-971c-a02c0aaddcd6.png)

<br>


### 1-4. REST(Representational State Transfer)

#### 1. REST의 개념
- REST는 웹과 같은 분산 하이퍼미디어 환경에서 **자원의 존재/상태 정보를 표준화된 HTTP 메서드로 주고받는 웹 아키텍처**임
- REST는 웹의 창시자(HTTP) 중의 한 사람인 Roy Fielding의 2000년 논문에 의해서 소개됨

#### 2. REST의 기본 형태
- REST는 크게 리소스(자원), 메서드(처리), 메시지 3가지 요소로 구성됨

![image](https://user-images.githubusercontent.com/87363461/232177226-2482ba1b-a6d1-478a-8af6-5f2c2adbd1ce.png)

#### 사례
- "이름이 페코페코인 사용자를 생성한다"라는 호출이 있을 때
- "사용자"는 생성되는 리소스, "생성한다"라는 행위 메서드, '이름이 페코페코인 사용자'는 메시지가 됨

#### REST 메서드
- REST 메서드는 행위에 대한 메서드를 HTTP 메서드 중 CRUD에 해당하는 4가지 메서드만 사용함

|메서드|의미|
|:---:|:---|
|<b>POST</b>|Create(생성)|
|<b>GET</b>|Read(조회)|
|<b>PUT</b>|Update(수정)|
|<b>DELETE</b>|Delete(삭제)|

#### 3. REST 특징

|특징|설명|
|:---:|:---|
|<b>클라이언트/서버 구조</b>|역할이 명확히 구분되기 때문에 클라이언트와 서버는 독립적으로 구현되어야 하며 서로 간 의존성은 축소|
|<b>무 상태성</b>|- 작업을 위한 상태 정보를 따로 저장하고 관리하지 않기 때문에 API 서버는 들어오는 요청만 단순히 처리<br>- 서버에서 불필요한 정보를 관리하지 않음으로써 구현이 단순함|
|<b>일관된 인터페이스</b>|- HTTP 표준에만 따른다면 특정 언어나 기술에 종속되지 않고 모든 플랫폼에 사용할 수 있음<br>- URL로 지정한 리소스에 대한 조작이 가능한 아키텍처 스타일|
|<b>- 캐시 처리 기능</b>|- HTTP가 가진 캐싱 기능 적용 가능<br>- HTTP 프로토콜 표준에서 사용하는 Last-Modified 태그나 E-Tag를 이용하면 캐싱 구현 가능|
|<b>자체 표현 구조</b>|- API 메시지 자체만 보고도 API를 이해할 수 있는 구조를 가짐<br>- 리소스와 메서드를 이용해서 어떤 메서드에 무슨 행위를 하는지를 알 수 있음<br>- 또한 메시지 포맷 역시 JSON을 이용해서 직관적으로 이해가 가능한 구조|


<br>

---

<br>



# 인터페이스 보안 기능 적용(:star::star:)


## 1. 인터페이스 보안 취약점

### 1-1. 데이터 통신 시 데이터 탈취 위협
- 인터페이스를 위한 송수신 시스템 간의 데이터 통신 시 **스니핑을 통해 데이터 전송 내역을 감청하여 데이터를 탈취하는 위협이 존재**함

### 1-2. 데이터 통신 시 데이터 위변조 위협
- 인터페이스를 위한 송수신 시스템 간의 데이터 통신 시 데이터에 대한 삽입, 삭제, 변조 공격을 통한 시스템 위협이 존재

## 2. 인터페이스 보안 구현 방안


### 2-1. 시큐어 코딩 가이드 적용
- 인터페이스 개발 시 보안 취약점을 방지할 수 있는 시큐어 코딩 가이드에 따른 개발 수행 필요

#### 시큐어 코딩 가이드
|적용 대상|보안 약점|대응 방안|
|:---:|:---|:---|
|<b>입력데이터 검증 및 표현</b>|프로그램 입력값에 대한 검증 누락 및 부적절한 검증 잘못된 형식 지정|사용자 및 프로그램 입력 데이터에 대한 유효성 검증 체계를 수립하고 실패 시 처리 기능 설계 및 구현|
|<b>보안 기능</b>|보안 기능(인증, 접근 제어, 기밀성, 암호화, 권한 관리 등)의 부적절한 구현|인증 및 접근 통제, 권한 관리, 비밀번호 등의 정책이 적절하게 반영되도록 설계 및 구현|
|<b>시간 및 상태</b>|거의 동시에 수행 지원하는 병렬 시스템, 하나 이상의 프로세스가 동작하는 환경에서 시간 및 상태의 부적절한 관리|공유 자원의 접근 직렬화, 병렬 실행 가능 프레임워크 사용, 블록문 내에서만 재귀 함수 호출|
|<b>에러 처리</b>|에러 미처리, 불충분한 처리 등으로 에러 메시지에 중요 정보가 포함|- 에러 상황을 처리하지 않거나, 불충분하게 처리되어 중요 정보 유출 등 보안 약점 발생하지 않도록 시스템 설계 및 구현|
|<b>코드 오류</b>|개발자가 범할 수 있는 코딩 오류로 인해 유발|코딩 규칙 도출 후 검증 가능한 스크립트 구성과 경고 순위의 최상향 조정 후 경고 메시지 코드 제거|
|<b>캡슐화</b>|기능성이 불충분한 캡슐화로 인해 인가되지 않은 사용자에게 데이터 누출|디버거 코드 제거와 필수정보 외에 클래스 내 프라이빗 접근자 지정|
|<b>API 오용</b>|의도된 사용에 반하는 방법으로 API를 사용하거나, 보안에 취약한 API의 사용|개발 언어별 취약 API 확보 및 API 검출 프로그램 사용|


### 2-2. 데이터베이스 보안 적용
- 데이터베이스의 기밀성을 유지하기 위해서 인터페이스 시 활용되는 중요 데이터에 대해서는 필요한 보안 요구사항을 적용함
- 현재 시점에서 안전성이 검증된 암호화 알고리즘을 활용하여 중요한 민감 데이터는 반드시 암호화하고, 데이터베이스 보안 요구사항은 해당 인터페이스 조건에 부합되도록 적용

#### 1. 데이터베이스 암호화 알고리즘

|구분|설명|
|:---:|:---|
|<b>대칭 키 암호화<br>알고리즘</b>|암호화 알고리즘의 한 종류로, 암호화 및 복호화에 같은 암호 키를 쓰는 알고리즘을 의미<br><br>- 예) ARIA 128/192/256, SEED|
|<b>비대칭 키 암호화<br>알고리즘</b>|공개키는 누구나 알 수 있지만, 그에 대응하는 비밀키는 키의 소유자만이 알 수 있도록, 공개키와 비밀키를 사용하는 알고리즘<br><br>- 예) RSA, ECC, ECDSA|
|<b>해시 암호화<br>알고리즘</b>|해시값으로 원래 입력값을 찾아낼 수 없는 일방향성의 특성을 가진 알고리즘<br><br>- 예) SHA-256/384/512, HAS-160|

#### 2. 데이터베이스 암호화 기법

|구분|구성도|설명|
|:---:|:---:|:---|
|<b>API 방식</b>|![image](https://user-images.githubusercontent.com/87363461/232177912-18e692eb-7ce9-4485-91d8-68d765d4b317.png)|- 애플리케이션 레벨에서 암호 모듈(API)을 적용하는 애플리케이션 수정 방식<br>- 애플리케이션 서버에 암.복호화, 정책 관리, 키 관리 등의 부하 발생|
|<b>Plug-in 방식</b>|![image](https://user-images.githubusercontent.com/87363461/232177939-249245ea-5218-40f0-afe1-d33fe91d9cf5.png)|- 암.복호화 모듈이 DB 서버에 설치된 방식<br>- DB 서버에 암.복호화, 정책 관리, 키 관리 등의 부하 발생|
|<b>TDE 방식</b>|![image](https://user-images.githubusercontent.com/87363461/232177976-f13c08d6-a4fc-4ad6-a194-6cf8d71564ee.png)|- DB 서버의 DBMS 커널이 자체적으로 암.복호화 기능을 수행하는 방식<br>- 내장되어 있는 암호화 기능(TDE, Transparent Data Encryption)을 이용|
|<b>Hybrid 방식</b>|![image](https://user-images.githubusercontent.com/87363461/232178008-e358786f-78ea-4ec5-b7ce-1f61933937fe.png)|- API 방식과 Plug-in 방식을 결합하는 방식<br>- DB 서버와 애플리케이션 서버로 부하|

<br>

---

<br>

# 인터페이스 구현 검증(:star::star:)

## 1. 인터페이스 구현 검증 도구의 개념
- 인터페이스 구현 검증 도구는 **인터페이스 동작 상태를 검증하고 모니터링할 수 있는 도구**임
- 인터페이스 구현을 검증하기 위해서는 인터페이스 세부 기능을 기능 단위로 테스트하는 단위 테스트와 전체 인터페이스 흐름을 확인할 수 있는 시나리오를 통한 통합 테스트가 필요함
- 인터페이스 구현 검증 도구들을 통해서 테스트의 효율성을 높일 수 있음


## 2. 인터페이스 구현 검증 도구의 종류

|도구|설명|
|:---:|:---|
|<b>xUnit</b>|- 자바(jUnit), C++(cppUnit), .net(nUnit) 등 다양한 언어를 지원하는 단위테스트 프레임워크<br>- 소프트웨어의 함수나 클래스 같은 서로 다른 구성 원소(단위)를 테스트할 수 있게 해주는 도구|
|<b>STAF</b>|- 서비스 호출, 컴포넌트 재사용 등 다양한 환경을 지원하는 테스트 프레임워크<br>- 각 테스트 대상 분산 환경에 데몬을 사용하여 테스트 대상 프로그램을 통해 테스트를 수행하고, 통합하며 자동화하는 검증 도구|
|<b>FitNesse</b>|- 웹 기반 테스트 케이스 설계/실행/결과 확인 등을 지원하는 테스트 프레임워크<br>- 사용자가 테스트 케이스 테이블을 작성하면 빠르고 편하게 자동으로 원하는 값에 대해 테스트를 할 수 있는 장점이 있음|
|<b>NTAF</b>|- FitNesse의 장점인 협업 기능과 STAF의 장점인 재사용 및 확장성을 통합한 NHN(Naver)의 테스트 자동화 프로그램|
|<b>Selenium</b>|- 다양한 브라우저 지원 및 개발언어를 지원하는 웹 애플리케이션 테스트 프레임워크<br>- 테스트 스크립트 언어를 학습할 필요 없이 기능 텍스트를 만들기 위한 도구 제공|
|<b>watir</b>|- 루비 기반 웹 애플리케이션 테스트 프레임워크<br>- 모든 언어 기반의 웹 애플리케이션 테스트와 브라우저 호환성 테스팅 가능|

## 3. 인터페이스 감시 도구
- 인터페이스의 돚악이 잘 진행되는지 지속적으로 확인하기 위해서는 애플리케이션 모니터링 툴(APM, Application Performance Management)을 사용하여 동작 상태 감시 가능
- 데이터베이스, 웹 애플리케이션의 트랜잭션과 변숫값, 호출 함수, 로그 및 시스템 부하 등 종합적인 정보를 조회하고 커넥션 풀(Connection Pools)등 지속적인 모니터링이 필요한 자원을 효과적으로 관리할 수 있음

#### 인터페이스 감시 도구
|도구|설명|
|:---:|:---|
|<b>스카우터</b><br>(SCOUTER)|애플리케이션에 대한 모니터링 및 DB Agent를 통해 오픈 소스 DB 모니터링 기능, 인터페이스 감시 기능 제공|
|<b>제니퍼</b><br>(Jennifer)|애플리케이션의 개발부터 테스트, 오픈, 운영, 안전화까지 전 생애주기 단계 동안 성능을 모니터링하고 분석해주는 APM 소프트웨어|

## 4. 인터페이스 구현 검증에 필요한 설계 산출물
- 모듈 설계 설계서(컴포넌트 명세서, 인터페이스 명세서), 인터페이스 정의서, 정적 및 동적 모형 설계도, 식별된 인터페이스 기능 목록, 인터페이스 데이터 표준 정의서 등 인터페이스 설계 산출물 분석이 인터페이스 구현 검증에 필요함
- 인터페이스 단위 테스트 케이스, 통합 테스트 케이스를 활용하여 최종적으로 인터페이스 구현 검증함

## 5. 인터페이스 구현 검증 프로세스

### 5-1. 인터페이스 명세서를 통한 구현 검증에 필요한 요건 분석
- 작성된 인터페이스 명세서의 세부 기능을 참조하여 구현 검증 및 감시에 필요한 기능을 분석함
- 각 기능의 특징에 맞게 구현 검증의 요건을 도출함

#### 인터페이스 명세서를 참조하여 구현 검증의 요건 분석
|기능 구현 정의|검증 요건|감시 요건|
|:---:|:---|:---|
|<b>송신 측에서<br>인터페이스<br>대상 선택 전송</b>|- 입력한 대상과 생성된 인터페이스 객체의 정보가 일치하는지 확인|- 데이터베이스 SQL 모니터링<br>- 조회 트랜잭션 모니터링<br>- 제이슨(JSON) 생성 객체 모니터링|
|<b>인터페이스<br>객체 전송</b>|- 암호화된 통신으로 올바르게 수신측에 전달되었는지 확인<br>- 전달된 정보가 수신된 정보와 일치하는지 확인<br>- 파싱된 정보가 송신된 정보와 일치하는지 확인|- 통신 암호화 모니터링<br>- 패킷 정보 모니터링<br>- 연결된 트랜잭션 변수 모니터링|
|<b>수신 후 수신측<br>트랜잭션 결과 반환</b>|- 수신된 데이터와 연관 있는 이후 트랜잭션의 결괏값과 일치 여부|- 객체 입력, 출력값 모니터링<br>- 객체 동작 성공, 실패 여부 모니터링|

### 5-2. 구현 검증에 필요한 감시 및 검증 도구 준비
- 구현 검증 및 감시에 필요한 요건을 확인 후 **적절한 감시 및 검증에 필요한 도구 선택**
- 최근에는 오픈 소스 기반의 구현 검증 및 감시 도구가 많이 활용되고 있으므로 기능 분석을 통해 가장 적절한 도구 선택

### 5-3. 인터페이스 구현 검증 수행
- 인터페이스 구현 검증을 위하여 외부 시스템(송수신)과 연계 모듈(수송신)의 동작 상태를 인터페이스 구현 검증 도구를 통해 확인함
- 인터페이스 명세서 기반으로 도출된 요구 분석 내용을 토대로 인터페이스 동작 프로세스 상에서 예상되는 결괏값과 검증 값을 비교함
- 단계별 오류 처리도 적절하게 구현되어 있는지 검증 도구를 통해 확인함
