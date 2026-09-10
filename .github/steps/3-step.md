## 3단계: 사용량을 읽는 법을 정리한다

관리자 업무의 절반은 "지금 얼마나 쓰고 있는가" 를 답하는 일입니다.
GitHub 은 이것을 두 갈래로 보여줍니다.

- **License Usage Stats**: 좌석을 몇 개 샀고 몇 개가 실제로 쓰이는지. 사람 단위입니다
- **Metered Usage Report**: Actions 분, Packages 저장용량, Copilot 같이 쓴 만큼 과금되는 것들입니다

여기서 관리자가 실제로 하는 결정이 나옵니다.
90일 동안 로그인하지 않은 좌석을 회수할지, 셀프호스트 러너로 Actions 분을 줄일지 같은 것입니다.

### 할 일

`docs/license-usage.md` 파일을 만들고 아래를 담으세요.

1. `License Usage Stats` 로 무엇을 알 수 있는지 한 줄
2. `Metered usage` 리포트로 무엇을 알 수 있는지 한 줄, 그리고 metered 항목을 두 개 이상 나열
3. 미사용 좌석을 다루는 절차를 `회수` 라는 말을 넣어 두 줄 이상

<details>
<summary>어디서 보는 화면인가요</summary><br/>

엔터프라이즈 계정의 **Settings → Billing and licensing** 아래에 있습니다.
개인 계정에는 이 화면이 없으므로, 이 단계는 문서로만 정리합니다.
강사가 실제 엔터프라이즈 화면을 띄워 보여줍니다.

</details>
