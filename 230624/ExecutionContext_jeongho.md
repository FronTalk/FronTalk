실행 컨텍스트에 대해서 알아보겠습니다.

## 실행 컨텍스트란?

- 코드를 **실행**하는데 필요한 **환경**(코드 실행에 영향을 주는 조건이나 상태)을 제공하는 객체
- 자바스크립트 엔진은 소스 코드를 실행할 때 **생성 단계**를 통해 실행 컨텍스트를 생성하고 **실행 단계**를 통해 결과물을 도출합니다.

> 생성 단계 (Creation Phase)

- 실행 컨텍스트 (Execution Context 생성)
- 선언문만 실행해서 환경 레코드에 기록

> 실행 단계 (Execution Phase)

- 선언문 외 나머지 코드를 순차적으로 실행
- 환경 레코드를 참조하거나 업데이트

## 실행 컨텍스트 구조!

![](https://velog.velcdn.com/images/hyeon9782/post/84652bcf-cd2b-49b0-aa59-be42066bba59/image.png)

- 실행 컨텍스트를 이루는 컴포넌트들은 위의 사진보다 더 많고 복잡합니다.
- 하지만 오늘은 **렉시컬 환경 , 환경 레코드 , 외부 환경 참조**를 기준으로 알아보겠습니다.

## 실행 컨텍스트 이해하기!

```jsx
function A() {
  function B() {}
}
```

- 다음과 같은 코드를 실행시키면 자바스크립트 엔진은 **Call Stack**에 **전역 실행 컨텍스트**를 담습니다.
- 만약 전역에서 함수A를 호출할 경우 함수A의 실행 컨텍스트를 생성해서 Call Stack에 담습니다.
- Call Stack에서는 **가장 최근에 추가된 실행 컨텍스트만 활성화**됩니다. (지금은 함수 A 실행 컨텍스트)
- 만약 함수A에서 함수B가 호출되면 함수B의 실행 컨텍스트를 Call Stack에 담습니다.
- 함수B의 실행을 마치고 함수B가 종료되면 함수B의 실행 컨텍스트가 Call Stack에서 제거됩니다.
- 그럼 실행중인 실행 컨텍스트는 함수A의 실행 컨텍스트가 됩니다.
- 함수A가 종료되면 함수B의 실행 컨텍스트가 Call Stack에서 제거됩니다.
- 그럼 실행중인 실행 컨텍스트는 전역 실행 컨텍스트가 됩니다.
- 전역에 있는 코드가 마지막 라인까지 모두 실행되면 전역 실행 컨텍스트도 Call Stack에서 제거됩니다.

> 실행 컨텍스트 스택 (Call Stack)

- 실행 컨텍스트를 **스택** 자료구조로 관리하는 객체
- 실행 컨텍스트 스택은 코드의 **실행 순서**를 관리합니다.
- 현재 **실행 중인 실행 컨텍스트**는 가장 최근에 추가한 실행 컨텍스트입니다.

## Record로 호이스팅 이해하기!

### 환경 레코드 (Environment Record)

- 식별자와 식별자에 바인딩된 값을 기록해두는 객체

> 호이스팅 (Hoisting)

- 선언문이 마치 최상단에 끌어올려진 듯한 현상

> 선언 & 초기화

- 선언 : 메모리 공간을 확보하고 식별자와 연결
- 초기화 : 식별자에 값을 바인딩

### 변수 호이스팅

#### var

```tsx
console.log(pet); // undefined

var pet = "cat";

console.log(pet); // cat
```

- 전역 실행 컨텍스트를 생성하고 전체 코드를 돌면서 선언할 것이 있다면 먼저 선언해둡니다.
- 선언하는 과정에서 환경 레코드안에 pet이라는 식별자를 기록합니다.
- var 키워드로 선언했기 때문에 undefined로 값을 초기화 해둡니다.
- 첫 번째 console.log가 출력됩니다. var 키워드로 선언한 변수는 선언과 동시에 undefined로 초기화 하기 때문에 undefined가 출력됩니다.
- pet이라는 변수에 "cat"이라는 데이터를 할당합니다.
- 두 번째 console.log가 출력되면 환경 레코드를 참조해서 "cat"이라는 문자를 출력합니다.

#### let , const

```jsx
console.log(pet); // Reference Error

const pet = "cat";

console.log(pet); // cat
```

- 앞에 과정은 var와 동일하게 이루어집니다.
- let이나 const로 선언한 변수는 생성 단계에서 선언만하고 초기화를 하지 않습니다.
- 따라서 첫 번째 console.log가 실행되면 Reference Error가 발생합니다.

> 일시적 사각지대 (Temporal Dead Zone)

- let 또는 const로 선언했을 때, 선언 이전에 식별자를 참조할 수 없는 구역

### 함수 호이스팅

#### 함수 표현식

```jsx
study1(); // Type Error
study2(); // Reference Error

var study1 = () => {
  // do study
};

const study2 = () => {
  // do study
};
```

- 변수에 함수를 담아 선언하는 방식
- 변수 호이스팅과 동일하게 동작
- var를 사용할 경우 식별자에 undefined가 바인딩되어 있기 때문에 TypeError 발생
- let, const를 사용할 경우 식별자에 바인딩된 값이 없기 때문에 Reference Error 발생

#### 함수 선언문

```jsx
study(); // 호출 성공~

function study() {
  // do study
}
```

- 자바스크립트 엔진이 함수의 선언과 동시에 완성된 함수 객체를 생성해서 환경 레코드에 기록합니다.
- 선언과 동시에 함수가 생성되어 선언 전에도 함수를 사용할 수 있음

## Outer로 스코프체이닝 이해하기!

### 외부 환경 참조 (Outer Environment Reference)

- 바깥 렉시컬 환경을 가르킵니다.

> **렉시컬 환경 (Lexical Environment)**

- Record와 Outer를 포함하고 있는 자료구조로 실행 컨텍스트를 이루는 컴포넌트 중 하나입니다.

> **식별자 결정 (Identifier Resolution)**

- 코드에서 변수나 함수의 값을 결정하는 것

```

const animal = 'cat';
const pet = "cat";

function goTo2F(){
	let pet = 'puppy';
    console.log(pet); // puppy
    console.log(animal); // cat
    console.log(corona); // Reference Error
}
```

- goTo2F() 함수를 실행시키면 첫 번째 console.log 함수를 통해 pet을 출력합니다.
- pet을 출력하기 위해 실행 컨텍스트의 렉시컬 환경에가서 pet을 찾습니다.
- 두 번째 console.log 함수를 통해 animal을 출력합니다.
- animal을 출력하기 위해 렉시컬 환경에가서 animal을 찾지만 현재 렉시컬 환경에서는 animal이 존재하지 않습니다.
- 이때 outer를 통해 바깥 렉시컬 환경(여기서는 전역 환경)으로 이동 후 전역 변수인 animal을 찾고 출력합니다.
- 세 번째로 corona를 출력하기 위해 전역 실행 컨텍스트의 렉시컬 환경에 가서 corona를 찾습니다. 하지만 현재 렉시컬 환경에서는 찾지 못합니다.
- 이번에는 outer를 통해 바깥 렉시컬 환경으로 이동 후 corona를 찾습니다. 하지만 바깥 렉시컬 환경에서도 corona를 찾지 못하여 Reference Error를 발생시킵니다.

> 변수 섀도잉 (Variable Shadowing)

- 동일한 식별자로 인해 상위 스코프에서 선언된 식별자의 값이 가려지는 현상

> 스코프 체인 (Scope Chain)

- 식별자를 결정할 때 활용하는 스코프들의 연결리스트

### References

- [[10분 테코톡] 하루의 실행 컨텍스트](https://www.youtube.com/watch?v=EWfujNzSUmw)
- [[10분 테코톡] 부엉이의 Execution Context](https://www.youtube.com/watch?v=QkCNba92Vqo)
- [모던 자바스크립트 Deep Dive](https://product.kyobobook.co.kr/detail/S000001766445)
