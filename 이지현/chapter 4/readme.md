# 4-2. 제어권

- 호출 시점
- **인자**
- **this**

<br>

# 4-2-2. 인자

## map 메서드

**[코드]**

```js
const newArr = [10, 20, 30].map(function (currentValue, index) {
  console.log(currentValue, index);
  return currentValue + 5;
});

console.log(newArr);
```

**[결과]**

```js
10 0
20 1
30 2
[ 15, 25, 35 ]
```

<br>

## map 메서드 구조

![map구조](https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/7c84d056-ae3c-4b3b-975c-0af3a82e7a8c)


- 첫 번째 인자 - `callbackfn` (콜백 함수)
  - value: 배열의 요소 값
  - index: 배열의 현재 요소의 인덱스
  - array: map 을 호출한 배열 자체
 
- 두 번째 인자 - `thisArg` (this가 참조할 객체)
  - 생략 가능 (전역객체 바인딩)

<br>

> 배열의 모든 요소들을 처음부터 끝까지 하나씩 꺼내어 콜백 함수를 반복 호출
> <br> 콜백 함수의 실행 결과들을 모아 새로운 배열 생성

<br>

## 인자의 순서를 임의로 바꿈

**[코드]**

```js
const newArr = [10, 20, 30].map(function (index, currentValue) {
  console.log(currentValue, index);
  return currentValue + 5;
});

console.log(newArr);
```

**[결과]**

```js
0 10
1 20
2 30
[ 5, 6, 7 ]
```

<br>

> 이름에 상관없이 **순서**가 중요
> <br> 메서드 규칙에 콜백 함수의 인자로 넘어올 값, 순서 포함

<br>

### [이름에 상관없이 순서가 중요]

```js
const newArr = [10, 20, 30].map(function (hello, leejh) {
  console.log(hello, leejh);
  return hello + 5;
});

console.log(newArr);
```

<br>

### [메서드 규칙에 콜백 함수의 인자로 넘어올 값, 순서 포함]

![reduce](https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/4d704aaf-371b-4fc1-9f27-2dcb923a5a78)


<br>

# 4-2-3. this

기본적으로 this 가 전역객체 참조
<br> 콜백 함수에 별도로 this 지정 가능

<br>

## map 직접 구현

**[코드]**

```js
Array.prototype.map = function (callback, thisArg) {
  let mappedArr = [];
  for (let i = 0; i < this.length; i++) {
    let mappedValue = callback.call(thisArg || window, this[i], i, this);
    mappedArr[i] = mappedValue;
  }
  return mappedArr;
};
```

<br>

### map 메서드 - thisArg 지정 X

**[코드]**

```js
const newArr = [10, 20, 30].map(function (currentValue, index) {
  console.log(this);
});
```

**[결과]**

<img src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/c2523ef9-8efa-49e6-b3ac-47a78ea5107e" alt="결과" width="300" />

<br>

### map 메서드 - thisArg 활용

**[코드]**

```js
const ArgTest = {
  greet: function () {
    return 'Hello, ';
  },
};

const ArgTestResult = ['HTML', 'CSS', 'JavaScript'].map(function (name) {
  return this.greet() + name;
}, ArgTest);

console.log(ArgTestResult);
```

**[결과]**

```js
['Hello, HTML', 'Hello, CSS', 'Hello, JavaScript'];
```
