## 2단계: 쓴 만큼 얼마인지 직접 계산한다

플랜을 골랐으면 다음 질문은 "그래서 얼마 드는가" 입니다. GitHub 은 좌석 값과 쓴 만큼 내는 값을 따로 청구합니다.
이 단계는 쓴 만큼 내는 쪽, 그중 Actions 분을 직접 재서 월 예상치를 냅니다.

> [!NOTE]
> Dependabot 을 켜는 실습은 이 랩에 없습니다. GH-100 모듈 4 의 공식 랩
> [Secure your repository supply chain](https://github.com/skills/secure-repository-supply-chain) 이
> 의존성 그래프, 경고, 보안 업데이트, 버전 업데이트를 4단계로 다룹니다. 그쪽에서 하세요.

### 📖 Theory: 청구는 두 갈래다

| | 좌석(seat) | 미터링(metered) |
|---|---|---|
| 무엇 | 사람 수. 라이선스 | 쓴 양. Actions 분, Packages 저장용량, Copilot 등 |
| 어디서 보나 | License Usage Stats | Metered Usage Report |
| 줄이는 법 | 미사용 좌석 회수 | 실행 횟수와 러너 종류 조정 |

Actions 분에서 관리자가 알아야 할 규칙 세 가지입니다.

- **public 리포는 GitHub-hosted 러너가 무료입니다.** 그래서 이 실습은 돈이 들지 않습니다. 계산만 합니다.
- private 리포는 플랜별 무료 분이 있고, 초과하면 분 단위로 과금됩니다.
- **matrix 는 분을 곱합니다.** job 3개가 각 1분이면 1분이 아니라 3분입니다. 러너 종류에 따라 배수도 붙습니다.

### ⌨️ Activity: 재고 계산한다

1. `.github/workflows/usage-probe.yml` 을 만듭니다. 이름은 반드시 **`Usage probe`** 로 합니다.
   matrix 로 job 을 3개 만들어 곱셈을 눈으로 봅니다.

   ```yaml
   name: Usage probe

   on:
     workflow_dispatch:

   permissions: {}

   jobs:
     probe:
       runs-on: ubuntu-latest
       strategy:
         matrix:
           slot: [1, 2, 3]
       steps:
         - name: 일부러 시간을 조금 쓴다
           run: |
             echo "slot ${{ matrix.slot }} 시작"
             sleep 20
             echo "slot ${{ matrix.slot }} 끝"
   ```

2. **Actions 탭 → Usage probe → Run workflow** 로 한 번 실행합니다.
3. 실행이 끝나면 그 실행 화면 오른쪽 위 **Usage** 를 눌러 **billable time** 을 확인합니다.
   job 3개의 합이 한 job 시간의 세 배에 가까운지 봅니다. GitHub 은 job 마다 분 단위로 올려서 셉니다.
4. `docs/usage-estimate.md` 를 만들고 아래를 적습니다.
   - 실행 화면에서 본 **billable** 시간을 그대로 (단위 포함)
   - 하루에 몇 번 돌릴지 가정하고, `월 예상 분:` 으로 시작하는 줄에 계산 결과를 적습니다
   - private 리포라면 이 값이 무료 분을 넘는지, 넘으면 어떻게 할지
   - 줄이는 방법 두 가지 이상. 반드시 `self-hosted` 러너를 포함해 비교합니다
   - `Metered` 리포트와 좌석 리포트 중 이 수치는 어디서 보이는지 한 줄
5. `docs/usage-estimate.md` 를 push 합니다.

> [!IMPORTANT]
> 채점기는 `Usage probe` 워크플로의 **실행이 완료됐는지**를 봅니다. 파일만 만들면 통과하지 않습니다.

<details><summary>self-hosted 가 항상 싼가요</summary><br/>

아닙니다. GitHub-hosted 는 분당 과금이지만 관리가 없습니다. self-hosted 는 Actions 분이 청구되지 않는 대신
VM 값과 운영 부담이 생깁니다. 실행량이 꾸준히 많고 이미 서버가 있는 조직에서만 이득입니다.
시험에서는 "어느 쪽을 권할 상황인가" 로 묻습니다.

</details>

<details><summary>채점 기준</summary>

- `docs/usage-estimate.md` 가 있다
- 그 안에 `billable` 이 있다 (실행 화면에서 본 값을 옮겼다는 뜻)
- 그 안에 `월 예상 분:` 이 있다
- 그 안에 `self-hosted` 가 있다
- `Usage probe` 워크플로의 실행이 완료됐다
</details>
