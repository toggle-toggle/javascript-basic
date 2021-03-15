## 데이터 타입 변환 2가지

### 1. 명시적 변환
값의 타입은 개발자의 의도에 따라 다른 타입으로 변환할 수 있다. 개발자가 의도적으로 값의 타입을 변환하는 것을 명시적 타입 변환 또는 타입 캐스팅이라 한다.
```javascript
var x = 10;
var str = x.toString();
console.log(typeof str, str); // string 10
  
// 그렇다고 변수 x의 값이 변경된 것은 아니다.
console.log(typreof x, x); // number 10
```
또한 String(), Number(), Boolean()과 같은 생성자 함수를 new 연산자 없이 호출하는 방법도 있다.
```javascript
String(123) // -> "123"
Number("123") // -> 123
```
### 2. 암묵적 변환
자바스크립트 엔진에 의해 암묵적으로 타입이 자동 변환되기도 한다. 이를 **암묵적 타입 변환** 또는 **타입 강제 변환**이라 한다.
```javascript
var str = x + '';
console.log(typrof str, str) // string 10
```
암묵적 타입 변환은 기존 변수 값을 재할당하여 변경하는 것이 아니다. 자바스크립트 엔진은 표현식을 에러 없이 평가하기 위해 피연산자의 값을 암묵적으로 타입 변환해 새로운 타입의 값을 만들어 단 한 번 사용하고 버린다.

#### 2.1 문자열 타입으로 변환
```javascript
1 + "2" // -> "12"
```
- +연산자는 피연산자 중 하나라도 문자열이면 문자열 연결 연산자로 동작한다.

#### 2.2 숫자 타입으로 변환
```javascript
1 - "1" // -> 0
1 * "20" // -> 20
1 / "one" //-> NaN
"1" > 0 // -> true
```
- 자바스크립트 엔진은 산술 연산자,  비교 연산자 표현식을 평가하기 위해 피연산자들을 검사하고, 이 중 숫자 타입이 아닌 피연산자들은 숫자 타입으로 암묵적 변환한다.
- 숫자 타입으로 암묵적  변환이 불가능한 경우는, 연산이 불가하므로 NaN을 반환한다.

#### 2.3 불리언 타입으로 변환
```javascript
if (' ')       console.log("true") // -> "true"
if ('string')  console.log("true") // -> "true"
if (null)      console.log("true") // -> (아무것도 찍히지 않음)
```
- if문이나 for문 같은 논리적 참/거짓으로 평가되어야 하는 표현식의 경우에는, 조건식의 평가 결과를 불리언 타입으로 암묵적 변환한다.
- 자바스크립트 엔진은 불리언 타입이 아닌 값을 Truthy 값(참으로 평가되는 값) 또는 Falsy 값(거짓으로 평가되는 값)으로 구분한다.


## 타입 종류 시스템 3가지

### 1. Nominal Typing
특정 키워드를 통해 타입을 지정하는 방식으로, 서로 호환 가능 하다고 명시적으로 표현된 타입 값의 할당만을 허용한다. 정적언어인 C#, C++, Java가 nominal typing방식으로 타입 체킹이 이루어진다.
```java
int num = 100;
char str = "abc";

num = str // -> ERROR
```

### 2. Structural Typing
nominal typing과 반대인 개념으로, 멤버에 따라 타입을  검사하는 방법이다. 비교하는 두 데이터의 타입 구조를 비교하여 호환되는지 검사한다. 한 타입이 다른 타입이 갖는ㄴ 멤벌르 모두 가지고 있다면 두 타입은 호환 가능하다. Typescript, Go가 구조적 타이핑을 기반으로 타입 시스템을 갖는다.
```typescript
interface Named {
    name: string;
}

class Person {
    name: string;
}

let p: Named;
// 성공, 구조적 타이핑이기 때문입니다.
p = new Person();
```
### 3. Duck Typing
동적 타이핑의 한 종류로, 변수 및 메소드의 집합이 객체의 타입을 결정하는 것을 말한다. 파이썬과 루비에서 사용된다.
```python
class Duck:
    def __init__(self):
        self.name = "오리"

    def sound(self):
        print("꽥꽥!")

    def walk(self):
        print(f"{self.name}가 걷는다.")

class Dog:
    def __init__(self):
        self.name = "개"

    def sound(self):
        print("왈왈!")

    def walk(self):
        print(f"{self.name}가 걷는다.")
```
`Duck`클래스와 `Dog`클래스 모두 `sound`, `walk` 메서드를 갖는다. 즉, 두 클래스는 서로 다른 클래스이지만 같은 메서드와 필드를 갖는다. 따라서, 아래와 같은 코드가 에러없이 동작한다.
```python
def make_sound(duck):
    duck.sound()

def take_walk(dog):
    dog.walk()

duck = Duck()
dog = Dog()

make_sound(duck) # 꽥꽥!
make_sound(dog) # 왈왈!

take_walk(duck) # 오리가 걷는다.
take_walk(dog) # 개가 걷는다.
```
## 단축 평가
  ```javascript
  'Cat' && 'Dog' // -> "Dog"
  ```
- 논리곱 연산다는 두 개의 피연산자가 모두 true로 평가될 때 true를 반환한다. 또한, 논리곱 연산자는 좌항에서 우항으로 평가가 진행된다.
- 논리곱 연산자는 논리 연산의 결과를 결정하는 두 번째 피연산자, 즉 문자열 'Dog'를 그대로 반환한다.

  ```javascript
  'Cat' || 'Dog' // -> 'Cat'
  ```
- 논리합 연산자는 두 개의 피연산자중 하나만 true로 평가되어도 true를 반환한다.
- 첫 번째 피연산자 'Cat'은 Truthy의 값이므로 true로 평가횐다. 이 시점에서는 두 번째 피연산자까지 평가를 진행하지 않아도 되므로 논리 연산의 결과를 결정한 첫 번째 피연산자 'Cat'을 그대로 반환한다.
- 논리 연산의 결과를 결정하는 피연산자를 타입 변환하지 않고 그대로 반환하는 것을 `단축 평가`라고 한다. 단축 평가는 표현식을 평가하는 도중에 평가 결과가 확정된 셩우 나머지 평가 과정을 생략하는 것을 말한다.
  ```javascript
  // 논리합(||) 연산자
  'Cat' || 'Dog' // -> "Cat"
  false || 'Dog' // -> "Dog"
  'Cat' || false // -> "Cat"
  
  // 논리곱(&&) 연산자
  'Cat' && 'Dog' // -> "Dog"
  false && 'Dog' // -> false
  'Cat' && false // -> false
  ```

### 출처
https://alstn2468.github.io/Javascript/2020-05-11-Implicit_Explict_Nominal_Structuring_DuckTyping/

https://corock.tistory.com/459

https://typescript-kr.github.io/pages/type-compatibility.html

모던 자바스크립트Deep Dive
