# Week04 Starter - Spring Boot Memory CRUD

## 목표
DB 없이 `Map<Long, Book>`을 저장소로 사용하여 REST CRUD API를 완성합니다.

## 구조
`Controller -> Service -> BookRepository -> MemoryBookRepository -> Map`

## 구현 API
- POST `/api/books`
- GET `/api/books`
- GET `/api/books/{id}`
- PUT `/api/books/{id}`
- DELETE `/api/books/{id}`

## 실습 순서
1. MemoryBookRepository TODO 1~5
2. BookService TODO 6~10
3. BookController TODO 11~15
4. Postman/curl 테스트
5. 없는 id 요청 시 404 확인

## 실행
IntelliJ에서 `Week04BookCrudApplication` 실행 또는 Gradle의 `bootRun` task를 실행하세요.
