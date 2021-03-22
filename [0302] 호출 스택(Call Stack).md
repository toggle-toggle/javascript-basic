## 호출 스택 (Call Stack) = Excecution Stack

### 1. 호출 스택이란?
- 실행할 코드에 제공할 환경 정보들을 모아놓은 객체이다. 자동으로 생성되는 전역공간을 제외하면 거의 함수 실행으로 이루어져 있다.
- 함수들이 호출되는 순서를 기억했다가 함수가 끝나면 원래 있던 자리로 돌아가기 위해 쓰이는 자료구조 중 하나이다. 모든 프로세스와 스레드에는 저마다의 call stack이 존재한다.
- 자바스크립트 내에서 함수가 호출되면, Call Stack에 push 실행이 되면 pop 해준다.
- 자바스크립트는 어떤 call stack이 활성화되는 시점에 선언된 변수를 위로 끌어올리고, 외부 환경 정보를 구성하고, this 값을 설정하는 등의 동작을 수행한다.

### 2. Execution Context

---
#### 참고문서
https://blog.sessionstack.com/how-does-javascript-actually-work-part-1-b0bacc073cf
https://blog.bitsrc.io/understanding-execution-context-and-execution-stack-in-javascript-1c9ea8642dd0
https://ui.dev/ultimate-guide-to-execution-contexts-hoisting-scopes-and-closures-in-javascript/
https://medium.com/@kkak10/lexical-environment-4e0cffcad98d
https://velog.io/@paulkim/e

https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/this
In most cases, the value of this is determined by how a function is called (runtime binding).
호출될 때 쓰인다고 합니다!
