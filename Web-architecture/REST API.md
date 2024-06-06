# REST API

- 참고 링크
    - [https://www.ibm.com/kr-ko/topics/rest-apis](https://www.ibm.com/kr-ko/topics/rest-apis)

![Untitled](./REST%20API%20images/Untitled.png)

- **REST API**란?
    - **REST API**는 **REST(Representational State Transfer)** 아키텍처 스타일의 설계 원칙을 준수하는 **API(Application Programming Interface)**이다.
    - **REST API**는 어플리케이션을 통합하고 **마이크로서비스** 아키텍처의 구성 요소를 연결하는 유연하고 가벼운 방법을 제공한다.
    - **HTTP** **URI**를 통해 제어할 자원(Resource)을 명시하고, `HTTP method(GET/POST/PUT/DELETE)`를 통해 해당 자원(Resource)를 제어하는 명령을 내리는 방식의 아키텍처이다.
    - 표준이 정해진 것이 없어 관례 정도로 사용하는 Rule이 있음
        - 하이픈(-)은 사용 가능하지만 언더바(_)는 사용하지 않는다.
        - 특별한 경우를 제외하고 대문자 사용은 하지 않는다.(대소문자 구분을 하기 때문)
        - URI 마지막에 슬래시(/)를 사용하지 않는다.
        - 슬래시(/)로 계층 관계를 나타낸다.
        - 확장자가 포함된 파일 이름을 직접 포함시키지 않는다.
        - URI는 명사를 사용한다.

- REST 구성
    - **자원(Resouce) - URL**
        - 모든 자원에는 고유 ID가 존재하고, 이 자원은 Server에 존재한다.
        - 자원을 구별하는 ID는 **HTTP URI(Uniform Resource Identifier)**이다.
    - **행위(Verb) - HTTP method**
        - HTTP 프로토콜의 method를 사용한다.
        - HTTP 프로토콜은 `GET`, `POST`, `PUT`, `DELETE`와 같은 메소드를 제공한다.
    - **표현(Representation)**
        - Client가 자원의 상태(정보)에 대한 조작을 요청하면 Server는 이에 적절한 응답(Response)를 보낸다.
        - REST에서 하나의 자원은 JSON, XML 등 여러 형태의 응답으로 나타낼 수 있다.
        - 현재는 대부분 **JSON**으로 주고받는다.

- 기존 Service와 **REST API Service**
    - 기존 Service : 요청에 대한 처리를 한 후 가공된 data를 이용하여 **특정 플랫폼에 적합한 형태의 View로 만들어서 반환**
    - **REST API Service** : data 처리만 하거나 처리 후 반환될 data가 있다면 **JSON이나 XML 형식으로 전달**한다. View에 대해서 신경쓰지 않아 **Open API에서 많이 사용**한다.
        
        ![Untitled](./REST%20API%20images/Untitled%201.png)
        

- API URI 설계(기존)
    - 기존의 접근 방식은 GET과 POST 만으로 자원에 대한 C / R / U / D를 처리
    - **URI에 해당 기능을 추가 작성함**
    
    ![Untitled](./REST%20API%20images/Untitled%202.png)
    

- API URI 설계(REST API)
    - URI는 board라는 Resource를 활용하여 식별
    - **HTTP method를 통해 C / R / U / D 행위를 구분**
    
    ![Untitled](./REST%20API%20images/Untitled%203.png)
    

- REST 설계 원칙
    - 균일한 인터페이스
        - 동일한 리소스에 대한 모든 **API** 요청은 요청의 출처에 관계없이 동일하게 표시되어야 한다.
        - **API**는 사용자의 이름 또는 이메일 주소와 같은 동일한 데이터가 하나의 **URI(Uniform Resource Identifier)**에만 속하도록 해야 한다.
        - 리소스가 너무 커서는 안 되며 클라이언트가 필요로 할 수 있는 모든 정보를 포함해야 한다.
    - 클라이언트-서버 분리
        - **REST API** 설계에서 클라이언트 및 서버 애플리케이션은 서로 완전히 독립적이어야 한다.
        - 클라이언트 애플리케이션이 알아야 하는 유일한 정보는 요청된 리소스의 URI이며 서버 애플리케이션과 다른 방법으로 통신할 수 없다.
        - 마찬가지로 서버 애플리케이션은 HTTP를 통해 요청된 데이터에 클라이언트 애플리케이션을 전달하는 것 외에는 클라이언트 애플리케이션을 수정해서는 안 된다.
    - 무상태
        - **REST API**는 **무상태성**이기 때문에 각 요청에는 처리에 필요한 모든 정보가 포함되어야 한다.
        - 즉, **REST API**에는 **서버 측 세션이 필요하지 않다**는 의미이다..
        - 서버 애플리케이션은 클라이언트 요청과 관련된 데이터를 저장할 수 없습니다.
    - 캐시 가능성
        - 가능한 경우 클라이언트나 서버 측에서 리소스를 캐시할 수 있어야 한다.
        - 서버 응답에는 전달된 리소스에 대해 캐싱이 허용되는지 여부에 대한 정보도 포함되어야 한다.
        - 목표는 클라이언트 측의 성능을 향상시키는 동시에 서버 측의 확장성을 높이는 것이다.
    - 계층화된 시스템 아키텍처
        - **REST API**에서는 호출과 응답이 서로 다른 계층을 거친다.
        - 일반적으로 클라이언트와 서버 애플리케이션이 서로 직접 연결된다고 가정하지 않는다.
        - 통신 루프에는 다양한 중개자가 있을 수 있다.
        - **REST API**는 **클라이언트나 서버가 최종 애플리케이션과 통신하는지 중개자와 통신하는지 알 수 없도록 설계**해야 한다.
    - 코드 온디맨드(선택 사항)
        - **REST API**는 일반적으로 정적 리소스를 전송하지만 경우에 따라 응답에 실행 코드(예: Java 애플릿)가 포함될 수도 있다.
        - 이러한 경우 코드는 온디맨드 방식으로만 실행되어야 한다.

- REST API 작동 방식
    - **REST API**는 HTTP 요청을 통해 통신하여 리소스 내에서 레코드를 생성하고 읽기, 업데이트 및 삭제(CRUD)와 같은 표준 데이터베이스 기능을 수행한다.
    - **GET** 요청은 레코드를 검색한다.
    - **POST** 요청은 새 레코드를 생성한다.
    - **PUT** 요청은 레코드를 업데이트한다.
    - **DELETE** 요청은 레코드를 삭제한다.
    - **API** 호출에는 모든 HTTP 방식을 사용할 수 있다.
    - 잘 설계된 **REST API**는 HTTP 기능이 내장된 웹 브라우저에서 실행되는 웹 사이트와 유사하다.