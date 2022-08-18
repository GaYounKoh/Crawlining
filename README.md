# Crawlining
크롤링, 데이터 이어붙이기, ... (데이터 수집 과정에 쓰이는 코드, 2022 여름 정형철교수님 작업.) <br>


# 중요한 내용이라 앞으로 뺌
```python
f'지역 수 * 병 수 * 기간 수 = {272*63*258} = 4421088'
f'지역 2개의 전체기간 데이터 : {258*2} = 516'
f'지역으로만 따지면 : 지역 수 * 병 수 = {272*63} = 17136 개'
f'지역으로만 따졌을 때 다운받는데 걸리는 시간 : 지역 수 * 병 수 * 한 지역의 전체 기간 데이터 받는데 걸리는 시간 = {272*63*1.5} = 25704 시간'
# --> 교수님 작업 데이터 수
```


# 220717
코드 수정사항 발생
질병별 군구별 다 각각으로 나눠야함.

# 220714
### 프로젝트별 코드 정리는 정말 중요한 작업이다. (2022.07.14의 가연...)
미래의 내가 복붙해다 쓰기만 하면 되는 거니까.... <br>
+ 이해를 잘 해놓는 것도 굉장히 중요하다. <br>
그래야 나중에 바로 쓰기 편하다. <br>
내가 정리한, 잘 이해해봤던 코드가 있냐 없느냐의 차이가 일할 때 꽤 크게 작용한다. <br>

## 크롤링은 생각보다 쉽다.
이미 정리해둔, 한 번 쎄게 고생하면서 짜봤던 코드가 있었기 때문. <br>
그리고 내가 생각보다 크롤링 코드를 짜는걸 재밌어 한다. <br>
(개발자모드 들어가서 이것저것 보는게 멋있어보여서 재밌나보다.) <br>

## 크롤링은 로컬에서만 사용 가능하다.
서버는 안되는건가보다. <br>

[참고 코드1. Key.RETURN, Key.BACKSPACE, ... 등](https://coding-kindergarten.tistory.com/151) <br>
[참고 코드2. Key.BACKSPACE 사용 코드 (쓸모는 없었는데 driver.implicitly_wait(0.1)의 쓸모를 기억해내게 함.)](https://www.tutorialspoint.com/how-do-i-send-a-delete-keystroke-to-a-text-field-using-selenium-with-python) <br>


## 자동화 기술은 어쩌면 개인 시간을 벌어주는게 아닐까
라는 생각을 하게됐다. <br>
대략 200만회의 클릭 수를 몇 번의 실행만으로 줄여냈다. <br>

하지만 코드에 에러가 발생하는 문제가 있어 꽤나 골치가 아프긴 했다. <br>

그러나 단순히 앉아서 일일이 누르고 있는 것 보다는 당연히 훨씬 나은 선택이긴하다. <br>
** 개인시간 : (양치하는 시간, 잠자는 시간 같이 사소한 것부터 자기계발 시간 같이 중요한 시간까지) <br>

# 220715
- 통계작성 클릭 이후 시간 (텀)을 더 길게 아주 여유롭게 주고, 새로고침 텀을 줄였더니 에러 안남. 짱신기... <br>

- 잘 짠 코드 하나 열 연구원 안부럽다........ <br>

# 220720
- selenium update issue
아니 업데이트는 6월 29일에나 됐는데 왜 내가 코드 짤 때는 아무렇지 않았다가 이제야 에러가 나서는... <br>
몹시 화가 나지만...... 그러려니... <br>
그래도 처음에 짤 때 에러가 안나서 전체적인 코드 이해 했으니까... <br>
아 그리고 chromedriver도 교수님 컴퓨터에서는 앞에 path랑 뒤에 .exe 확장자 붙여줘야함.

    - update 내역
    [한국인 작성자의 빡침이 드러나는 페이지로 확인](https://velog.io/@thovy/selenium-AttributeError-Webdriver-object-has-no-attribute-findelementbyid) <br>
    [stack over flow의 문답으로 확인](https://stackoverflow.com/questions/72773206/selenium-python-attributeerror-webdriver-object-has-no-attribute-find-el) <br>
    ```python
    from selenium.webdriver.common.by import By # 이건 원래도 썼었음.
    
    # 원래
    browser.find_element_by_xpath("")

    # update 되면서 바뀐 부분
    driver.find_element(By.XPATH, " ")
    driver.find_elements(By.XPATH, " ")

    driver.find_element(By.CLASS_NAME, " ")
    driver.find_elements(By.CLASS_NAME, " ")
    ```

# 220721 목
오늘 강북 강서 다운 완.
다음 주 군구 = 4 (관악)부터 받기 시작하면 됨.

# 220727 수
오늘 군구 6 구로까지 다운 완.
내일 군구 = 7부터 받기 시작하면 됨.


# 220728 목
군구 = 8 노원구 부터 다시 해야함. 데이터 수가 안맞음.


# 220803
연도 2001 ~ 2021까지 한 번에 받기로 하고 코드 뒤엎음. <br>

# 220804
file renaming 하다가 괴로워짐. 다시 받아서 다시 시도해야할듯. 기존에 있던 name은 바꿔주는 name list에 없었는데 그렇다면 무엇이 문제? <br>
심지어 2번째 test에서는 또 수정한 시간별 (0~741 순)로 이름 잘 변경됨. <br>

확인 결과 numbering 할 때 100이 안생김....... 그거 이유좀 알아봐야겠으니 파일 지우지 말고.... 딱 기다려... <br>
100부터 밀린건 또 아님... 코드 살펴봐야함;;;.......... <br>

# 220805
- 폴더명은 일단 제일 앞 번호여야 할 파일(수정 순으로 정렬하면 됨.)부터 순서대로 끝까지 다 긁어서 제일 앞 번호여야 할 파일 위에서 우클릭해서 공통이름부분만 남기면 됨.
- 시도 바뀔 때마다의 에러는 해결했음. 에러 빈도수 줄여볼 것.
- 일단.... 파일을 깔끔히 정리해보려고 하느라 파일에서 삭제된 내용이 일부 있으니 새로 7차로 저장. 앞으로 뭔가 더 내용을 삭제하지 않는 한 계속 7차를 최종 코드로 하자.
<br>


# 220806-7 try except 구문 배우고 추가함.
에러났을 때 병 iter 기준으로 다시 돌기 때문에 서울 강남구부터 다시 도는 것을 220810에 확인함.
<br>

# 220810 try_except 구문 다듬음.
0. 병도 iter와 함께 출력 
1. 에러나서 except 구문 실행시 try 지나친 표시 출력.
2. `자동화()` 함수 수정하여서 에러났을 때 에러났던 해당 시도부터 돌도록 하고 (현재 돌아가는 시도 표시를 위해 출력해줄 때마다 iter와 함께 출력 -> 실수로 군구 idx를 출력해버림...... 다시... __수정할 것....__)💛💛🧡🧡💛💛
3. csv 다운로드 쪽 함수에 try except 구문 넣어줌.
4. 매번 병 끝날 때마다 `272로 나누어 떨어지는지 여부`와 `개수` 반환하게 함.
<br>


## 220815 데이터 다운로드 완

## 220818 데이터 합치는 중
- shape은 일단 나중에 다듬기
[df도 원하는 위치에 열 생성 이런게 가능함. insert, assign 등.....](https://zephyrus1111.tistory.com/48) <br>
[행은 idx로 삭제가 가능한데, 열은 열이름으로만 삭제 가능...???????](https://benn.tistory.com/27) - ㄴㄴ.<br>
열도 idx로 삭제 가능.... <br>
```python
# 숫자를 사용하여 삭제도 가능합니다.
# 밑은 iris 데이터셋의 첫 번째 (0), 두 번째 (1), 네 번째 (3) 열을 삭제하는 예제 코드입니다.

iris = iris.drop(iris.columns[[0,1,3]], axis=1)
```
<br>



## 날짜 list 만드는 코드... (월의 시작일과 말일만 있으면 되는데.... 잘못해서 다 넣어버림...)
```python
# 윤년list (4년에 한 번씩)
윤년list = [2020 - i*4 for i in range(5)]


# 날짜list
날짜lst = []
for 연도 in range(2001, 2022):
    for 월 in range(1, 13):
        if 월 in [1, 3, 5, 7, 8, 10, 12]:
            for 일 in range(1, 32):
                날짜lst.append(f'{연도}-{월}-{일}')
            
        elif 월 in [4, 6, 9, 11]:
            for 일 in range(1, 31):
                날짜lst.append(f'{연도}-{월}-{일}')
                
        elif 월 == 2:
            for 일 in range(1, 30):
                if 연도 not in 윤년list:
                    if 일 == 29:
                        pass
                    else:
                        날짜lst.append(f'{연도}-{월}-{일}')
                else:
                    날짜lst.append(f'{연도}-{월}-{일}')


## 머리가 아프니, 2022년은 따로 만들어서 붙이도록 한다.
for 월 in range(1, 7):
    if 월 in [1, 3, 5, 7, 8, 10, 12]:
        for 일 in range(1, 32):
            날짜lst.append(f'{2022}-{월}-{일}')

    elif 월 in [4, 6, 9, 11]:
        for 일 in range(1, 31):
            날짜lst.append(f'{2022}-{월}-{일}')

    elif 월 == 2:
        for 일 in range(1, 30):
            if 2022 not in 윤년list:
                if 일 == 29:
                    pass
                else:
                    날짜lst.append(f'{2022}-{월}-{일}')
            else:
                날짜lst.append(f'{2022}-{월}-{일}')
```
