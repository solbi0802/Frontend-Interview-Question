# Frontend-Interview-Question

>  면접에서 자주 물어보는 질문들을 정리해서 공부하고 있어요.

## 👩‍💻 Web
### 브라우저 렌더링 원리를 설명하세요.
   ![image](https://github.com/user-attachments/assets/01d43587-bd6d-4244-8b5d-c4dd3b0c93a0)
  1. DNS 조회: IP주소 찾기
  2. TCP 핸드 셰이크
  3. Parsing: 브라우저가 코드를 이해하고 사용할 수 있는 구조로 변환함(HTML, CSS 파싱)
  4. RenderTree 형성: DOM + CSSOM을 결합해서 렌더 트리 형성
  5. Lsyout: 렌더 트리에서 계산되지 않은 크기, 위치, 레이어 순서와 같은 정보 계산 후 좌표에 나타냄
  6. Paint: UI기반의 구성 요소들에게 색을 입히고, 레이어 위치 결정
     
  - 요약
  1. HTML로부터 DOM 트리를, CSS로부터 CSSOM트리를 빌드
  2. DOM, CSOM을 결합해서 렌더 트리 형성
  3. 렌더 트리에서 레이아웃을 실행하여 각 노드의 기하학적 형태 계산
  4. 개별 노드를 화면에 페인트(그리기)
     
[참고 자료]
- [브라우저 동작원리](https://poiemaweb.com/js-browser)
- [웹페이지를 표시한다는 것: 브라우저는 어떻게 동작하는가](https://developer.mozilla.org/ko/docs/Web/Performance/How_browsers_work)
- [프론트엔드 개발자라면 알고 있어야 할 브라우저의 동작 과정](https://yozm.wishket.com/magazine/detail/1338/)

### reflow와 repaint의 차이점에 대해서 설명해주세요.
reflow와 repaint는 브라우저가 화면에 렌더링할 때 발생하는 두 가지 과정으로, DOM 변화로 인해 발생합니다.  <br/>
- reflow: 레이아웃이 변경될 때 마다 발생합니다. 요소의 크기, 위치 or 화면 배치가 변경되면 브라우저는 페이지의 전체 레이아웃을 다시 계산합니다. <br/>
          이 과정은 모든 자식 요소와 관련된 부모 요소까지 영향을 주기 때문에 비용이 많이 드는 작업입니다.  <br/>
          예를 들어, DOM요소를 추가하거나 크기를 변경할 때 발생합니다.  <br/>
          reflow는 성능 비용이 높습니다.  
- repaint: 요소의 스타일이 변경되어 시각적 업데이트가 필요할 때 발생합니다. <br/>
           색상, 배경, 그림자와 같은 스타일 속성의 변화는 레이아웃을 변경하지 않으므로 repaint만 발생합니다. <br/>
           repaint는 reflow보다 비용이 적습니다.
reflow는 레이아웃을 다시 계산하는 과정이고 repaint는 그 계산 결과를 화면에 다시 그리는 과정이라고 할 수 있습니다.
- 최적화 방법
   1) reflow를 유발하는 CSS 속성 사용 최소화
      - DOM 요소를 수정할 때 Batching을 사용합니다. 예를 들어, 여러 스타일 변경은 하나의 class에 적용한 후 추가합니다.
      - DocumentFragment를 사용해 DOM 업데이트를 한 번에 처리합니다.
   2) CSS 최적화
      - 복잡한 CSS 셀렉터를 피하고, flat DOM 구조 유지합니다.
      - 애니메이션을 GPU가 처리하는 속성(transform, opacity)에서 실행합니다.
   3) 읽기, 쓰기 분리: 레이아웃 정보(ex. offsetHeight, offsetWidth)를 읽은 후 DOM을 수정하면 Reflow가 발생하므로, 한 번에 작업합니다.
   4) 이미지와 리소스 최적화: 적절한 이미지 크기와 포맷을 사용하고, lazy loading을 활용합니다.
   5) 불필요한 작업 줄이기
      - will-change 속성을 사용해 성능을 향상시킬 애니메이션만 미리 예약합니다.
      - 스크롤이나 리사이즈 이벤트에 Debouncing/Throttling을 적용합니다.
       
## 👩‍💻Javascript
### 이벤트 루프에 대해서 알고 있는대로 말해보세요. <br/>
  자바스크립트는 싱글스레드로 동작해 한 번에 하나의 작업만 처리할 수 있지만, 이벤트 루프를 통해 비동기 작업을 효율적으로 관리합니다.  <br/>
  이벤트 루프의 작동 방식은 코드가 실행되면서 호출 스택에 함수들이 쌓이고 실행되며, 비동기 작업(ex. SetTimeout, HTTP 요청 등)은 Web APIs가 처리합니다.  <br/>
  비동기 작업이 완료되면 해당 콜백은 태스크 큐로 이동하고, 호출 스택이 비면 이벤트 루프가 태스크 큐의 작업을 호출 스택으로 이동시켜 실행합니다.  <br/>
  이러한 방식으로 비동기 작업을 수행해서 자바스크립트가 중단되지 않고 응답성을 유지할 수 있습니다. 

 ### Javascript 는 싱글스레드 언어인데 어떻게 비동기 통신이 가능할까요? <br/>
   ```
   JavaScript는 싱글스레드 언어이지만 JavaScript 엔진의 멀티스레드 구조와 Web APis를 통해 가능합니다.
   JavaScript자체는 싱글스레드이지만, JavaScript엔진(V8 등)은 멀티스레드로 동작합니다.
   브라우저나 Node.js 같은 런타임 환경은 Web APIs를 통해 멀티스레드 작업을 지원합니다.

   - Web APIs와 백그라운드 스레드
    - 타이머(setTimeout), HTTP 요청(fetch), 이벤트 리스너 등은 Web APIs로 제공됩니다.
    - 이러한 작업들은 백그라운드 스레드에서 처리되어 메인 스레드와 분리됩니다.
 
   - 이벤트 루프(Event Loop)와 태스크 큐(Task Queue)
    - 백그라운드 작업이 완료되면, 해당 콜백 함수는 태스크 큐에 추가됩니다.
    - 이벤트 루프는 메인 스레드가 비어 있을 때 태스크 큐에서 작업을 가져와 실행합니다.
    
   - 결론 
    - JavaScript자체는 싱글스레드지만, JavaScript 엔진과 런타임 환경의 멀티스레드 기능으로 비동기 처리가 가능합니다.
    - 엔진과 환경이 제공하는 멀티스레드 기능을 활용하여 비동기 통신을 구현합니다.
   ```
### 실행 컨텍스트에 대해서 설명해주세요.
실행 컨텍스트는 자바스크립트에서 코드가 실행되는 환경을 말합니다. 
자바스크립트 엔진은 코드를 실행할 때 전역 컨텍스트와 함수 컨텍스트를 생성하며, 이를 통해 변수와 함수의 범위 및 실행 순서를 관리합니다.
실행 컨텍스트는 생성 단계와 실행 단계 두 가지 단계로 나뉩니다.

1. 전역 실행 컨텍스트
   - 프로그램 시작 시 가장 먼저 생성됩니다.
   - 전역 스코프에 선언된 변수와 함수가 포함되며, 자바스크립트 프로그램이 종료될 때까지 유지됩니다.
   - 브라우저 환경에서는 window 객체가 전역 객체로 작동합니다.
2. 함수 실행 컨텍스트
   - 함수가 호출될 때마다 새롭게 생성됩니다.
   - 함수 내부의 변수, 매개변수, 그리고 선언된 함수들이 포함됩니다.
   - 함수 호출이 끝나면 해당 컨텍스트는 스택에서 제거됩니다.
    

#### 실행 컨텍스트의 구성 요소
- 변수 객체(Variable Object)
  변수, 함수 선언 및 arguments 객체를 포함하며, 생성 단계에서 초기화됩니다.
- 스코프 체인(Scope Chain)
  현재 컨텍스트와 상위 컨텍스트를 연결하는 구조로, 변수를 검색할 때 사용됩니다.
- this 바인딩
  실행 컨텍스트가 참조하는 객체를 지정합니다. 전역 컨텍스트에서는 전역 객체를, 함수 컨텍스트에서는 호출 방식에 따라 바인딩됩니다.

#### 실행 컨텍스트의 동작 예시
 ```
 var globalVar = 'I am global';

function outer() {
  var outerVar = 'I am outer';
  function inner() {
    var innerVar = 'I am inner';
    console.log(globalVar, outerVar, innerVar);
  }
  inner();
}
outer();
 ```
 위 코드에서 실행 컨텍스트는 다음 순서로 생성됩니다.
 1. 전역 컨텍스트가 생성되어 globalVar가 등록됩니다.
 2. outer()가 호출되면서 함수 실행 컨텍스트가 생성되고 outerVar가 등록됩니다.
 3. inner() 호출 시 새로운 함수 컨텍스트가 생성되어 innerVar가 등록됩니다.
 4. console.log() 호출 시 변수는 스코프 체인을 따라 검색됩니다.

### 클로저에 대해서 설명해주세요.

## 👩‍💻 TypeScript
## 👩‍💻 React
## 👩‍💻 Etc
