### Javascript is a single threaded language. This means it has one call stack and one memory heap. If javascript is single threaded, how is it asynchronous?

Javascript engine (V8, Spidermonkey, JavaScriptCore, etc...) has Web APIs like `setTimeout` that are able to handle tasks in the background. The call stack recognizes functions of the Web API and hands them off to be handled by the browser. Once those tasks are finished by the browser, they return and are pushed onto the stack as a callback.

➡️ V8은 단일 호출 스택(Single Call Stack)을 사용(자바스크립트가 싱글 쓰레드), 브라우저와 Node에서 XMLHttpRequest, setTimeout과 같이 비동기 호출을 하는 메서드는 모두 자바스크립트 엔진 밖의 영역에 정의되어 있다. 그래서 동시성(여러 개의 쓰레드가 번갈아가면서 실행)을 만족시켜서 비동기가 가능하다. 결국 자바스크립트를 구동하는 엔진은 싱글 쓰레드가 맞고, 그 외부인 구동 환경(브라우저, Node)이 멀티 쓰레드기 때문에 비동기 처리가 가능하게 되는 것이다.

(In short, although js is a single threaded-language, it can be asynchronous because the outer environment like browser or Node is multi-threaded.)

### Ref

- [https://dev.to/steelvoltage/if-javascript-is-single-threaded-how-is-it-asynchronous-56gd](https://dev.to/steelvoltage/if-javascript-is-single-threaded-how-is-it-asynchronous-56gd)
