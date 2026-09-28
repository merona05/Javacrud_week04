# Week04 Starter - Spring Boot Memory CRUD
# 📚 도서 관리 REST API

Spring Boot와 Java Collection(`Map`)을 활용한 도서 관리 REST API입니다.
Layered Architecture를 적용하여 Controller → Service → Repository 구조로 CRUD 기능을 구현했습니다.

## 1. 프로젝트 주제

**도서 관리 REST API**

도서의 정보를 등록하고 조회, 수정, 삭제할 수 있는 REST API입니다.

### 도서 데이터

* `id`: 도서 식별자
* `title`: 도서 제목
* `author`: 저자
* `price`: 가격
* `category`: 카테고리
* `isbn`: ISBN

총 5개의 데이터를 관리하며, `id`는 자동으로 생성됩니다.

## 2. CRUD 기능

| 기능    | HTTP Method | URL               | 설명        |
| ----- | ----------- | ----------------- | --------- |
| 도서 등록 | POST        | `/api/books`      | 새로운 도서 등록 |
| 전체 조회 | GET         | `/api/books`      | 전체 도서 조회  |
| 단건 조회 | GET         | `/api/books/{id}` | 특정 도서 조회  |
| 도서 수정 | PUT         | `/api/books/{id}` | 특정 도서 수정  |
| 도서 삭제 | DELETE      | `/api/books/{id}` | 특정 도서 삭제  |

존재하지 않는 `id`로 단건 조회, 수정, 삭제를 요청하면 `404 NOT_FOUND`를 반환합니다.

## 3. 프로젝트 구조

```text
src/main/java/com/webservice/week04
├── controller
│   └── BookController.java
├── service
│   └── BookService.java
├── repository
│   ├── BookRepository.java
│   └── MemoryBookRepository.java
├── domain
│   └── Book.java
└── dto
    ├── BookRequest.java
    └── BookResponse.java
```

### 계층 구조

```text
HTTP Request
     ↓
BookController
     ↓
BookService
     ↓
BookRepository
     ↓
MemoryBookRepository
     ↓
Map<Long, Book>
     ↓
JSON Response
```

## 4. 핵심 구현 내용

* **REST API**: HTTP Method와 URL을 이용하여 도서 CRUD API 구현
* **Layered Architecture**: Controller → Service → Repository로 역할을 분리
* **Repository Interface**: `BookRepository` 인터페이스를 통해 저장소 구현을 추상화
* **In-Memory Storage**: `Map<Long, Book>`을 사용하여 데이터를 메모리에 저장
* **DTO**: `BookRequest`, `BookResponse`를 사용하여 요청과 응답 데이터를 분리

## 5. 주요 기술 키워드

* Spring Boot
* Spring Web
* REST API
* HTTP Method
* JSON
* Controller
* Service
* Repository
* Interface
* DTO
* Layered Architecture
* Java Collection
* `Map`
* In-Memory Storage

## 6. 실행 방법

프로젝트를 실행한 후 다음과 같은 API 요청을 통해 도서 CRUD 기능을 테스트할 수 있습니다.

### 도서 등록

```http
POST /api/books
Content-Type: application/json
```

```json
{
  "title": "스프링 부트 입문",
  "author": "홍길동",
  "price": 25000,
  "category": "Programming",
  "isbn": "9781234567890"
}
```

### 전체 조회

```http
GET /api/books
```

### 단건 조회

```http
GET /api/books/1
```

### 수정

```http
PUT /api/books/1
Content-Type: application/json
```

```json
{
  "title": "스프링 부트 입문 개정판",
  "author": "홍길동",
  "price": 30000,
  "category": "Programming",
  "isbn": "9781234567890"
}
```

### 삭제

```http
DELETE /api/books/1
```

## 7. Weekly Report

### Week 4

* Spring Boot 프로젝트의 기본 구조와 실행 방법을 학습했다.
* Controller, Service, Repository 계층으로 역할을 분리하여 REST API CRUD를 구현했다.
* Java Collection인 `Map`을 이용하여 데이터베이스 없이 데이터를 저장하는 In-Memory Repository를 구현했다.
* DTO를 사용하여 API 요청과 응답 데이터를 분리했다.
* 존재하지 않는 도서 ID에 대해 `404 NOT_FOUND`를 반환하도록 구현했다.

###
Key Learning: **Spring Boot REST API, Controller, DTO와 HTTP 상태 코드**

CRUD Flow: **HTTP Request → Controller → Service → Repository → Memory(Map) → JSON Response**

Problem & Solution: 지난 수업을 듣지 못해서 스프링부트 전반에 대해 이해하지 못한채 과제를 시작하였으나 프로그래머이신 아버지께 질문을드려서 스프링부트가 무엇이고 이전에 했던 것과 어떻게 다른지 공부하였습니다.

Code Review: 
저는 BookController의 도서 생성 코드가 제일 중요하다고 생각하였습니다.
이 코드를 통해 HTTP POST 요청을 받아 DTO로 데이터를 전달하고, Service에서 처리한 결과를 다시 응답으로 반환하는 REST API의 전체적인 흐름을 이해할 수 있었고,  201 Created를 사용하여 요청이 성공적으로 처리되었음을 HTTP 상태 코드로 표현하는 방법도 알게 되었습니다.
새롭게 배운 부분을 명확히 짚어내는 코드라고 생각해서 중요하다고 보았습니다.

Reflection: 스프링부트를 쓰면서도 데이터베이스를 사용하지 않았던 이유가 무엇인지 궁금합니다. 단지 새로운 작업이기에 우선은 제외한 것인지, 아니면 특별한 이유가 있는지 알고 싶습니다.

## 8. 테스트 결과

Postman을 이용하여 다음 CRUD 기능을 테스트했다.

* [ ] 도서 등록 (POST)
* [ ] 전체 도서 조회 (GET)
* [ ] 단건 도서 조회 (GET)
* [ ] 도서 수정 (PUT)
* [ ] 도서 삭제 (DELETE)
* [ ] 존재하지 않는 ID 요청 시 404 확인

### 실행 화면

> 여기에 Postman CRUD 테스트 결과 스크린샷을 추가합니다.

![POST - 도서 등록](./images/post-create.png)

![GET - 전체 조회](./images/get-all.png)

![GET - 단건 조회](./images/get-one.png)

![PUT - 도서 수정](./images/put-update.png)

![DELETE - 도서 삭제](./images/delete.png)
