## Logical Operator

#### 1. 논리 연산자

- 논리 연산자는 and, or, not이 존재한다.
  and와 or 연산자는 피연산자가 두 개이지만
  not 연산자는 피연산자가 하나이다.

- 참고로 And, AND와 같이 대문자로 쓰면 오류가 발생하며
  and와 같이 반드시 소문자로 써야한다.

  ##### 1-1 and 연산자

  - and 연산자는 두 개의 피연산자가 모두 True이면 True를 리턴하고
    하나라도 False라면 False를 리턴한다.

  - 다음은 and 연산자의 예제이다.

    ```python
    >>> True and True
    True
    >>> True and False
    False
    >>> False and True
    False
    >>> False and False
    False
    ```

  ##### 1-2 or 연산자

  - or 연산자는 두 개의 피연산자 중 하나라도 True라면 True를 리턴하는
    논리 연산자이다.

  - 다음은 or 연산자의 예제이다.

    ```python
    >>> True or True
    True
    >>> True or False
    True
    >>> False or True
    True
    >>> False or False
    False
    ```

  ##### 1-3 not 연산자

  - not 연산자는 하나의 피연산자를 가지며 not x와 같이 사용됩니다.
    피연산자가 True라면 False를 리턴하고 False라면 True를 리턴하는 논리 연산자이다.

  - 다음은 not 연산자의 예제이다.

    ```python
    >>> not True
    False
    >>> not False
    True
    ```

#### 2. 논리 연산자와 비교 연산자

- 논리 연산자와 비교 연산자를 같이 사용하게 되면 어떻게 될까?
  다음은 논리 연산자와 비교 연산자를 같이 사용한 예제이다.

  ```python
  >>> 1 == 1 or 1 == 2
  True
  ```

- 위를 해석하면 1==1은 True이고 1==2는 False이며
  or은 하나만 True여도 True를 리턴하므로 True가 답이 된다.

- 여기서 잘 생각해보면 첫 번째 == 연산자가 작동한 뒤 or이 아니라
  두 번째 == 연산자를 실행시키는 것을 알 수 있다.
  하지만 이것은 어찌보면 당연한 일이다.
  왜냐하면 or 연산자의 피연산자는 모두 bool 타입이여야하는데
  ==이 연산되지 않은 상태의 or 연산자의 피 연산자는 1과 1이므로 bool타입이 아님을 알 수 있다.

- 따라서 논리 연산자와 비교 연산자가 잇으면 당연히 비교 연산자가 먼저 계산된다.
  하지만 파이썬의 연산자 우선순위에서는 논리 연산자보단 비교 연산자가 먼저 계산 되도록
  되어 있기 때문에 이 때문이라고 볼 수도 있다.

#### 3. bool 타입 변환

- bool 타입 변환은 기존의 정수 타입 변환과 실수 타입 변환과 마찬가지로 bool() 함수를 이용한다.
  하지만 여기서 중요한 점은 bool으로 타입 변환을 할 수 있다가 아니라 변환되는 기준이다.
- bool() 함수의 매개변수로 0이 아닌 숫자가 들어가면 True가 리턴되고
  0이 들어가면 False가 리턴된다.
  또한 문자열도 포함될 수 있는데 문자열이 비어 있으면 False를 리턴하고
  비어있지 않으면 True를 리턴한다.
  문자열의 내용은 생각하지 않기 때문에 문자열이 'False'라도 True를 리턴한다.

#### 4. 단락 평가

- 단락 평가란 논리 연산자를 계산할 때 첫 번째 피연산자를 보고 결과를 알 수 있다면
  그 뒤의 피연산자를 확인하지 않고 결과를 내는 것을 말한다.

- 예를 들어서 and 연산자를 이용하는데 첫 번째 피연산자가 False라면
  두 번째 피연산자가 True든, False든 간에 결과는 False이므로 두 번째 피연산자를 확인하지 않는다.
  이러한 기능을 단락 평가라고 한다.

  ```python
  >>> True or (...)
  True
  ```

- 지금은 적어놓지는 않았지만 or 뒤의 피연산자가 무엇이든 간에 무조건 True가 리턴되므로
  뒤의 피연산자를 확인하지 않는다.