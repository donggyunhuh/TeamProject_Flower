# 꽃 관리 기능

## 관리자 페이지_꽃 관리
<img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EA%B4%80%EB%A6%AC%EC%9E%90%20%ED%8E%98%EC%9D%B4%EC%A7%80/%EA%B4%80%EB%A6%AC%EC%9E%90%ED%8E%98%EC%9D%B4%EC%A7%80UI/%EA%BD%83%EA%B4%80%EB%A6%AC.png?raw=true">

## FlowerController 클래스

<img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EA%B4%80%EB%A6%AC%EC%9E%90%20%ED%8E%98%EC%9D%B4%EC%A7%80/%EA%BD%83%EA%B4%80%EB%A6%AC/FlowerController.png?raw=true">

`FlowerController` 클래스는 `/admin/recommend` 경로에 매핑되며, 관리자 페이지에서 꽃 관련 정보를 관리하는 컨트롤러입니다.

### 메소드 요약

- `flowerList(Model model)`: `GET` 요청을 처리하며, 모든 꽃의 정보를 조회하여 리스트로 반환합니다.
- `addFlower(FlowerInfo flowerInfo, RedirectAttributes redirectAttributes)`: `POST` 요청을 처리하며, 새로운 꽃 정보를 추가합니다.
- `editFlower(List<FlowerInfo> flowerInfoList)`: `POST` 요청을 처리하며, 여러 꽃의 정보를 수정합니다.
- `deleteFlower(Map<String, List<Long>> payload)`: `DELETE` 요청을 처리하며, 선택된 꽃들을 삭제합니다.

## FlowerEditService 클래스
`FlowerEditService` 클래스는 꽃 정보를 추가, 수정, 삭제하는 로직을 담당하는 서비스입니다.

### 주요 기능

- `addWeightsByFlower(Flower flower, List<Keywords> allKeywords)`: 새로운 꽃이 추가될 때, 해당 꽃에 대한 모든 키워드의 가중치 정보를 생성합니다.
<img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EA%B4%80%EB%A6%AC%EC%9E%90%20%ED%8E%98%EC%9D%B4%EC%A7%80/%EA%BD%83%EA%B4%80%EB%A6%AC/addWeightByFlower.png?raw=true">

- `addFlower(FlowerInfo flowerInfo)`: 새 꽃 정보를 데이터베이스에 추가하고, 가중치 정보를 생성합니다.
<img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EA%B4%80%EB%A6%AC%EC%9E%90%20%ED%8E%98%EC%9D%B4%EC%A7%80/%EA%BD%83%EA%B4%80%EB%A6%AC/addFlower.png?raw=true">

- `editFlowerList(List<FlowerInfo> flowerInfoList)`: 여러 꽃의 정보를 수정하고, 결과 리스트를 반환합니다.
<img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EA%B4%80%EB%A6%AC%EC%9E%90%20%ED%8E%98%EC%9D%B4%EC%A7%80/%EA%BD%83%EA%B4%80%EB%A6%AC/editFlowerList.png?raw=true">

- `deleteFlower(List<Long> flowerNos)`: 주어진 식별자(ID) 목록에 해당하는 꽃들을 삭제합니다.
<img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EA%B4%80%EB%A6%AC%EC%9E%90%20%ED%8E%98%EC%9D%B4%EC%A7%80/%EA%BD%83%EA%B4%80%EB%A6%AC/deleteFlower.png?raw=true">

## FlowerInfoService 클래스
`FlowerInfoService` 클래스는 꽃 정보 조회를 담당하는 서비스입니다.

### 주요 기능

- `getAllFlowers()`: 데이터베이스에서 모든 꽃 정보를 조회합니다.
- `getFlowerByFlowerNo(Long flowerNo)`: 특정 식별자(ID)를 가진 꽃 정보를 조회합니다.

## FlowerRepository 인터페이스
`FlowerRepository` 인터페이스는 `JpaRepository`를 상속받으며, 꽃 정보에 대한 데이터베이스 작업을 추상화합니다.

### 주요 메소드

- `findByFlowerNm(String flowerNm)`: 꽃 이름으로 꽃 정보를 조회합니다.
- `findByFlowerNo(Long flowerNo)`: 꽃 식별자로 꽃 정보를 조회합니다.

## FlowerInfo 클래스
`FlowerInfo` 클래스는 꽃 정보를 전달하는 데이터 모델입니다.

### 주요 속성

- `flowerNo`: 꽃의 식별자입니다.
- `flowerNm`: 꽃 이름입니다.
- `flowerMean`: 꽃말을 나타냅니다.
- `bloomseason`: 꽃이 피는 시기입니다.
- `season`: 꽃이 해당하는 계절입니다.
- `flowerImages`: 꽃 이미지의 경로입니다.
- `likes`: 꽃에 대한 좋아요 수입니다.