# Crawlining
크롤링, 데이터 이어붙이기, ... (데이터 수집 과정에 쓰이는 코드, 2022 여름 정형철교수님 작업.) <br>

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
    
    # update 되면서 바뀐 부분
    driver.find_element(By.XPATH, " ")
    driver.find_elements(By.XPATH, " ")

    driver.find_element(By.CLASS_NAME, " ")
    driver.find_elements(By.CLASS_NAME, " ")
    ```


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
