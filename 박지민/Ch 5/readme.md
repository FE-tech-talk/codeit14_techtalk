
    - # Chapter 5 Closure

## 접근 권한 제어(정보 은닉)

## 접근 권한의 종류

### 1. public (외부에서 접근 가능)

### 2. private (내부에서만 사용)

### 3. protected

- return 을 통한 접근 권한 제어
    
    ![image](https://github.com/CitrusSoda/codeit14_techtalk/assets/162524947/469abe23-4481-4512-8c98-ce3ee54b6a70)

     
    
- 클로저의 역할
    - 클로저를 이용하면 public 한 값과 private 값을 구분할 수 있다
    - 값을 바꾸지 못하도록 방어할 수 있다.
    - 객체가 아닌 함수로 만들고, 필요한 멤버만을 return 한다
    - 클로저를 사용하여 내부 변수를 보호하고 필요한 경우에만 외부에서 그 변수에 접근할 수 있도록 제어할 수 있다
    
    <aside>
    💡 [클로저를 활용해 접근 권한을 제어하는 방법]
    
    1. 함수에서 지역변수 및 내부함수를 생성
    
    2. 외부에 접근권한을 주고자 하는 대상들로 구성된 참조형 데이터를 return 한다
        (return 한 변수들은 공개 멤버가 되고, 그렇지 않은 변수들은 비공개 멤버
    
    </aside>
    
    - 클로저로 변수를 보호하지 않은 자동차 객체
        ![image](https://github.com/CitrusSoda/codeit14_techtalk/assets/162524947/1ae4144b-0708-4686-8f69-e4cf80d34f6a)

        
    - 클로저로 변수를 보호한 자동차 객체
        ![image](https://github.com/CitrusSoda/codeit14_techtalk/assets/162524947/f2a6c65f-093b-49cf-8540-d6c86c7f7f49)
