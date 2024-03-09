Что такое Selenium и как он работает
WebDriver — это API, независимый от языка интерфейс для управления поведением веб-браузеров. Каждый браузер поддерживается определенной реализацией WebDriver, называемой драйвером.

Driver — это компонент/сущность, отвечающий за делегирование полномочий браузеру. Ну и важно понимать, что драйвер обеспечивает обмен данными между Selenium и браузером.

Selenium - это фреймворк, он связывает все эти части вместе с помощью пользовательского интерфейса (например кода на Python) и позволяет легко использовать все части браузера, обеспечивая кросс-браузерную и кросс-платформенную автоматизацию.

Важно понимать, что Selenium - не является инструментом автоматизации тестирования, это инструмент для управления браузером.

![AltSource 3](https://thumb.tildacdn.com/tild6461-3833-4436-b130-646239373264/-/format/webp/image.png)

Создание виртуального окружения
Виртуальное окружение нужно для изоляции проекта, чтобы все устанавливаемые библиотеки использовались только в рамках текущего проекта и не было конфликтов с другими зависимостями.

Первым делом создадим виртуальное окружение:
python3 -m venv venv
В результате, в директории проекта появится папка venv.

Теперь необходимо активировать окружение:

Mac OS:
source venv/bin/activate
Windows:
venv/Scripts/activate.ps1
В результате, в терминале вы увидите префикс с названием окружения примерно такого формата:

Важно знать: окружение работает в рамках текущей сессии окна терминала, т.е если вы закроете терминал, то окружение снова нужно будет активировать.

Но если вы решили удалить папку venv, и пересоздать окружение, то сначала деактивируйте его командой:
deactivate

Установка Selenium и зависимостей
После создания и активации тестового окружения в нашем проекте необходимо установить все зависимости (библиотеки) для начала работы.

Первая и самая главная библиотека, это и есть selenium. Установка происходит следующим образом:
pip3 install selenium
Обычно этого достаточно, но иногда дополнительно требуется установить библиотеку packaging
pip3 install packaging
Последнее, что нам понадобится, это библиотека webdriver-manager. Она нужна непосредственно для работы с драйверами Chrome, Firefox и т.д.
pip3 install webdriver-manager

Инициализация Chromedriver
Первое, что необходимо сделать, это обновить selenium и сам Chrome браузер. Далее воспользуйтесь одним из предложенных вариантов инициализации:

Иницализация в одну строчку, через SeleniumManager - он автоматически распознает ваш Chrome и запустит его.
from selenium import webdriver

driver = webdriver.Chrome()
2. Инициализация через WebDriverManager
from webdriver_manager.chrome import ChromeDriverManager
from selenium.webdriver.chrome.service import Service

service = Service(ChromeDriverManager().install())
driver = webdriver.Chrome(service=service)
2. Инициализация через WebDriverManager + версия Chrome
from webdriver_manager.chrome import ChromeDriverManager
from selenium.webdriver.chrome.service import Service

service = Service(ChromeDriverManager(driver_version="114.0.5735.16").install())
driver = webdriver.Chrome(service=service)
В данный момент работа Chromedriver не совсем стабильна, поэтому используйте тот вариант который сработает для вас!

Отслеживайте проблемы и новости тут: https://chromedriver.chromium.org/downloads

Инициализация Firefox
Тут все просто) Используем WebDriverManager, либо SeleniumManager и все.

Selenium Manager
from selenium import webdriver

driver = webdriver.Firefox()
2. WebDriverManager
from selenium import webdriver
from webdriver_manager.firefox import GeckoDriverManager
from selenium.webdriver.chrome.service import Service

service = Service(GeckoDriverManager().install())
driver = webdriver.Firefox(service=service)


ПРАКТИЧЕСКОЕ ЗАДАНИЕ
Повторение теории и практики
Создать новый проект в Aqua IDE.
Создать виртуальное окружение и активировать.
Установить необходимые для работы библиотеки
Создать python-файл с любым названием.
Написать инициализацию драйвера.
Запустить, чтобы все работало.
Работа является самостоятельной. Для сдачи, просто отпишитесь, все ли получилось.
