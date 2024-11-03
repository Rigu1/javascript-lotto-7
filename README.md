# javascript-lotto-precourse

**간단한 로또 발매기**

## 기능 요구 사항
- 로또 번호의 숫자 범위는 1~45까지이다.
- 1개의 로또를 발행할 때 중복되지 않는 6개의 숫자를 뽑는다.
- 당첨 번호 추첨 시 중복되지 않는 숫자 6개와 보너스 번호 1개를 뽑는다.
- 당첨은 1등부터 5등까지 있다. 당첨 기준과 금액은 아래와 같다.
- 1등: 6개 번호 일치 / 2,000,000,000원
- 2등: 5개 번호 + 보너스 번호 일치 / 30,000,000원
- 3등: 5개 번호 일치 / 1,500,000원
- 4등: 4개 번호 일치 / 50,000원
- 5등: 3개 번호 일치 / 5,000원
- 로또 구입 금액을 입력하면 구입 금액에 해당하는 만큼 로또를 발행해야 한다.
- 로또 1장의 가격은 1,000원이다.
- 당첨 번호와 보너스 번호를 입력받는다.
- 사용자가 구매한 로또 번호와 당첨 번호를 비교하여 당첨 내역 및 수익률을 출력하고 로또 게임을 종료한다.
- 사용자가 잘못된 값을 입력할 경우 "[ERROR]"로 시작하는 메시지와 함께 Error를 발생시키고 해당 메시지를 출력한 다음 해당 지점부터 다시 입력을 받는다.
## 주요 기능 분리
### 로또 구매
**구매 금액 입력받기**
- 입출력 포맷에 맞게 입력 메시지 출력
**로또 구매 금액 포맷팅**
- 입력받은 로또 구매 금액 문자열을 숫자로 변환
#### LottoPurchase 클래스
**발행한 로또 수량 출력하기**
- 로또 구매 금액을 1000으로 나눈 몫만큼 로또를 발행
- 구매 수량 메시지 출력

**번호 출력하기**
- 1부터 45까지의 수 중에서 랜덤으로 구성된 중복되지 않은 정수로 이뤄진 배열 생성
- 구매한 로또 수량만큼 반복
- 생성된 로또 번호 배열 출력

**예외처리**
- 자연수가 아닌 값이 입력된 경우 예외 발생
- 1000단위로 나누어 떨어지지 않는 금액이 입력된 경우 예외 발생

##### 단위 테스트
- LottoPurchaseTest.js 테스트 진행
- 예외처리가 올바르게 작동하는지 확인
  - 구매 금액이 자연수가 아닌 경우
  - 1000원 단위가 아닌 경우
- 기능 테스트

### 당첨 번호, 보너스 번호 입력 받기
#### 당첨 번호 입력받기
**당첨 번호 포맷팅**
- (,)을 기준으로 입력받은당첨 번호 문자열 분리
- 입력받은 로또 구매 금액 문자열을 숫자로 변환
- 변환된 숫자로 배열 생성

**예외처리**
- 6개의 수를 입력 받았는지 검사
- 중복된 수가 없는지 검사
- 각 요소가 자연수가 입력되었는지 검사
- 각 요소가 1 ~ 45 사이의 값인지 검사

#### 보너스 번호 입력받기
**보너스 번호 포맷팅**
- 입력받은 보너스 번호 문자열을 숫자로 변환
**예외처리**
- 자연수가 입력되었는지 검사
- 1 ~ 45 사이의 값인지 검사
### 당첨 내역 출력하기
**각 배열에서 당첨 번호와 일치하는 갯수 확인하기**
- 당첨여부 (3 ~ 6개가 일치하는 경우)체크
- 5개가 일치하는 경우 보너스 볼이 일치하는지 체크
- 각 케이스에 체크된 수 당첨 금액과 함께 출력
### 수익률 출력하기
**수익률 계산히기**
- 투자 금액 대비 수익률 계산
- 수익율은 소수점 둘쨰 자리에서 반올림하기
### 예외 상황
**구입 금액이 잘못 입력된 경우**
- 1000원 단위가 아닌 경우
**로또 번호가 잘못 입력된 경우**
- 1부터 45 사이의 정수가 입력되지 않은 경우
- ','로 구분되지 않는 경우
**보너스 번호가 잘못 입력된 경우**
- 1부터 45 사이의 정수가 입력되지 않은 경우
## 입출력 요구 사항
### 입력
- 로또 구입 금액을 입력 받는다. 구입 금액은 1,000원 단위로 입력 받으며 1,000원으로 나누어 떨어지지 않는 경우 예외 처리한다.
- 당첨 번호를 입력 받는다. 번호는 쉼표(,)를 기준으로 구분한다.
- 보너스 번호를 입력 받는다.
### 출력
- 발행한 로또 수량 및 번호를 출력한다. 로또 번호는 오름차순으로 정렬하여 보여준다.
- 당첨 내역을 출력한다.
- 수익률은 소수점 둘째 자리에서 반올림한다.
- 예외 상황 시 에러 문구를 출력해야한다. 단, 에러 문구는 "[ERROR]"로 시작해야 한다.
### 실행 결과 예시
```javascript
구입금액을 입력해 주세요.
8000

8개를 구매했습니다.
[8, 21, 23, 41, 42, 43] 
[3, 5, 11, 16, 32, 38] 
[7, 11, 16, 35, 36, 44] 
[1, 8, 11, 31, 41, 42] 
[13, 14, 16, 38, 42, 45] 
[7, 11, 30, 40, 42, 43] 
[2, 13, 22, 32, 38, 45] 
[1, 3, 5, 14, 22, 45]

당첨 번호를 입력해 주세요.
1,2,3,4,5,6

보너스 번호를 입력해 주세요.
7

당첨 통계
---
3개 일치 (5,000원) - 1개
4개 일치 (50,000원) - 0개
5개 일치 (1,500,000원) - 0개
5개 일치, 보너스 볼 일치 (30,000,000원) - 0개
6개 일치 (2,000,000,000원) - 0개
총 수익률은 62.5%입니다.
```
## 프로그래밍 요구 사항
### 프로그래밍 요구 사항 1
- Node.js 20.17.0 버전에서 실행 가능해야 한다.
- 프로그램 실행의 시작점은 App.js의 run()이다.
- package.json 파일은 변경할 수 없으며, 제공된 라이브러리와 스타일 라이브러리 이외의 외부 라이브러리는 사용하지 않는다.
- 프로그램 종료 시 process.exit()를 호출하지 않는다.
- 프로그래밍 요구 사항에서 달리 명시하지 않는 한 파일, 패키지 등의 이름을 바꾸거나 이동하지 않는다.
- 자바스크립트 코드 컨벤션을 지키면서 프로그래밍한다.
- 기본적으로 JavaScript Style Guide를 원칙으로 한다.
### 프로그래밍 요구 사항 2
- indent(인덴트, 들여쓰기) depth를 3이 넘지 않도록 구현한다. 2까지만 허용한다.
- 예를 들어 while문 안에 if문이 있으면 들여쓰기는 2이다.
- 힌트: indent(인덴트, 들여쓰기) depth를 줄이는 좋은 방법은 함수(또는 메서드)를 분리하면 된다.
- **3항 연산자를 쓰지 않는다.**
- 함수(또는 메서드)가 한 가지 일만 하도록 최대한 작게 만들어라.
- Jest를 이용하여 정리한 기능 목록이 정상적으로 작동하는지 테스트 코드로 확인한다.
### 프로그래밍 요구 사항 3
- 함수(또는 메서드)의 길이가 15라인을 넘어가지 않도록 구현한다.
- 함수(또는 메서드)가 한 가지 일만 잘 하도록 구현한다.
- else를 지양한다.
- 때로는 if/else, when문을 사용하는 것이 더 깔끔해 보일 수 있다. 어느 경우에 쓰는 것이 적절할지 스스로 고민해 본다.
- 힌트: if 조건절에서 값을 return하는 방식으로 구현하면 else를 사용하지 않아도 된다.
- **구현한 기능에 대한 단위 테스트를 작성한다. 단, UI(System.out, System.in, Scanner) 로직은 제외한다.**
- **단위 테스트 작성이 익숙하지 않다면 LottoTest를 참고하여 학습한 후 테스트를 작성한다.**
### 라이브러리
- @woowacourse/mission-utils에서 제공하는 Random 및 Console API를 사용하여 구현해야 한다.
- Random 값 추출은 Random. pickUniqueNumbersInRange()를 활용한다.
- 사용자의 값을 입력 및 출력하려면 Console.readLineAsync()와 Console.print()를 활용한다.
**사용 예시**
- 1에서 45 사이의 중복되지 않은 정수 6개 반환
```javascript
MissionUtils.Random.pickUniqueNumbersInRange(1, 45, 6);
```
## Lotto 클래스
- 제공된 Lotto 클래스를 사용하여 구현해야 한다.
- Lotto에 numbers 이외의 필드(인스턴스 변수)를 추가할 수 없다.
- numbers의 접근 제어자인 #은 변경할 수 없다.
- Lotto의 패키지를 변경할 수 있다.
```javascript
class Lotto {
  #numbers;

  constructor(numbers) {
    this.#validate(numbers);
    this.#numbers = numbers;
  }

  #validate(numbers) {
    if (numbers.length !== 6) {
      throw new Error("[ERROR] 로또 번호는 6개여야 합니다.");
    }
  }

  // TODO: 추가 기능 구현
}
```