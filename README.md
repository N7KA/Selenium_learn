# Изучение автоматизации тестирования с помощью Selenium на Python

## Задание: поиск элементов с помощью Selenium

Вам нужно открыть страницу по [ссылке](http://suninjuly.github.io/simple_form_find_task.html) и заполнить форму на этой странице с помощью Selenium. Если всё сделано правильно, то вы увидите окно с проверочным кодом.  
### [Решение](https://github.com/N7KA/Selenium_learn/blob/main/Code/lesson6_step4.py)
```Python
from selenium import webdriver
from selenium.webdriver.common.by import By
import time 

link = "http://suninjuly.github.io/simple_form_find_task.html"

try:
    browser = webdriver.Chrome()
    browser.get(link)

    input1 = browser.find_element(By.TAG_NAME, "input")
    input1.send_keys("Ivan")
    input2 = browser.find_element(By.NAME, 'last_name')
    input2.send_keys("Petrov")
    input3 = browser.find_element(By.CLASS_NAME, 'city')
    input3.send_keys("Smolensk")
    input4 = browser.find_element(By.ID, "country")
    input4.send_keys("Russia")
    button = browser.find_element(By.CSS_SELECTOR, "button.btn")
    button.click()

finally:
    # успеваем скопировать код за 30 секунд
    time.sleep(30)
    # закрываем браузер после всех манипуляций
    browser.quit()

# оставить пустую строку в конце файла
```

## Задание: На указанной ниже странице вам нужно найти зашифрованную ссылку и кликнуть по ней:

+ Добавьте в самый верх своего кода import math
+ Добавьте в код команду, которая откроет страницу: http://suninjuly.github.io/find_link_text
+ Добавьте команду, которая найдет ссылку с текстом. Текст ссылки, который нужно найти, зашифрован формулой (можно вставить данное выражение в свой код, а можно выполнить в интерпретаторе, скопировать оттуда результат и уже его использовать в вашем коде):
```Python
str(math.ceil(math.pow(math.pi, math.e)*10000))
``` 
+ Добавьте команду для клика по найденной ссылке: она перенесет вас на форму регистрации.
+ Заполните скриптом форму так же как вы делали в предыдущем шаге урока
+ После успешного заполнения вы получите код

### [Решение](https://github.com/N7KA/Selenium_learn/blob/main/Code/lesson6_step5.py)
```Python

import math
nl = str(math.ceil(math.pow(math.pi, math.e)*10000))

from selenium import webdriver
from selenium.webdriver.common.by import By
import time 

link = "http://suninjuly.github.io/find_link_text"

try:
    browser = webdriver.Chrome()
    browser.get(link)

    link = browser.find_element(By.LINK_TEXT, nl)
    link.click()

    input1 = browser.find_element(By.TAG_NAME, "input")
    input1.send_keys("Ivan")
    input2 = browser.find_element(By.NAME, "last_name")
    input2.send_keys("Petrov")
    input3 = browser.find_element(By.CLASS_NAME, "city")
    input3.send_keys("Smolensk")
    input4 = browser.find_element(By.ID, "country")
    input4.send_keys("Russia")
    button = browser.find_element(By.CSS_SELECTOR, "button.btn")
    button.click()

finally:
    # успеваем скопировать код за 30 секунд
    time.sleep(30)
    # закрываем браузер после всех манипуляций
    browser.quit()

# оставить пустую строку в конце файла
```

