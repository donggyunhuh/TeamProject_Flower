# 개발일지: 포스트카드(엽서) 이미지 생성 서비스

## 엽서 디자인 서비스

![엽서_디자인_서비스](https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EB%A9%94%EC%9D%B8%ED%8E%98%EC%9D%B4%EC%A7%80/%EC%97%BD%EC%84%9C%20%EC%A0%9C%EC%9E%91%20%EA%B8%B0%EB%8A%A5%20%EC%98%88%EC%8B%9C.gif?raw=true)


## 개요

Spring Boot를 이용하여 사용자가 텍스트 프롬프트를 통해 이미지를 생성할 수 있는 포스트카드 서비스를 구현하고 있습니다. OpenAI의 DALL·E API를 활용합니다.

## 구성 요소 및 로직

### RestClientConfig (`RestClientConfig.java`)
- Spring의 `RestTemplate`을 빈으로 정의하여 HTTP 요청을 손쉽게 보낼 수 있습니다.
- `@Configuration` 어노테이션을 통해 설정 클래스임을 선언합니다.
- <img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EC%97%BD%EC%84%9C%EC%A0%9C%EC%9E%91%EA%B8%B0%EB%8A%A5/RestClientConfig.png?raw=true">

### OpenAIService (`OpenAIService.java`)
- `RestTemplate`와 OpenAI API 키를 사용하여 DALL·E API로 요청을 보내는 서비스 클래스입니다.
- `createImage` 메서드는 주어진 프롬프트로 이미지를 생성하는 요청을 DALL·E API에 보내고, 응답을 `Map<String, Object>` 타입으로 반환합니다.
- <img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EC%97%BD%EC%84%9C%EC%A0%9C%EC%9E%91%EA%B8%B0%EB%8A%A5/createImage.png?raw=true">
- `@Service` 어노테이션은 이 클래스가 서비스 계층의 컴포넌트임을 명시합니다.
- `@Value` 어노테이션은 외부 설정으로부터 API 키를 주입받습니다.

### OpenAIController (`OpenAIController.java`)
- `OpenAIService`를 이용하여 사용자의 프롬프트에 따라 이미지를 생성하고 그 결과를 뷰에 전달하는 컨트롤러입니다.
- <img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EC%97%BD%EC%84%9C%EC%A0%9C%EC%9E%91%EA%B8%B0%EB%8A%A5/openAIController.png?raw=true">
- `@Controller` 어노테이션으로 컨트롤러임을 선언합니다.
- `@RequestMapping("/postCard")`로 이 컨트롤러의 모든 메서드가 `/postCard` 경로로 매핑됩니다.
- `showCreateImageForm` 메서드는 이미지 생성을 위한 폼 페이지를 보여줍니다.
- `createImage` 메서드는 사용자가 제출한 프롬프트로 이미지를 생성하고, 생성된 이미지 URL을 `result.html`에 전달합니다.

### HTML Templates (`main.html` and `result.html`)
- `main.html`은 사용자가 프롬프트를 입력할 수 있는 폼을 제공합니다.
- `result.html`은 생성된 이미지를 표시하는 페이지입니다.

## 작동 흐름

1. 사용자는 `main.html`에 접속하여 이미지 생성을 위한 프롬프트를 입력합니다.
2. 폼 데이터가 `OpenAIController`의 `createImage` 메서드로 POST 요청을 통해 전송됩니다.
3. `OpenAIService`는 DALL·E API에 이미지 생성 요청을 보내고 결과를 받습니다.
4. `createImage` 메서드는 응답에서 이미지 URL을 추출하여 `result.html`에 전달합니다.
5. 사용자는 `result.html` 페이지에서 생성된 이미지를 볼 수 있습니다.

이 서비스는 사용자의 입력을 받아 OpenAI의 API를 통해 이미지를 생성하고, 결과를 웹 페이지를 통해 사용자에게 제공하는 전체적인 프로세스를 담당합니다.

Spring Boot를 사용하여 OpenAI의 DALL·E API에 연결하는 서비스를 구현하고 꽃과 키워드, 엽서 단어를 입력함으로써 사용자의 취향에 맞는 엽서 이미지를 생성해줍니다.