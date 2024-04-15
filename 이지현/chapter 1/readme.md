# 1-5. 자바스크립트 불변 객체

## 사전 지식
자바스크립트에서 **기본형 데이터**는 **불변값** 이고, **참조형 데이터**는 **가변값** 이다. 

<br />

# ☘️ 1. 불변 객체란?

**불변 객체**란? **변하지 않는 객체** 이다.

## 1-1. 불변 객체가 필요한 경우

원본 객체가 변하지 말아야 할 상황에 **불변 객체**가 필요하다.

### [불변 객체 필요한 상황]
<img width="500" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/2d821290-8f1d-45b9-9082-7733ae4327eb" />

### [결론]
위에 코드처럼 객체의 **가변성** 에 따른 문제를 해결하기 위해 원본 객체의 값이 변하지 않도록 
**불변 객체**를 만들어야 한다. 

<br />


# ☘️ 2. 불변 객체 만들기
## 2-1. 새 객체를 만들어 반환
새로운 객체를 만들고, 원복 객체 내부의 값을 **복사** 하고 반환한다.

<img width="500" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/7ff51f68-a58e-427d-9765-89bcca4b6722" />

### [문제점 - 하드코딩]
객체의 정보가 많거나, 변경해야 할 정보가 많을 경우 번거로워진다.

<br />

## 2-2. 얕은 복사
반복문을 사용해 **모든 프로퍼티(속성)를 복사** 하여 새 객체를 반환한다.

<img width="500" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/b175d263-bf6d-4d81-9255-39b1dd09c036" />

### [문제점 - 중첩된 객체 복사]
바로 아래 단계 값만 복사되어 중첩된 객체는 복사를 못 한다.

<img width="500" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/b6f1b67a-2f00-4684-a819-ea53efc2e956" />

### [결론]
중첩된 객체 프로퍼티의 데이터도 불변 객체로 만들어야 한다.

<br />

## 2-3. 깊은 복사
깊은 복사를 구현하기 위해 2가지 방법이 있다.
1. 재귀적인 복사
2. JSON.stringify 

### 2-3-1. 재귀적인 복사
깊은 복사 함수를 **재귀적으로 호출** 하여, 내부에 존재하는 모든 단계의 객체들을 복사한다.

<img width="500" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/01ead4db-9aa7-4f45-92f5-a49b77242c0d" />

### 2-3-2. JSON.stringify 
객체를 **문자열** 로 변환 후, 다시 **JSON 객체** 로 변경한다.
이 방법이 실제로 업무에서 많이 사용한다고 한다.

<img width="500" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/d5399f2a-6b14-409d-8aa0-6a5bbac81639" />




