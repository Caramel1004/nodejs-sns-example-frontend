# nodejs-sns-example-frontend
-리엑트 템플릿-
프런트엔드: react.js
백엔드: node.js

- fetch api사용하여 데이터를 요청하도록 합니다.
```javascript
// Example POST method implementation:
async function postData(url = "", data = {}) {
  // Default options are marked with *
  const response = await fetch(url, {
    method: "POST", // *GET, POST, PUT, DELETE, etc.
    mode: "cors", // no-cors, *cors, same-origin
    cache: "no-cache", // *default, no-cache, reload, force-cache, only-if-cached
    credentials: "same-origin", // include, *same-origin, omit
    headers: {
      "Content-Type": "application/json",
      // 'Content-Type': 'application/x-www-form-urlencoded',
    },
    redirect: "follow", // manual, *follow, error
    referrerPolicy: "no-referrer", // no-referrer, *no-referrer-when-downgrade, origin, origin-when-cross-origin, same-origin, strict-origin, strict-origin-when-cross-origin, unsafe-url
    body: JSON.stringify(data), // body data type must match "Content-Type" header
  });
  return response.json(); // parses JSON response into native JavaScript objects
}

postData("https://example.com/answer", { answer: 42 }).then((data) => {
  console.log(data); // JSON data parsed by `data.json()` call
});
```

# React &&연산자
- JSX 안에는 중괄호를 이용해서 표현식을 포함 할 수 있습니다. 그 안에 JavaScript의 논리 연산자 &&를 사용하면 쉽게 엘리먼트를 조건부로 넣을 수 있습니다.
JavaScript에서 true && expression은 항상 expression으로 평가되고 false && expression은 항상 false로 평가됩니다.
따라서 && 뒤의 엘리먼트는 조건이 true일때 출력이 됩니다. 조건이 false라면 React는 무시하고 건너뜁니다.

-&&연산자 앞부분은 조건식 &&연산자 뒷부분은 expression
```javascript
import React from 'react';

import './Paginator.css';

const paginator = props => (
  <div className="paginator">
    {props.children}
    <div className="paginator__controls">
      {(props.currentPage > 1) && (
        <button className="paginator__control" onClick={props.onPrevious}>
          Previous
        </button>
      )
      }
      {(props.currentPage === 1 || props.currentPage < props.lastPage) && (
        <button className="paginator__control" onClick={props.onNext}>
          Next
        </button>
      )
      }
    </div>
  </div>
);

export default paginator;
```

# 오류
- 포트 충돌 오류

```t
Something is already running on port 3000. Probably:
```
해결: 
해당 프로세스를 종료하는 방법을 검색 할 수 있습니다.

Linux / Mac OS 검색의 경우 터미널에서 (sudo) 실행 :

$ lsof -i tcp:3000
$ kill -9 PID
Windows :

netstat -ano | findstr :3000
tskill typeyourPIDhere 
git bash에서 taskkill 에 대한 tskill 변경