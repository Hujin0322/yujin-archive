# 프리코스 3주차 미션 - 로또

## 목표 - 간단한 로또 발매기 구현
- 사용자에게 로또 구입 금액을 입력받은 뒤 구입 금액에 해당하는 만큼 로또를 발행한다.
- 당첨 번호와 보너스 번호를 입력받은 뒤 발행된 로또와 비교하여 당첨 내역 및 수익률을 출력한다.

## 기능 목록

### 금액 입력 받기
- `구입금액을 입력해 주세요. : ` 메시지를 출력한다.
  - 금액을 입력받는다.

### 로또 번호 발행
- 로또 번호 범위
  - 1부터 45까지
- 로또 티켓 발행
  - 1개의 로또를 발행할 때 중복되지 않는 6개의 숫자를 뽑는다.
  - 입력된 구입 금액만큼 로또를 발행한다. (1장 당 1,000원)
- 발행된 로또 출력
  - 발행한 로또 수량을 입력한다.
    - 예시: `8개를 구매했습니다.`
  - 번호(오름차순)를 출력한다.
    - 예시: `[8, 21, 23, 41, 42, 43] `
  
### 당첨 번호 입력 받기
- `당첨 번호를 입력해 주세요. : ` 메시지를 출력한다.
  - 중복되지 않는 숫자 6개를 입력받는다.
- `보너스 번호를 입력해 주세요. : ` 메시지를 출력한다.
  - 중복되지 않는 숫자 1개를 입력받는다.

### 당첨 등수 및 상금
- 당첨은 1등부터 5등까지 있다. 당첨 기준과 금액은 아래와 같다.
  - 1등: 6개 번호 일치 / 2,000,000,000원
  - 2등: 5개 번호 + 보너스 번호 일치 / 30,000,000원
  - 3등: 5개 번호 일치 / 1,500,000원
  - 4등: 4개 번호 일치 / 50,000원
  - 5등: 3개 번호 일치 / 5,000원

### 결과 출력
- 발행한 로또 티켓 번호를 오름차순으로 정렬하여 보여준다.
- 당첨 내역과 각 등수별 당첨 개수를 출력한다.
  - 예시: `3개 일치 (5,000원) - 1개`
- 총 수익률을 계산하여 소수점 둘째 자리에서 반올림하여 출력한다.
  - 예시: `총 수익률은 62.5%입니다.`

### 예외 처리
- 사용자가 잘못된 값을 입력할 경우 `IllegalArgumentException`을 발생시킨다.
- `[ERROR]`로 시작하는 에러 메시지를 출력 후 그 부분부터 입력을 다시 받는다.
  1. 구입 금액 입력 예외 처리
     - 빈 칸 혹은 공백일 경우: `[ERROR] 구매 금액을 입력해주세요.`
     - 문자인 경우: `[ERROR] 금액은 숫자로만 입력해주세요.`
     - 1,000원 미만인 경우: `[ERROR] 로또 구입 최소 금액은 1,000원입니다.`
     - 1,000원 단위가 아닐 경우: `[ERROR] 1,000원 단위로 입력해주세요.`
     
  2. 번호 입력 예외 처리
     - 빈 칸 혹은 공백일 경우: `[ERROR] 1부터 45 사이의 번호를 입력해주세요.` 
     - 문자인 경우: `[ERROR] 번호는 숫자로만 입력해주세요.`
     - 쉼표(,) 제외 특수기호가 존재하는 경우: `[ERROR] 쉼표(,) 이외의 특수기호는 사용할 수 없습니다.`
     - 번호가 범위를 벗어난 경우: `[ERROR] 로또 번호는 1에서 45 사이여야 합니다.`
     - 번호가 중복된 경우: `[ERROR] 로또 번호는 중복될 수 없습니다.`
     - 공백 존재 혹은 6개가 입력되지 않은 경우: `[ERROR] 6개의 번호를 입력해주세요`