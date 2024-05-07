# Chapter 6

 

- prototype 객체 내부 → Constructor 프로퍼티

- 인스턴스의 _ _ proto_ _ 객체 내부 → 생성자 함수의 prototype 프로퍼티 참조

- 
![image](https://github.com/CitrusSoda/codeit14_techtalk/assets/162524947/36597c39-6dc7-4655-bd39-c56e4dae74d2)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/90836cba-7d02-4907-8281-4cff2e0cc86e/62db1568-aa7c-4fbf-a259-582f0010bd54/Untitled.png)

- constructor 는 값을 변경할 수 있다.
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/90836cba-7d02-4907-8281-4cff2e0cc86e/6f12becc-381a-4487-9f40-2d157306ef79/Untitled.png)
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/90836cba-7d02-4907-8281-4cff2e0cc86e/732c874b-1cb3-4d73-a8ad-aed4de00fdd0/Untitled.png)
    ![image](https://github.com/CitrusSoda/codeit14_techtalk/assets/162524947/8e35bba8-ba66-4cbf-8922-1cabcdcc9260)

    <aside>
    💡 constructor을 변경하더라도 참조하는 대상이 변경될 뿐, 인스턴스의 원형은 바뀌지 않는다.
    
    </aside>
    
- 

- 다양한 constructor 접근 방법
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/90836cba-7d02-4907-8281-4cff2e0cc86e/661f8ad8-41ed-4139-9e5a-153d7bd3f331/Untitled.png)
    ![image](https://github.com/CitrusSoda/codeit14_techtalk/assets/162524947/64e16671-51ce-4486-98c9-36c9dfeb70ef)


- 공식:
    1. 다음 각 줄은 모두 동일한 대상을 가리킨다.
    2. 다음 각 줄은 모두 동일한 객체에 접근할 수 있다.
 
  ![image](https://github.com/CitrusSoda/codeit14_techtalk/assets/162524947/076ad43e-99e6-44ab-8b17-ee4d5e6813a8)
