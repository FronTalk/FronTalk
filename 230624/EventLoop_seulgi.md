# Event Loop

![](https://velog.velcdn.com/images/sgsg9447/post/a03c6893-c9d2-43f5-940a-a43ba7153bb7/image.jpeg)

## Content

![](https://velog.velcdn.com/images/sgsg9447/post/ecc38e3f-8e09-434f-af42-8924a12d95a2/image.jpeg)

## Event Loop

### Event?

- 사용자가 버튼을 클릭하거나, 데이터가 도착하는 등 액션이 일어나는 것
- 이러한 이벤트들이 일어나면 그에 대응하는 코드 즉 콜백함수 가 실행되어야 함

### Loop?

- 반복적으로 일어나는 일련의 동작

### Event Loop?

- 즉, 발생한 이벤트들을 순서대로 처리하고, 또 다른 이벤트가 발생하면 그것을 계속 처리하는 반복적인 역할

## 왜 필요하지?

### 싱글스레드

- 자바스크립트는 한번에 하나의 작업을 처리함
- 웹 브라우저는 많은일들을 동시에 처리해야함
  - 예: 버튼을 클릭하거나, 새로운 데이터가 로드되거나, 애니메이션이 움직이는 것
- 싱글 스레드인 자바스크립트가 여러 작업을 동시에 처리하는것 처럼 보이게 만드는 것
- 즉, 이벤트루프는 오래걸리는 작업들을 백그라운드로 보내고, 그 작업이 끝나면 다시 메인 스레드로 가져와서 처리

### 동기 vs 비동기

- Synchronous
  - 한 작업이 끝나야 다음 작업이 순차적으로 실행
  - 하나의 작업이 끝나지 않으면 다음 작업은 아무리 준비되어 있어도 대기 상태를 유지
- Asynchronous
  - 작업이 끝나지 않아도 다음 작업을 시작하는 방식
  - 현재 실행중인 작업의 완료 여부와 관계없이 다음 작업을 진행할 수 있음
  - 완료 순서가 보장되지 않음

![](https://velog.velcdn.com/images/sgsg9447/post/26ceab79-f9d0-4be4-984b-bafed77e62f9/image.jpeg)

- YES!!
- 자바스크립트는 싱글스레드이기에 기본적으로 동기적으로 동작
- 이벤트루프와 비동기 API를 활용하면 동시에 여러가지 작업을 처리하는것처럼 보일 수 있음

![](https://velog.velcdn.com/images/sgsg9447/post/ed7edfdf-c35c-4b86-9dba-7146fce3466a/image.jpeg)

- 웹 브라우저나 Node.js와 같은 자바스크립트 엔진을 호스팅하는 환경에서 이루어지는 작업은 실제로 비동기적으로 처리됨
- 이벤트 루프는 비동기 작업의 결과를 순차적으로 처리할 수 있는 방법을 제공하며, 이를 통해 자바스크립트는 동시에 여러 작업을 처리하는 것처럼 보이게 됨

## 구성요소

![](https://velog.velcdn.com/images/sgsg9447/post/a80ee89d-1308-4590-8f72-e507a31f97ce/image.gif)

### 다시 이벤트루프란?

- 태스크가 들어오기를 기다렸다가 태스크가 들어오면 이를 처리하고, 처리할 태스크가 없는 경우에는 ? 끊임없이 돌아가는 자바스크립트 내부 루프

- 콜 스택과 콜백 큐를 계속해서 주시하고 있다가 콜 스택이 비었을 때 콜백 큐에 첫번째에 있는 콜백을 콜 스택에 밀어 넣는 일을 함

![](https://velog.velcdn.com/images/sgsg9447/post/d36acb0a-3cda-4a31-a310-700277b129be/image.jpeg)

### 콜스택

- 함수의 실행을 추적하는 자료 구조
- 함수가 호출되면 해당 함수는 콜 스택의 맨 위에 쌓이고, 함수의 실행이 완료되면 그 함수는 콜 스택에서 제거됨
- 자바스크립트가 어떤 함수를 호출했는지, 그 함수가 어디서 호출되었는지 등의 정보를 추적하는 데 사용됨

### Web APIs

- 웹 API는 브라우저가 제공하는 인터페이스의 일부로서, 자바스크립트 코드에서 브라우저의 기능을 이용하거나, 웹 환경과 상호작용하게 도와주는 역할
- 웹 API는 DOM 조작, AJAX 요청, 타이머 설정 등과 같은 작업을 가능하게 함

### 콜백큐

- 비동기 작업의 결과(주로 콜백 함수)를 저장하는 대기열
- 이 큐에 저장된 작업들은 메인 스레드가 현재 진행 중인 작업을 완료한 후 차례로 처리됨

### 마이크로 태스크 큐 vs 매크로 태스크 큐

- 콜백함수를 저장하는 큐
- 어떤 함수를 실행하느냐에 따라 달라짐
- Macro Task Queue
  - setTimeout, setInterval, setImmeditate, AJAX 콜백, 사용자 이벤트 콜백, requestAnimationFrame
- Micro Task Queue
  - Promise 콜백, MutationObserver

![](https://velog.velcdn.com/images/sgsg9447/post/9edd9926-2a1b-4d89-9f13-9dd43d292f91/image.png)

### Animation Frames?

- 웹 애니메이션을 만드는 데 사용
  - 화면이 새로 그려지는 각각의 순간을 의미함
  - 대부분의 웹 브라우저는 초당 약 60번의 화면 갱신(60Hz)을 수행
- 자바스크립트 메소드
- requestAnimationFrame
- 콜백 함수를 인자로 받아, 브라우저가 다음 리페인트를 진행하기 직전에
  해당 콜백 함수를 실행함
- 콜스택 비어있는지 확인 -> 마이크로 태스크 큐 비어있는지 확인 -> requestAnimationFrame에 의해 등록된 콜백 함수가 있는지 확인 -> 있다면 해당 함수 실행 -> 태스크 큐 비어있는지 확인

![](https://velog.velcdn.com/images/sgsg9447/post/f5951030-e8c6-4ca0-976c-ecbee2bc48a5/image.jpeg)

### Repaint?

- 웹 브라우저에서 특정 요소의 외관이 변경되었을 때 이루어지는 과정
- 색상이나 그림자와 같은 시각적 스타일이 변경되었을 때 발생함
- 이 과정에서 브라우저는 변경된 요소와 그 요소의 자식 요소들을 다시 그림

### Reflow?

- 요소의 레이아웃(ex. 너비, 높이)이 변경되었을 때 이루어지는 과정
- 리페인트보다 더 복잡하고 시간이 많이 소요됨
- 레이아웃 변경은 해당 요소뿐만 아니라 그 요소의 자식 요소들, 형제 요소들, 때로는 부모 요소나 전체 페이지까지도 다시 계산하고 그려야 할 수 있음

## 코드로 동작 과정을 이해해보기!

![](https://velog.velcdn.com/images/sgsg9447/post/428b255e-21a7-4a73-ba7d-11979b5dde2a/image.png)

![](https://velog.velcdn.com/images/sgsg9447/post/53bf1d78-783c-45fc-91ce-24301f424728/image.gif)

- console.log(“1”) 실행 -> 콜 스택 쌓이고 -> 바로 실행 -> “1” 출력
- setTimeout 함수가 콜스택에 쌓임 -> Web API로 전달 -> 콜스택 제거 -> 일정 시간 지나면 -> 콜백큐 추가
- console.log(“3”) 실행 -> 콜스택 쌓이고 -> 바로 실행 -> “3” 출력
  콜 스택 비었고, 이벤트 루프가 태스크 큐에서 다음 작업을 가져와 콜 스택에 쌓음
- console.log(“2”) 출력

![](https://velog.velcdn.com/images/sgsg9447/post/be4a471d-b830-4f25-aff4-16b8bf8a3c54/image.png)

- console.log(“1”) 실행 -> 콜 스택 쌓이고 -> 바로 실행 -> “1” 출력
  setTimeout 함수가 콜스택에 쌓임 -> Web API로 전달 -> 콜스택 제거 -> 일정 시간 지나면 -> 콜백큐 추가
- Promise.resolve().then 함수가 콜스택에 쌓임 -> 마이크로태스크 큐에 추가됨
- console.log(“4”) 실행 -> 콜스택 쌓이고 -> 바로 실행 -> “4” 출력
  콜 스택 비었고, 이벤트 루프가 마이크로 태스크 큐에서 다음 작업을 가져와 콜 스택에 쌓음 -> console.log(“3”)
- 콜 스택 비었고, 이벤트 루프가 태스크 큐에서 다음 작업을 가져와 콜 스택에 쌓음 -> console.log(“2”)

![](https://velog.velcdn.com/images/sgsg9447/post/ca14e5c7-6725-4923-a087-e75fc71301ba/image.png)

- 스크립트 시작하면 value = 100 설정
- Async IIFE 시작, await delay() 호출
- Delay 함수는 즉시 Promise 반환 -> console.log(“0”, 100)
- setTimeout Web API로 전달 -> delay 함수는 더 이상 진행하지 않고 async 함수의 제어를 반환함
- value = 300으로 변경 -> console.log(“3”, 300)
- setTimeout 콜백을 처리할 준비가 되면, 호출 -> console.log(“1”, 100) -> console.log(“2”, 200)
- setTimeout 콜백 내부에서 resolve(value) 가 호출되어 Promise 해결 -> 해결 값인 200은 await delay()의 결과로 사용
- console.log(“3”, 200) 출력

### 레퍼런스!

- [시각화 사이트](http://latentflip.com/loupe/?code=JC5vbignYnV0dG9uJywgJ2NsaWNrJywgZnVuY3Rpb24gb25DbGljaygpIHsKICAgIHNldFRpbWVvdXQoZnVuY3Rpb24gdGltZXIoKSB7CiAgICAgICAgY29uc29sZS5sb2coJ1lvdSBjbGlja2VkIHRoZSBidXR0b24hJyk7ICAgIAogICAgfSwgMjAwMCk7Cn0pOwoKY29uc29sZS5sb2coIkhpISIpOwoKc2V0VGltZW91dChmdW5jdGlvbiB0aW1lb3V0KCkgewogICAgY29uc29sZS5sb2coIkNsaWNrIHRoZSBidXR0b24hIik7Cn0sIDUwMDApOwoKY29uc29sZS5sb2coIldlbGNvbWUgdG8gbG91cGUuIik7!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D)
- [블로그 : 이벤트루프 동작 구조](https://inpa.tistory.com/entry/%F0%9F%94%84-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9D%B4%EB%B2%A4%ED%8A%B8-%EB%A3%A8%ED%94%84-%EA%B5%AC%EC%A1%B0-%EB%8F%99%EC%9E%91-%EC%9B%90%EB%A6%AC)
