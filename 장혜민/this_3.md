# 함수로서 호출할 때 그 함수 내부에서의 this

## 1. 함수 내부에서의 this
어떤 함수를 함수로서 호출할 경우에는 this가 지정되지 않고, Window 객체를 가리킨다.
```js
var func = function() {
    console.log(this);  //(1) Window{...}
    var func2 = function () {
        console.log(this);  //(2) Window{...}
    };
};
func();
```

## 2. 메서드의 내부함수에서의 this
outer 메서드 내부에 있는 함수<sup>innerFunc</sup>를 **함수**로서 호출하는 경우 this가 지정되지 않고, Window 객체를 가리킨다. 같은 함수를 **메소드**로서 호출하는 경우 this에 마지막 점 앞의 객체인 obj2가 바인딩된다.

```js
var obj1 = {
    outer: function () {
        console.log(this);  //(1) { outer: ƒ }
        var innerFunc = function () {
            console.log(this);  //(2) Window{...}   (3) { innerMethod: ƒ }
        }
        innerFunc();

        var obj2 = {
            innerMethod: innerFunc
        };
        obj2.innerMethod();
    }
};
obj1.outer();
```

> this 바인딩에 관해서는 함수를 샐행하는 당시의 주변 환경은 중요하지 않고, 오직 해당 함수를 호출하는 구문 앞에 점 또는 대괄호 표기가 있는지 없는지가 관건이다.

## 메서드의 내부 함수에서의 this를 우회하는 방법(ES5)
변수 활용하기!
```js
var obj1 = {
    outer: function () {
        console.log(this);  //(1) { outer: ƒ }
        var innerFunc1 = function () {
            console.log(this);  //(2) Window{...}
        }
        innerFunc1();

        var self = this;
        var innerFunc2 = function () {
            console.log(self);  //(3) { outer: ƒ }
        }
    }
};
```
## this를 바인딩하지 않는 함수(ES6)
화살표 함수<sup>arrow function</sup>는 실행 컨텍스트를 생성할 때 this 바인딩하지 않아, 상위 스코프의 this를 그대로 활용할 수 있다.
```js
var obj = {
    outer: function () {
        console.log(this);  //(1) { outer: ƒ }
        var innerFunc = () => {
            console.log(this);  //(2) { outer: ƒ }
        };
        innerFunc();
    }
};
obj.outer();
```