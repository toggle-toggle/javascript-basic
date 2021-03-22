# IIFE(Immediately Invoked Function Expression)

들어가기 전에..
## 함수 선언식과 표현식 (맛보기)

즉시 실행 함수 표현에 대해 알아보려면 먼저 함수 선언식과 표현식에 대해 알아야한다.
아래와 같이 쓰는 것을 **함수 선언식**이라고 한다. 함수 선언식은 호이스팅에 영향을 받는다.

```javascript
function 함수이름() {
  ...statements
}
```

아래와 같이 표현한 것을 **함수 표현식**이라고 한다. 함수 표현식은 호이스팅에 영향을 받지 않는다.
```javascript
const 함수이름 = function() {
  ...statements
}
```
## 그럼.. IIFE란?
말 그대로 정의되자마자 **즉시 실행되는 함수**
이러한 즉시 실행 함수는 global Scope 를 오염시키지 않기 위해 사용
다양한 라이브러리들이 IIFE 패턴을 사용해 충돌을 방지하고 있다.

IIFE는 아래와 같이 작성할 수 있다. (1,2번이 자주 사용되고, 나머지는 그냥 알고만 있으면 된다.)
연산자를 사용한 방식은 return값이 있을 때 예상치 못한 결과가 나타날 수 있기 때문에 1,2방식이 더 널리 활용된다.

```javascript
// 1.
(function() {
  ...statements
})();

// 2. 
(function () {
  ...statements
}());

// 3.
!function() {
  ...statements
})();

// 4.
+function() {
  ...statements
})();

// 5.
void function() {
  ...statements
})();
```

Javascript는 **function **이라는 키워드를 볼 때마다, 함수의 정의가 일어날 것이라고 예측 
하지만 앞에 `+`, `-`, `~`, `!` 등과 같은 1진 연산자들이 있으면 함수가 아닌 표현식으로 다룸
마지막 `void`는 함수를 식으로 다루어지게 강제하는 내용

IIFE는 결국 `식`의 한 종류이기 때문에, 앞서 말했던 호이스팅이 발생하지 않는다. 아래와 같이 예시를 들 수 있다.

```javascript
// 함수 선언식
boo(); // 실행된다.
function boo() {
	alert('booo!')
}

// 함수 표현식 
hoo(); // 실행되지 않는다.
var hoo = function () {
	alert('hooo!')
}

// 즉시 호출 함수 
(function mooyaho() {})();
alert(mooyaho()) // mooyaho not defined
```

### 즉시 실행 함수 표현의 장점
- 전역 스코프에 불필요한 변수를 추가해서 오염시키는 것을 방지할 수 있다.
- IIFE 내부 안으로 다른 변수들이 접근하는 것을 막을 수 있다. 
- 값을 리턴해 **변수에 할당**할 수 있다.
- 호출될 때, **인자**를 받을 수 있다.

예시 1)
- `init()`함수는 그 함수 바깥의 변수에 접근이 가능하지만, 바깥에서는 `init` 안으로 접근하지 못한다는 것을 알 수 있다.
  ```javascript
  (function example() {
    // 즉시실행함수 밖에서는 사용할 수 없는 변수들
    const a;
    const b;
    init();
    
    // 즉시실행함수 밖에서는 사용할 수 없는 함수
    function init() {
      a=1;
      b=2;
    }
  }());
  ```
예시 2)
- 즉시실행함수를 통해 반환된 'result입니다.'라는 string이 result 변수에 할당되는 것을 알 수 있다.
  ```javascript
  const result = (function() {
    return 'result입니다.';
  }());

  alert(result) // 'result입니다.' 출력
  ```
예시 3)
- IIFE는 호출시 인자를 전달할 수 있다.
  ```javascript
  (function(count) {
      for(let i=0; i<count; i++)
          console.log("I am IIFE");
  })(3);
  ```


### IIFE 사용 예제 
```javascript
// 예제 1.
const message = (function() {
    const secret = "I m scret!";
    return `The secret is ${secret.length} characters long.`
})();
console.log(message); //The secret is 10 characters long.

// 예제 2.
// 호출된 함수를 가지고 있는 변수 f
const f = (function() {
    let count = 0;
    return function() {
        return `i have been called ${++count} time(s).`
    }
})();

f(); // "i have been called 1 time(s)."
f(); // "i have been called 2 time(s)."
```

1의 예시에서 secret은 외부에서 접근할 수 없기 때문에 안전하게 보호된다.
2의 예시에서는 함수를 호출할 때마다 새로 연산되어 값이 리턴되는 것을 알 수 있다.

--- 
# 모듈이란?

개발하는 웹의 크기가 커지면 언젠가 파일을 여러개로 분리해야하는데, 이때 분리된 파일 각각을 "Module"이라고 부름
모듈에 export, import를 적용하면 다른 모듈을 불러와 함수를 호출할 수 있게 해준다.

```javascript
// hi.js
export function sayHi(user) {
  alert(`hello, ${user}!`)
}
```

```javascript
// main.js
import { sayHi } from "./hi.js"

alert(sayHi('John')) //alert가 뜸
```

### 모듈의 사용
- `<script type="module">` 속성을 설정해 해당 스크립트가 모듈이라는 것을 브라우저가 알 수 있게 해줘야 함 
- 위와 같이 설정하면 local에서는 사용하기 힘들고, live-server등을 사용해 서버를 켜야한다.

### 모듈의 Scope
- 모듈은 자신만의 scope가 있음 
- 그렇기 때문에 모듈에서 정의한 내부의 변수, 함수는다른 스크립트에서 접근할 수 없음
- 만약 모듈에서 외부로 공개하려면 `export`를 사용해 내보내야함 
- 모듈들을 다른 곳에서 가져와 사용하려면 import를 통해 가져와야함

### 모듈은 단 한번만 평가됨
- 동일한 모듈이 여러 곳에서 사용되더라도 모듈은 처음 호출시 한번만 실행됨 
- import를 몇번씩 해도 최초 import만 발생함

### 모듈은 단 한번만 실행되고, 실행된 모듈은 필요한 곳에 공유된다.
- 예시
  ```javascript
  // admin.js
  export let admin = {
    name: "John"
  };
  ```

  ```javascript
  // 1.js
  import {admin} from './admin.js';
  admin.name = "Pete";
  ```

  ```javascript
  // 2.js
  import {admin} from './admin.js';
  alert(admin.name); // Pete
  ```
1.js에서 변경한 내용을 2.js에서도 확인할 수 있다는 것을 알 수 있다!

### 최상위 레벨의 this는 undefined
- 모듈이 아닌 스크립트의 this는 전역 객체인데, 모듈은 undefined임

  ```javascript
  <script>
    alert(this); // window
  </script>

  <script type="module">
    alert(this); // undefined
  </script>
  ```

## type="module"와 일반 스크립트의 다른 점

### 항상 지연 실행된다.
- 모듈 스크립트는 HTML 문서가 완전히 준비될 때까지 대기 상태에 있다가 HTML이 다 만들어진 후에 실행됨
- 그래서 모듈 스크립트는 항상 완전한 HTML 페이지를 볼 수 있고, 문서 내 요소에도 접근할 수 있음
- 모듈은 HTML이 모두 로딩된 후에 실행되기 때문에, 모듈 스크립트를 불러오는 동안 Loading Indicator이나 투명 오버레이 등을 넣어주어 사용자의 혼란을 예방해주는게 좋음

### 인라인 스크립트의 비동기 처리
- 일반 스크립트에서 async 속성은 외부 스크립트를 불러올 때에만 유효한데, 모듈에서는 인라인 스크립트에도 적용할 수 있음
- 광고나 카운터 등과 같이 어디에도 종속되지 않는 기능을 구현할 때에 사용할 수 있음

  ```javascript
  <!-- 필요한 모듈(analytics.js)의 로드가 끝나면 -->
  <!-- 문서나 다른 <script>가 로드되길 기다리지 않고 바로 실행됩니다.-->
  <script async type="module">
    import {counter} from './analytics.js';

    counter.count();
  </script>
  ```

### 구식 브라우저 대응
- 구식 브라우저는 type="module"을 해석하지 못해서 만약 저게 붙어있으면 무시하고 넘어감 
- 해결 : `nomodule`을 붙여주면 대신 그걸 실행

  ```javascript
  <script type="module">
    alert("모던 브라우저를 사용하고 계시군요.");
  </script>

  <script nomodule>
    alert("type=module을 해석할 수 있는 브라우저는 nomodule 타입의 스크립트는 넘어갑니다. 따라서 이 alert 문은 실행되지 않습니다.")
    alert("오래된 브라우저를 사용하고 있다면, type=module이 붙은 스크립트는 무시합니다. 대신 이 alert 문이 실행됩니다.");
  </script>
  ```
---
# 네임스페이스 
## 네임스페이스 패턴이란? 

어플리케이션이나 라이브러리를 위해 전역 유효 범위에 많은 변수, 함수, 객체 등으로 어지럽히지 않도록 하기 위해 전역 객체를 하나만 만들고, 모든 기능을 이 객체에 추가하는 패턴
스크립트가 실행되는 환경을 항상 일정하게 만들어 관리하기 쉽게 만드는 일을 함
단순히 기능을 한데 묶기 위해 사용하는 객체를 네임스페이스라고 함

### 안티 패턴
```javascript
// 생성자 함수 2개
function a() {}
function b() {}

// 변수 1개
var variable = 0;

// 객체 1개
var module_object = {};
```
### 좋은 패턴
```javascript
var APP = {};

// 생성자
APP.a = function() {};
APP.b = function() {};

// 변수
APP.variable = 0;

// 객체
APP.module_object = {};
```

### 네임스페이스의 장점
- 계층적 의미에 맞춰서 기능들을 그룹화할 수 있음
- 해당 기능을 어디에서 호출하는지 혼란스럽지 않아 유지보수에 용이
- 전역 변수를 줄일 수 있음


프로그램이 복잡해지면서 코드의 각 부분들이 파일로 분리되어 문서에 포함되는 경우가 많은데, 그러다보면 이미 있는걸 덮어쓰는 경우가 있으니 아래 예시의 1번처럼 객체를 바로 선언하는게 아니라 2번처럼 MYAPP이 이미 선언되었는지 확인하고 정의해주어야 함(3번과 2번은 같음)  

```javascript
// 1번
var MYAPP = {};

// 2번
if (typeof MYAPP === "undefined") {
    var MYAPP = {};
}

// 3번
var MYAPP = MYAPP || {};
```
하지만 이런 코드의 문제는 Namespace의 깊이가 깊어질수록 단계별로 계속 확인해주어야 한다는 것
그래서 이렇게 이러한 작업을 맡을 함수를 미리 선언하고 전역 객체가 존재하는지 확인하고 만들어줄 수 있음

```javascript
var MYAPP = MYAPP || {}; // MYAPP이 이미 선언되었는지 확인 후 객체생성
MYAPP.nsFunc = function (ns_string) {
    // '.'으로 구분된 네임스페이스 표기를 쪼갬
    var sections = ns_string.split('.'),
        parent = MYAPP,
        i;

    // 최상단의 MYAPP객체는 이미 선언되었으므로 제거
    if (sections[0] === "MYAPP") {
        sections = sections.slice(1);
    }

    var s_length = sections.length;
    for (i=0; i<s_length; i+=1) {
        // 프로퍼티가 존재하지 않아야만 생성
        if (typeof parent[sections[i]] === "undefined") {
            parent[sections[i]] = {};
        }
        parent = parent[sections[i]];
    }
    return parent;
};
```

사용은 아래와 같이 하면 됨
```javascript
MYAPP.nsFunc('woowa.frontend.javascript.crew')
console.log(window.MYAPP)
```
