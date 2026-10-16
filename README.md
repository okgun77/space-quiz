# 우주 퀴즈 (Space Quiz)

우주에 관한 10개의 질문을 풀어 보는 한국어 퀴즈 웹 앱이에요. 문제마다 정답 해설을 보여 주고, 마지막에 점수를 알려 줘요.

- 라이브 사이트: https://okgun77.github.io/space-quiz/
- 모든 코드(HTML, CSS, JS)는 `index.html` 한 파일에 들어 있어요.
- 빌드 과정이나 의존성이 없어요.

## 로컬 실행 방법

1. 리포지토리를 클론해요.
2. `index.html`을 브라우저에서 바로 열어요.

또는 정적 서버로 실행할 수도 있어요.

```sh
python -m http.server 8000
```

이후 http://localhost:8000 에 접속해요.

## 배포

`main` 브랜치에 푸시하면 GitHub Actions(`.github/workflows/pages.yml`)가 GitHub Pages에 자동 배포해요.
