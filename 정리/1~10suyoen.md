## 2. Redux가 무엇인가요, 왜 Redux를 사용하시나요? 꼬리질문

Redux는 JavaScript 애플리케이션의 상태 관리를 위한 도구로, 예측 가능한 상태 업데이트와 중앙 집중화된 상태 관리를 제공합니다. Redux를 사용하면 상태를 효율적으로 관리하고 여러 컴포넌트에서 상태를 공유할 수 있습니다. 이로써 애플리케이션의 예측 가능성과 확장성을 높일 수 있습니다.

**중앙 집중화된 상태관리는 무엇인가요?**
중앙 집중화된 상태 관리는 애플리케이션의 상태를 하나의 중앙 저장소에 집중적으로 관리하는 패턴입니다.

**중앙 집중화된 상태관리는 flux패턴과 연관되어 있는데 flux 패턴은 무엇인가요?**
중앙 집중화된 상태 관리는 Flux 패턴과 관련이 있습니다. Flux는 Facebook에서 개발된 애플리케이션 아키텍처 패턴으로, 단방향 데이터 흐름을 강조하여 애플리케이션의 상태를 예측 가능하고 변화를 추적하기 쉽게 만듭니다. Flux 패턴은 다음과 같은 구성 요소로 이루어져 있습니다: 액션(Action), 디스패처(Dispatcher), 스토어(Store), 뷰(View).

**액션(Action)**은 애플리케이션에서 발생하는 특정 이벤트 또는 사용자의 동작을 나타내는 객체입니다. 예를 들어, 버튼 클릭, 데이터 업데이트 등이 액션에 해당합니다.

**디스패처(Dispatcher)**는 액션을 받고, 해당 액션을 처리할 스토어에게 알림을 보내는 역할을 합니다. 디스패처는 애플리케이션의 중앙 허브로서 액션을 분배하는 역할을 수행합니다.

**스토어(Store)**는 애플리케이션의 상태를 저장하고, 상태 변경을 처리하는 역할을 합니다. 스토어는 액션을 받아서 상태를 업데이트하고, 변경된 상태를 저장합니다. 스토어는 일반적으로 단일 상태 트리를 가지고 있으며, 상태 변경을 위한 로직을 포함합니다.

**뷰(View)**는 스토어의 상태를 사용하여 사용자에게 UI를 표시하는 역할을 합니다. 뷰는 스토어의 상태를 구독하고, 상태가 변경될 때마다 업데이트되어 사용자에게 최신 정보를 제공합니다.

## 3. Redux 말고 다른 전역 상태관리 아는 것 하나 와 차이점을 말해주세요

Redux 외에도 MobX는 또 다른 전역 상태 관리 라이브러리입니다.
Redux와 MobX는 모두 전역 상태 관리를 위한 라이브러리입니다. Redux는 명확한 문법과 일관된 패턴을 갖고 있으며, MobX는 간단하고 직관적인 문법을 가지고 있습니다. 또한, Redux는 React와의 통합이 강조되고 MobX는 코드를 간소화할 수 있는 특징적인 문법을 가지고 있습니다.

++ 저는 contextApi로 할게요!!
수연 답변: context api는 리액트에서 제공하는 전역 상태관리 api 입니다.
리덕스에 비에 초기 세팅이 쉽지만 자식 컴포넌트에서 상태값이 변할경우, 부모컴포넌트에서도
리렌더링이 일어난다고 들었습니다. 따라서 리덕스를 선택하였는데요
컴포넌트 간의 상태를 중앙 집중적으로 관리함으로써 자식 컴포넌트에서 상태를 변경하더라도 해당 상태는 리덕스 스토어에 저장되고, 부모 컴포넌트의 상태와는 직접적인 관계를 맺지 않는것으로 알고 있습니다.

**그렇다면 MobX말고 리덕스를 사용하는 이유는 무엇인가요??**
아무래도 리덕스의 단방향 패턴 flux 패턴의 장점때문에 사용 하고 있습니다.
리덕스의 flux 패턴덕분에 언제 어디서 상태값이 변하는지 쉽게 알기 쉽기때문에 상태 관리하는데 용이합니다.

## 4. 버츄얼 돔과 리얼 돔의 차이를 설명해주세요

버츄얼 돔(Virtual DOM)은 메모리 상에 존재하는 가상의 돔 트리로 , 돔 변경을 추적하고 효율적으로 업데이트하는 데 사용됩니다. 리얼 돔(Real DOM)은 브라우저의 실제 HTML 문서 구조를 나타내는 돔 트리입니다. 버츄얼 돔은 성능 최적화를 위해 돔 조작과 렌더링을 효율적으로 수행하는 방법 중 하나입니다.

**버츄어돔의 어떤면이 성능 최적화를 도울까요?**
버츄어돔은 불필요한 리렌더링을 막을수 있습니다.
리얼돔의 경우 상태값이 변하면 모든 데이터의 리렌더링이 일어나게 됩니다. 이로 인하여 변경된 상태에 따라 DOM을 업데이트하는 과정은 꽤나 비용이 나간다고 알고 있습니다. 이에반에 버추얼 돔은 실제 돔의 가벼운 복사본으로서 동작합니다. 상태 변화가 발생하면 가상 돔은 실제 돔과 비교하여 변경된 부분만을 실제 돔에 반영합니다. 이를 통해 불필요한 리렌더링을 막고, 변경된 부분만을 업데이트하여 성능을 향상시킵니다.

## 6. useEffect의 실행 순서에 대해 설명해주세요.

useEffect의 실행 순서는 컴포넌트의 마운트 시에 콜백 함수가 실행되고, 이후 의존성 배열을 검사하여 변경 여부를 확인합니다. 변경이 있을 경우 콜백 함수가 다시 실행되고, 변경이 없을 경우 이전에 실행된 클린업 함수가 실행됩니다.

**useEffect는 리액트의 생명주기에서 어디에 해당되나요??**
클래스 컴포넌트의 componentDidMount, componentDidUpdate, componentWillUnmount와 유사한 역할을 수행합니다.

1. 컴포넌트의 첫 렌더링 이후에 실행되는 효과를 구현할 수 있으며, 컴포넌트가 업데이트되거나 언마운트될 때에도 동작합니다. // componentDidMount
2. useEffect는 컴포넌트의 마운트 시에 한 번 실행되며, 의존성 배열에 의해 제어될 경우 해당 의존성이 변경될 때마다 실행될 수도 있습니다. //componentDidUpdate
3. 컴포넌트가 언마운트되기 전에 클린업(clean-up) 작업을 수행할 수 있는 기능도 제공합니다.
   //componentWillUnmount

componentDidMount: 클래스 컴포넌트에서 컴포넌트가 마운트된 후에 호출되는 생명주기 메서드입니다
componentDidUpdate: 컴포넌트가 새롭게 변경되었을때 호출되는 생명주기 메서드
componentWillUnmount :컴포넌트가 언마운트되기 전에 호출되는 생명주기 메서드입니다.

## 7. var, let, const의 차이에 대해 알려주세요.

var는 ES5 이전의 변수 선언 방식이며, 함수 스코프를 가지고 중복 선언이 가능합니다. let은 ES6에서 도입된 블록 스코프를 가지는 변수 선언 방식이며, 변수의 재할당이 가능합니다. const는 상수를 선언하는 방식으로, 값의 재할당이 불가능합니다.

**var의 특징과 문제점에 대해 말해주세요**
자바스크립트 코드는 실행이 되면 먼저 모든 변수가 최상단으로 끌려 올려져 초기화가 이루어집니다.
이를 호이스팅이라 하는데요.var키워드는 선언과 동시에 초기화가 이루어집니다. 이로 인하여 컴파일러가 선언부에 도달하기 이전에 변수를 호출할경우 에러가 아닌 undefined를 반환합니다. 또한 함수 스코프를 가지고 있어 함수의 코드블록만을 지역스코프로 인정합니다. 함수이외에 선언된 var는 모두 전역변수가 됩니다.

<br>

**let const의 특징을 var와 비교해서 말해주세요**
let은 블록 레벨 스코프를 가지고, var는 함수 레벨 스코프를 가집니다. 블록 레벨 스코프는 함수 레벨 스코프 보다 더 넓은 범위로 함수 뿐만아니라, if문, for문 등에서도 선언된 블록 안에서만 유효합니다.

두번째로는 var 키워드는 변수의 선언 단계와 초기화 단계가 한번에 이루어지지만, let 키워드는 분리되어 이루어집니다. var 키워드는 그래서 변수 선언문 이전에 변수를 호출하면 그냥 에러를 띄우는 대신 undefined를 출력합니다. 이는 변수가 스코프에 선언되었고, 이를 위한 메모리 공간 또한 확보 되었지만, 아직 값이 할당되어지지 않았기 때문입니다. 이와 달리 let 키워드는 변수 선언이 먼저 되고, 초기화는 변수 할당 단계와 같이 이루어지기 때문에 변수선언문 전에 변수를 호출하면 참조 에러가 발생합니다. (변수 is not defined) 이는 변수를 위한 메모리 공간 조차 확보 되지 않았기 때문입니다. 이러한 상태를 일시적 사각지대 (**TDZ**)라고 합니다.

세번째로는 호이스팅 문제가 있습니다.

+const는 let처럼 블록 레벨 스코프를 가지고, 재선언과 재할당 둘 다 안된다는 특징이 있습니다. 그러나 객체의 내용물은 변결 할 수 있습니다. 재할당이 안된 다는 것은 변수 또는 겍체가 참조하고 있는 데이터를 변경하지 못하게 보호하겠다는 의미입니다. 다만, 그 영역이 객체의 프로퍼티까지는 적용되지 않습니다. 재할당이 안된다는 것이 불변하다는 의미는 아닙니다.

## 8. Async/Await와 Promise의 차이

- 문법적인 차이: Promise는 체이닝을 통해 비동기 작업을 처리하는 반면, Async/Await는 비동기 코드를 동기적인 스타일로 작성할 수 있게 합니다.
- 에러 처리: Promise는 then()과 catch()를 사용하여 에러 처리를 합니다. 반면, Async/Await는 try-catch 문을 사용하여 에러를 처리합니다.
- 가독성: Async/Await는 비동기 코드를 동기적으로 작성할 수 있어 가독성이 좋습니다.

요약하면, Promise는 비동기 작업을 처리하는 객체이고, Async/Await는 Promise를 기반으로 한 간결한 비동기 코드 작성을 위한 문법입니다.

**async await를 호출하면 어떤걸 반환하나?**
async 함수를 호출하면 Promise 객체를 반환합니다. async 함수 내부에서 await 키워드를 사용하여 비동기 작업을 기다릴 때, 해당 작업은 Promise 객체로 감싸져 반환됩니다.

async 함수는 항상 Promise 객체를 반환하며, 그 결과 값은 Promise가 성공(resolve)할 때 해당 값으로 해결됩니다. 만약 async 함수에서 명시적으로 값을 반환하면, 해당 값은 Promise가 성공 상태가 될 때 반환됩니다. 반대로, async 함수에서 예외가 발생하면 Promise는 실패(reject) 상태가 됩니다.

따라서, async 함수를 호출하면 해당 함수가 비동기 작업을 수행하고 그 결과를 약속한(Promise로 감싼) 형태로 반환한다고 할 수 있습니다.

## 9. 데이터 10,000개를 가지고 무한 스크롤 구현시에 가장 중요하게 고려해야 할점은?

무한 스크롤 구현 시에는 성능, 네트워크 요청 최적화, 메모리 관리, 사용자 경험, 에러 처리 등을 중요하게 고려해야 합니다.

**무한스크롤을 사용하는 이유는??**

사용자 경험을 향상시키고 성능을 개선하기 위해서입니다.
사용자에게 보여줄 데이터가 많을때 이를 한꺼번에 보여주면 서버 과부하에 걸릴수 있습니다. 이를 해결하기위하여
페이지네이션이라던지, 무한스크롤을 이용하여 데이터를 잘라 사용자가 보고 있는 영역에만 일부의 데이터를 보여줌으로써 네트워크 낭비를 줄일수 있습니다.
