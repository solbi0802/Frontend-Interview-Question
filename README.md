# interview_questions

### Web
- 브라우저 렌더링 원리를 설명하세요.
   ![image](https://github.com/user-attachments/assets/01d43587-bd6d-4244-8b5d-c4dd3b0c93a0)
  - DNS 조회
   IP주소 찾기
  - TCP 핸드 셰이크
  -  
   - DOM트리와 CSSOM 트리 생성
   - 렌더
   - 스타일
   - 레이아웃
   - 페인트

참고 자료
- [브라우저 동작원리](https://poiemaweb.com/js-browser)
- [웹페이지를 표시한다는 것: 브라우저는 어떻게 동작하는가](https://developer.mozilla.org/ko/docs/Web/Performance/How_browsers_work)
- [브라우저는 어떻게 동작하는가](https://d2.naver.com/helloworld/59361)
- [프론트엔드 개발자라면 알고 있어야 할 브라우저의 동작 과정](https://yozm.wishket.com/magazine/detail/1338/)
  

### Javascript
- 이벤트 루트에 대해서 알고 있는대로 말해보세요
- Javascript 는 싱글쓰레드 언어인데 어떻게 비동기 통신이 가능할까요? <br/>
 JavaScript는 싱글쓰레드 언어이지만 JavaScript 엔진의 멀티스레드 구조와 Web APis를 통해 가능합니다.
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

### TypeScript
### React
### Etc
