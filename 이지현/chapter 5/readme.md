# 5-3-3. 부분 적용 함수

## 부분 적용 함수란?

> `n` 개의 인자를 받는 함수에 미리 `m`개의 인자만 넘겨 기억시켰다가, <br>
> 나중에 `(n - m)`개의 인자를 넘기면, 비로소 원래 함수의 실행 결과를 얻을 수 있겠끔 하는 함수

<br>

### bind 메서드를 활용한 부분 적용 함수

함수 인자 5개 미리 적용, 추후 나머지 인자 전달

(+ `bind` 의 첫 번째 인자로 `this` 가 들어가야 되는데 바인딩 할 객체가 없어 `null` 로)

```js
var add = function () {
  var result = 0;
  for (var i = 0; i < arguments.length; i++) {
    result += arguments[i];
  }
  return result;
};

var addPartial = add.bind(null, 1, 2, 3, 4, 5);
console.log(addPartial(7, 6, 8, 9, 10)); // 55
```

<br>

## 부분 적용 함수 구현 (1)

**partial**: 호출 시 익명 함수를 반환

**partialArgs**: 함수를 제외한 처음 전달된 인자를 배열로

**restArgs**: 익명 함수가 호출될 때 전달된 인자를 배열로



```js
// 직접 구현한 부분 적용 함수
var partial = function () {
  var originalPartialArgs = arguments;
  var func = originalPartialArgs[0];

  if (typeof func !== 'function') {
    throw new Error('첫 번째 인자가 함수가 아닙니다.');
  }

  // 익명 함수
  return function () {
    // 처음 전달된 인자에 함수를 제외한 나머지로 배열 만듦
    var partialArgs = Array.prototype.slice.call(originalPartialArgs, 1);
    // 익명 함수가 호출될 때 전달된 인자로 배열 만듦
    var restArgs = Array.prototype.slice.call(arguments);
    // 인자를 하나의 배열로 만들어 func 인자로 보냄
    return func.apply(this, partialArgs.concat(restArgs));
  };
};

// 인자의 값을 모두 더하는 add 함수
var add = function () {
  var result = 0;
  for (var i = 0; i < arguments.length; i++) {
    result += arguments[i];
  }
  return result;
};

var addPartial = partial(add, 1, 2, 3, 4, 5);
console.log(addPartial(6, 7, 8, 9, 10)); // 55
```

<br>

## 부분 적용 함수 구현 (2)

비어 있는 부분에 하나씩 넣기

```js
// _ 를 공백문자로
var _ = 'EMPTY_SPACE';

var partial2 = function () {
  var originalPartialArgs = arguments;
  var func = originalPartialArgs[0];

  if (typeof func !== 'function') {
    throw new Error('첫 번째 인자가 함수가 아닙니다.');
  }

  return function () {
    var partialArgs = Array.prototype.slice.call(originalPartialArgs, 1);
    var restArgs = Array.prototype.slice.call(arguments);

    // 비어있으면 restArgs 인자 차례대로 하나씩 넣기
    for (var i = 0; i < partialArgs.length; i++) {
      if (partialArgs[i] === _) {
        partialArgs[i] = restArgs.shift();
      }
    }

    return func.apply(this, partialArgs.concat(restArgs));
  };
};

var add = function () {
  var result = 0;
  for (var i = 0; i < arguments.length; i++) {
    result += arguments[i];
  }
  return result;
};

var addPartial = partial2(add, 1, 2, _, 4, 5, _, _, 8, 9);
console.log(addPartial(3, 6, 7, 10)); // 55
```

<br>

## 부분 적용 함수 - 디바운스

### 디바운스란?

> 짧은 시간 동안 동일한 이벤트가 많이 발생할 경우 이를 전부 처리하지 않고 <br>
> 처음 또는 마지막에 발생한 이벤트에 대해 한 번만 처리하는 것 <br>

⇒ 프론트엔드 성능 최적화에 큰 도움을 주는 기능 중 하나 <br>
(`scroll`, `wheel`, `mousemove`, `resize` 등에 적용하기 좋음)

<br>

### 디바운스

최초 `event`가 발생하면 `timeout` 의 대기열에 `wait` 시간 뒤 `func`를 실행

But! `wait` 시간이 경과하기 이전에 다시 동일한` event` 가 발생하면, <br> `clearTimeout` 으로 무조건 대기큐를 초기화하게 하여 다시 새로운 대기열을 등록

```js
var debounce = function (eventName, func, wait) {
  var timeoutId = null;

  return function (event) {
    var self = this;

    console.log(eventName, 'event 발생');

    clearTimeout(timeoutId);
    timeoutId = setTimeout(func.bind(self, event), wait);
  };
};

var moveHandler = function (e) {
  console.log('move event 처리');
};

var wheelHandler = function (e) {
  console.log('wheel event 처리');
};

document.body.addEventListener('mousemove', debounce('move', moveHandler, 500));
document.body.addEventListener(
  'mousewheel',
  debounce('wheel', wheelHandler, 700)
);
```

#### [디바운스 결과]

![화면-기록-2024-04-23-오전-2 52 56](https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/5d5b2a05-8351-49d9-951f-0679758f5e8e)
