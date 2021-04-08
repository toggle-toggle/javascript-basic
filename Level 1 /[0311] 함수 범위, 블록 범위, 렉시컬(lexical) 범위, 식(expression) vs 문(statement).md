# 함수 범위, 블록 범위, 렉시컬(Lexical) 범위

### 범위(Scope)란?

- 프로그래밍 언어에서 변수의 접근 가능과 생존 기간
- 전역 범위(**Global Scope**)와 지역 범위(**Local Scope**)
  - 전역 범위 - 코드 전체에서 참조 가능
  - 지역 범위 - 정해진 코드 부분에서만 참조 가능



### 자바스크립트에서의 특징

- 변수의 범위는 **함수 단위**
- 스크립트 실행시 **함수 범위의 변수 선언**은 **호이스팅**이 이루어짐
- 스크립트 실행시 **변수 관리**는 **렉시컬 영역**을 기준으로 함



### 함수 범위 (Function Scope)

- **함수 내부**에서 **변수를 선언**한 경우

- **함수 내부**에서 **선언된 변수**는 **함수 내부**에서만 **접근**이 **가능**

  ```javascript
  var variable = 1
  
  function functionScopeTest() {
  	if (true) {
  		var inCondition = 2
  	}
  
  	console.log(inCondition)
  }
  
  functionScopeTest()
  ```

- 변수 `inCondition`의 범위는 함수 단위



### 블록 범위 (Block Scope)

- 자바스크립트는 기본적으로 함수를 범위로 함

- `let` 과 `const` 키워드를 사용할 경우, **블록 범위**를 가짐

  ```javascript
  function usingVarKeyword() {
  	for(var i = 0; i < 3; i++) {}
  	console.log(i)
  }
  
  function usingLetKeyword() {
  	for(let i = 0; i < 3; i++) {}
  	console.log(i)
  }
  
  usingVarKeyword() // 3
  usingLetKeyword() // error
  ```

  

### 렉시컬 범위(Lexical Scope)

- **스코프**는 **함수**를 호출할 때가 아니라 **선언(정의)할 때** 생김

  - 렉시컬 스코프 또는 정적 스코프
  - 함수를 어디서 정의했는지에 따라 함수의 상위 스코프 결정
  - 함수가 호출된 위치는 상위 스코프 결정에 영향을 주지 않음

  ```javascript
  var x = 1;
  
  function foo() {
  	var x = 10;
  	bar();
  }
  
  function bar() {
  	console.log(x);
  }
  
  foo();
  bar();
  ```

  

### 호이스팅(Hoisting)

- 끌어올리기, 들어 올려 나르기

- 함수 호이스팅

  - 런타임 이전에 함수 객체가 먼저 생성되고, 자바스크립트 엔진은 함수 이름과 동일한 이름의 식별자를 암묵적으로 생성하며 생성된 함수 객체에 할당

  ```javascript
  hoistingTest()
  
  function hoistingTest() {
  	var x = 1
  	console.log(x)
  }
  ```

- 변수 호이스팅

  - 자바스크립트 엔진에 의해 먼저 실행되어 식별자를 생성하지만, 선언된 변수를 undefiend로 초기화

  ```javascript
  function hoistingTest() {
  	console.log(x)
  
  	var x = 1
  	console.log(x)
  }
  
  hoistingTest()
  ```

![image](https://user-images.githubusercontent.com/40762111/111163550-89713b80-85e0-11eb-8952-567e459fa787.png)


![image](https://user-images.githubusercontent.com/40762111/111163654-a148bf80-85e0-11eb-8fba-b719f9157993.png)




# 식(expression) vs 문(statement)

### 함수 선언식

- ```javascript
  function add(x, y) {
    return x + y;
  }
  ```

- 호이스팅에 영향 받음

### 함수 표현식

- ```javascript
  var add = function(x, y) {
  	return x + y;
  }
  ```

- 호이스팅에 영향을 받지 않음



---

참조

- https://alstn2468.github.io/Javascript/2020-05-13-FunctionScope_BlockScope_and_LexicalScope/

- 모던 자바스크립트 Deep Dive

- https://joshua1988.github.io/web-development/javascript/function-expressions-vs-declarations/

