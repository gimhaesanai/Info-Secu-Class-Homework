## Lambda

- 함수형 프로그래밍 방식이 처음에 나왔을때와는 다르게 요즘에는 핫한 프로그래밍 방식이 되어가고 있다.
  그에 따라 자바에서는 객체 지향형 프로그래밍 방식과 함수형 프로그래밍 방식을 합친 방식으로
  자바의 방향을 잡아가고 있다.
  그에 따라 자바에서는 익명 객체와 람다식과 같은 방식을 지원한다.

- 익명 객체를 이전에 다루었었고 람다식은 다루지 않았었다.
  람다식은 기본적으로 코드가 간결해진다는 장점을 가지고 있다.
  그리고 람다식은 런타임시에 익명 객체로 모두 변환된다.

- 다음은 기존의 익명 객체로 구현한 Runnable 인터페이스이다.

  ```java
  Runnable runnable = new Runnable() {
      public void run() {
          System.out.println("실행");
      }
  }
  ```

  다음은 람다식을 이용해서 구현한 Runnable 인터페이스이다.

  ```java
  Runnable runnable = () -> {
      System.out.println("실행");
  }
  ```

- 이전까지 람다식을 본적이 있다면 대충 알겠지만
  처음 본 사람은 어색할 수도 있다.
  일단 람다식은 괄호와 화살표 이후에 중괄호를 통해 인터페이스를 구현하게 된다.

- 첫 번째 괄호는 인터페이스 안의 구현해야하는 메소드의 매개변수를 넣는 자리이다.
  이미 매개변수는 인터페이스에 타입이 모두 선언되어 있기 때문에
  람다식을 작성할때 굳이 선언할 필요가 없다.
  따라서 타입을 제외한 매개변수를 넣는 곳이라고 알 수 있다.
  매개변수는 여러 개가 들어갈 수 있으며 매개변수가 하나일 경우 괄호를 생략할 수 있고,
  매개변수가 없을 경우에는 반드시 괄호를 사용해야 한다.

- 두 번째 화살표는 람다식임을 표현하는 기호이다.

- 세 번째 중괄호 속의 내용은 인터페이스의 메소드의 구현체를 정의하는 곳이다.
  구현하고자하는 인터페이스는 추상 메소드가 하나밖에 없기 때문에
  메소드의 형식을 만들 필요는 없다.
  단지 내용만을 정의하면 된다.
  만약 내용이 한 줄 밖에 안 되는 경우에는 중괄호도 생략할 수 있다.

  ```java
  () -> System.out.println("실행");
  ```

  만약 리턴문이 존재한다면 return을 사용하면 된다.
  만약 리턴문이 존재하는데 내용이 리턴문밖에 없는 경우에는 다음과 같이 중괄호와 return을 제거할 수 있다.

  ```java
  (x, y) -> x * y;
  ```

- 전에 말했듯이 람다식으로 구현하는 인터페이스는 추상 메소드가 하나만 존재하여야 한다.
  이렇게 추상 메소드가 하나인 인터페이스를 함수적 인터페이스(functional interface) 라고 한다.
  인터페이스를 선언할때 이러한 오류를 범하지 않기 위해서 @FunctionalInterface 어노테이션을 지원한다.
  이 어노테이션은 인터페이스가 추상 메소드 하나만을 가지고 있는지 확인하는 어노테이션이다.
  물론 사용하지 않아도 추상 메소드 하나라는 조건만 달성한다면 람다식으로 사용할 수 있다.
- 이렇게 람다식은 추상 메소드 하나 라는 조건을 가지고 있기 때문에
  모든 것을 대체할 수는 없다고 생각할 수 없다.