# Flower Recommendation Algorithm

<br>
이 문서에서는 이번 프로젝트의 주요 기능중 하나인 '키워드 기반 꽃 추천' 기능에 사용될 알고리즘을 소개한다.<br><br>

## 꽃 추천 알고리즘
먼저 키워드 기반 꽃 추천이 어떻게 이루어지는지 설명하자면 사용자는 웹에서 '풍성한', '연인', '부모님', '졸업식', '크리스마스' 등 과 같은
미리 정해져 있는 키워드 중 몇 가지를 순위를 매겨 선택하게 된다.
복수 선택된 키워드들을 기반으로 우리가 가지고 있는 꽃의 데이터들에
점수를 매긴 뒤 높은 점수를 가지는 꽃들을 우선으로 추천해주는 방식이다.<br>
#### ex) 장미의 각 키워드별 점수
<a href="https://imgbb.com/"><img src="https://i.ibb.co/rtRp5qV/image.png" alt="image" border="0"></a>
<br><br>
## 행렬 곱
여러 추천 알고리즘 중 사용자가 선택할 키워드의 종류와 추천 받을 꽃의 종류가 정해져있다는 점에서
채택하게 된 것은 '행렬 곱 알고리즘'이다.<br>
행렬 곱이란 말 그대로 행렬끼리 곱해주는 것을 말한다. 다음은 대표적인 행렬 곱의 예시이다.<br><br>
<img src="https://velog.velcdn.com/images%2Fdongchyeon%2Fpost%2Fadf0feaa-fa34-42c1-b609-96043e5f8ca6%2FCodeCogsEqn.png">
<br><br>
첫번째 행렬을 A, 두번째 행렬을 B, 결과 행렬을 C라 한다면 **C행 i열 j의 값 = A의 i행의 값 * B의 j열의 값**으로 정의할 수 있다.
기본적으로 행렬의 곱은 1번째 행렬의 열과 2번째 행렬의 행이 같을 때 연산이 가능한데 만약 M x K 행렬과 K x N 행렬의 곱이 이루어진다면
그 결과 행렬은 M x N 행렬이 된다. 이를 우리의 방식에 적용해보면 사용자 x 키워드 행렬과 키워드 x 꽃 행렬을 다음과 같이 만들 수 있다.
<br><br>
#### 1 x N 행렬 (사용자와 키워드)
<a href="https://imgbb.com/"><img src="https://i.ibb.co/hMRR6yk/Kakao-Talk-20230926-021417383.png" alt="Kakao-Talk-20230926-021417383" border="0"></a>
<br>a00 ~ a0(N-1)에는 사용자가 정한 키워드들의 우선순위를 고려한 적절한 값이 들어갈 예정이다.<br><br>
#### N x M 행렬 (키워드와 꽃)
<a href="https://imgbb.com/"><img src="https://i.ibb.co/FVrVV3r/image.png" alt="image" border="0"></a>
<br>b00 ~ b(N-1)(M-1)에는 각각의 키워드에 해당되는 꽃의 점수가 들어갈 예정이다.<br><br>
#### 1 x M 행렬 (결과행렬) (사용자와 꽃)
<a href="https://ibb.co/yY7qfhz"><img src="https://i.ibb.co/ZY7xLHQ/image.png" alt="image" border="0"></a><br>
이렇게 두 행렬을 곱한 결과행렬에는 꽃별로 "얼마나 사용자가 선택한 키워드에 어울리는지"를 수치화한 값이 들어간다.
마지막으론 꽃들 중 가장 높은 값을 가지는 3~4개 정도의 꽃을 사용자에게 추천하게 된다.<br>

## 시간복잡도
기본적으로 N x K의 행렬과 K x M의 행렬을 곱한다했을때 필요한 연산수는 N * K * M번이기때문에
행렬 곱 알고리즘은 O(N^3)의 복잡도를 지닌다. 그러나 우리가 실제로 사용할 첫번째 행렬, 즉 N x K 행렬은
사용자와 키워드 행렬으로 N(사용자)이 1로 고정된 값을 지니게 된다. 따라서 필요한 연산수는
K(키워드 개수) * M(꽃 개수)번이 되므로 O(N^2)의 복잡도를 지닌다.
<br><br>
<a href="https://ibb.co/YyTcnjz"><img src="https://i.ibb.co/pRrfVXt/image.png" alt="image" width="250" height="250" border="0"></a>

## 알고리즘 개발 일지

### 컨트롤러 (`RecommendController`)
- `@GetMapping`을 통해 사용자가 키워드를 선택할 수 있는 페이지를 제공합니다.
- `@PostMapping("/loading")`에서는 사용자가 선택한 키워드를 받아 로딩 페이지를 보여줍니다.
- `@GetMapping("/result")`에서는 사용자가 선택한 키워드 번호(`keywordNos`)를 기반으로 최적의 꽃을 계산하여 결과 페이지에 제공합니다.

### 서비스 (`FlowerInfoService`, `KeywordInfoService`, `WeightInfoService`)
- 각 서비스는 `Repository`와 연동하여 꽃(`Flower`), 키워드(`Keywords`), 가중치(`FlowerWeight`)의 정보를 데이터베이스에서 가져오거나 처리합니다.
- `WeightInfoService`에서는 가중치 정보를 활용하여 각 꽃에 점수를 매기고, 이를 통해 최종 추천 꽃을 결정합니다.

### 레포지토리 (`FlowerRepository`, `KeywordRepository`, `WeightRepository`)
- 각 엔티티에 대한 CRUD 작업을 수행할 수 있는 JPA 레포지토리들입니다.
- `FlowerRepository`는 꽃에 대한 정보 조회, `KeywordRepository`는 키워드 관리, `WeightRepository`는 가중치 정보 관리를 담당합니다.

## 알고리즘의 특징
- 사용자의 선택을 반영하여 동적으로 꽃을 추천합니다.
- 가중치 시스템을 통해 복수의 키워드가 주어졌을 때 각각의 중요도를 다르게 적용하여 꽃에 점수를 부여합니다.
- 최종적으로 점수가 가장 높은 꽃을 사용자에게 추천합니다.















