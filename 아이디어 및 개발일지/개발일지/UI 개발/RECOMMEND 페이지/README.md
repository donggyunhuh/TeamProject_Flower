# 꽃 추천 화면 개발일지

## 꽃 추천 기능 서비스

![꽃 추천 기능](https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EB%A9%94%EC%9D%B8%ED%8E%98%EC%9D%B4%EC%A7%80/%EC%B6%94%EC%B2%9C%EC%84%9C%EB%B9%84%EC%8A%A4.gif?raw=ture)


## 개요
본 문서는 꽃 추천 시스템 개발에 대한 개발일지를 정리하기 위한 `readme.md` 파일입니다. 해당 시스템은 사용자가 선호하는 키워드를 바탕으로 꽃을 추천해주는 알고리즘을 구현합니다.

## 알고리즘 설명
사용자는 키워드를 선택하고, 시스템은 각 꽃에 대응하는 가중치 정보를 활용하여 최적의 꽃을 추천합니다. 

### 컨트롤러 (`RecommendController`)
- <img src="">
- `@GetMapping`을 통해 사용자가 키워드를 선택할 수 있는 페이지를 제공합니다.
- `@PostMapping("/loading")`에서는 사용자가 선택한 키워드를 받아 로딩 페이지를 보여줍니다.
- `@GetMapping("/result")`에서는 사용자가 선택한 키워드 번호(`keywordNos`)를 기반으로 최적의 꽃을 계산하여 결과 페이지에 제공합니다.

### 서비스 (`FlowerInfoService`, `KeywordInfoService`, `WeightInfoService`)
- 각 서비스는 `Repository`와 연동하여 꽃(`Flower`), 키워드(`Keywords`), 가중치(`FlowerWeight`)의 정보를 데이터베이스에서 가져오거나 처리합니다.
- `WeightInfoService`에서는 가중치 정보를 활용하여 각 꽃에 점수를 매기고, 이를 통해 최종 추천 꽃을 결정합니다.
- <img src="">

### 레포지토리 (`FlowerRepository`, `KeywordRepository`, `WeightRepository`)
- 각 엔티티에 대한 CRUD 작업을 수행할 수 있는 JPA 레포지토리들입니다.
- `FlowerRepository`는 꽃에 대한 정보 조회, `KeywordRepository`는 키워드 관리, `WeightRepository`는 가중치 정보 관리를 담당합니다.

## 알고리즘의 특징
- 사용자의 선택을 반영하여 동적으로 꽃을 추천합니다.
- 가중치 시스템을 통해 복수의 키워드가 주어졌을 때 각각의 중요도를 다르게 적용하여 꽃에 점수를 부여합니다.
- 최종적으로 점수가 가장 높은 꽃을 사용자에게 추천합니다.

