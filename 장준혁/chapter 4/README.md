# 콜백 함수란?

콜백 함수는 다른 코드의 인자로 넘겨주는 함수입니다.

예제

```javascript
function hello(param) {
  console.log("hello");
  param();
}

function world() {
  console.log("world!");
}

hello(world);
```

예제와 같이 함수의 인자로 넘겨주어 순차적으로 실행시킬 수 있습니다.

# 제어권 호출 시점

setInterval 예제

```javascript
var count = 0;
var timer = setInterval(function () {
  console.log(count);
  if (++count > 4) clearInterval(timer);
}, 300);
```

setInterval의 구조는 var a = scope.setInterval(func, delay[, param1, param2, ...]); 입니다.

scope에는 Window객체 또는 Worker의 인스턴스가 들어올 수 있습니다.
일반적인 브라우저 환경에서는 window를 생략해서 함수처럼 사용합니다.
func는 함수, delay는 매 ms마다 func를 실행시키며 나머지(param들)은 func 함수를 실행할 때 매개변수로 전달할 인자입니다.

예제 코드를 실행시키면 setInterval함수가 동작하여 0, 1, 2, 3, 4를 0.3초 간격으로 출력한 후 종료됩니다.

더 쉽게 코드를 수정하면 다음과 같은 예제가 됩니다.

```javascript
var count = 0;
var countFunc = function () {
  console.log(count);
  if (++count > 4) clearInterval(timer);
};
var timer = setInterval(countFunc, 300);
```

코드 실행 방식과 제어권은 다음과 같게 됩니다.

| 코드                        | 호출 주체   | 제어권      |
| --------------------------- | ----------- | ----------- |
| setInterval(countFunc, 300) | setInterval | setInterval |
| countFunc()                 | 사용자      | 사용자      |

setInterval은 countFunc의 제어권을 넘겨받아 익명함수를 실행시킵니다.

콜백 함수의 제어권을 넘겨받은 코드는 콜백 함수 호출 시점에 대한 제어권을 가지게 됩니다.
