# 3-2 call & apply 메서드
명시적으로 this 를 바인딩하는 방법
1. **call**
2. **apply**
3. bind

#### 명시적으로 this 를 바인딩?
함수 내에서 `this`가 특정 객체를 참조하도록 분명하게 지정


# ☘️ call 메서드
메서드의 호출 주체인 **함수를 즉시 실행**

## call 메서드 - 사용 방법
- **첫 번째 인자** - this 로 바인딩
	- **임의의 객체**를 this 로 지정
- 나머지 인자
	- 호출할 **함수의 매개변수**

```js
함수명.call(임의의 객체, 호출할 함수의 매개변수, ...)
```

## call 메서드 - 사용 전 1
#### [소스코드]
<img width="500" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/e9510cc0-501b-470e-9f39-51c84e8b2626">


#### [결과]
<img width="379" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/8a3f63fa-6077-4a84-8ac8-e74d07457251">


```js
Window{...} 1 2 3
```

## call 메서드 - 사용 예시 1
- call 메서드 사용
- 첫 번째 인자로 임의의 객체
#### [소스코드]
<img width="500" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/e2b24626-2308-471a-a09a-be36c12af771">

#### [결과]
<img width="236" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/a6e1ff33-816f-4186-9057-10c4b856efc3">


```js
{ x: 1 } 1 2 3
```

## call 메서드 - 사용 전 2
객체의 메서드
#### [소스코드]
<img width="550" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/7c0d73cc-39b5-4024-89ec-3685339b73c8">


#### [결과]
<img width="96" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/13906cdf-d744-49e0-a30d-5bb96f90daac">

```js
1 2 3
```

+) this 자체 출력
```js
{ a: 1, method: [Function: method] }
```

## call 메서드 - 사용 예시 2
- call 메서드 사용
- 첫 번째 인자로 임의의 객체
#### [소스코드]
<img width="550" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/ea116757-25a2-40f4-80e9-568d94674b97">


#### [결과]
<img width="105" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/8144a97c-0977-450f-b664-e1da25a235b2">

```js
4 2 3
```

# ☘️ apply 메서드
- **첫 번째 인자** - this 로 바인딩
	- **임의의 객체**를 this 로 지정
- 두 번째 인자
	- 호출할 **함수의 매개변수**를 **배열**로 받음

## apply 메서드 - 사용 예시

#### [소스코드]
<img width="600" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/b0a7906b-43d3-4db1-84ce-c39e8f2a8088">

#### [결과]
<img width="241" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/90f901f6-de0c-41ee-bfed-f65f5d2eb227">

```js
{ x: 1 } 1 2 3
4 2 3
```

# ☘️ call / apply 메서드의 활용
## 1. 유사 배열 객체에 배열 메서드 적용
객체에서는 배열의 메서드 사용 X
#### [소스코드]
<img width="600" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/9d1c0db6-b3d5-414c-8357-97778a846063">


#### [결과]
<img width="596" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/bab9e146-626d-4126-980c-2b7eef014de2">

```js
{ '0': 'a', '1': 'b', '2': 'c', '3': 'd', length: 4 }
[ 'a', 'b', 'c', 'd' ]
```

## 2. ES6 의 Array.from 메서드
#### [소스코드]
<img width="600" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/af1697ea-5115-49a3-8917-b8420ac034a5">

#### [결과]
<img width="595" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/f1f30cb2-970f-480a-b4a3-2afceb50ef91">

```js
{ '0': 'a', '1': 'b', '2': 'c', '3': 'd', length: 4 }
[ 'a', 'b', 'c', 'd' ]
```

## 3. 생성자 내부에서 다른 생성자 호출
#### [소스코드]
<img width="650" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/8d501aed-f921-4279-9f4d-e01f779ed674">

#### [결과]
<img width="697" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/a72c8755-54f6-4448-8dd8-40591a8349eb">


## 4. 여러 인수를 받는 메서드
#### [소스코드]
<img width="600" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/6f053b3e-6d7b-4709-9f41-418496e71dde">


#### [결과]
<img width="104" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/d26f6290-4c7e-4269-a708-486e8e51f06b">


## 3-1. ES6의 스프레드 연산자 활용
#### [소스코드]
<img width="550" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/a594b288-9614-4b9d-b15e-036f9fd69d76">


#### [결과]
<img width="108" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/56182846-f3a8-4ba3-8e3e-013a162dcfa1">

