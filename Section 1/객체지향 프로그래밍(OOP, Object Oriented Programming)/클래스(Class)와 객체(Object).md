### 클래스(Class)
- 객체(Object)의 속성과 기능을 정의한 설계도, 틀(Frame)

### 객체(Object)
(클래스와 함께 쓰인다고 가정하면) 클래스의 정의된 설계 내용에 따라 그 속성과 기능을 가지고 생성된 어떠한 것(객체).
<br><br>
Ex) 설계도(클래스)를 가지고 그 속성과 기능을 따라 각각의 집(객체)이 만들어진다.
<br>![설계도와 집]()
<br>![붕어빵 틀과 붕어빵]()
<br><br>
이렇게 클래스를 통해 생성된 객체를 인스턴스(instance)라고 한다.
<br><br>
*✓ 객체와 인스턴스의 차이가 뭘까?*
<br>크게 보자면 같은 의미이고(보통 같은 뜻으로 혼용해서 쓴다.),
<br>더 엄격히 보자면
<br>객체(object)는 모든 인스턴스를 포괄하는 넓은 의미이다.
<br>인스턴스(instance)는 해당 객체가 어떤 클래스로부터 생성된 것인지를 강조한다는 데 그 차이가 있다.
<br><br>
+<br>
Class: 객체를 만들기 위한 설계도<br>
Objcet: 클래스로 구현한 대상<br>
Instance : 메모리에 할당된 데이터<br>
(인스턴스 던전(인던)을 생각하자. 플레이어가 던전에 들어올 때 인스턴스에 할당된 데이터인 던전이 출력된다.)
<br><br><br>

## 클래스의 구성요소와 기본문법
```java
class 클래스명 {

}
```
<br>

### 클래스의 구성요소
- 필드 : 클래스의 속성을 나타내는 변수.  Ex) 차의 경우. 바퀴 수, 색깔, 에어컨 유무 등등

- 메서드 : 클래스의 기능(행위)을 나타내는 함수. Ex) 가속하기, 정차하기 등등

- 생성자 : 클래스의 객체를 생성하는 역할.

- 이너 클래스 : 클래스 내부의 클래스를 의미.

(필드, 메서드, 이너 클래스를 클래스 멤버라 부름)
<br><br><br>

## 클래스와 객체, 코드 예시

```java
public class Basic_OOP_Practice {
    public static void main(String[] args) {
        Car car = new Car("BMW 740i", "검은색");  // 객체 생성
        // <Car> 클래스 타입의 참조 변수를 선언하고,
        // <new> 키워드를 통해 객체 생성(인스턴스 생성 후, 객체의 주소를 참조 변수에 저장.

        System.out.println("제 차는 " + car.model + "이고, 색깔은 " + car.color + "입니다."); // 필드
        car.power();       // 메서드 호출
        car.accelerate();  // 메서드 호출
        car.stop();        // 메서드 호출
        car.mileage(3.3);
        // < . >(포인트 연산자)는 해당 위치에 있는 객체 안으로 가서 필드/메서드로 접근하라는 연산자.
        // Ex) car.power(); -> car 객체 안에 있는 power 메서드로 접근해라.
    }
}


    class Car {
        public String model;   // 필드 선언
        public String color;   // 필드 선언

            public  Car(){} // 기본생성자. 생성자가 없는 경우 자동 생성(오버로딩과 기본생성자 예시를 위해 사용했지만, 현재 코드에서는 사용하지 않아도 된다. -> 밑에 생성자가 있기 때문에)

        // 생성자 오버로딩
        public Car(String model, String color) { // 매개변수가 있는 생성자
                this.model = model;
                this.color = color;
        }

        void power() {
            System.out.println("시동을 걸었습니다.");  // 메서드 선언
        }
        void accelerate () {
            System.out.println("가속");       // 메서드 선언
        }
        void stop() {
            System.out.println("정지");           // 메서드 선언
        }
        // 메서드 오버로딩
        public void mileage(double d) {
            System.out.println("주행거리는 " + d + "km/h 입니다.");
        }
    }
```


![출력된 값]()
<br><br><br>

### 추가 설명
- [생성자]()
- [오버로딩]()
- [this()와 this 키워드]()