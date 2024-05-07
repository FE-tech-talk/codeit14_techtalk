# Chapter7

## 3-2

## 클래스(prototype)가 구체적인 데이터를 지니지 않게 하는 방법

- 클래스 상속을 구현했다 ⇒ 프로토타입 체이닝을 잘 연결했다

- 다만, 프로토타입을 직접 연결하면 구조적으로 안정성이 떨어진다 ⇒ 클래스 상속 추상화

---

<aside>
💡 <클래스 상속을 흉내 내기 위한 세 가지 방법>

1. SubClass.prototype에 SuperClass의 인스턴스를 할당한 다음 프로퍼티를 모두 삭제하는 방법
2. 빈 함수(Bridge)를 활용하는 방법
3. Object.create을 이용하는 방법

</aside>

- 클래스를 일단 만들고 , 일일이 지우고, 더는 새로운 프로퍼티를 추가할 수 없게 하는 것이다.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/90836cba-7d02-4907-8281-4cff2e0cc86e/4c00add5-1608-4f84-94f5-77285ae29d42/Untitled.png)
![image](https://github.com/CitrusSoda/codeit14_techtalk/assets/162524947/45ccac51-9f16-40fc-9503-da8219f2d434)

### 1. 방법(1) -인스턴스 생성 후 프로퍼티 제거

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/90836cba-7d02-4907-8281-4cff2e0cc86e/7e684b50-7ab2-4a45-8e9b-d69d93efec13/Untitled.png)
![image](https://github.com/CitrusSoda/codeit14_techtalk/assets/162524947/298e6fa7-bbc6-4674-9c5f-3cfa4793ad8c)

### 방법(2) -빈 함수를 활용

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/90836cba-7d02-4907-8281-4cff2e0cc86e/28ab02a0-e3d1-4c8d-8fed-3a8db78c7246/Untitled.png)
![image](https://github.com/CitrusSoda/codeit14_techtalk/assets/162524947/0c0ec943-9e86-42a3-a56d-ebe668152881)

- Bridge 라는 빈 함수 만들기
- Bridge 프로토타입이 Rectangle 프로토타입을 참조하게 한 다음
- Square 프로토타입에 new Bridge() 를 할당하면

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/90836cba-7d02-4907-8281-4cff2e0cc86e/fc5246a9-7224-49a9-97be-7ba05084a857/Untitled.png)
![image](https://github.com/CitrusSoda/codeit14_techtalk/assets/162524947/7cb9ddf0-c139-4b24-8b08-e7973a6bd68f)

### 방법(3) - Object.create 활용
![image](https://github.com/CitrusSoda/codeit14_techtalk/assets/162524947/a2a84876-fa86-4389-b5ee-afe874a52535)
