## 캡슐화(Encapsulation)
우리가 먹는 약은, 약에 따라 약이 녹아야 하는 위치와 시간이 다르다.(어떤 약은 위에서 녹아야 하고, 어떤 약은 장에서 녹아야 한다.)이 때, 캡슐 알약의 캡슐은 녹는 시간(위치)를 조절하는 역할을 한다. 만일 캡슐을 쓰지 않는다면 약이 올바른 위치에서 녹지 못해 약의 효능이 떨어질 수 있으며, 올바른 위치에 녹지 못한 약 때문에 장기가 다칠 수 있다. 즉, 외부로터 약을 보호함과 동시에 외부(장기)를 보호하는 역할을 하는 것이다.
<br><br>

이처럼 OOP에서의 캡슐화는 특정 객체 안에 관련된 속성과 기능을 하나의 캡슐로 만들어 데이터를 외부로부터 보호하고, 외부 또한 불필요한 변경으로부터 보호하기 위해 사용된다.<br>
![캡슐화이미지](https://github.com/Luxahn/TIL/blob/main/img/Encapsulation-illustration-with-capsule.png)
<br><br>

**목적**
- 데이터 보호
- 내부적으로만 사용되는 데이터에 대한 불필요한 외부 노출을 막기 위해
- 정보 은닉(Data Hiding)

이러한 캡슐화의 가장 큰 장점은 '정보 은닉(Data Hiding)'이다. <br>
즉, 외부로부터 객체의 속성과 기능이 함부로 변경되지 못하게 막으며 <br>
데이터가 변경되더라도 다른 객체에 영향을 주지 않아 독립성을 확보할 수 있다. <br>
그리고, 유지보수와 코드 확장 시에도 오류 범위를 최소화할 수 있어, 효과적으로 코드를 유지보수할 수 있게끔 한다.<br><br><br>

## 패키지
특정한 목적을 공유하는 클래스와 인터페이스의 묶음을 의미한다.<br>
코드를 쓸 때 제일 위에 쓰이는 ```package 패키지명```이 패키지를 선언하는 것이다.<br>
→ 컴퓨터의 폴더의 역할과 비슷하다.

**자바의 패키지**
- 물리적인 하나의 디렉토리<br>
→ 하나의 패키지에 속한 클래스나 인터페이스 파일은 모두 해당 패키지에 속해있음.

- 계층구조를 가지고 있다.<br>
→ < . >으로 구분한다.

- 소스 코드의 첫번 째 줄에 반드시 표기 되어야 한다. (없으면 이름없는 패키지에 속하게 됨.) <br>
→ 'package 패키지명'으로 선언 <br><br>

```java
package packagename.test; // 패키지가 없으면 구문이 필요없다.

public class Ex {

}
```

**패키지의 장점**
- 같은 클래스 명을 쓰더라도 다른 패키지에 있으면 구별이 가능해 충돌을 방지할 수 있다.

<br><br>
### Import문
다른 패키지에 있는 클래스를 사용할 수 있도록 해준다. <br>
- 패키지 구문과 클래스문 사이에 작성한다.

```java
import 패키지명.클래스명;
```

<br><br>
해당 패키지의 모든 클래스를 사용하는 경우
```java
import 패키지명.*;
```
<br><br>

## 접근 제어자
접근 제어자를 보기전에 먼저 이를 포함하는 개념인 제어자에 대해 알아보자.

### 제어자(Modifier)
클래스, 필드, 메서드, 생성자 등에 부가적인 의미를 부여하는 키워드. <br>
('따스한 햇빛'에서 '따스한'처럼 형용사 같은 역할.)

접근 제어자와 기타 제어자로 나뉨.

- 접근 제어자 <br>
→ public, protected, default, private

- 기타 제어자 <br>
→ static, final, abstract, native, transient, synchronized 등

<br><br>

### 접근 제어자(Access Modifier)
가장 많이 쓰이는 캡슐화의 핵심. <br>
클래스 내부에 있는 데이터의 불필요한 노출을 방지(data hiding)하고, <br>
외부로부터 멋대로 데이터에 관여하여 변경되지 않도록 막아줄 수 있다.<br><br>

가장 열려 있는 접근 제어자 순으로 <br>
**public > protected > default > private**

|접근 제어자|클래스 내|패키지 내|다른 패키지 내, 자신의 하위 클래스|패키지 외|
|:------:|:-----:|:-----:|:------------------------:|:-----:|
|public|O|O|O|O
|protected|O|O|O|X|
|default|O|O|X|X|
|private|O|X|X|X|

<br><br>

## setter와 getter 메서드
캡슐화의 데이터 보호와 데이터 은닉을 지키면서 데이터의 변경이 필요할 경우 <br>
setter와 getter 메서드를 사용할 수 있다.

- setter <br>
set+메서드명 [Ex. setName()] <br>
외부에서 메서드에 접근하여 조건에 맞을 경우 데이터 값을 변경하게 해준다.

- getter
get+메서드명 [Ex. getAge()] <br>
특정 데이터를 읽어오는 데 사용된다.

[코드 예시]

```java
public class SetterGetterEX {
    public static void main(String[] args) {
        People a = new People();
        a.setName("김모씨");
        a.setAge(25);
        a.setGender("남자");

        String name = a.getName();
        System.out.println("이름: " + name);
        int age = a.getAge();
        System.out.println("나이: " + age);
        String gender = a.getGender();
        System.out.println("성별: " + gender);
    }
}

class People {
    private String name; // 변수의 은닉화. 외부로부터 접근 불가
    private int age;
    private String gender;

    public String getName() { // 멤버변수의 값
        return name;
    }

    public void setName(String name) { // 멤버변수의 값 변경
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        if(age < 1) return;
        this.age = age;
    }

    public String getGender() {
        return gender;
    }

    public void setGender(String gender) {
        this.gender = gender;
    }
}

//Output
//  이름: 김모씨
//  나이: 25
//  성별: 남자
```

한 클래스내에 private에 변수가 있고, <br>
그 클래스 내에서 private에 접근할 수 있는 public 접근 제어자의 getter,setter 메서드를 만들어 설정하면, <br>
다른 클래스에서도 public 접근제어자의 getter, setter 메서드를 통해 <br>private에 있는 변수 값에 접근할 수 있다.

<br><br>
setter만, 혹은 getter만 쓰는 경우
- setter O, getter X   → 쓰기 전용
- setter X, getter O   → 읽기 전용

