# CH1. **REST API**💁🏻

## 1. REST API의 탄생

REST는 Representational State Transfer라는 용어의 약자로서 2000년도에 로이 필딩 (Roy Fielding)의 박사학위 논문에서 웹(http)의 장점을 최대한 활용할 수 있는 아키텍처로써 최초로 소개되었습니다.

REST API는 **웹에서 사용되는 데이터나 자원(Resource)을 HTTP URI로 표현하고, HTTP 프로토콜을 통해 요청과 응답을 정의하는 방식**을 말합니다.

HTTP프로토콜을 기반으로 요청과 응답에 따라 리소스를 주고받기 위해서는 알아보기 쉽고 잘작성된 메뉴판 역할인 API가 필요합니다. 

## 2. 모두가 잘알아볼 수 있는 REST API

REST API를 잘 적용하기 위한 4단계모델인 리차드슨의 REST성숙도 모델이있습니다. 


## 3. 그래서 REST API가 뭐야…?

HTTP URI(Uniform Resource Identifier)를 통해 자원(Resource)을 명시하고, HTTP Method (POST, GET, PUT, DELETE)를 통해 해당 자원에 대한 CRUD Operation을 적용하는 것을 의미한다고 합니다. 

즉, **REST는 자원기반의 구조 설계의 중심에 리소스가 있고, HTTP Method를 통해 리소스를 처리하도록 설계된 아키텍쳐**입니다. 

월드 와일드 웹(www)과 같은 분산 하이퍼미디어 시스템을 위한 소프트웨어 개발 아키텍쳐의 한 형식이며, REST는 기본적으로 웹의 기존기술과 HTTP 프로토콜을 그대로 활용하기 때문에 **웹의 장점을 최대한 활용할 수 있는 아키텍쳐** 스타일 입니다. (아키텍쳐는 컴퓨터 시스템의 하드웨어 구조를 말합니다.)

## 4. REST 구성요소

1. 자원(Resource) : URI
2. 행위(Verb) : HTTP Method
3. 표현(Representation of Resource)

# CH2. **REST API 성숙도 모델**💁🏻

## 1. 성숙도 모델 0단계- HTTP 사용

- 단순히 **HTTP 프로토콜**을 사용하기만 해도됩니다. 해당 API를 REST API라고 할 수는 없으며, 0단계는 REST API를 작성하기 위한 기본 단계입니다.
- EX) 요청 엔드포인트는 모두 /appointment 사용
    
    

## 2. 성숙도 모델 1단계- 개별 리소스와의 통신 준수

- 개별 리소스와의 통신을 준수해야합니다.
- REST API 는 **웹에서 사용되는 모든 데이터나 자원(Resource)을 HTTP URI로 표현한다**고 이야기했습니다. 따라서 모든 자원은 개별 리소스에 맞는 엔트포인트를 사용해야하며 요청하고 받는 자원에 대한 정보를 응답으로 전달해야 한다는 것이 1단계의 핵심입니다.
- EX) 요청하는 리소스에 따라 각기 다른 엔드포인트로 구분
    
    
- 엔드포인트 작성시 주의해야할 점
    - 동사, HTTP 메서드 혹은 어떤 행위에 대한 단어 사용은 지양해야합니다.
    - 리소스에 집중해 명사 형태의 단어로 작성해야합니다.
- EX) 요청에 따른 응답으로 리소스 전달시 성공,실패 여부를 반환해야합니다.
    
    

## 3. 성숙도 모델 2단계- HTTP 메소드 원칙 준수

- CRUD (Create, Read, Update, Delete) 에 맞게 적절한 HTTP 메서드를 사용해야합니다.
    
    
    | CRUD Operation |  |
    | --- | --- |
    | Creat(생성) | POST |
    | READ(조회) | GET |
    | Update(수정) | PUT |
    | Delete(삭제) | DELETE |
    | HEAD(header의 정보조회) | HEAD |
- EX) 예약가능한 시간을 확인하는 것은 **조회(READ)**하는 행위→ **`GET`** 메서드를 사용히야 요청
    - 특정시간에 예약하는 것은 **생성(CREAT)**하는 행위 → **`POST`** 메서드를 사용하여 요청
    - 새롭게 생성된 리소스를 보내주기 떄문에, 응답고크는 **201 Created**
    
    
- HTTP 메서드 사용시 주의사항
    - `GET` 메서드 같은 경우는 서버의 데이터를 변화시키지 않는 요청에 사용해야 합니다.
    - `POST` 메서드는 요청마다 새로운 리소스를 생성하고 `PUT` 메서드는 요청마다 같은 리소스를 반환합니다. 이렇게 매 요청마다 같은 리소스를 반환하는 특징을 멱등([idempotent](https://developer.mozilla.org/en-US/docs/Glossary/Idempotent))하다고 합니다. 그렇기 때문에 멱등성을 가지는 메서드 `PUT`과 그렇지 않은 메서드`POST`는 구분하여 사용해야 합니다.
    - `PUT` 메서드와 `PATCH` 메서드도 구분하여 사용해야 합니다. `PUT`은 교체, `PATCH`는 수정의 용도로 사용합니다.

## 4. 성숙도 모델 3단계- HATEOAS 원칙준수

- **HATEOAS(Hypertext As The Engine Of Application State)**라는 약어로 표현되는 하이퍼미디어 컨트롤을 적용합니다.
- 3단계의 요청은 2단계와 동일하지만, 응답에는 리소스의 URI를 포함한 **링크** 요소를 삽입하여 작성해야 합니다.
- EX) 응답 내에 새로운 링크를 넣어 새로운 기능에 접근할 수 있도록함
