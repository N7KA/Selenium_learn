## Задание: поиск элемента по XPath
На этот раз воспользуемся возможностью искать элементы по XPath.  
На странице http://suninjuly.github.io/find_xpath_form вы найдете такую же форму регистрации, как в шаге 3, при этом в нее добавилась куча одинаковых кнопок отправки. Но сработает только кнопка с текстом "Submit", и наша задача нажать в коде именно на неё.  
Ваши шаги:
1. В коде из шага 4 замените ссылку на  http://suninjuly.github.io/find_xpath_form.
2. Подберите уникальный XPath-селектор так, чтобы он находил только кнопку с текстом Submit. XPath можете формулировать как угодно (по тексту, по структуре, по атрибутам) - главное, чтобы он работал.
3. Модифицируйте код таким образом, чтобы поиск кнопки происходил с помощью XPath.
4. Запустите ваш код.  
   Если вы подобрали правильный селектор и все прошло хорошо, то вы получите код.

### [Решение](https://github.com/N7KA/Selenium_learn/blob/main/Code/Lesson6_step7.py)
```Python
from selenium import webdriver
from selenium.webdriver.common.by import By
import time 

link = "http://suninjuly.github.io/find_xpath_form"

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
    button = browser.find_element(By.XPATH, "/html/body/div/form/div[6]/button[3]")
    button.click()

finally:
    # успеваем скопировать код за 30 секунд
    time.sleep(30)
    # закрываем браузер после всех манипуляций
    browser.quit()

# оставить пустую строку в конце файла
```