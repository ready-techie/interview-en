# Javascript asynchronous

1. **Explain the difference between synchronous and asynchronous functions.** 
    1. Synchronous functions are blocking while asynchronous functions are not.
    2. Synchronous functions can be run when front statements is completed.
    3. Asynchronous functions usually receive callback function as a parameter, move next line immediately.
    4. The callback is only **invoked** when the asynchronous **operation** is complete and the stack is empty.
    - trans

        동기, 비동기 함수의 차이점

        1. 동기함수는 Blocking 이 발생하지만, 비동기 함수는 그렇지 않다. 
        2. 동기함수는 앞에 있는 코드의 실행이 완료되어야 다음으로 넘어간다. 
        3. 비동기 함수는 보통 콜백 함수를 파라미터로 받고, 실행 즉시 다음 라인에 있는 코드로 넘어간다.
        4. 콜백은 비동기 작업이 완료되고 스택이 비었을때 실행된다. 

2. **What is Event Loop? What is the difference between call stack and task queue?**
    1. Monitor call stack and checks if there is any work to be done in the task queue, a callback fuction is dequeued and pushed onto the call stack to be executed.
    2.  The synchronous function, like console.log function is pushed call stack and executed immediately.
    3. The asynchronous webapi settimeout is poped immediately   in a call stack. and browser execute timmer. When finished timer, callback is enqueued to task queue. The event loop that was being monitered pushed the callback to the stack.
    - trans
        1. 이벤트 루프란 무엇인가요 ? Call Stack 과 Task Queue 의 차이점에 대해 설명해주세요.
            1. 동기함수는 call stack 에 즉시 추가, 비동기 콜백은 task queue 에 대기하고 있다가 event loop 가 stack 에 추가 
            2. 이벤트 루프란 callstack을 모니터링 하고 있다가 callstack 이 비어있고, task queue 에 callback 함수가 있다면, 함수는 queue 에서 제거 되고 실행을 위해 stack 에 push 된다. 
            3. console.log 같은 동기 함수는 스택에 바로 들어가고 실행된다. 
            4. 비동기 web api 인 settimeout 은 스택에 들어간 후 바로 지워지고, 대신 웹 **브라우저에서** 타이머를 실행시킨다. 타이머가 끝나면, callback 을 task queue 에 추가하고, 모니터링 하고있던event loop가  callback 을 stack 에 push 해서 실행한다. 

3. **How can javascript asynchronous programming be done ?** 
    1. There is the way using callback, promise and async/await.
    - trans
        1. javascript 비동기 프로그래밍 할 수 있는 방법은 ? 
            1. callback, promise, async/await 

4. **What are the pros and cons of using Promise instead of callbacks?**
    1. pros 
        1. Promise can do avoid callback hell which can be unreadable.
        2. Using `then()` , makes it easy to write **sequential** asynchronous code that is readable. 
        3. Using  `Promise.all()`, makes it easy to write paralle asynchronous code 
    2. cons 
        1. In older browser where ES2015 is not supported, you need to complied with Babel.
    - trans
        1. 콜백대신 프로미스를 사용하는 것의 장점과 단점은? 
            1. 장점
                1. 가독성 떨어지는 콜백 지옥에서의 탈출
                2. .then() 을 사용하여 **순차적인 비동기 작업**을 **가독성 있게** 작성할 수 있다. 
                3. promise.all() 을 사용해서 **병렬로** 실행되는 비동기 작업을 쉽게 작성 할 수 있다.
            2.  단점
                1. ES2015 를 지원하지 않는 구형 브라우저에서는 사용할 수 없으며 Babel 을 통한 컴파일이 필요하다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/009a79f0-fe5e-4769-b2e9-3b856341bcd3/1_4lHHyfEhVB0LnQ3HlhSs8g.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/009a79f0-fe5e-4769-b2e9-3b856341bcd3/1_4lHHyfEhVB0LnQ3HlhSs8g.png)

참고 : [https://blog.rhostem.com/posts/2020-04-13-fe-interview-handbook-js-2](https://blog.rhostem.com/posts/2020-04-13-fe-interview-handbook-js-2)

---

- 오픽 스피킹
- youtube interview
- 단어와 단어 사이에 갭이 많았습니다.
- break point 가 많아요
- practice speak english
- missing grammer point
