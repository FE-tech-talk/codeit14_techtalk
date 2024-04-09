# 2-3-1 **environmentRecord**

## 1. 실행 컨텍스트
### 1-1. 실행 컨텍스트 정의

- 실행할 코드에 제공할 환경 정보들을 모아놓은 객체
- 콜 스택에 쌓아 올렸다가 가장 위에 쌓여있는 컨텍스트와 관련 있는 코드들을 실행
### 1-2. 실행 컨텍스트에 담기는 내용
- VariableEnvironment
	- 현재 컨텍스트 내의 식별자들에 대한 정보 + 외부 환경 정보
	- 최초 실행 시의 스냅샷으로 유지되어 변경 사항 반영 X
- **LexicalEnvironment**
    - VariableEnvironment 를 복사하여 생성
    - 주로 사용하여, 변경 사항이 실시간으로 반영
- ThisBinding

## 2. LexicalEnvironment
### 2-1. 수집하는 정보
- **environmentRecord**
	- 식별자들에 대한 정보
- outerEnvironmentReference
	- 외부 환경 정보


# ☘️ **environmentRecord**
- 코드의 **식별자(변수명) 정보들이 저장**
- 매개변수명, 선언된 함수, var로 선언된 변수명 등이 저장
- 처음부터 끝까지 훑어나가며 **순서대로** 수집


> 코드가 실행 전, 이미 해당 환경에 속한 코드의 변수명들을 모두 알고 있음 <br/>
>  => 식별자들을 최상단으로 끌어올려놓은 다음 실제 코드를 실행

ㅤ

# ☘️ 호이스팅 규칙
- 변수: 선언부와 할당부를 나누어 선언부만 끌어올림
- 함수: 함수 전체를 끌어올림
## 1. 매개변수와 변수에 대한 호이스팅
### 원본 코드

<img width="447" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/1506e51d-485a-4072-96ed-2fe320b04055">


### 매개변수를 변수 선언/할당 취급
<img width="446" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/31030a0a-78e0-4e6c-b075-ca1c94960d2e">


### 호이스팅 수행
변수명만 끌어올려 호이스팅

<img width="446" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/4c70e230-88a0-42fa-9a9f-ff68b4462769">


### 결과
```bash
1
1
2
```

## 2. 함수 선언의 호이스팅
### 원본 코드
<img width="447" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/4a283489-3a64-4f51-b8de-3b8d580e191f">

### 호이스팅 수행
변수명과 함수선언 끌어올려 호이스팅

<img width="445" alt="image" src="https://github.com/CitrusSoda/codeit14_techtalk/assets/98106371/9ebd4ccc-2226-4f3a-81c1-2b3a3fa39e27">

### 결과
```js
[Function: b]
bbb
bbb
```
