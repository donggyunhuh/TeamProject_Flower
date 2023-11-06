# Entity 및 테이블 관계 상세 설명

## 일시
- 2023년 10월 08일

## 개발 내용: 테이블 및 Entity 설계
- 이 README는 꽃 추천 웹사이트 데이터베이스 스키마의 주요 엔터티(entities)와 그들 간의 관계(relationships)에 대하여 설명합니다.

### User Entity

<img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EC%97%94%ED%8B%B0%ED%8B%B0%20%EB%AA%A8%EB%8D%B8%EB%A7%81/Users.png?raw=true">

- `User` 엔터티를 통해서 사용자 정보를 관리한다.
- 기본키, 인덱스, 이메일, 이름, 닉네임, 패스워드, 전화번호, 생년월일, 권한 및 연관 엔터티를 포함한다.

  #### 관계
- `Order`: 1:N (하나의 사용자가 여러 주문을 가질 수 있습니다.)
- `Store`: 1:N (하나의 사용자가 여러 매장을 소유할 수 있습니다.)
- `KeywordSelect`: 1:N (하나의 사용자가 여러 키워드 선택을 가질 수 있습니다.)

### Order Entity

<img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EC%97%94%ED%8B%B0%ED%8B%B0%20%EB%AA%A8%EB%8D%B8%EB%A7%81/Orders.png?raw=ture">

- `Order` 엔터티에서는 주문 정보를 관리한다.
- 주문 식별자, 사용자의 ID, 픽업 날짜, 픽업 시간, 꽃 종류, 꽃 색상, 가격 범위, 메시지 등의 정보가 포함된다.

  #### 관계
- `User`: N:1 (여러 주문이 하나의 사용자에 속할 수 있습니다.)
- `Store`: N:1 (여러 주문이 하나의 매장에 속할 수 있습니다.)

### Store Entity

<img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EC%97%94%ED%8B%B0%ED%8B%B0%20%EB%AA%A8%EB%8D%B8%EB%A7%81/StoreInfo.png?raw=true">

- `Store` 엔터티를 통해 매장의 기본 정보를 관리한다.
- 매장 식별자, 이름, 사용자의 ID, 영업 시간, 위치, 연락처 및 이미지 정보를 가지고 있다.

  #### 관계
- `User`: N:1 (여러 매장이 하나의 사용자에 속할 수 있습니다.)
- `Order`: 1:N (하나의 매장은 여러 주문을 가질 수 있습니다.)

### StoreImage Entity

<img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EC%97%94%ED%8B%B0%ED%8B%B0%20%EB%AA%A8%EB%8D%B8%EB%A7%81/StoreImage.png?raw=true">

- `StoreImage` 엔터티에서는 매장 이미지의 정보를 관리한다.
- 이미지 식별자, 이미지 경로 및 해당 매장의 정보가 담겨있다.

  #### 관계
- `Store`: N:1 (여러 매장 이미지는 하나의 매장에 속할 수 있습니다.)

### Flower Entity

<img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EC%97%94%ED%8B%B0%ED%8B%B0%20%EB%AA%A8%EB%8D%B8%EB%A7%81/FlowerInfo.png?raw=true">

- `Flower` 엔터티는 꽃에 대한 모든 정보와 연관된 다른 엔티티들과의 관계를 관리한다.
- 꽃 ID, 꽃명, 꽃말, 개화시기, 계절, 꽃 이미지 경로 정보가 포함된다.

  #### 관계
- `FlowerKeywordMapping`: 1:N (하나의 꽃이 여러 키워드 매핑을 가질 수 있습니다.)

### KeywordSelect Entity
- `KeywordSelect` 엔터티는 사용자가 선택한 키워드와 그에 대한 가중치를 관리한다.
- 선택 ID, 사용자 정보, 키워드, 가중치 정보가 포함된다.

  #### 관계
- `User`: N:1 (여러 키워드 선택이 하나의 사용자에 속할 수 있습니다.)

### Keywords Entity

<img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EC%97%94%ED%8B%B0%ED%8B%B0%20%EB%AA%A8%EB%8D%B8%EB%A7%81/Keywords.png?raw=true">

- `Keywords` 엔터티에서는 키워드의 기본 정보와 연관된 다른 엔터티들과의 관계를 관리한다.
- 키워드 식별자, 키워드 이름, 연관된 꽃 키워드 매핑 및 키워드 선택 정보가 포함되어 있다.

### BaseEntity
- `BaseEntity`는 모든 엔터티에서 상속받아 사용할 수 있는 엔터티로, 기본적인 정보 (생성 일시, 수정 일시, 삭제 일시)를 담고 있다.
- `@MappedSuperclass`를 통해 다른 엔터티에서 상속 받아 사용되며, 직접적인 엔터티로 사용되지 않는다.


### Relationships 설명
- `User` ↔ `Order`: 한 명의 사용자는 여러 개의 주문을 가질 수 있으며, 이를 위해 `Order` 테이블에 `userId`를 외래키(FK)로 설정합니다.
  
- `User` ↔ `Store`: 한 명의 사용자는 여러 개의 매장을 등록할 수 있습니다. `Store` 테이블에 `userId`를 외래키로 설정합니다.

- `User` ↔ `KeywordSelect`: 사용자가 선택한 키워드는 여러 개일 수 있으므로 `KeywordSelect`에 `userId`를 외래키로 설정합니다.

- `Store` ↔ `StoreImage`: 한 매장은 여러 이미지를 가질 수 있습니다. `StoreImage` 테이블에 `storeId`를 외래키로 설정합니다.

- `KeywordSelect` ↔ `Keywords`: 사용자가 선택한 키워드는 기존의 키워드 테이블에 있으므로 `KeywordSelect`에 `keywordId`를 외래키로 설정합니다.

## 논의 및 문제점
- `Order` 엔터티의 상태 정보(‘접수중’, ‘매장 선택중’,‘매칭 실패’, ‘매칭 완료’)가 구현되어 있지 않음. 이를 enum 타입으로 추가할 필요가 있음.
- `KeywordSelect` 엔터티와 `Keywords` 엔터티 간의 연관 관계 및 로직 처리 방식에 대한 논의가 필요함.
- `User`, `Order`, `Store`, `StoreImage` 엔터티에 관계 설정이 되어있지만, 실제 연관관계의 주인을 어떻게 처리할 것인지 논의가 필요함.
- 데이터 검증 (Validation)에 대한 전반적인 구현 방식 논의가 필요함.

## 다음 단계
- 논의 및 문제점에서 언급된 내용을 바탕으로 각 엔터티와 관계에 대한 수정 및 보완이 필요하다.
- 각 엔터티의 Service Layer 및 Repository Layer를 설계하고 구현한다.
- 테스트 코드 작성으로 각 엔터티 및 메서드가 예상대로 동작하는지 검증한다.



