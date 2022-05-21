## 스트림
다양한 데이터 소스(컬렉션, 배열 등등)를 표준화된 방법으로 다루기 위한 것.<br>
⭐︎데이터의 연속적인 흐름.<br><br>

이전에 표준화된 방법을 쓰기 위해 컬렉션 프레임워크를 만들었는데 이것은 반쪽짜리 표준화된 방법.(List, Set, Map의 사용 방법이 달랐다.)<br><br>

그런데 JDK 1.8부터 진짜 표준화 된 방법이 나옴. -> 스트림<br><br><br>


컬렉션프레임워크, 배열 등 데이터 소스로부터 스트림을 만들 수 있다.<br><br>

데이터 소스 -> 스트림 -> 중간연산(n번) -> 최종 연산(1번) -> 결과<br><br>

1. 스트림 만들기
2. 중간연산(0~n번)
3. 최종연산 (0~1번) => 결과
<br><br><br>

스트림은 데이터 소스로부터 데이터를 읽기만할 뿐 변경하지 않는다.(원본을 가지고 작업만 할뿐)<br><br>

스트림은 Iterator(컬렉션의 모든 요소를 읽을 때 사용하는 것)처럼 일회용이다. (필요하면 다시 스트림을 생성해야 함)<br>
-> 최종연산을 하고 나면 스트림이 닫힘.<br><br>

스트림은 최종 연산 전까지 중간연산이 수행되지 않는다. -> 지연된 연산.<br>
-> 말이 안되는 코드도 최종연산을 하기 전까지는 써진다.<br><br>

스트림은 작업을 내부 반복으로 처리한다. ->코드가 간결해진다.<br><br>

스트림의 작업을 병렬로 처리 -> 병렬스트림 parallel()메서드 사용.<br><br>

기본형 스트림 -> **IntStream, LongStream, DoubleStream**<br>
	- 오토박싱&언박싱의 비효율이 제거됨(Stream<integer> 대신 IntStream 사용) -> 성능이 좋아짐<br>
	- 숫자와 관련된 유용한 메서드를 Stream<T>보다 더 많이 제공.<br><br><br>

  
 ### 스트림 만들기 - 컬렉션
Collection 인터페이스(List와 Set이 들어있음)의 stream() 메서드로 컬렉션을 스트림으로 변환
  
  ```java
  import java.util.Arrays;
import java.util.List;
import java.util.stream.Stream;

public class StreamEX {
    public static void main(String[] args) {
        List<Integer> list = Arrays.asList(1,2,3,4,5);
        Stream<Integer> intStream = list.stream(); // list를 Stream으로 변환
        intStream.forEach(System.out::print); // forEach() 최종연산

        // Stream은 1회용. Stream에 대해 최종연산을 수행하면 Stream이 닫힌다.
        intStream = list.stream();  // list로부터 stream 생성
        intStream.forEach(System.out::print);
    }
}
  ```


