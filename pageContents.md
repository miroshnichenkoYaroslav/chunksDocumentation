# Текст страницы

Позволяет добавлять не ссылку, а страницу целиком, со всем размещенным на ней контентом.
    
## Входные параметры:
+ `Дата публикации` – если установить эту галку, то текст будет выведена с датой публикации, если у страницы задано время появления;
+ `Добавить заголовок страницы (курсивом)` – эта опция позволяет включить или отключить отображение заголовка страницы – источника контента;
+ `Понижать уровень заголовков` – понижает уровень заголовков импортируемой страницы на один уровень;
+ `Только первая часть заголовка»` – задает включение в текст только основного заголовка страницы;

После пользовательских установок сформируется массив `body`, который будет отправлен на сервер, все элементы, которого имеют тип `string`:

```php
$masBits = [
	0  => "AE748208B4CF49D99CDBE3828744E7C5",
	1  => "3",
	2  => "91",
	3  => "0",
	4  => "0",
	5  => "0",
	6  => "0",
	7  => "0",
	8  => "0",
	9  => "0",
	10 => "01.04.2013",
	11 => "01.04.2013",
	12 => "0",
	13 => "0",
	14 => "0",
	15 => "0",
	16 => "0",
	17 => "0",
	18 => "0"
];
```
## Описание каждого элемента массива:


**1. Вкладка "Элемент" в десктопном клиенте.**

![page contents](https://github.com/miroshnichenkoYaroslav/chunksDocumentation/blob/master/images/page-contents.jpg)

+ `$masBits[0]` - идентификатор страницы, на которой используется чанк;
+ `$masBits[1]` - тип чанка, в данном случае `3` - это **текст страницы**;
+ `$masBits[2]` - передается в качестве аргумента в функцию `analyseBit()` - в ней число конвертируется в двоичную систему, полученная строка перегоняется в массив, массив переворачивают, дописуют элементы в массив `0 (int)` до размера массива `10` и возвращают массив флагов `$masFlag`. В десктопной версии это "Свойства элемента";
  - `$masFlag[0]` - дата публикации;
  - `$masFlag[1]` - понижать уровень заголовков;
  - `$masFlag[2]` - добавить заголовок страницы (курсивом);
  - `$masFlag[3]` - только первая часть заголовка;
+ `$masBits[3]` - к вложенным страницам;
+ `$masBits[4]` - все уровни вниз;

**2. Вкладка "Настройки списка" в десктопном клиенте.**

![page contents](https://github.com/miroshnichenkoYaroslav/chunksDocumentation/blob/master/images/list-settings.jpg)

+ `$masBits[5]` - лимит (не более);
+ `$masBits[6]` - сортировка, последних опубликованных (новые выше);
+ `$masBits[7]` - не используется в проекте;
+ `$masBits[8]` - отобразить начиная с даты;
+ `$masBits[9]` - отобразить до даты;
+ `$masBits[10]` - дата - опубликованные в период с;
+ `$masBits[11]` - дата - опубликованные в период по;
+ `$masBits[12]` - пагинация;
+ `$masBits[13]` - на одной странице;
+ `$masBits[14]` - не используется в проекте;
+ `$masBits[15]` - не используется в проекте;
+ `$masBits[16]` - не используется в проекте;
+ `$masBits[17]` - категории;
+ `$masBits[18]` - хранит в себе тип ссылки(нормальная, мажорная, пользовательская, динамическая);


## HTML код текста страницы

В html документ вставиться такой код:

```html
<p><strong><b>Page Title <!-- [Date]--></b></strong></p>
<!-- Далее конкотенируется html строка тела страницы -->
```
