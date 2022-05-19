## 람다
- 함수(메서드)를 간단한 ‘식(expression)’으로 표현하는 방법.
- 익명 함수(anonymous function). * 자바에서 객체는 클래스 바깥에 있을 수 없기 때문에 람다식은 ‘익명 객체’라고 말하는게 더 맞다, 그런데  그 객체를 익명 함수처럼 표현할 수 있기 때문에 겉모습은 익명 함수의 모습이 있다.
    - ✓ 반환타입 없이 화살표(->)로 식을 만듬 
    ```java
    int max(int a, int b) {     return a > b ? a : b; } 를  (int a, int b) -> { return a > b ? a : b; }
    ```
    로 표현할 수 있다. 그래서 익명함수라는 말이 나옴

- 함수와 메서드는 근본적으로 동일하다. 그러나 함수는 일반적 용어이고 메서드는 객체지향개념 용어이다.  원론적으로 함수는 클래스에 독립적이고 메서드는 클래스에 종속적이다. 그런데 자바에서 객체는 클래스 바깥에 있을 수 없다. 때문에 모두 메서드. 그렇지만 람다식은 함수형 언어를 자바에서 쓸 수 있도록 한 것이기 때문에 메서드이지만 함수처럼 쓰임.  즉, 람다식은 익명 함수가 아니라 익명 객체이다!


반환값이 있는 경우, 식이나 값만 적고 return문 생략 가능(끝에 ;를 안붙임) 	
```java
(int a, int b) -> a > b ? a : b
```

매개변수의 타입이 추론 가능하면 생략가능(대부분의 경우 생략가능)
		```java
    (a, b) -> a > b ? a : b ```

주의사항
1. 매개변수가 하나인 경우, 괄호() 생략 가능.(타입이 없을 때만) 
```java
(a) -> a * a           =>.          a -> a * a    // O

(int a) -> a * a.     =>.          int a -> a * a   // X
 						                        (타입이 생략이 안될 경우도 있음)
                                    ```

2. 블록 안의 문장이 하나뿐 일 때, 괄호{} 생략 가능 (끝에 ; 안 붙임) 
```java
(int i) -> {      System.out.println(i) ;        =>.   (int i) -> System.ot.println(i) } 
```



@FunctionalInterface // 함수형 인터페이스는 단 하나의 추상 메서드만 가져야 함.
interface myFunction {
    public abstract int max(int a, int b);
   // public abstract int max2(int a, int b); 
    // @FunctionalInterface를 붙이면 myFunction이 함수형 인터페이스라는 뜻이다.
    // 그렇기 때문에 추상 메서드를 두 개 붙이면 에러가 뜬다.
    
    
    
   <br><br><br><br>
   ```java
   public class Lambda {
    public static void main(String[] args) {
        myFunction function = (a, b) -> a > b ? a: b; // 람다식(익명 객체)을 다루기 위한 참조변수의 타입은 함수형 인터페이스로 한다.
                                        // a가 b보다 크면 a를 반환하고, 작으면 b를 반환하라.
            int value = function.max(3, 5);
        System.out.println("value="+value);
    }
}
// 함수형 인터페이스를 쓸 때는 람다식하고 매개변수와 반환타입이 일치해야한다.



@FunctionalInterface // 함수형 인터페이스는 단 하나의 추상 메서드만 가져야 함.
interface myFunction {
    int max(int a, int b); // max() 추상 메서드를 통해 람다식을 호출한다.
   // public abstract int max2(int a, int b);
    // @FunctionalInterface를 붙이면 myFunction이 함수형 인터페이스라는 뜻이다.
    // 그렇기 때문에 추상 메서드를 두 개 붙이면 에러가 뜬다.
}



// + 함수형 인터페이스를 통해 메서드의 매개변수로 람다식을 받을 수 있다.
// + 메서드의 반환타입으로 함수형 인터페이스를 적어줘서 람다식을 반환할 수 있다.
```




인터페이스가 가질 수 있는 메서드는
default 메서드, static메서드, ⭐︎추상 메서드
이 3개.

