# Конфиг мегаменю

## Меню
JSON массив элементами которого являются объекты - *вкладки*
```json
[
  {},
  {},
  {}
]
```

## Вкладка
Вкладка являет я объектом с ключами, содержащими настройки.

`name` - тип: строка
* Название пункта меню
```json
"name": "WoW Retail"
```

`link` - тип: строка
* ссылка на раздел
* не обязательный параметр
* рекомендуется использовать относительные пути
```json
"link": "/wow-retail"
```

`background` - тип: строка
* адрес размещение картинки фона вкладки
* рекомендуется использовать относительные пути
```json
"background": "/media/82/ac/eb/1599163965/game_wow.jpg"
```

`icon` - тип: строка
* референс к svg иконке из бандла
```json
"icon": "wow-retail"
```

`slots` - тип: строка
* опциональо, если слоты не указаны, то блоки встают последовательно в 3 колоки
* референс к svg иконке из бандла
* испольуется техика описания именнованных темплейтов [css grid template](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template)
```json
"slots": "'a b c d' 'a e f g'"
```

`blocks` - тип: массив объектов
* содержимое вкладки мегаменю
```json
"blocks": [
  {},
  {},
  {}
]
```

## Блоки
`slot` - тип: строка
* указание на слот, в котором будет располагаться блок
```json
"slot": "a"
```

`elements` - тип: массив объектов
* содержимое блока
```json
"elements": [
  {},
  {},
  {}
]
```

## Элементы
В зависимости от типа элемента имеет разный состав ключей.
Поддерживается несколько типов элементов.

Типы: `title`, `list`, `image`, `custom`

### Тип `title`
```json
{
    "type": "title",
    "content": "Category Name Slot A",
    "link": "/wow-retail"
}
```

`type` - тип: строка
* указание тип элемента

`content` - тип: строка
* Заголовок блока

`link` - тип: строка
* ссылка с залоговка
* не обязательный параметр
* рекомендуется использовать относительные пути

### Тип `list`
```json
{
  "type": "list",
  "items": [
    {
        "content": "item 1",
        "link": "#"
    },
    {
        "content": "item 2",
        "link": "#"
    },
    {
        "content": "item 3",
        "link": "#"
    },
    {
        "content": "item 4",
        "link": "#"
    }
  ]
}
```

`type` - тип: строка
* указание тип элемента

`items` - тип: массив объектов
* содержимое элемента
* каждый элемента имеет 2 собсвенных ключа со строчными значениями:
  * `content` - строка - текст пункта меню
  * `link` - строка - ссылка
  * аналогично общему правилу рекомендуется использовать относительные пути

### Тип `image`
```json
{
    "type": "image",
    "image": "/media/4d/15/84/1598989521/BfA-High-End-Character-Season-4.jpg",
    "link": "#"
}
```

`type` - тип: строка
* указание тип элемента

`image` - тип: строка
* адрес размещение картинки
* рекомендуется использовать относительные пути

`link` - тип: строка
* ссылка с картинки
* не обязательный параметр
* рекомендуется использовать относительные пути

### Тип `custom`
```json
{
    "type": "custom",
    "content": "Super schnell und super freundlicher Kontakt. <a href=\"#\">Wie immer alles<\/a> spitze, danke!"
}
```

`type` - тип: строка
* указание тип элемента

`content` - тип: строка
* содержимое блока, текст или экранированный HTML

# Слоты
Суть слотов в том что создаются именованные области, в которые потом назначаются блоки. Техника объявления слотов аналогична [css grid template](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template) и, собственно, ее и использует "под капотом".

Количество объявляемых слотов ограничено здравым смыслом.

Примеры:
***
```json
"slots": "'a b c'"
```

<table>
  <tr>
    <td>a</td>
    <td>b</td>
    <td>c</td>
  </tr>
</table>

***
```json
"slots": "'a b c' 'a d e'"
```

<table>
  <tr>
    <td rowspan="2">a</td>
    <td>b</td>
    <td>c</td>
  </tr>
  <tr>
    <td>d</td>
    <td>e</td>
  </tr>
</table>


***
```json
"slots": "'a a a' 'b c d'"
```

<table>
  <tr>
    <td colspan="3">a</td>
  </tr>
  <tr>
    <td>b</td>
    <td>c</td>
    <td>d</td>
  </tr>
</table>

***
```json
"slots": "'a a a' 'b c d'"
```

<table>
  <tr>
    <td>a</td>
    <td rowspan="2">b</td>
    <td>c</td>
  </tr>
  <tr>
    <td>d</td>
    <td>e</td>
  </tr>
</table>

***
```json
"slots": "'a a a' 'b c d'"
```

<table>
  <tr>
    <td>a</td>
    <td colspan="2">b</td>
  </tr>
  <tr>
    <td>c</td>
    <td>d</td>
    <td>e</td>
  </tr>
</table>

***

```json
"'specials mounts banners' 'pvp raids banners'"
```

<table>
  <tr>
    <td>specials</td>
    <td>mounts</td>
    <td rowspan="2">banners</td>
  </tr>
  <tr>
    <td>pvp</td>
    <td>raids</td>
  </tr>
</table>

***
