ЗАНЯТИЕ 3 - ПОЛУЧЕНИЕ ДАННЫХ ИЗ БРАУЗЕРА И XPATH (ЧАСТЬ 1)
Запись занятия
Получение текущего URL-страницы
Получение заголовка страницы
Получение всего содержимого страницы
Валидация данных - assert
Поиск нескольких веб-элементов
Что такое Xpath и как с ним работать
Xpath - Глобальный поиск
Xpath - Поиск по уровню вложенности
Xpath - Поиск по порядковому номеру
Xpath - Поиск по атрибутам
Xpath - Поиск по содержимому


Получение текущего URL страницы
В дальнейшем, вам пригодится команда для получения URL-адреса страницы из адресной строки браузера, например для того чтобы убедиться в том, что действительно открыта нужная вам веб-страница.

Это можно сделать обратившись к атрибуту current_url.
driver.current_url
Для удобства Вы можете записать его в переменную для дальнейшего использования:
PAGE_URL = driver.current_url # Получаем текущий URL-адрес в переменную

print(PAGE_URL) # Выводим значение переменной


Получение заголовка страницы
Ранее мы разобрали как получить URL-адрес веб-страницы, но иногда нам нужно получать значение тега <titile/> на веб-странице.

Как пример все для той же проверки правильного открытия страницы. Это можно сделать обратившись к атрибуту title.
driver.title
По аналогии с получением URL-адреса, мы можем записать значение title в переменную для дальнейшего использования.
PAGE_TITLE = driver.title # Записываем значение title в переменную page_title

print("Title страницы: ", PAGE_TITLE) # Выводим значение переменной на экран


Получение всего содержимого страницы
Чтобы получить весь html-код страницы для дальнейших манипуляций, существует атрибут page_source.
PAGE_SOURCE = driver.page_source # Записываем в переменную всю веб-страницу

print(PAGE_SOURCE) # Печатаем HTML-код в терминал


Assertion | Проверка на истинность
В автоматизации, нам необходимо проверять правдивость данных, соответствуют ли они ожидаемому результату или нет. Для этого используются либо условные операторы, либо чуть более интересная конструкция называемая assert.

Данная конструкция имеет следующий вид:
a = 2
b = 2
assert a == b, "A не равно Б"
Т.е если утверждение правдивое, то все хорошо, если же нет, то будет ошибка с указанным после запятой текстом.

Давайте рассмотрим более реальный пример, предположим, что мы заранее знаем Title страницы, например для страницы https://dzen.ru/

title - в данном случае “Дзен”
driver.get("https://dzen.ru") # Открываем страницу

assert driver.title == "Дзен", "Страница не открылась"


Поиск нескольких веб-элементов
Мы уже научились искать один элемент, но иногда, нам понадобиться найти множество элементов, и сделать это можно с помощью метода find_elements().

Данный метод имеет те же аргументы, что и find_element(), но главное различие в том, что find_elements() возвращает список элементов.

Пример:
LIST_OF_H1_TAGS = driver.find_elements(By.TAG_NAME, "h2")

print(LIST_OF_H1_TAGS)
В результате мы получим стандартный список, в котором будут лежать все веб-элементы имеющий тег h2:
[<selenium.webdriver.remote.webelement.WebElement (session="aa2baed948cbe55eedad6d34832f571a", element="b4573195-37c8-4300-a474-a7b0e459bb50")>,
<selenium.webdriver.remote.webelement.WebElement (session="aa2baed948cbe55eedad6d34832f571a", element="6f7520e1-9dda-4b7f-8c66-73f464a107f3")>,
<selenium.webdriver.remote.webelement.WebElement (session="aa2baed948cbe55eedad6d34832f571a", element="2d40c5e9-4a00-4a7d-a367-b99af8aea06b")>,]
Как можно работать с таким списком?
Да как и с обычными списками в Python, например мы хотим спарсить все h2 заголовки со страницы:
elements = driver.find_elements(By.TAG_NAME, "h2") # Находим все элементы h2
for element in elements: # Перебираем список элементов h2
    print(element.text) # Выводим текст элементов h2
Тут можно заметить, что я получаю атрибут text, он существует у всех элементов в которых содержится како-либо текст, что логично)

Или к примеру если мы хотим получить определенный веб-элемент из списка, то просто обращаемся по индексу
ELEMENTS = driver.find_elements(By.TAG_NAME, "h2") # Находим все элементы h2
print(ELEMENTS[2])


Поиск нескольких веб-элементов
Мы уже научились искать один элемент, но иногда, нам понадобиться найти множество элементов, и сделать это можно с помощью метода find_elements().

Данный метод имеет те же аргументы, что и find_element(), но главное различие в том, что find_elements() возвращает список элементов.

Пример:
LIST_OF_H1_TAGS = driver.find_elements(By.TAG_NAME, "h2")

print(LIST_OF_H1_TAGS)
В результате мы получим стандартный список, в котором будут лежать все веб-элементы имеющий тег h2:
[<selenium.webdriver.remote.webelement.WebElement (session="aa2baed948cbe55eedad6d34832f571a", element="b4573195-37c8-4300-a474-a7b0e459bb50")>,
<selenium.webdriver.remote.webelement.WebElement (session="aa2baed948cbe55eedad6d34832f571a", element="6f7520e1-9dda-4b7f-8c66-73f464a107f3")>,
<selenium.webdriver.remote.webelement.WebElement (session="aa2baed948cbe55eedad6d34832f571a", element="2d40c5e9-4a00-4a7d-a367-b99af8aea06b")>,]
Как можно работать с таким списком?
Да как и с обычными списками в Python, например мы хотим спарсить все h2 заголовки со страницы:
elements = driver.find_elements(By.TAG_NAME, "h2") # Находим все элементы h2
for element in elements: # Перебираем список элементов h2
    print(element.text) # Выводим текст элементов h2
Тут можно заметить, что я получаю атрибут text, он существует у всех элементов в которых содержится како-либо текст, что логично)

Или к примеру если мы хотим получить определенный веб-элемент из списка, то просто обращаемся по индексу
ELEMENTS = driver.find_elements(By.TAG_NAME, "h2") # Находим все элементы h2
print(ELEMENTS[2])


Что такое Xpath и как с ним работать
Данная тема не простая и не очень сложная, но изучив ее, вы станете магистром в поиске элементов!

XPATH (XML Path Language) - это язык запросов к элементам XML, HTML документов, и других документов класса xml.

Данный язык основывается на структуре DOM (древесная структура) и позволяет искать элементы относительно корня, другу друга, соседей и т.д.

Мы разберем то, что я сам использую уже несколько лет и никогда не испытывал проблем с поиском элементов.


Символы, которые используются в XPATH-локаторах:

// - глобальный поиск относительно корня (начала) документа (обычно корень - это html тег)
/ - поиск по уровню вложенности, например когда элемент внутри элемента


Xpath - Глобальный поиск
Представим, что тут мы хотим найти элемент employee, но как это сделать если он вложен в div, еще и в body?
<html class="v2" dir="ltr" lang="en">
    <head>
        <meta src="xxxxxxx"></meta>
    </head>
	
    <body>
        <div class="table">
            <employee id="1">
                <empid>101</empid>
                <name>David</name>
		<designation discipline="web" experience="3 year">Senior Engineer</designation>
		<email>david@myemail.com</email>
	    </employee>
         </div>
    </body>
</html>
Локатор: //employee

Тут мы нашли элемент employee глобально, от корня страницы.

Хотим получить тег name? Легко: //name и нам не важно как глубоко закопан это тег, так как поиск ведется глобально, относительно корня.


Xpath - Поиск по уровню вложенности
Представим, что нужно найти тег name, но в этот раз у нас их на странице 2.

Используя способ глобального поиска //name, мы найдем оба элемента, и как же обойти эту ситуацию, как найти именно тот name, что лежит в теге employee?
<html class="v2" dir="ltr" lang="en">
    <head>
        <meta src="xxxxxxx"></meta>
    </head>
	
    <body>
	<div class="table">
            <name>Alex</name>
	    <employee id="1">
	        <empid>101</empid>
	        <name>David</name>
		<designation discipline="web" experience="3 year">Senior Engineer</designation>
		<email>david@myemail.com</email>
	    </employee>
	</div>
    </body>
</html>
Решение простое, использовать прямой путь, т.е по уровню вложенности.

Локатор: //employee/name

Тут мы говорим, найди мне глобально тег employee, и уже внутри него, найди мне тег name.)


Поиск по порядковому номеру
Для доступа по порядковому номеру, необходимо использовать [n], все как в Python) Но есть пара нюансов!

Допустим, у нас есть HTML-код и нам необходимо найти div с текстом 2:
<root>
    <header>
        <div>1</div>
        <div>2</div>
        <section>
            <div>3</div>
            <div>4</div>
        </section>
    </header>
</root>
Казалось бы, если мы напишем такой запрос: //header//div[2] то получим второй div внутри header, как раз который нам нужен, но нет! Мы получим "Каждый второй div лежащий внутри header"

Такой способ в изучаемом нами подходе не будет работать и врятли пригодиться, ибо нам вернуться 2 div блока, а нам нужно немного другое!

Мы напишем следующий Xpath: (//header//div)[2]
Разобьем по частям, чтобы было понятнее:
1. (//header//div) - как вы видите стоят скобки, они вернут нам список всех div-блоков внутри header.
Пример для наглядности: (<div>1</div>, <div>2</div>, <div>3</div>, <div>4</div>)

2. (//header//div)[2] - тут мы получаем второй div из полученного списка и все работает)

Важно: индексация элементов в Xpath идет не с 0 как в Python, а с 1


Xpath - Поиск по атрибутам
Синтаксис для поиска по атрибутам выглядит следующим образом:
// элемент [ @атрибут = ’значение атрибута’ ]
Исключением является text, в нем не используется знак @, а дописываются круглые скобки, text()=’текст’, потому что это не атрибут, а параметр!
<html class="v2" dir="ltr" lang="en">
    <head>
        <meta src="xxxxxxx"></meta>
    </head>
        <body>
            <div class="table">
                <employee id="1">
                    <empid>101</empid>
                    <name>David</name>
                    <designation discipline="web" experience="3 year">Senior Engineer</designation>
                    <email>david@myemail.com</email>
                </employee>
                <employee id="2">
                    <empid>102</empid>
                    <name>John</name>
                    <designation discipline="web" experience="3 year">DBA Engineer</designation>
                    <email>john@email.com</email>
                </employee>
            </div>
    </body>
</html>
Примеры локаторов:

//div[@class=’table’] - по классу
//employee[@id=’2’] - по id
//employee[@id=’1’]/name[text()=’John’] - по тексту
//name[text()=’John’] - по тексту
и т.д


Xpath - Поиск по содержимому
Представим, у элемента прописано несколько классов
<button class="btn btn-active">Join</button>
Еще и при этом, класс btn-active динамичный, т.е меняется из-за каких то обстоятельств.

В таком случае, если мы напишем локатор ниже
//button[@class=’btn btn-active’]
То возможно, в результате мы найдем элемент да, но если один из классов измениться, в данном случае btn-active, то ничего не выйдет.

Ну окей, тогда попробуем использовать только тот класс, который не меняется и напишем следующий локатор
//button[@class=’btn’]
Мимо, так работать не будет, так как в элементе есть еще классы… Как же быть?

Решение - это использование поиска по содержимому. Синтаксис будет выглядеть следующим образом:
//элемент [содержит (@атрибут, ‘значение содержимого’) ]
Давайте рассмотрим простой пример
<button class="btn btn-white">Join</button>
В результате получим:
//button[contains(@class, 'btn')]
А лучше вообще по тексту, что точно:
//button[contains(text(), 'Join')]


ПРАКТИЧЕСКОЕ ЗАДАНИЕ
Домашнее задание
Домашнее задание на тему "Получение данных и Xpath"

Задание 1
Инициализировать драйвер (любой, попробуйте Firefox) p.s: не забудьте его установить.
Открыть любую страницу, например: vk.com.
Получить и вывести title в консоль.
Открыть любую другую страницу, например: ya.ru.
Получить и вывести title в консоль.
Вернуться назад и, используя assert, убедиться, что вы точно вернулись обратно.
Сделать рефреш страницы.
Получить и вывести URL-адрес текущей страницы.
Вернуться "вперед" на страницу из пункта 4.
Убедиться, что URL-адрес изменился.
Задание 2
1. Создать файл locators.py
2. Записать все xpath-локаторы, для всех элементов на странице https://hyperskill.org/tracks в следующем формате:

'''# Header
LOGO = ("xpath","//a[@class='xxx']")

# Body
ALL_TRACKS_TAB = ("xpath","//button[@id='xxx']")

'''
3. Обязательно проверить, что все локаторы валидные, т.е элемент по ним находится.



