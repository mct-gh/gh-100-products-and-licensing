## 1단계: 시나리오에 맞는 플랜을 고른다

GitHub 의 계정은 세 종류입니다. 개인(Personal), 조직(Organization), 엔터프라이즈(Enterprise).
플랜은 그 위에 얹힙니다. GitHub Free, GitHub Pro, GitHub Team, GitHub Enterprise 입니다.

시험에서 자주 나오는 구분은 이렇습니다.

- **GitHub Free**: 개인과 조직 모두 쓸 수 있습니다. 퍼블릭 리포는 대부분의 기능이 무료입니다
- **GitHub Team**: 조직 전용입니다. 프라이빗 리포에서 코드 소유자 리뷰와 보호 브랜치를 씁니다
- **GitHub Enterprise Cloud**: SAML SSO, 감사 로그 API, EMU, 엔터프라이즈 정책이 여기부터입니다

### 시나리오

Contoso 교육 사업부는 사내 개발자 40명이 프라이빗 리포로 협업합니다.
회사는 Entra ID 로 계정을 관리하고, 퇴사자 계정이 자동으로 회수되기를 원합니다.
감사 담당자는 누가 언제 무엇을 했는지 API 로 뽑아야 한다고 요구합니다.

### 할 일

`docs/plan-choice.md` 파일을 만들고 아래를 담으세요.

1. `GitHub Free`, `GitHub Team`, `GitHub Enterprise Cloud` 세 플랜을 각각 한 줄씩 설명합니다
2. 위 시나리오에 고른 플랜을 `선택한 플랜` 이라는 말로 시작하는 줄에 적습니다
3. 왜 그 플랜인지 근거를 두 줄 이상 적습니다. 시나리오의 요구사항과 연결하세요

<details>
<summary>힌트가 필요하면</summary><br/>

시나리오에 나온 요구 세 가지가 각각 어느 플랜부터 가능한지 생각해 보세요.
프라이빗 협업, 자동 계정 회수, 감사 로그 API 입니다.
이 중 하나라도 하위 플랜에서 안 되면 그 플랜은 답이 아닙니다.

</details>
