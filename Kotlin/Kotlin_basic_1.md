#### 코틀린 언어의 주요 특징: 실용성, 상호운용성, 안정성

* 실용성: 언어의 복잡도가 자바에 비해 줄어들었다, 도구를 강조한다
* 상호운용성: 자바 라이브러리와 완벽하게 호환된다.
* 안정성: 언어 구조가 개발자가 실수할 가능성을 원천적으로 방지해 오류의 가능성을 줄여준다.

#### Kotlin 함수
```
fun FunctionName ( argument ) : Unit(생략가능) {
	content
}
```

이것이 kotlin 함수의 기본형이다. 여기서 Unit은 Java의 void와 같은 역할을 하며 Redundant하므로 생략이 가능하다. 
**(Unit이 아닌 Type을 이용한다면 내부에 return이 필요함!!)**

```
fun Test(a: Int, b: String) : Int { }
```

위 예시처럼 Argument는 Int a, Int b 형식이 아닌 a: Int, b: Int 처럼 변수가 먼저, 타입이 뒤에 오는 형식으로 사용된다.

```
fun Test(a: Int, b: Int = 3) : Int { 
	println(a+b)
    return a+b
}
```

변수 b가 선언된 방식처럼 default 값을 함수 argument 내에서 지정해 이용할 수 있다. (Overloading을 이용하지 않아도 됨!!)
