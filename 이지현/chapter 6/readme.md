# 6-2-1. 메서드 오버라이드

## 클래스 기반 언어(ex. java) 에서 오버라이딩이란?

상속 관계에 있는 클래스에서 부모 클래스의 메서드를 자식 클래스에서 재정의

<img width="300" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/093d44b9-84eb-4467-95d7-380e1bac2d47" />

<br>

## 자바스크립트에서 오버라이딩이란?

자바스크립트? ➩ 프로토타입 언어

### 프로토타입 기반 언어

> 프로토타입 기반 언어는 클래스 기반 언어에서 상속을 사용하는 것과는 다르게, <br>
> 객체를 원형(프로토타입)으로 하는 복제 과정을 통해 객체의 동작 방식을 재사용 <br> _[출처] : 위키백과_

<br>

## 메서드 오버라이드란?

인스턴스가 동일한 이름의 프로퍼티 또는 메서드를 가진다면?

#### [소스 코드]

```js
var Person = function (name) {
  this.name = name;
};

// 동일한 이름 1
Person.prototype.getName = function () {
  return this.name;
};

var myName = new Person('지현');

// 동일한 이름 2
myName.getName = function () {
  return '안녕 ' + this.name;
};

console.log(myName.getName());
```

#### [출력 결과]

```bash
안녕 지현
```

<br>

➩ myName 객체에 있는 `getName` 메서드 호출

<br>

### 메서드 오버라이드 발생

원본이 그대로 있는 상태에서 다른 대상을 그 위에 얹었다 (덮어씌웠다)

<br>

## 메서드 오버라이드 동작

### getName 메서드 찾는 방식

1. 가장 가까운 대상 (자신 프로퍼티) 검색
2. 그 다음으로 가까운 __ proto __ 검색

<br>

➩ __ proto __ 는 검색 순서에 밀려 호출되지 않음

<br>

### __ proto __ 접근 방법

메서드 오버라이딩 상황에서 prototype 메서드 접근 방법

#### [첫번째 방법 - 소스코드]

```js
console.log(myName.__proto__.getName());
```

#### [첫번째 방법 - 실행결과]

```bash
undefined
```

➩ this 가 prototype 객체를 가리키는데 name 프로퍼티가 없음

<br>

#### [두번째 방법 - 소스코드]

```js
console.log(myName.__proto__.getName.call(myName));
```

#### [두번째 방법 - 실행결과]

```bash
지현
```

➩ call 이나 apply 를 사용해서 this 를 바꿔줌
