# 원시 자료형(Primitive Data Type)

### 1. 자바스크립트의 자료형

- 원시자료형
- 참조자료형

### 2. 자료형 별 종류

- 원시 자료형, 원시 데이터 타입(Primitivie Data Type)

  - Number 숫자
  - String 문자열
  - Boolean 불리언
  - Null
  - Undefined
  - Symbol (ES6)

- 참조 자료형, 참조 타입(Reference Type)
  - Object 객체
    - Function
    - Date
    - Array
    - RegExp
    - Map. WeakMap
    - Set, WeakSet

### 3. 데이터 타입의 필요성

- 각 데이터 타입 마다 저장에 필요한 데이터 영역의 크기가 다르기 때문에 타입을 구분할 필요성이 있음.

### 4. 데이터 타입 결정 방식에 따른 프로그래밍 언어 분류

- 동적 타입 언어

  - 값이 할당되는 과정에서 스스로 추론하여 자동으로 타입이 결정됨.
  - 특정 변수에 숫자를 대입했더라도, 재할당으로 추후에 문자열과 같은 다른 데이터 타입의 값을 대입할 수 있음.
  - 자바스크립트

- 정적 타입 언어
  - 변수 선언 단계에서 타입이 결정됨.
  - C, 자바

### 5. 자료형 별 특징

- 원시 타입(Primitive type)
  - 변수가 이동할 때 메모리 상에 값을 바로 저장함.
  - 저장에 많은 공간이 필요하지 않음.

```javascript
let num = 1; // 저장되는 값은 1, 기능이 없어 공간을 적게 차지
```

- 내용(값)으로 비교함.
- 프로퍼티를 바꾸거나, 추가하거나, 제거할 수 없음.
- 변경 불가능한 값 (immutable value)
- 원시값 자체를 변경할 수 없지만, 변수값은 재할당을 통해 변경할 수 있음.

- 참조 타입(reference type) = 객체
  - 변수가 이동할 때 값이 아닌 객체를 저장한 메모리의 주소값을 저장함.(주소값은 가리키는 곳이라는 의미에서 포인터, 레퍼런스라고도 부름.)
  - 여러 타입이 합쳐진 복잡한 형태로 저장에 큰 공간이 필요함.
  - 객체를 사용하는 과정에서 객체의 이동이나 복사 등이 발생하는데,
    객체는 크기를 가늠할 수 없기 때문에 변수를 이동할 때마다 모두 복사해서 메모리에 저장한다면
    성능이 현저히 떨어지게 될 것
  - 다른 변수로 값을 복사할 때 주소 값만 복사하기 때문에
    다른 변수는 그 주소를 보고 객체를 찾아가 사용할 수 있어서 효율적
  - 프로퍼티를 자유롭게 추가, 변경, 제거할 수 있음.
  - 변수의 원본과 사본 중 한 쪽에서 변경이 일어나면 양쪽에 영향을 미침.

### 6. 자료형 별 예시

- 원시 타입

```javascript
let a = 1;
function test(v) {
  v++;
}
test(a);
console.log(a);

// 1
// a의 값인 1은 원시타입이기 때문에 값 자체가 복사되어 2가 아닌 1이 찍힘.
```

- 참조 타입

```javascript
let a = { x: 1 };
function test(v) {
  v.x++;
}
test(a);
console.log(a.x);

// 2
// 오브젝트가 할당되는 것이 아니라, 오브젝트가 가리키는 주소값, 포인터, 레퍼런스가 할당됨.
// a의 주소 값을 복사했고, a가 수정됐기 때문에 2가 찍힘.
```

### 7. 심볼

```javascript
const id = Symbol("id입니다");
```

- 자기 자신을 제외한 모든 값과 다른 유일한 값을 의미
- 유일성 보장
- 뒤 괄호에 문자열로 이름을 부여해서 생성할 수 있음. 이 문자열은 심볼 생성에는 어떠한 영향도 미치지 않으며 디버깅 시 용이함.
- 같은 문자열을 준 symbol을 두 개 만들더라도 유일성이 보장되어 둘을 비교하면 false. 심볼은 이름이 같더라도 모두 다른 존재임.
- 심볼 이름을 얻는 방법

```javascript
id.description; // 'id입니다'
```

### 8. 전역 심볼

```javascript
Symbol.for();
```

- 전역 심볼. 하나를 생성한 뒤 키를 통해 같은 심볼을 공유

```javascript
const id1 = Symbol.for("id");
const id2 = Symbol.for("id");
id1 === id2; // true
```

- 전역 심볼일 때 심볼 이름인 얻는 법

```javascript
Symbol.keyFor(id1); // 'id'
```

### 9. 심볼을 사용하는 이유

- 타 개발자가 만들어놓은 객체가 있고 for문을 돌려서 이미 그 객체를 사용하고 있는 경우
- 그 객체에 어떤 function을 추가하고 싶을 때,
- 원하지 않는 키 값이 추가되면 이미 돌아가던 for문에서 에러가 나는 등 원하지 않는 결과가 도출될 수 있음.
- 다른 사람이 만들어둔 프라퍼티를 건드리거나, 덮어씌울 일 없이 나만의 프라퍼티를 사용할 수 있는 방법이 바로 심볼임.

```javascript
const user = { name: 'Mike', age: 30 }   // 다른 개발자가 만들어놓은 객체
for (let key in user) { console.log(`His ${key} is ${user[key]}.`}   // 키 값을 순회하며 사용자에게 콘솔을 찍는 상황
user.showName = function() {console.log(this.name}   // 이렇게 추가하면 원치 않는 결과가 생길 수 있음
 
const showName = Symbol('show name');
user[showName] = function() {console.log(this.name}   // 심볼로 추가하면 for문에는 숨겨져서 영향을 미치지 않음
user[showName] ( )   // 원 객체에는 영향을 미치지 않으면서, 원하는 Mike를 찍을 수 있음
```

- 숨겨진 Symbol을 포함한 객체의 모든 키를 보는 법

```javascript
Reflect.ownKeys(객체명);
```

- 숨겨진 Symbol Key 보는 법

```javascript
Object.getOwnPropertySymbol(객체명);
```
