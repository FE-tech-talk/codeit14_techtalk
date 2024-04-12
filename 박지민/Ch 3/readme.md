# 명시적 this 바인딩

## bind()메서드

- bind() 메서드가 call(), apply() 메서드와 다른점은 cal()l과 apply()메서드는 바로 함수를 호출하는데
- bind() 메서드는 호출하지 않고 바인딩된 **새로운 함수**를 만듭니다. 즉, 객체에 **함수를 묶는 것**입니다.
- this 및 함수에 넘길 인수를 일부 지정해서 새로운 함수를 만듭니다.
    
![image](https://github.com/CitrusSoda/codeit14_techtalk/assets/162524947/bfd22b5b-925e-47a7-a1d9-795e3ce47dd8)

  
    

## name 프로퍼티

- name 프로퍼티에 동사 bind 의 수동태인 ‘bound ‘ 가 붙는다

![image](https://github.com/CitrusSoda/codeit14_techtalk/assets/162524947/38e2aad4-c7e1-4e96-b38a-681c81581c11)


## 내부 함수에 this 전달

![image](https://github.com/CitrusSoda/codeit14_techtalk/assets/162524947/65e8b8c9-0e1c-4d37-bfdc-35048badc54c)


## 별도의 인자로this 를 받는 경우 (콜백 함수 내에서의 this)

- this로 지정할 객체(thisArg) 를 인자로 지정할 수 있는 경우
- thisArg 값을 지정하면 콜백 함수 내부에서 this 값을 원하는 대로 변경 가능

---
![image](https://github.com/CitrusSoda/codeit14_techtalk/assets/162524947/4876921a-c859-4775-9405-b4090f044923)






## 화살표 함수의 예외 사항

- 화살표 함수(arrow function)에서는 this를 직접적으로 binding하지 않고 상위 스코프의 this를 가르키기 때문에 가능하다. 즉 함수 내부에는 this 가 아예 없으며,
- 스코프체인상 가장 가까운 this에 접근
- ![image](https://github.com/CitrusSoda/codeit14_techtalk/assets/162524947/a12269a8-4324-485c-a285-2f3c4ccc7697)

