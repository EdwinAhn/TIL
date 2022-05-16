## 상속 (Inheritance)
말 그대로 부모가 가진 것을 자손에게 물려주듯
<br> 상위 클래스의 멤버(필드,메서드,이너 클래스)를 하위 클래스에게 물려주는 것.
<br>그렇기에 하위 클래스의 멤버 수는 상위 클래스의 멤버 수와 같거나 많다.
<br><br> * (더 확실한 이해를 위해 "객체지향 프로그래밍 기초"에서 예시를 들은 '사람모양의 게임캐릭터 제작 예시'를 생각하자.)

![상속 예시](https://github.com/Luxahn/TIL/blob/main/img/%E1%84%89%E1%85%A1%E1%86%BC%E1%84%89%E1%85%A9%E1%86%A8%20%E1%84%8B%E1%85%A8%E1%84%89%E1%85%B5.png)
<br><br>
### 상속의 이점
- 상속을 통해 코드의 중복을 줄일 수 있다. (효율 증가)
- 다형적 표현이 가능하다.
    * 다형적 표현: 하나의 객체가 여러 모양으로 표현 될 수 있는 것. (Ex. "프로그래머는 프로그래머이다."는 참이다. 그와 동시에 "프로그래머는 사람이다." 또한 참.)

<br><br>

## 상속(Inheritance)을 사용하는 방법
- ``` extends ``` 키워드를 사용한다.

```java
class Person {
    String name;
    int designation;

    void learn(){
        System.out.println("공부");
    };
    void walk(){
        System.out.println("걷기");
    };
    void eat(){
        System.out.println("먹기");
    };
}

class Programmer extends Person { // Person 클래스로부터 상속. extends 키워드 사용 
    String companyName;

    void coding(){
        System.out.println("코딩하기");
    };
}

class Dancer extends Person { // Person 클래스로부터 상속. extends 키워드 사용
    String groupName;

    void dancing(){
		    System.out.println("춤 추기");
		};
}

class Singer extends Person { // Person 클래스로부터 상속. extends 키워드 사용
    String bandName;

    void singing(){
		    System.out.println("노래하기");
		};
    void playGuitar(){
		    System.out.println("기타 치기");
		};
}

public class HelloJava {
    public static void main(String[] args){

        //Person 객체 생성
        Person p = new Person();
        p.name = "김개발";
        p.designation = junior;
        p.learn();
        p.eat();
        p.walk();
        System.out.println(p.name);

        //Programmer 객체 생성
        Programmer pg = new Programmer();
        pg.name = "이코딩";
        pg.designation = senior;
        pg.learn(); // Persons 클래스에서 상속받아 사용 가능
        pg.coding(); // Programmer의 개별 기능
        System.out.println(pg.name);

    }
}
```
<br><br>

## 포함(composite) 관계
```java
 public class Student{
        int id;
        String name;
        EduBG major;

        public Student(int id, String name, EduBG major) {
            this.id = id;
            this.name = name;
            this.major = major;
        }

        void showInfo() {
            System.out.println(id + " " + name);
            System.out.println(major.major+ " " + major.school);
        }

        public static void main(String[] args) {
            EduBG major1 = new EduBG("컴공", "서울대");
            EduBG major2 = new EduBG("경영학", "하버드대");

            Student s = new Student(1, "김개발", major1);
            Student s2 = new Student(2, "이경영", major2);

            s.showInfo();
            s2.showInfo();
        }
    }

    class EduBG {
        String major, school;

        public EduBG(String major, String school) {
            this.major = major;
            this.school = school;
        }
    }

```

원래라면 ```EduBG``` 클래스에 포함되어 있는 인스턴스 변수 major와 school을 각각 ```Student  ``` 클래스의 변수로 정의해줘야 하지만,<br> ```EduBG``` 클래스로 해당 변수들을 묶어준 다음 ```Student  ``` 클래스 안에 참조변수를 선언하는 방법으로 코드의 중복을 없애고 포함 관계로 코드를 재사용 하고 있다.

### 상속 관계를 맺어야 하는지, 포함 관계를 맺어야 하는지 구분하는 방법
- 상속 관계
    - '~은(는) ~이다.(IS-A)의 문장 형식을 대입해보자.
<br>

- 포함 관계
    - '~은(는) ~을(를) 가지고 있다.(HAS-A)'의 문장 형식을 대입해보자.

둘 중 더 자연스러운 문장이 무엇인지 생각해서 코드를 짜보면 된다.

EX)<br>
 "Student"는 "EduBG(Educational Background)"이다. -> 어색.
<br>
"Student"는 "EduBG(Educational Background)"를 가지고 있다. -> 자연스러움.
<br>
때문에 위의 경우 포함관계를 쓰는 것이 더 적합하다고 볼 수 있다.
<br><br><br>

## 최상위 클래스, Object 클래스
자바 클래스 상속계층도에서 최상위에 위치한 클래스가 Object 클래스이다.
- 자바의 모든 클래스는 Object 클래스를 상속 받는다. -> True;

아무것도 상속하고 있지 않은 class는 자동으로 extends Object를 추가한다. <br>
그리고 이는 모든 class가 Object 클래스의 멤버들을 자동으로 상속받아 사용할 수 있다는 뜻이다.<br><br><br>

**주로 쓰이는 Object 클래스의 메서드**

|메서드 이름|반환타입|내용|
|------------------|------|---|
|toString()|String|객체 정보를 문자열로 출력|
|equals(Object obj)|boolean|등가 비교 연산(==)과 동일하게 스택 메모리값을 비교|
|hashCode()|int|객체의 위치정보 관련. Hashtable 또는 HashMap에서 동일 객체여부 판단|
|wait()|void|현재 쓰레드 일시정지|
|notify()|void|일시정지 중인 쓰레드 재동작

<br><br><br>

## 메서드 오버라이딩(Method Overriding)
메서드 오버라이딩(Method Overriding)은 상위 클래스로부터 상속받은 메서드와 동일한 이름의 메서드를 재정의 하는 것을 의미한다.
<br>
→ 컴퓨터 파일 덮어쓰기 기능과 비슷한 역할

<br>

### 메서드 오버라이딩의 3가지 조건
1. 메서드의 선언부(메서드 이름, 매개변수, 반환타입)가 상위 클래스의 메서드와 완전히 일치해야한다.

2. 접근 제어자의 범위가 상위 클래스의 메서드보다 같거나 넓어야 한다.

3. 예외는 상위 클래스의 메서드보다 많이 선언할 수 없다.


### 메서드 오버라이딩 사용 예시
```java
public class Main {
        public static void main(String[] args) {
            BrownHorse brownHorse = new BrownHorse(); // 각각의 타입으로 선언 + 각각의 타입으로 객체 생성
            WhiteHorse whiteHorse = new WhiteHorse();
            BlackHorse blackHorse = new BlackHorse();

            brownHorse.run();
            whiteHorse.run();
            blackHorse.run();

        //    Horse brownHorse2 = new BrownHorse(); // 상위 클래스 타입으로 선언 + 각각 타입으로 객체 생성
        //    Horse whiteHorse2 = new WhiteHorse();
        //    Horse blackHorse2 = new BlackHorse();

        //    brownHorse2.run();
        //    whiteHorse2.run();
        //    blackHorse2.run();
        }
    }

    class Horse {
        void run() {
            System.out.println("Horse is running");
        }
    }

    class BrownHorse extends Horse {
        void run() {
            System.out.println("Brown Horse is running");
        }
    }

    class WhiteHorse extends Horse {
        void run() {
            System.out.println("White Horse is running");
        }
    }

    class BlackHorse extends Horse {
        void run() {
            System.out.println("Black Horse is running");
        }
    }
    
// Output
    // Brown Horse is running
    // White Horse is running
    // Black Horse is running
```

**배열을 이용하면 더 편하게 관리할 수 있다.**
```java
Horse[] horse = new Horse[] { new BrownHorse(), new WhiteHorse(), new BlackHorse()};
for (Horse horse : horse) {
    horse.run();
}

// Output
    // Brown Horse is running
    // White Horse is running
    // Black Horse is running
```

## super()와 super 키워드 (this, this()파일에 함께 넣자.)

this() 메서드는 같은 클래스의 다른 생성자를 호출하는데 사용되는 메서드이고(생성자 안에서만 사용 가능하고, 반드시 생성자의 첫줄에 위치해야 함.) <br>
this는 자기 객체를 가리키는 참조 변수명이다.

그와 쓰임새가 비슷하지만 super()는 상위 클래스의 생성자, <br>
super는 상위 클래스의 객체를 의미한다.

