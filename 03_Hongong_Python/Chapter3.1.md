# Chapter03 조건문

## 💡 학습 목표
* 불에 대해 이해합니다.
* if 조건문의 기본적인 사용 방법을 알아봅니다.
* 현실의 조건과 프로그래밍에서의 조건에 차이가 있다는 것을 이해합니다.
___

# 3-1 불 자료형과 if 조건문
`불` `비교 연산자` `논리 연산자` `if 조건문`

프로그래밍 언어에서는 기본적으로 자료형으로 참과 거짓을 나타내는 값이 있습니다. 이를 **불**(boolean)이라고 부릅니다. 불 자료를 만드는 방법과 이와 관련된 연산자에 대해 알아보겠습니다.

## 시작하기 전에
**Boolean**은 **불린** 또는 **불리언**이라는 발음으로 부릅니다. 여기서는 불이라고 표현하겠습니다. 지금까지 살펴보았던 숫자와 문자열은 만드는 형태에 따라 무한에 가까운 종류를 만들 수 있었습니다.
```
10, 100, 200, "안녕하세요", "hello", "파이썬"
```

하지만 불은 오직 **True(참)**과 **False(거짓)**값만 가질 수 있습니다. 코드를 실행하면 다음과 같습니다.
```python
>>> print(True)
>>> print(False)
True
False
```
하지만 참과 거짓을 그대로 입력하는 것은 큰 의미가 없습니다. 참과 거짓은 '어떤 명제'의 결고가 될 때 의미를 갖습니다.
___
## 불 만들기 : 비교 연산자
불은 **비교연산자**를 통해 만들 수 있습니다. 파이썬에는 여섯 개의 비교 연산자가 있습니다. 중고등학교 수학 시간에 배우는 기본적인 연산자인데, 모양은 다르지만 쉽게 이해할 수 있습니다.

| 연산자 | 설명        |
| ------ | ----------- |
| ==     | 같다        |
| !=     | 다르다      |
| <      | 작다        |
| >      | 크다        |
| <=     | 작거나 같다 |
| >=     | 크거나 같다 |

비교 연산자는 숫자 또는 문자열에 적용할 수 있습니다. 아래 결과로 살펴보겠습니다.
```python
print(10 == 100)
print(10 != 100)
print(10 < 100)
print(10 > 100)
print(10 <= 100)
print(10 >= 100)

# 실행 결과
False
True
True
False
True
False
```

**파이썬은 문자열에도 비교 연산자를 적용할 수 있습니다.** 이때 한글은 사전 순서 (가나다순)으로 앞에 있는 것이 작은 값을 갖습니다. 예를 들어 '가방'과 '하마'를 비교하면 사전 순서로 '가방'이 앞에 있으므로 '가방'이 '하마'보다 작은 값을 갖습니다. 다음 코드를 통해 결과를 살펴보겠습니다.
```python
print("가방" == "가방")
print("가방" != "하마")
print("가방" < "하마")
print("가방" > "하마")

#실행 결과
True
True
True
False
```
> **여기서 잠깐! 범위 구하기**
> 파이썬은 다음과 같은 코드를 사용해 변수의 범위 등도 비교할 수 있습니다. 실행하면 다음과 같은 결과를 출력합니다.
```python
>>> x = 25
>>> print(10 < x < 30)
True
>>> print(40 < x < 60)
False
```


___
## 불 연산하기 : 논리 연산자
불을 만들 때는 비교 연산자를 사용한다고 했습니다. 그리고 불 끼리는 **논리 연산자**를 사용할 수 있습니다. 파이썬에는 다음과 같은 세 개의 논리 연산자가 있습니다.

| 연산자 | 의미   | 설명                                                         |
| ------ | ------ | ------------------------------------------------------------ |
| not    | 아니다 | 불을 반대로 전환합니다.                                      |
| and    | 그리고 | 피연산자 두 개가 모두 참일 때 True를 출력하며, 그 외는 모두 False를 출력합니다. |
| or     | 또는   | 피연산자 두 개 중 하나라도 참이면 True를 출력하며, 두 개 모두 거짓일 때 False 출력 |

> **여기서 잠깐! 단항 연산자와 이항 연산자**
> <span style="color:blue">단항 연산자</span>는 피연산자가 한 개라는 말이고, <span style="color:blue">이항 연산자</span>는 피연산자가 두 개라는 말입니다.
> 단항 연산자 예 : +10, -10   (피연산자 한개)
> 이항 연산자 예 : 10+10, 10-10, 10*10    (연산자 양쪽에 피연산자)

### ☑️ not 연산자
not 연산자부터 알아보겠습니다. **not 연산자**는 **단항 연산자**로, **참과 거짓을 반대로 바꿀 때 사용**합니다.
```python
>>> print(not True)
False
>>> print(not False)
True
```
위의 코드처럼 True와 False에 바로 not 연산자를 적용하는 경우는 없습니다. 일반적으로 다음과 같이 비교 연산자로 불 자료형의 벼수를 만들고, 여기에 not 연산자를 적용합니다.

### 👉 not 연산자 조합하기
`소스 코드 boolean.py`
```python
x = 10
under_20 = x < 20
print("under_20 : ", under_20)
print("not under_20 : ", not under_20)

# 실행 결과
under_20 :  True
not under_20 :  False
```


### ☑️ and 연산자와 or 연산자
not 연산자는 대부분 쉽게 이해하지만, and 연산자와 or 연산자는 처음 본 사람들한테는 이해하기 힘든 연산자입니다. 먼저 최종적인 결과를 확인하고 해당 내용은 차근차근 설명하겠습니다.

**and 연산자**는 양쪽 변의 값이 모두 참일 때만 True를 결과로 냅니다.

| 좌변  | 우변  | 결과  |
| ----- | ----- | ----- |
| True  | True  | True  |
| True  | False | False |
| False | True  | False |
| False | False | False |
반면 **or연산자**는 둘 중 하나만 참이어도 True를 결과로 냅니다.

| 좌변  | 우변  | 결과  |
| ----- | ----- | ----- |
| True  | True  | True  |
| True  | False | True  |
| False | True  | True  |
| False | False | False |

and 연산자와 or 연산자 코드를 실행해보겠습니다.
```python
>>> print(True and True)
True
>>> print(True and False)
False
>>> print(False and True)
False
>>> print(False and False)
False
>>> print(True or True)
True
>>> print(True and False)
True
>>> print(False and True)
True
>>> print(False and False)
False
```
___
## 논리 연산자의 활용
논리 연산자는 많은 곳에서 사용됩니다. 지금부터 같이 살펴보겠습니다.

### ☑️ and 연산자
and 연산자를 사용하는 경우를 생각해 봅시다. 공연 티켓을 예매하는 경우를 생각해 보겠습니다. '티켓을 1장만 구매하면서 오후 3시 이후'라는 조건은 어떻게 나타낼 수 있을까요?
<span style="color:gray">'티켓 한장 이하' and '오후 3시 이후' = 티켓 구매 가능</span>
두 가지 조건을 모두 충족할 때만 티켓 구매가 가능한 것처럼 **and(그리고) 연산자**도 같은 방식으로 적용됩니다.

### ☑️ or 연산자
**or 연산자**를 사용하는 경우를 생각해 봅시다. 예를 들어 '결제한 카드가 우리카드나 신한카드라면 10% 할인해 준다'라는 조건은 어떻게 나타낼 수 있을까요?
<span style="color:gray">'우리카드' or '신한카드' = 10% 할인</span>
논리 연산자는 현실에서도 많이 사용됩니다.
___
## if 조건문이란?
파이썬에서 **if 조건문**은 조건에 따라 코드를 실행하거나, 실행하지 않게 만들고 싶을 때 사용하는 구문입니다. 이는 코드의 실행 흐름을 변경한다는 뜻입니다. 이렇게 조건을 기반으로 실행의 흐름을 벼경하는 것을 **조건 분기**라고 부릅니다.

if 조건문의 기본적인 구조는 다음과 같습니다.
```python
if 불 값이 나오는 표현식 :   #if 조건문 뒤에는 반드시 콜론(:)을 붙여줘야 합니다.
☐☐☐☐ 불 값이 참일 때 실행할 문장    #☐☐☐☐는 4칸 들여쓰기
☐☐☐☐ 불 값이 참일 때 실행할 문장
```
조건문의 기본적인 형태 예제를 실행해 보겠습니다.
```python
>>> if True :
        print("True입니다...!")
        print("정말 True입니다...!")

# 실행 결과
True입니다...!
정말 True입니다...!
```
다음과 같이 if 뒤에 있는 불 값이 거짓인 경우에는 들여쓰기 된 명령문이 있다고 하더라도 아무것도 실행되지 않습니다.
```python
>>> if False :
        print("False입니다...!")
>>>
```
다음은 **if문**을 사용하여 양수를 입력하면 "양수입니다"를, 음수를 입력하면 "음수입니다"를, 0을 입력하면 "0입니다"를 출력하는 예시입니다.

### 👉 조건문의 기본 사용
`소스코드 condition.py`
```python
# 입력을 받습니다.
number = input("정수를 입력하세요 > ")   # 사용자에게 값 받기
number = int(number)                 # 받은 값 정수(int) 형태로 저장

# 양수 조건
if number > 0 :
    print("양수입니다")

#음수 조건
if number < 0 :
    print("음수입니다")
    
# 0 조건
if number == 0 :
    print("0입니다")
    
# 실행 결과
정수를 입력하세요 > 30
양수입니다

정수를 입력하세요 > -50
음수입니다

정수를 입력하세요 > 0
0입니다
```
> **여기서 잠깐! 들여쓰기**
> 파이썬 개발에서는 일반적으로 들여쓰기로 '띄어쓰기 4번'을 많이 사용하며 이는 `Tab`키를 누르면 자동으로 띄어쓰기 네 개를 시행합니다. 이런 기능을 소프트 탭 이라 부릅니다.
> 들여쓰기를 제거하고 싶을 때는 `Shift` + `Tab` 키를 누릅니다.
> 여러 줄을 한꺼번에 들여쓰기 하고 싶다면 여러 줄을 선택하고 `Tab`키를 누릅니다.
> 여러 줄의 들여쓰기를 한번에 제거하고 싶다면 여러 줄을 선택하고 `Shift` + `Tab` 키를 누릅니다.

___
## 날짜/시간 활용하기
시간을 조건으로 구분하여 오전인지 오후인지 출력하는 프로그램을 작성해 보겠습니다. 아래 예제에서 2행과 5행 코드로 날짜와 시간을 구할 수 있는데 외우지는 말고 어딘가 적어 둔 후 필요할 때마다 복붙하자...^^

### 👉 날짜/시간 출력하기
`소스 코드 date.py`
```python
# 날짜/시간과 관련된 기능을 가져옵니다.
import datetime

#현재 날짜/시간을 구합니다.
now = datetime.datetime.now()

# 출력합니다.
print(now.year, "년")
print(now.month, "월")
print(now.day, "일")
print(now.hour, "시")
print(now.minute, "분")
print(now.second, "초")

# 실행 결과
2021 년
5 월
7 일
22 시
57 분
6 초
```
우선 7장에서 배울 **모듈**이라는 기능을 활용해서 `datetime`이라는 기능을 가져오는 게 첫 번째 해야할 일입니다.(2행) 그런 다음 `datetime.datetime.now()`라는 함수로 현재의 시간을 구해 now.hour(시), now.minute(분), nowsecond(초)를 사용해 현재의 년, 월, 일, 시, 분, 초를 출력합니다.(8~13행)

이는 현재 시각을 기반으로 하고 있기 때문에 그 결과는 실행할 때마다 다르게 나타납니다.
이전에 배웠던 `format()`함수를 활용하면 날짜를 한눈에 볼 수 있게 출력할 수 있습니다.

### 👉 날짜/시간을 한 줄로 출력하기
`소스코드 date01.py`
```python
# 날짜/시간과 관련된 기능을 가져옵니다.
import datetime

# 현재 날짜/시간을 구합니다.
now = datetime.datetime.now()

# 출력합니다.
print("{}년 {}월 {}일 {}시 {}분 {}초".format(
     now.year,
     now.month,
     now.day,
     now.hour,
     now.minute,
     now.second
))

# 실행 결과
2021년 5월 7일 23시 8분 22초
```
이제 날짜/시간과 조건문을 활용해 현재 시각을 12시 이전과 이후로 나누어 오전과 오후를 구분하는 프로그램을 작성해 보겠습니다.

> **여기서 잠깐! 파이썬에서 월 출력하기**
> 대부분 프로그래밍 언어는 월을 0~11까지 출력합니다. 이는 문자열의 첫 번째 글자를 0번째라고 세었던 것처럼 프로그래밍 언어와 규칙을 지키기 위한 목적입니다. 하지만 사람이 볼 때는 자주 헷갈리는 부분입니다.
> 따라서 파이썬은 사람이 이해하기 쉬운 형태로 월을 출력합니다. 다른 프로그래밍 언어와 다르므로 주의하세요.

### 👉 오전과 오후를 구분하는 프로그램
`소스코드 datd02.py`
```python
# 날짜/시간과 관련된 기능을 가져옵니다.
import datetime

# 현재 날짜/시간을 구합니다.
now = datetime.datetime.now()

# 오전 구분
if now.hour < 12 :
    print("현재 시각은 {}시로 오전입니다".format(now.hour))

# 오후 구분
if now.hour >= 12 :
    print("현재 시각은 {}시로 오후입니다".format(now.hour))
    
 # 실행 결과
 현재 시각은 0시로 오전입니다
```
다음과 같이 월을 사용하면 계절을 구분할 수도 있습니다.

### 👉 계절을 구분하는 프로그램
`소스코드 datd03.py`
```python
# 직접 해보는 손코딩 p119
# 계절을 구분하는 프로그램

# 날짜/시간과 관련된 기능을 가져옵니다.
import datetime

# 현재 날짜.시간을 구합니다.
now = datetime.datetime.now()

# 봄 구분
if 3 <= now.month <= 5 :
    print("이번달은 {}월로 봄입니다".format(now.month))
    
# 여름 구분
if 6 <= now.month <= 8 :
    print("이번달은 {}월로 여름입니다.".format(now.month))
    
# 가을 구분
if 9 <= now.month <= 11 :
    print("이번달은 {}월로 가을입니다.".format(now.month))
    
# 겨울 구분
if now.month == 12 or 1 <= now.month <= 2 :
    print("이번달은 {}월로 겨울입니다.".format(now.month))
    
# 실행 결과
이번달은 5월로 봄입니다
```

봄, 여름, 가을, 겨울을 조건문에서 구분했습니다.
겨울의 경우는 12월과 1~2월이므로 or연산자를 사용해 범위를 연결했습니다.
___
## 컴퓨터의 조건
if 조건문의 형식에 대해서는 다음과 같이 배웠습니다.
```python
if 불 값이 나오는 표현식 : 
☐☐☐☐ 불 값이 참일 때 실행할 문장    # ☐☐☐☐은 들여쓰기 4칸
```

if문의 '불 값이 나오는 조건문'을 어떻게 만들 것인가가 핵심입니다. 따라서 여기서는 불 값에 어떤 조건식을 넣으면 좋을지에 대해 다시 한번 생각해 보는 시간을 가져보겠습니다.

홀수와 짤수를 구분하는 예제를 통해 알아보겠습니다.

### 👉 끝자리로 짝수와 홀수 구분
`소스코드 condition01.py`

```python
# 입력을 받습니다
number = input("정수 입력 >")

# 마지막 자리 숫자를 추출
last_character = number[-1]

# 숫자로 변환하기
last_number = int(last_character)

# 짝수 확인
if last_number == 0 \
    or last_number == 2 \
    or last_number == 4 \
    or last_nember == 6 \
    or last_number == 8 :
    print("짝수입니다")

# 홀수 확인
if last_number == 1 \
    or last_number == 3 \
    or last_number == 5 \
    or last_number == 7 \
    or last_number == 9 :
    print("홀수입니다")
    
 # 실행 결과 1
 정수 입력 >100
짝수입니다

 # 실행 결과 2
 정수 입력 >253
홀수입니다
```

코드를 간단하게 수정해 보겠습니다. 앞서 in 연산자에 대해 배웠는데요, in 연산자는 어떤 문자열 내부에 찾고자 하는 문자열이 있는지를 확인할 때 사용했습니다. in 연산자를 활용해 코드를 수정해 보겠습니다.

### 👉 in 문자열 연산자를 활용해서 짝수와 홀수 구분
`소스코드 condition02.py`

```python
# 입력을 받습니다
number = input("정수 입력 > ")
last_character = number[-1]

# 짝수 조건
if last_character in "02468":
    print("짝수입니다")
    
# 홀수 조건
if last_character in "13579":
    print("홀수입니다.")
    
# 실행 결과 1
정수 입력 > 100
짝수입니다

# 실행 결과 2
정수 입력 > 13
홀수입니다.
```
3행의 last_charater에 있는 문자열이 "02468"이라는 문자열에 포함되어 있는지(6행) 혹은 "13579"라는 문자열에 포함되어 있는지(10행)를 확인해 홀수 혹은 짝수를 출력하도록 하는 코드입니다. 코드가 훨씬 깔끔해졌습니다.

한가지 더 살펴볼까요? 컴퓨터는 모든 것을 숫자로 계산하기 때문에 문자열 연산보다 숫자 연산이 조금 더 빠릅니다. 이번 예제에서는 **숫자 연산을 통해 홀수와 짝수를 구분해 보겠습니다.**

### 👉 나머지 연산자를 활용해서 짝수와 홀수 구분
`소스코드 condition03.py`

```python
# 입력을 받습니다
number = input("정수 입력 > ")
number = int(number)

# 짝수 조건
if number % 2 == 0 :
    print("짝수입니다")
    
# 홀수 조건
if number % 2 == 1 :
    print("홀수입니다")
    
# 실행 결과 1
정수 입력 > 243
홀수입니다

# 실행 결과 2
정수 입력 > 568
짝수입니다
```

단순하게 2로 나눈 나머지가 0이면 '짝수', 1이면 '홀수'라고 지정한 것입니다. 이처럼 우리는 짝수와 홀수를 구분할 때 숫자의 끝자리가 2, 4, 6, 8, 0이라면 곧바로 짝수라고 생각하지만, **컴퓨터는 2로 나눈 나머지가 0인지를 확인하는 것이 좋습니다.** 그래서 조건문을 만들 때는 언제나 '컴퓨터에서는 어떻게 하는 게 더 빠를까'를 생각해야 합니다.

___
## 마무리
### 🔍 4가지 키워드 핵심 포인트
* **불**(boolean)은 파이썬의 기본 자료형으로 True(참)와 False(거짓)을 나타내는 값입니다.
* **비교 연산자**는 숫자 또는 문자열에 적용하며, 대소를 비교하는 연산자입니다.
* **논리 연산자**는 not, and, or 연산자가 있으며, 불을 만들 때 사용합니다.
* **if 조건문**은 조건에 따라 코드를 실행하거나 실행하지 않게 만들고 싶을 때 사용하는 구문입니다.

### 🔍 확인문제
#### 1. 비교 연산자를 사용한 조건식입니다. 결과가 참이면 True를, 거짓이면 False를 적어 보세요.

| 조건식    | 결과  |
| --------- | ----- |
| 10 == 100 | False |
| 10 != 100 | True  |
| 10 > 100  | False |
| 10 < 100  | True  |
| 10 <= 100 | True  |
| 10 >= 100 | False |

#### 2. 다음 세 개의 예제 중 "참입니다"를 출력하는 것은 몇 번 예제인가요?
```python
# 1번
#1번
x = 2
if x > 4 :
    print("참입니다")
    
# 2번
x = 1
if x > 4 :
    print("참입니다")
    
# 3번
x = 10
if x > 4 :
    print("참입니다")
```
정답 :  3번

#### 3. 다음 상황들은 선택 조건으로 and 및 or 연산자를 적용하고 있습니다. 어떤 연산자가 사용되었을까요? and 연산자라면 'a', or 연산자라면 'o'를 괄호 안에 적어 보세요.

① 치킨이나 햄버거가 먹고 싶어서, 음식 주문 애플리케이션에서 치킨과 햄버거를 선택했다 (<span style="color:blue">and</span>)
② H 브랜드가 출시한 10만원 이하의 가방을 구매하고 싶어서, H 브랜드와 10만원 이하를 조건으로 선택해서 검색했다 (<span style="color:blue">and</span>)
③ 고궁에 입장하는데, 65세 이상의 어르신과 5살 이하의 아동은 무료 입장이었다. (<span style="color:blue">or</span>)

#### 4. 사용자로부터 숫자 두 개를 입력받고 첫 번째 입력받은 숫자가 큰지, 두 번째 입력받은 숫자가 큰지를 구하는 프로그램을 다음 빈칸을 채워 완성해 보세요.
```python
# input 함수로 사용자에게 입력 받은 문자 float 함수로 숫자형 변환
a = float(input("> 1번째 숫자 : "))
b = float(input("> 2번째 숫자 : "))
print()

if a>b :
    print("처음 입력했던 {}가 {}보다 큽니다".format(a,b))
    
if a<b :
    print("두 번째로 입력했던 {}가 {}보다 큽니다.".format(b,a))
    
# 실행 결과
> 1번째 숫자 : 123
> 2번째 숫자 : 44

처음 입력했던 123.0가 44.0보다 큽니다
```

> 윤성인, 『혼자 공부하는 파이썬』, 한빛미디어(2019), p106-125.