# Git 컨벤션

## 1️⃣  Git 작업 전체적인 약속

1. 소스코드 작성 및 Git 작업을 시작하기 전에 JIRA 이슈 생성하기
2. **리뷰어에게 꼭 코드리뷰 받기! LGTM!**

## 2️⃣  커밋 메세지 작성 규칙 with git-cz

```jsx
💍 feat: login - [FE] 로그인 화면 제작
git-cz | 브랜치명  | 분류 및 커밋 메세지
```

1. `sudo npm install -g git-cz` 로  글로벌 환경에 설치
2. `git add .` 로 스테이지에 변경된 파일 추가하기
3. `git cz` 로 실행하기
    1. 아이콘이 있는 대분류 지정
    2. `브랜치명` `-` `[분류] 커밋메세지`
    3. 마지막 단계의 issue 등록은, `JIRA의 이슈 번호`를 등록하여 연결한다.

        커밋 메세지는 `한글로 작성`하며, 메세지가 `너무 길어질 경우 Description 에 추가로 기술`한다.

    ![_2021-04-18__10.03.59](/uploads/f072ea05899a8233e472e77de074d7d2/_2021-04-18__10.03.59.png)

```jsx
test : 테스트 코드
feat : 새로운 기능 추가
fix : 버그 수정
chore : 그 외 자잘한 작업
docs : 문서 수정
refactor : 성능 개선
style : 코드 의미에 영향을 주지 않는 변경사항 (포맷, 세미콜론 누락, 공백 등)

// build : 시스템 또는 외부 종속성에 영향을 미치는 변경사항 (npm, gulp, yarn 레벨)
// ci : CI관련 설정
```

## 3️⃣  브랜치명 규칙

**모든 작업은 develop**으로 **MR을 요청**하여 진행함.

develop 브랜치에선 **절대 작업을 금지**함.  🙅  🙅‍♀️

```jsx
master    : 최종 배포 단계 / 태그로 관리
develop   : feat에서 작업 후 병합하는 브랜치 / *절대 작업 금지
feat      : 
ㄴ room
ㄴ  ...
```

```markdown
커밋유형/요약
ex) feat/setting
```

- `브랜치명`은 JIRA의 `epic` 단위로 생성하여 관리한다.

---

[https://peter-cho.gitbook.io/book/](https://peter-cho.gitbook.io/book/)