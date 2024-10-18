# AIFFEL Data Scientist Campus Code Peer Review Templete

코더 : [여혜미]

리뷰어 : [김규민]

---

🔑 **PRT(Peer Review Template)**

[V]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
- 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
	- (문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 퀘스트 문제 요구조건 등을 지칭)
- 해당 조건을 만족하는 코드를 캡쳐해 근거로 첨부
import random

acc_num_ex = str(random.randint(1,999)).zfill(3) + '-' + str(random.randint(1, 99)).zfill(2) + '-' + str(random.randint(1,999999)).zfill(6)

class Account:
  object_count = 0

  def __init__(self, name, balance):
    self.name = name
    self.balance = balance
    self.bank_name = 'SC은행'
    self.account_num = acc_num_ex
    self.deposit_count = 1
    Account.object_count += 1
    self.dep_history = ''
    self.wit_history = ''

  def get_account_num(self):
    return Account.object_count

  def deposit(self, amount):
    if self.deposit_count < 5:  # 5회 이하로 입금했을 경우
      if amount >= 1:
        self.balance += amount
        self.deposit_count += 1
        self.dep_history += f'금액: {amount}, 계좌잔액: {self.balance}\n'
      else:
        return "1원 이상을 입금해주세요."
    else:                       # 5회 이상 입금했을 경우
      if amount >= 1:
        self.balance += amount
        self.balance *= 1.01
        self.deposit_count = 1
        self.dep_history += f'금액: {amount}, 계좌잔액: {self.balance}\n'
      else:
        return "1원 이상을 입금해주세요."

  def withdraw(self, amount):
    if amount > self.balance:
      return "잔액보다 출금액이 큽니다."
    else:
      self.balance -= amount
      self.wit_history += f'금액: {amount}, 계좌잔액: {self.balance}\n'

  def display_info(self):
    return f'은행이름: {self.bank_name}, 예금주: {self.name}, 계좌번호: {self.account_num}, 잔고: {self.balance: ,}원'

  def deposit_history(self):
    print(f'{self.dep_history}')

  def withdraw_history(self):
    print(f'{self.wit_history}')

a = Account('지우', 1000000)
b = Account('혜미', 1500000)
c = Account('정은', 800000)

account_list = [a, b, c]

for i in account_list:
  if i.balance >= 1000000:
    print(i.display_info())

a.display_info()

a.deposit(100)
a.deposit(200)
a.deposit(0)
a.deposit(200000)
a.deposit(400000)
a.deposit(2000)

a.deposit_history()

a.get_account_num()

[O]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
	주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
- 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
- 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
입금을 5회를 기준으로 나눔을 주석으로 설명을 했고, 출력 결과들에 string을 잘 넣어서 이해하기 쉽게했습니다.
- 주석을 보고 코드 이해가 잘 되었는지 확인
	- 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
  def deposit(self, amount):
    if self.deposit_count < 5:  # 5회 이하로 입금했을 경우
      if amount >= 1:
        self.balance += amount
        self.deposit_count += 1
        self.dep_history += f'금액: {amount}, 계좌잔액: {self.balance}\n'
      else:
        return "1원 이상을 입금해주세요."
    else:                       # 5회 이상 입금했을 경우
      if amount >= 1:
        self.balance += amount
        self.balance *= 1.01
        self.deposit_count = 1
        self.dep_history += f'금액: {amount}, 계좌잔액: {self.balance}\n'
      else:
        return "1원 이상을 입금해주세요."

  def withdraw(self, amount):
    if amount > self.balance:
      return "잔액보다 출금액이 큽니다."
    else:
      self.balance -= amount
      self.wit_history += f'금액: {amount}, 계좌잔액: {self.balance}\n'

  def display_info(self):
    return f'은행이름: {self.bank_name}, 예금주: {self.name}, 계좌번호: {self.account_num}, 잔고: {self.balance: ,}원'
        
[X]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록"을 남겼거나 "새로운 시도 
또는 추가 실험"을 수행해봤나요?**
- 문제 원인 및 해결 과정을 잘 기록하였는지 확인 또는
해당 기록은 없었습니다.
- 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 실험이 기록되어 있는지 확인
	- 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
        
[X]  **4. 회고를 잘 작성했나요?**
- 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해 배운점과 아쉬운점, 느낀점 등이 상세히 기록되어 있는지 확인
회고에 대한 내용은 없었습니다.
    - 딥러닝 모델의 경우, 인풋이 들어가 최종적으로 아웃풋이 나오기까지의 전체 흐름을 도식화하여 모델 아키텍쳐에 대한 이해를 돕고 있는지 확인

[O]  **5. 코드가 간결하고 효율적인가요?**
- 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
잘 준수하였습니다.
- 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 모듈화(함수화) 했는지
	- 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.

모듈화 잘 한 부분
import random

acc_num_ex = str(random.randint(1,999)).zfill(3) + '-' + str(random.randint(1, 99)).zfill(2) + '-' + str(random.randint(1,999999)).zfill(6)

class Account:
  object_count = 0

  def __init__(self, name, balance):
    self.name = name
    self.balance = balance
    self.bank_name = 'SC은행'
    self.account_num = acc_num_ex
    self.deposit_count = 1
    Account.object_count += 1
    self.dep_history = ''
    self.wit_history = ''
최소화 한 것인지는아직 잘 판단이 안됩니다 ㅠ


---
### 참고 문헌
