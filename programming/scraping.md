# Веб-скрапинг

## Запрос html-файла и его чтение в Python

```python
from urllib.request import urlopen
html = urlopen("https://pythonscraping.com/pages/page1.html")
print(html.read())
```

Библиотека urllib разделена на подмодули urllib.request, urllib.parse и
urllib.error и является частью стандартной библиотеки python.

## Beautiful Soup 4

BeautifulSoup помогает отформатировать и систематизировать грязные
интернет-данные, исправляя плохо размеченные HTML-страницы и выводя их
в виде легко обрабатываемых XML-структур.

```python
from urllib.request import urlopen
from bs4 import BeautifulSoup
html = urlopen("https://pythonscraping.com/pages/page1.html")
bsObj = BeautifulSoup(html.read())
# print header of the file
print(bsObj.h1)
```

## Обработка ошибок

```python
from urllib.request import urlopen
from urllib.error import HTTPError
from bs4 import BeautifulSoup

def getTitle(url):
    try:
        html = urlopen(url)
    except HTTPError as e:
        print(e)
        return None
    try:
        bsObj = BeautifulSoup(html.read())
        title = bsObj.body.h1
    except AttributeError as e:
        print(e)
        return None
    return title

title = getTitle("http://pythonscraping.com/pages/page1.html")
if title == None:
    print("Title couldn't be found")
else:
    print(title)
```

## Поиск по тегу и стилю CSS

```python
from urllib.request import urlopen
from bs4 import BeautifulSoup
html = urlopen("http://www.pythonscraping.com/pages/warandpeace.html")
bsObj = BeautifulSoup(html)

nameList = bsObj.findAll("span", {"class":"green", "class":"red"})
for name in nameList:
    print(name.get_text())
```

## Объекты BeautifulSoup

- BeautifulSoup (bsObj)
- Tag (bsObj.div.h1)
- NavigatableString: для представления текста внутри тегов вместо самих тегов
- Comment: для поиска HTML-комментариев
