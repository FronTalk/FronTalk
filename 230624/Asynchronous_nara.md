# 목차

- 비동기
  - 비동기 단어 뜻
  - 동기와 비동기의 차이
- 프론트엔드로써 왜 비동기를 사용해야할까?
- JavaScript에서 비동기의 활용
  - CallBack함수
    - 장단점
    - 예시
  - Promise객체
    - 탄생배경
    - 장단점
    - 예시
  - Generate함수
    - 탄생배경
    - 장단점
    - 예시
  - Async함수
    - 탄생배경
    - 장단점
    - 예시

# 비동기

비동기에 뜻은 어떤 뜻일까요?

비동기 : 또는 이전 객체 또는 이벤트가 완료될 때까지 기다리지 않고 발생하는 여러 관련 작업. - MDN

동기 : 각 참여자가 즉시(또는 가능한 한 즉시) 메시지를 수신(필요시 처리 및 회신)하는 실시간 통신을 말합니다.

제가 비동기에 대해서 설명하라고 한다면

순서대로 처리한다 = 동기적, ‘순서’를 상관않고 처리한다 = 비동기적

이렇게 비동기적으로 문제를 해결한다면 하나를 완전히 끝마치지않고도 동시에 일을 처리할 수 있습니다.

# 프론트엔드로써 왜 비동기를 사용해야할까?

프론트엔드로써 왜 비동기 프로그래밍을 사용해야할까요?

위에서 나온 말처럼 “동시에 일을 처리할 수 있다.”라는 말은 중요한 포인트입니다.

웹은 현대로 넘어오면서 단순히 정보전달하는 역할을 넘어서 다양한 인터렉션이 발생하며 이는 사용자간 상호작용이 이뤄지고 이런 점이 더욱 중요해지고있습니다.

예를들어 예측할 수 없는 이벤트들, 네트워크 통신, 애니메이션이 생겨나며 이를 통해 대기시간이 발생합니다.

이런 대기시간은 사용자에게 그대로 전달되며 이런 현상은 사용자의 이탈로 이어질 수 있습니다.

그러므로 프론트엔드로써 비동기를 시기적절하게 써야한다고 생각합니다.

## JavaScript에서의 비동기처리

### 콜백함수(CallBack Function)

콜백함수란

다른 코드의 인자로 넘겨 주는 함수 - 재남님, 위키백과

맞습니다. 콜백함수는 다른코드에 인자로 넘겨주는 함수입니다. 이것을 다른말로하면 ‘제어권’도 함께 넘겨주는 뜻입니다.

예를들어 회사와 하청업체를 예시로 들어보겠습니다.

회사는 필요한 자제가 생겼고 그에 따라 하청업체에 요구서와 함께 자체생산을 요청했습니다.

이로써 회사는 제작된 자제를 받을 수 있게되었습니다. 하지만 하청업체에서 어떤 과정이 잘못되어 잘못된 자재가 생산되어 납품이 된다고 가정했을 때 회사는 납품자제를 받을 때 까지 알 수 없습니다. 이것이 바로 ‘제어권’을 넘겨주는 것입니다.

이것을 코드로 봅시다.

```jsx
let count = 0;
let callBackFunction = function () {
  console.log(count);
  if (++count > 4) clearinterval(timer);
};

let timer = setInterval(callBackFunction, 300);
// 결과물은 0,1,2,3,4가 나올 것이며 0.3초마다 결과가 발생할 것입니다.
```

코드를 보면 setInterval함수에 callBackFunction이 인자로 전달되었습니다. 즉 callBackFunction의 호출 시점은 setInterval함수가 정하며 이는 ‘제어권’이 callBackFunction → setInterval함수로 넘어갔는 거라고 볼 수 있습니다. 이런 현상을 you don’t know js저자가 ‘제어의 역전’이라고 부릅니다.

이런 제어권을 넘겨주는 것은 디버깅을 함에 있어 어려움이 생길 수 있습니다.

### Promise

Promise는 콜백함수의 단점을 보안하기 위해 나온 문법입니다.

```jsx
function request() {
  return new Promise(function (resolve, reject) {
    ajax("url", function (data) {
      if (data) {
        resolve(data);
      } else {
        reject("Error");
      }
    });
  });
}

function asyncTask() {
  const promise = request();

  promise
    .then(function (data) {
      //받아온 data를 이용한 작업 수행
    })
    .catch(function (error) {
      // 받아온 error를 이용한 예외처리
    });
}
```

request함수는 비동기가 실행됨에 따라 data를 넘겨줄 콜백을 인자로 받습니다.

promise객체는 then, catch메서드를 활용하여 data를 넘겨받을 콜백함수를 연결시킵니다.

이처럼 콜백함수에서 활용하는 메커니즘이 아닌 비동기 요청에 대한 결과를 받아와 직접 처리가 가능하게끔 할 수 있습니다.

여기서 중요한점은 Promise객체가 만들어지면 함수가 바로 실행된다는 것을 알고있어야 합니다.

- Promise는 제어의 역전을 막을 수 있으며 비동기 요청을 수행함에 있어 (성공, 실패, 대기)상태가 존재합니다.
- then,catch체이닝을 통해서 콜백을 작성이 가능합니다.
- 하지만 이런 Promise객체는 외부에서의 Promise안의 흠에 대한 예외처리가 어려울 수 있으며
- 단일 값을 전달할 때 한계점이 있습니다.

Promise가 등장한 이유 중 하나 ‘가독성’에 대해서 말을 할 수 있습니다.

Promise객체를 활용하여 콜백함수를 활용할 때 보다 좀 더 나은 가독성을 가질 수 있지만 애초에 비동기 프로그래밍은 인간이 순차적으로 생각하기에 한계가 있습니다.

이와같은 생각으로 es6에서 나온 문법인 generate Function이 생겼습니다.

### Generate Function

generate함수는 비동기처리를 위해 등장한 기술은 아니지만 비동기처리가 마치 동기적으로 움직이게 보이도록 하게 만들 수 있습니다.

- async이전에 나온 함수
- 완전한 비동기 처리를 위해 나온 기술이 아니다.
- 비동기를 동기적인 처리를 하는 것처럼 보이게 하는 것에 유용하다.
- 특징
  - - : generator함수를 작성하기 위한 규칙, function 키워드 뒤나 식별자 앞에 선언
  - Iterator: generator호출로 반환된 객체. next()메서드를 가지고있습니다.
  - next() : generator함수안에 yield문으로 넘어가기 위한 메서드
  - yield: next 메서드가 호출되엇을 때, 중간에 멈추고 데이터를 받는 지점

```jsx
function *asyncTask() {
	const data = yield request();
// 받아온 data를 활용해 작업수행
}

function request() {
	ajax('url', function (data){
		if.next(data);
});
}

const it = asyncTask();

it.next()
```

- asyncTask함수를 호출하여 iterator객체를 반환받고 이후 next메서드를 호출하여 함수의 로직을 수행합니다.
- 수행하는 도중 yield를 만난다면 뒤에있는 request함수를 호출하고 asyncTask함수의 진행을 잠시 중단합니다.
- request함수에서 비동기 요청을 하고 값이 도출된다면 중단된 시점에 되돌아가 값을 저장하고 asyncTask함수를 재진행합니다.

여기서 포인트는 함수를 중단하고 중간시점에 값을 보낸다는 점입니다.

### Async Function

async함수는 promise에 generator개념이 더해진 문법으로 나왔습니다.

- 함수 안에서 await을 만난다면 실행을 잠시 중지
- await뒤에 promise결과값을 받아와 중단되었던 함수를 재진행시킵니다.

```jsx
async function asyncTask() {
  const data = await request();

  // 작업수행
}

function request() {
  return new Promise((resolve) => {
    ajax("url", function (data) {
      resolve(data);
    });
  });
}
```

코드에서 await문은 뒤에 오는 값이 Promise일때만 기다립니다.

만약 값이 에러가 발생하면 throw해주며 아니라면 결과값을 반환합니다.

여기서 볼수 있는 장점은 promise의 수행된 ‘값’이기에 예외처리에 용이성, 높은 가독성이 있습니다.

하지만 함수안에서 다수의 Promise를 병렬적으로 처리가 힘들며 async키워드를 항상 선언을 해줘야하는 상황도 만날 수 있습니다.
