## Задание: На указанной ниже странице нужно найти зашифрованную ссылку и кликнуть по ней

1. Добавьте в самый верх своего кода import math
1. Добавьте в код команду, которая откроет страницу: http://suninjuly.github.io/find_link_text
1. Добавьте команду, которая найдет ссылку с текстом. Текст ссылки, который нужно найти, зашифрован формулой: `str(math.ceil(math.pow(math.pi, math.e)*10000))` (можно вставить данное выражение в свой код, а можно выполнить в интерпретаторе, скопировать оттуда результат и уже его использовать в вашем коде)
2. Добавьте команду для клика по найденной ссылке: она перенесет вас на форму регистрации.
3. Заполните скриптом форму.  
   После успешного заполнения вы получите код

### [Решение](https://github.com/N7KA/Selenium_learn/blob/main/tasks_solution/lesson6_step5.py)
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