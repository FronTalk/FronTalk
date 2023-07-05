# Prototype 발표자료

![‎prototype ‎001](https://github.com/FronTalk/FronTalk/assets/83911617/f5b72173-d9d3-478f-be81-5c2ac6254efa)
![‎prototype ‎002](https://github.com/FronTalk/FronTalk/assets/83911617/aad866ff-16e5-4fc6-8bf0-d0baaeb93fe7)
![‎prototype ‎003](https://github.com/FronTalk/FronTalk/assets/83911617/4e805a7d-daf9-4c46-99a0-5a85c6b3c1f8)
![‎prototype ‎004](https://github.com/FronTalk/FronTalk/assets/83911617/229379fd-5477-4b8b-b305-6da6bcdcdbc7)
![‎prototype ‎005](https://github.com/FronTalk/FronTalk/assets/83911617/20c9f34a-78e4-4894-849e-a87951c38391)
![‎prototype ‎006](https://github.com/FronTalk/FronTalk/assets/83911617/7b216fc5-f221-4b2f-9dea-da7a8bc0a4fc)
![‎prototype ‎007](https://github.com/FronTalk/FronTalk/assets/83911617/e14a7dc1-3f1b-45dd-9517-4e82f7bc850e)
![‎prototype ‎008](https://github.com/FronTalk/FronTalk/assets/83911617/a7fad723-482a-4900-851d-56ffe78c0bc1)
![‎prototype ‎009](https://github.com/FronTalk/FronTalk/assets/83911617/2e2ae5bf-03ac-4a6c-be34-9bd11652e1b1)
![‎prototype ‎010](https://github.com/FronTalk/FronTalk/assets/83911617/9a763591-cb78-46c7-97e0-4f04ff050353)
![‎prototype ‎011](https://github.com/FronTalk/FronTalk/assets/83911617/cbbe8f2c-d517-4dea-9065-246b5d1ab95c)
![‎prototype ‎012](https://github.com/FronTalk/FronTalk/assets/83911617/15d9be19-0831-42c5-919a-2590885991f9)
![‎prototype ‎013](https://github.com/FronTalk/FronTalk/assets/83911617/0e6bdea8-7d38-4d5e-bf71-ac831c201c47)
![‎prototype ‎014](https://github.com/FronTalk/FronTalk/assets/83911617/a5dee265-6285-46c1-83c5-4b452b56f76e)
![‎prototype ‎015](https://github.com/FronTalk/FronTalk/assets/83911617/14032ab9-8d52-43d1-aa55-ff16f3587522)
![‎prototype ‎016](https://github.com/FronTalk/FronTalk/assets/83911617/071e0dbc-7ab1-4e8d-b25b-3b3b3b9d003f)
![‎prototype ‎017](https://github.com/FronTalk/FronTalk/assets/83911617/20b28fbe-8e30-4980-8350-18340bfa34da)


<br>
<br>

## 발표 대본

<br>

(2번이동)

프로토타입이란 무엇일까요?

프로토타입의 사전적 의미부터 알아보겠습니다.

위키백과에서 소개하는 프로토타입은 무언가 제품을 만드는 과정에서 시험용으로 미리 만들어보는 물건을 뜻합니다.

이를 단어로 축약하면 ‘초기형’, ‘원형’, ‘예시’라고 생각합니다.

(3번이동)

그렇다면 JavaScript에 존재하는 prototype은 어떤 뜻일까요?

**JavaScript의 모든 객체는 상위 객체를 참조하며, 상위 객체를 프로토타입이라고 부른다합니다.**

여기서 눈여겨 본 점은 모든객체 ,상속받기위한, 프로토타입 객체를 가짐 입니다.

(4번이동)

간단하게 prototype이라는 정의를 알아보았습니다..

그럼 이 prototype을 어디에 사용을 할까요

(5번이동)

많은 사용성이 존재하겠지만 제가 중점적으로 볼 점은 ‘상속’입니다.

상속이라는 개념은 객체지향언어에서많이 등장하는 요소이며 많이 사용됩니다.

만약 여러분이 Javascript에서의 상속을 떠올린다면 class를 떠올릴 수 있을겁니다.

(6번이동)

javascript에서 class는  가독성과 적은 코드량을 위해 ES6에 도입되었습니다.

하지만 javascript는 ES6이전에는 class라는 문법이 존재하지않았습니다.

그렇다면 class전에는 어떻게 상속개념을 사용하였을까요?

맞습니다 이번에 공부한 Prototype 개념을 활용하였습니다. 

(7번이동)

여기서 저는 생각했습니다. “아 그럼 prototype 상속은은 class의 상속과 같은것이고, 같은 방식으로 **상속**을 하는구나.” 여기서 말하는 class는 javascript의 class가 아닌 다른 언어에서 사용되는 class입니다.

여러분은 어떤가요?

하지만 조금만 구글링을 해본다면 많은 사람들이 class의 상속 개념과 prototype의 상속 개념은 차이점이 있다고 얘기합니다.

왜일까요?

흔히 java와 같은 언어의 상속과 JavaScript는 ‘상속’의 개념이 다르다고 얘기합니다.

그럼 개념적인 부분에서 다를까요? 

(8번이동)

다시 상속에 대한 의미를 되짚어보았습니다.

“상속” : 객체지향 프로그래밍에서 상속은 “객체들 간의 관계를 구축하는 방법” - 위키피디아

또는 기존에 정의된 모든 필드와 메서드를 “물려받아” 새로운 클래스를 생성… - TCP

이 글을 이해해본다면 다른 객체지향언어들에 사용되는 상속의 의미는 기존의 코드나 환경을 그대로 “복사”하여 추가적인 기능을 추가하거나 재정의하여 사용하는 것 입니다.

그렇다면 JavaScript에서의 상속은 개념과 다른점이 있는걸까요? 아님 실제로 동작이 달리할까요?

지금부터 이 점을 생각하면서 Prototype에 대해서 파헤쳐 보겠습니다.

(9번이동)

먼저 prototype은 어떨때 생성되는지 부터 알아보겠습니다.

이전에 나왔듯이 javascript의 모든 객체는 prototype객체를 가지고있습니다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/147c7f40-3743-44c6-bb9f-4ac8ad5af6a5/Untitled.png)

위 예시의 빨간선 안의 값들이 a객체의 프로토타입이라고 말합니다.

그럼 이 prototype을 이용해서 어떻게 상속을 구현할까요?

(다음이동)

바로 `__proto__` 를 활용합니다.

이 `__proto__` 는 객체와 객체를 연결하는 링크라고 생각할 수 있겠습니다. (proto역시 객체라고 볼 수 있습니다.)

`__proto__` 을 활용하여 prototype의 상속 개념을 구현할 수 있습니다.

(10번이동)

간단한 객체를 생성했습니다. 이 a의 객체에는 Object생성자 함수로 생성이 됩니다. 이때 a에는 `__proto__` 내부 링크가 존재합니다. 

이 `__proto__` 는 Object생성자 함수의 Object.prototype에 연결됩니다

이때 Object.prototype을 prototype객체입니다.

prototype객체와 prototype은 이런식으로 형성이 됩니다.

(11번 이동)

Javascript는 이 `__proto__` 를 활용하여 상속과 비슷한 개념을 구현할 수 있습니다.

간단한 예시를 하나 더 만들어보겠습니다.

arr객체를 생성하고 hasOwnProperty를 활용하여 ‘hasOwnProperty’와 ‘length’가 존재하는지 확인해보았습니다.

왜 hasOwnProperty가 없다고 나올까요?

(12번 이동)

우선 array객체 안에서 hasOwnProperty가 없는걸 확인합니다. 이후  `__proto__` 를 통하여 Array.prototype으로 접근하여 확인합니다. Array.prototype에도 없는 것 을 확인한 후  `__proto__` 를 통해 Object.Prototype을 확인합니다. 이때 hasOwnProperty가 존재하는 것을 확인 할 수 있습니다.

즉 array객체에는 hasOwnProperty메서드가 없다는 것을 알 수 있지만 이 hasOwnProperty를 사용할 수 있는 것은  `__proto__` 를 통해서 상위 prototype을 타고타고 올라가는 것을 

(13번 이동)

“프로토타입 체인”이라고 말합니다.

이때 알고 있어야 하는 점은  prototype chain에서 최상위는 항상 Object.prototype라는 것 입니다.

자 이제 우리는 JavaScript의 prototype이 어떤 방식으로 상위 프로퍼티를 참조하며 사용하는지 흐름을 알게되었습니다.

여기서 아까의 질문으로 돌아가겠습니다.

(14번 이동)

class에서 사용되는 상속과 prototype에서 상속은 같은 의미일까요?

이번에 공부하면서 알게된 점은 객체를 만드는 것에 있어 차이점이 존재한다는 것입니다.

(15번 이동)

class로 객체를 생성하기위해서는 class에 행위와 속성을 정의합니다. (제가 느끼기엔 설계도)

이후 행위와 속성에 따라 객체가 만들어집니다.

하지만 prototype으로 새로운 객체를 생성하기 위해서는 Object생성자 함수를 통해서 만들어집니다. 하지만 이 Object생성자 함수 또한 객체입니다.

이말은 Prototype에서 객체를 생성할려면 실제로 있는 대상을 통해 객체가 생성된다는 점입니다. (말 그대로 프로토타입이 있어야 객체가 만들어진다는 말.)

실제로 메모리 힙을 본다면 class로 만든 객체는 객체만 올라와있지만 prototype에는 생성자함수와 객체가 함께 올라와있습니다.

(16번 이동)

이번주는 프로토타입과 class와 상속의 차이를 알아보았습니다. 처음에는 무작정 prototype이란 무엇이며 어떻게 동작하고 이후 어떻게 사용하는지에 대해서 설명할려고 했지만 자바스크립트의 가장 중요한 개념이기도 하고 그냥 기술 소개가 되어버리는 것 같아  제가 생각한 흐름을 작성해보았고 차근차근 개념을 확장하는 방법이 좋은 방향인 것 같아 발표를 준비해보았습니다. 감사합니다.
