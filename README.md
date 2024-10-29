# interview_questions

### Web
- 브라우저 렌더링 원리를 설명하세요.
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
  

### Javascript
- 이벤트 루프에 대해서 알고 있는대로 말해보세요. <br/>
  자바스크립트는 싱글스레드로 동작해 한 번에 하나의 작업만 처리할 수 있지만, 이벤트 루프를 통해 비동기 작업을 효율적으로 관리합니다.  <br/>
  이벤트 루프의 작동 방식은 코드가 실행되면서 호출 스택에 함수들이 쌓이고 실행되며, 비동기 작업(ex. SetTimeout, HTTP 요청 등)은 Web APIs가 처리합니다.  <br/>
  비동기 작업이 완료되면 해당 콜백은 태스크 큐로 이동하고, 호출 스택이 비면 이벤트 루프가 태스크 큐의 작업을 호출 스택으로 이동시켜 실행합니다.  <br/>
  이러한 방식으로 비동기 작업을 수행해서 자바스크립트가 중단되지 않고 응답성을 유지할 수 있습니다. 

  [참고 자료]
  - [이벤트 루프와 매크로태스크, 마이크로태스크](https://ko.javascript.info/event-loop) 

  - Javascript 는 싱글스레드 언어인데 어떻게 비동기 통신이 가능할까요? <br/>
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
### TypeScript
### React
### Etc
