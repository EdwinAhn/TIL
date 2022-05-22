**null을 간접적으로 다루기 위한 방법이 Optional**<br><br><br>
 

null을 직접 다루는 것은 위험하다. -> NullPointerException이 발생할 수 있음.<br><br><br>

 

때문에 null을 체크해주어야 하는데 원래라면 if문이 필수로 들어가야되게 된다.(null 체크) -> 코드가 지저분해진다.<br><br><br><br>

 

 

이러한 문제를 해결하기 위해 나온 것이 Optional<T>.<br><br>

result null 일때,<br><br>

null을 Optional 객체에 넣어준다.(Optional 객체는 객체이니, 주소가 존재한다.) -> Optional의 value가 null이 됨.<br><br>

때문에 result의 값은 null이 아닌 Optional 객체의 주소가 된다.<br><br><br><br>

 

덕분에<br>

1. NullPointerException이 발생하지 않으며<br><br>

2. null 체크가 필요 없어진다.<br><br>

 
```java
Optional<String> opt = Optional.empty();
```
  <br><br><br>

### Optional<T> 객체 생성하는 방법
```java
String str = "abc";
Optional<String> optVal = Optional.of(str);

Optional<String> optVal = Optional.of("abc");

// Optional<String> optVal = Optional.of(null); // NullPointerException발생

Optional<String> optVal = Optional.ofNullable(str);  // OK
```
앞으로 null이 될 수 있는 값은 그냥 쓰지 말고 Optional<T>객체를 사용하자.
<br><br><br><br>
 

### Optional<T> 객체의 값 가져오기
- get(), orElse(), orElseGet(), orElseThrow()
  
```java
Optional<String> optVal = Optional. of("abc");
String str1 = optVal.get();      // optVal에 저장된 값을 반환. null이면 예외발생
String str2 = optVal.orElse("") // 많이쓰임.  // null일 때 반환값. optVal에 저장된 값이 null일 때는, ""를 반환
String str3 = optVal.orElseGet(String::new); //많이 쓰임  // 람다식 사용가능. () -> new String()
String str4 = optVal.orElseThrow(NullPointerException::new); // nell이면 예외발생.
```

 <br><br><br>

- isPresent()
  -Optional객체의 값이 null이면 false, 아니면 true를 반환
  
```java
if (Optional.ofNullable(str).isPresent()) {   // if(str!=null)
	Ststem.out.println(str);
    }
```

 <br><br><br>

- ifPresent
  -(Consumer) null이 아닐때만 작업 수행, null이면 아무 일도 안 함.
  
```java
Optional.ofNullable(str).ifPresent(System.out::println);
```

 <br><br><br><br>

- OptionalInt, OptionalLong, OptionalDouble
기본형 값을 감싸는 Wrapper Class -> 더 높은 성능을 내기 위해서 쓴다.
```java
public final class OptionalInt {
	...
	private final boolean isPresent; //값이 저장되어 있으면 true.
    	// OptionalInt opt = OptionalInt.of(0);과
   	 	// OptionalInt opt2 = OptionalInt.empty(); 일 때 기본값이 0으로 초기화 될텐데 이 두 코드를 어떻게 구분할 수 있을까?
        // ✓ isPresent를 써서 boolean 타입으로 true, false을 통해 구별한다.
        // 	System.out.println(opt.isPresent()); ☞ true
        // 	System.out.println(opt2.isPresent()); ☞ false
    	
  	private final int value; // int타입의 변수
```
  <br><br><br>

|Optional클래스|타입|값을 반환하는 메서드|
|------------|---|-------------|
|Optional<T> |	T |                 get()|
|OptionalInt|	int |                  getAsint()|
|OptionalLong|	long |               getAsLong()|
|OptionalDouble|	double |          getAsDouble()|

  
  <br><br><br><br>

출처: [남궁성의 정석코딩, 자바의 정석-기초편]

https://youtu.be/W_kPjiTF9RI
