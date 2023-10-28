![](https://velog.velcdn.com/images/phwon7/post/c75e386c-ca9d-4c64-b49b-2660f31d303d/image.png)


그동안 안드로이드 개발을 해오면서..아무생각없이 마구 쓰긴 했지만(특히 나는 Java가 아닌 Kotlin으로 개발을 시작했기 때문에 무작정(?) 써오긴 했지만ㅎㅎ)기초가 부족하다는 생각을 항상 해왔다..

> 작은 기능 하나를 만들더라도 A-Z까지 명확하게 아는 상태에서 만들고 싶어!!

라는 나의..소망을 이루기 위해서..ㅎㅎ 그리고 우테코 6기를 지원하고 프리코스를 진행하면서 인강과 교재를 통해 Kotlin과 Android에 대해서 기초부터 심화까지 정리해보려고 한다. 

<br>

### Kotlin 이란?

Kotlin은 2011년 인텔리제이 IDE를 개발하던 JetBrains에서 JVM기반으로 만든 언어이다. 언어의 이름인 Kotlin은 러시아의 섬 이름에서 따왔다고 한다.

Kotlin은 스크립트 언어처럼 간결한 문법을 제공하면서 Java와의 호환성이 매우 뛰어나 실용적인 언어이다. 사용자가 점점 늘어나면서 구글이 2017년에 안드로이드 개발 공식 언어로 정하면서 인기가 더욱 높아졌다.

#### 안드로이드 개발에 있어서 Kotlin은 이제 Java의 다음 세대로 완전히 자리매김했다!!

<br>

#### Kotlin 언어의 주요 특징 -> 실용성, 상호운용성, 안정성

* 실용성: 언어의 복잡도가 자바에 비해 줄어들었다, 도구를 강조한다
* 상호운용성: 자바 라이브러리와 완벽하게 호환된다.
* 안정성: 언어 구조가 개발자가 실수할 가능성을 원천적으로 방지해 오류의 가능성을 줄여준다.


<br>


### Kotlin 함수

```kotlin
fun FunctionName ( argument ) : Unit(생략가능) {
	content
}
```




이것이 kotlin 함수의 기본형이다. 여기서 Unit은 Java의 void와 같은 역할을 하며 Redundant하므로 생략이 가능하다. **(Unit이 아닌 Type을 이용한다면 내부에 return이 필요하다)** Kotlin 함수는 반환값이 존재하는 경우에만 반환 타입을 명시하면 된다.

* Unit: wrapper class로 Singleton으로 생성되며 내부는 toString 메소드로만 구현되어있다.
** *wrapper class란 기본형(primitive type)변수를 감싸는 클래스로 Integer, Character등이 있다.*

```kotlin
fun Test(a: Int, b: String) : Int { }
```

위 예시처럼 Argument는 Int a, Int b 형식이 아닌 a: Int, b: Int 처럼 **변수가 먼저, 타입이 뒤에** 오는 형식으로 사용된다.

```kotlin
fun Test(a: Int, b: Int = 3) : Int { 
	println(a+b)
    return a+b
}
```

변수 b가 선언된 방식처럼 default 값을 함수 argument 내에서 지정해 이용할 수 있다. (Overloading을 이용하지 않아도 되어 비교적 간편하다.)


#### Trailing Comma(,)
: Kotlin의 장점 중 하나로, 마지막 parameter에 콤마(,)추가를 허용해주어 code generation이 간편해진다. 아래는 예시이다.

```kotlin
data class PersonWithTrailingComma(
    val name: String,
    val age: Int,
    val gender:String,
    val natinality: String,
    val address: String,
    val dateOfBirth: LocalDate,
)
```

이처럼 data class에서 마지막 val을 선언할 때 trailing comma를 붙여줌으로써 추가적인 변수를 선언할때 더 손쉽게 사용할 수 있고, 속성을 추가/삭제할 때 diff가 한줄이 돼서 히스토리를 좀 더 깔끔하게 관리할 수 있다는 장점이 있다.

<br>

### Kotlin 변수

Kotlin에서 변수는 다른 언어와 비슷하게 값을 저장하고, 이를 참조할 수 있다. 그러나 다른 점은 **Kotlin에서는 타입을 지정하지 않고도 변수를 선언할 수 있다.**

1. 타입을 지정한 경우 그대로 초기화까지 이어서 진행하면 된다
2. 타입을 생략한 경우, 초기화를 하면서 **초기화 값으로 타입 추론이 가능하다.**

```Kotlin
val testInt: Int = 10 // 1번의 경우
val test = 10 // 2번의 경우, test의 타입을 Int로 추론이 가능하다. 
```

그리고 또 하나의 중요한 특징으로 Kotlin에서는 변수를 **immutable(불변)**, **mutable(가변)**로 구분한다. 

- val: val은 value로 대표적인 immutable한 변수 타입이다. (읽기 전용)
- var: var은 variable로 mutable한 변수 타입 이다. (읽기 쓰기 모두 허용)

```kotlin
//1. val
val name = "이름"
name = "이름 변경" // val로 선언되어있기때문에 재할당이 불가능
//2. var
var age = 25
age = 24 // var 변수이므로 값 할당이 가능하다.
```

<br>

### Kotlin의 타입

Kotlin의 타입에는 아래와 같은 종류들이 있다. 

|표현형|종류|
|--|--|
|정수 표현형|Byte, Short, Int(default), Long|
|floating point 표현형|Float, Double(default)|
|Unsigned integers| UByte, UShort, UInt, ULong|
|true/false 표현형|Boolean|
|문자 표현형|char|
|문자열 표현형|String|


#### String template
: Kotlin에서는 문자열 템플릿(String Template)이라는 식(Expression)을 통해 Java보다 간편하게 원하는 문자열을 생성할 수 있습니다.
```kotlin
fun main() {
    val testInt = 30
    val testString = "안녕하세요"
    println(testString + "Java 예시입니다." + testInt)
    println("$testString Kotlin 예시입니다. $testInt")
 }
```

```kotlin
fun main() {
    val testInt = 30
    val testString = "안녕하세요"
    println("$testString 크기는 $testInt입니다.") // 에러발생
    println("${testString} 크기는 ${testInt}입니다")
}
```

위와 같이 String Template의 표현식은 $로 시작한다. "" 안에서 이 기호로 시작하는 식이나 변수는 자동으로 문자열로 출력되는데 여기서 주의해야 할 점은 $뒤에 바로 문자열이나 문자를 입력하는 경우 점(.)이나 쉼표(,) 같은 기호나 공백이 나오기 전 까지는 변수 이름으로 인식한다는 점이다. 

바로 예시에서 에러 발생이라는 주석이 달린 경우가 그렇다. 그렇기때문에 $ 뒤를 {}로 감싸는 ${expression}의 형태로 표기해주는 것이 좋다.

${} 안에는 expression(식)이 들어가므로 연산의 수행 결과 및 함수 호출까지 가능하다는 장점이 있다.

<br>

### When 조건문

<br>

### Statement와 expression의 차이


<br>

### Collection


<br>


### List, Map, Set

<br>

### Typecheck

<br>

### Casting

<br>

### NullPointException과 Kotlin의 NullSafe

<br>

#### 참조
- 자바 알고리즘 인터뷰 with 코틀린 - 박상길
- https://torbjorn.tistory.com/744
- https://manorgass.tistory.com/73

