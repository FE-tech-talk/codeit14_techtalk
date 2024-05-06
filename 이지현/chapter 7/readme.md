# 7-4. ES6의 클래스 및 클래스 상속

> JavaScript 자바스크립트 = **프로토타입** 기반 언어 <br>
> ➞ `class` 와 `상속`의 개념이 존재 X

But, **ES6** 이후 `class` 문법 추가

<br>

## 7-4-1. ES5, ES6 클래스 문법 비교

### [ES5 코드]

(1) 생성자 함수 선언 <br>
(2) 정적 메서드 (인스턴스X, 생성자 함수 자체에서 호출) <br>
(3) 인스턴스 메서드가 생성자 함수 프로토타입에 추가 (인스턴스에서 접근)

```js
// (1)
var ES5 = function (name) {
  this.name = name;
};

// (2)
ES5.staticMethod = function () {
  return this.name + ' staticMethod';
};

// (3)
ES5.prototype.method = function () {
  return this.name + ' method';
};

// ES5 라는 생성자 함수를 호출해 es5Instance 인스턴스 생성
var es5Instance = new ES5('es5');
console.log(ES5.staticMethod); // ES5 staticMethod
console.log(es5Instance.method); // es5 method
```

### [ES6 코드]

(1) `class` 사용하여 클래스 선언, `constructor` 사용하여 메서드 정의 <br>
(2) 정적 메서드 `static` 사용하여 클래스 자체에서 호출 가능 <br>
(3) 클래스 프로토타입에 추가되어, 클래스 인스턴스에서 호출 <br>

```js
// (1)
var ES6 = class {
  constructor(name) {
    this.name = name;
  }

  // (2)
  static staticMethod() {
    return this.name + ' staticMethod';
  }

  // (3)
  method() {
    return this.name + ' method';
  }
};

// ES5 라는 생성자 함수를 호출해 es5Instance 인스턴스 생성
var es6Instance = new ES6('es6');
console.log(ES6.staticMethod()); // ES6 staticMethod
console.log(es6Instance.method()); // es6 method
```

<br>

## 7-4-2. ES6 클래스 상속

### [ES6 코드]

(1) Rectangle 클래스 선언, `constructor` 메서드 정의 <br>
(2) 클래스 프로토타입에 추가되어, 클래스 인스턴스에서 호출 <br>
(3) `extends` 사용하여, Rectangle 를 상속하는 클래스 Square 선언 <br>
(4) `super` 사용하여, 부모 메서드 호출

```js
// (1)
var Rectangle = class {
  constructor(width, height) {
    this.width = width;
    this.height = height;
  }

  // (2)
  getArea() {
    return this.width * this.height;
  }
};

// (3)
var Square = class extends Rectangle {
  constructor(width) {
    super(width, width);
  }

  // (4)
  getArea() {
    console.log('size: ', super.getArea());
  }
};
```
