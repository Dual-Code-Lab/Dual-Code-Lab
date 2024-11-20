## let, const 키워드

### 함수 레벨 스코프

var 키워드로 선언한 변수는 오로지 **함수**의 코드 블록만을 지역 스코프로 인정한다.

따라서 함수 외부에서 var 키워드로 선언한 변수는 코드 블록 내에서 선언해도 모두 전역 변수다.

```js
var x = 1;
if (true) {
  var x = 10;
}
console.log(x); // 10
```

함수 레벨 스코프는 전역 변수의 남발을 유발하는 원인이 된다.

### 변수 호이스팅

var 키워드로 변수를 선언하면 변수 호이스팅에 의해 변수 선언문이 스코프의 선두로 끌어 올려진 것처럼 동작한다.

```js
console.log(foo); // undefined
foo = 1;
var foo;
```

에러를 발생시키진 않지만 흐름상 맞지 않을뿐더러 가독성을 떨어뜨리고 오류를 발생시킬 여지를 남긴다.

### let

var 키워드의 단점을 보완하기 위해 ES6에서 도입된 새로운 변수 선언 키워드다.

var 키워드로 이름이 동일한 변수를 중복 선언하면 아무런 에러가 나지 않지만 let 키워드로 이름이 동일한 변수를 중복 선언하면 문법 에러가 발생한다.

```js
var foo = 123;
var foo = 456; // 중복 선언 가능

let bar = 123;
let bar = 456; // SyntaxError: Identifier 'bar' has already been declared
```

#### 블록 레벨 스코프

var 는 오로지 함수의 코드 블록만을 지역 스코프로 인정하는 함수 레벨 스코프다.

하지만 let 키워드로 선언한 변수는 모든 코드 블록(함수, if문, for문, while문, try/catch문 등)을 지역 스코프로 인정하는 블록 레벨 스코프다.

```js
let foo = 1; // 전역 변수
if (true) {
  let foo = 10; // 지역 변수
}
console.log(foo); // 1
```

var와 달리 let의 변수 호이스팅은 발생하지 않는 것처럼 동작한다.

```js
console.log(foo); // ReferenceError: foo is not defined
let foo;
```

변수 선언문 이전에 참조하면 참조 에러가 난다.
var 키워드와 차이점은 var로 선언한 변수는 런타임 이전에 엔진에 의해 암묵적으로 선언, 초기화 단계가 한번에 진행되지만 let 키워드로 선언한 변수는 선언 단계와 초기화 단계가 분리되어 진행된다.

초기화 단계는 변수 선언문에 도달했을 때 실행되며 초기화 단계 이전에 접근하려 하면 참조 에러가 발생한다.

스코프의 시작 지점부터 초기화 시작 지점까지 변수를 참조할 수 없는 구간을 일시적 사각지대(TDZ, Temporal Dead Zone)라고 부른다.

> 선언-일시적 사각지대-초기화-할당

#### let도 호이스팅은 발생한다.

```js
// 호이스팅 발생의 예
let foo = 1; // 전역 변수 선언
{
  console.log(foo); // ReferenceError: foo is not defined
  let foo = 2; // 지역 변수 선언
}
```

let으로 선언한 변수의 경우 변수 호이스팅이 발생하지 않는다면 위 예제는 전역 변수 foo의 값을 출력해야 하지만 참조 에러가 발생한다.

#### let으로 선언한 전역 변수는 전역 객체의 프로퍼티가 아니다.

var 키워드로 선언한 전역 변수는 전역 객체의 프로퍼티다.

하지만 let 키워드로 선언한 전역 변수는 전역 객체의 프로퍼티가 아니다.

```js
let foo = 123;
// let, const 키워드로 선언한 전역 변수는 전역 객체의 프로퍼티가 아니다.
console.log(window.foo); // undefined
```

### const

const 키워드는 상수를 선언하기 위해 사용하는 키워드다.

const 키워드로 선언한 변수는 반드시 선언과 동시에 초기화해야 하며 재할당이 금지된다.

let과 마찬가지로 블록 레벨 스코프를 가지며 호이스팅이 발생하지 않는 것처럼 동작한다.

#### 선언과 동시에 초기화

```js
const foo = 1;
const foo; // SyntaxError: Missing initializer in const declaration
```

#### 호이스팅

마찬가지로 호이스팅이 발생하지 않는 것처럼 동작한다.

```js
console.log(foo); // ReferenceError: foo is not defined
const foo;
```

#### 재할당 ❌

var, let 과 달리 const 키워드로 선언한 변수는 재할당이 금지된다.

```js
const foo = 1;
foo = 2; // TypeError: Assignment to constant variable.
```

#### 상수

변수의 상대 개념인 상수는 재할당이 금지된 변수를 말한다.

const 키워드로 선언한 변수에 원시 값을 할당한 경우 변수 값을 변경할 수 없다.

하지만 상수에 객체를 할당한 경우 객체는 변경 가능한 값이다.
상수는 상태 유지와 가독성, 유지보수의 편의를 위해 적극적으로 사용해야 한다.

```js
const TAX_RATE = 0.1;

let base = 100;
let sufix = "원";

console.log(`지불할 금액은 ${base + base * TAX_RATE} ${sufix}입니다.`);
```

#### const 키워드와 객체

const 키워드로 객체를 선언한 경우 객체의 프로퍼티는 변경할 수 있다.

```js
const person = {
  name: "Lee",
};

person.name = "Kim";
console.log(person); // {name: "Kim"}
```

변경 불가능한 값인 원시 값은 재할당 없이 변경할 수 있는 방법이 없다.

```js
const foo = 1;
foo = 2; // TypeError: Assignment to constant variable.
```

**const 키워드는 재할당을 금지하는 것이지 불변을 의미하지는 않는다.**

ES6를 사용한다면 var는 지양하고 let, const를 사용하는 것이 좋다.

재할당이 필요한 경우에만 let을 사용하고 그렇지 않은 경우 const를 사용하자.

일단 그냥 const를 사용하자.
