# 코드 컨벤션

# **git flow 정리**

1. 원격에 있는 master, develop, feature 브랜치 가져오기 /

    `-`

    - 로컬에서 `feature` 이름의 브랜치가 생성됨
2. feature/기능 브랜치 생성

    `git checkout -b feature/기능`

    - 로컬에서 `feature/기능` 브랜치가 생성됨
3. 기능 업로드

```jsx
git status
git add .
git commit -m "[Feat] ~~~"
```

1. feature 브랜치로 push

    `git push origin feature/기능`

2. gitlab에서 feature -> develop 브랜치로 merge request
3. pull 받아서 최신화하기

    `git pull origin develop`

---

### **커밋 메시지 규칙 (수정할 것)**

- 보통은 팀과 컨벤션을 맞추는 경우가 많은 것 같다. 그래도 보통 기본적으로 통용되는 규칙
    1. 제목과 본문을 한 줄 띄워 분리하기
    2. 제목은 영문 기준 50자 이내
    3. 제목 첫 글자를 대문자
    4. 제목 끝에 **. 금지**
    5. 본문은 자유!

---

### **자주 커밋 로그에 사용하는 영어 단어 목록**

1. **feat**: 새로운 기능에 대한 커밋 (feature를 축악형으로 쓴 것) / Minor 버전에 해당하는것 
2. **fix**: 버그 수정에 대한 커밋 (Patch버전 의미하는 형태) 
3. **chore**: 그 외 자잘한 수정에 대한 커밋 
4. **docs**: 도큐먼트 수정에 대한 커밋 
5. **hotfix:** 배포후 발견한 긴급한 버그 수정 
- 적용 범위
    - 부가적인 정보로, 선택사항이지만 적용 범위를 명시하게 되면 해당 커밋이 어떤 범위에 대한 수정 사항인지 이해하는지 도움이 되는 정보이다.
- 휴지통
    1. **style**: 코드 문법 또는 포맷에 대한 수정에 대한 커밋
    2. **build**: 빌드 관련 파일 수정에 대한 커밋
    3. **test**: 테스트 코드 수정에 대한 커밋

### Commit Message 예시

[Feat] Add review function

### 폴더 트리 구조

---

```
.
ㄴ backend
	ㄴ gradle
	ㄴ src
ㄴ frontend
	ㄴ src
	ㄴ components
ㄴ data
ㄴ README.md

Master
ㄴ Develop <- Feature_fe/Login
ㄴ Develop <-
```

### Reference

- 커밋 메시지 규약을 지켜야 하는 이유 (참고)
    - 협업을 하면서, 내가 혹은 다른 상대방이 어떤 일을 했는지 직관적으로 알 수 있어야 하기 때문에
    - 코드는 혼자 보는게 아니기 때문에/코드는 혼자 짜는게 아니기 때문에
    - 이후 프로젝트나, 일했던 것을 볼 때 어떤 일을 했는지 파악 가능하기 때문에
    - 보통 코드를 보기도 하지만, 통상적으로는 커밋 메시지로 어떤 일을 했는지 파악하기 때문에
    - 커밋 메시지가 하나의 의미를 담고 있기 때문에, 단일 커밋 단위로 의미있는 수정들이 일어나도록 장려할 수 있기 때문에
    - 규약을 통해 Changelog에 대한 생성을 자동화할 수 있기 때문에(조금 더 공부 필요)
    - 커밋을 통해 Semantic version관리를 명확하게 할 수 있고 자동화할 수 있기 때문에

Cleancode - pr_checklist 

[woowacourse/woowacourse-docs](https://github.com/woowacourse/woowacourse-docs/blob/master/cleancode/pr_checklist.md)

[MariaDB 코딩컨벤션](https://www.notion.so/MariaDB-3fedeafd2afa4314ac1bc0504d9f2544)

[JIRA 컨벤션](https://www.notion.so/JIRA-35daae623842401585886564de238f7f)