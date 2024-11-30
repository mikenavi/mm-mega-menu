**UPDATE 2020/11/14** Конфиг разбит на вкладки, каждая вкладка теперь редактируется отдельно через кастомное поле, каждое в своей категории

---

# Конфиг мегаменю

## Меню

~~JSON массив элементами которого являются объекты - *вкладки*~~

## Вкладка

Вкладка являет я объектом с ключами, содержащими настройки.
```json
  {
    "name": "WoW Retail",
    "link": "/wow-retail",
    "background": "/media/82/ac/eb/1599163965/game_wow.jpg",
    "icon": "wow-retail",
    "slots": "'a b c d'",
    "blocks": [
      {
        "slot": "a",
        "elements": [
          {
            "type": "title",
            "content": "Category Name Slot A"
          },
          {
            "type": "list",
            "items": [
              {
                "content": "item 1"
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
        ]
      },
      {
        "slot": "d",
        "elements": [
          {
            "type": "title",
            "content": "Category Name Slot D",
            "link": "#"
          },
          {
            "type": "list",
            "items": [
              {
                "content": "Recent Arrivals",
                "link": "#"
              },
              {
                "content": "Visions of N'Zoth",
                "link": "#"
              },
              {
                "content": "Rise of Azshara",
                "link": "#"
              },
              {
                "content": "On Sale",
                "link": "#"
              },
              {
                "content": "Best Sellers",
                "link": "#"
              },
              {
                "content": "Battle for Azeroth",
                "link": "#"
              }
            ]
          }
        ]
      },
      {
        "slot": "b",
        "elements": [
          {
            "type": "title",
            "content": "Category Name Slot B",
            "link": "#"
          },
          {
            "type": "image",
            "image": "/media/4d/15/84/1598989521/BfA-High-End-Character-Season-4.jpg",
            "link": "#"
          },
          {
            "type": "custom",
            "content": "Super schnell und super freundlicher Kontakt. <a href=\"#\">Wie immer alles<\/a> spitze, danke!"
          }
        ]
      }
    ]
  }
```

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

* опционально, если слоты не указаны, то блоки встают последовательно в 3 колонки
* референс к svg иконке из бандла
* используется техника описания именованных темплейтов [css grid template](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template)

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

Типы: `title`, `list`, `image`, `custom`, `card`

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

* ссылка с заголовка
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
* каждый элемента имеет 2 собственных  ключа со строчными значениями:
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

### Тип `card`

```json
{
  "type": "card",
  "image": "/media/4d/15/84/1598989521/BfA-High-End-Character-Season-4.jpg",
  "link": "#",
  "content": "Some title"
}
```

`type` - тип: строка

* указание тип элемента

`image` - тип: строка

* адрес размещение картинки
* рекомендуется использовать относительные пути

`link` - тип: строка

* ссылка с картинки
* рекомендуется использовать относительные пути

`content` - тип: строка

* Заголовок блока

## Слоты

Суть слотов в том что создаются именованные области, в которые потом назначаются блоки. Техника объявления слотов аналогична [css grid template](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template) и, собственно, ее и использует "под капотом".

Количество объявляемых слотов ограничено здравым смыслом.

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
"slots": "'a b c' 'd b e'"
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
"slots": "'specials mounts banners' 'pvp raids banners'"
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

## Примеры конфигов


```json
  {
    "name": "WoW Classic",
    "link": "/wow-classic",
    "background": "/media/e9/0f/8a/1599163965/game_wow-classic.jpg",
    "icon": "wow-classic",
    "slots": "'a b c d' 'a b c d'",
    "blocks": [
      {
        "slot": "a",
        "elements": [
          {
            "type": "title",
            "content": "Category Name Slot A",
            "link": "#"
          },
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
        ]
      },
      {
        "slot": "c",
        "elements": [
          {
            "type": "title",
            "content": "Category Name Slot D",
            "link": "#"
          },
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
        ]
      }
    ]
  }
```
  
```json
  {
    "name": "The Division 2",
    "link": "/the-division-2",
    "icon": "the-division-2",
    "background": "/media/b6/91/5f/1599163992/game_division.jpg",
    "slots": "'a b c d' 'e f g h' 'i i i j'",
    "blocks": [
      {
        "slot": "a",
        "elements": [
          {
            "type": "title",
            "content": "Category Name Slot A",
            "link": "#"
          },
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
        ]
      },
      {
        "slot": "g",
        "elements": [
          {
            "type": "custom",
            "content": "We cooperate only with qualified and..."
          }
        ]
      },
      {
        "slot": "i",
        "elements": [
          {
            "type": "title",
            "content": "Category Name Slot D",
            "link": "#"
          },
          {
            "type": "custom",
            "content": "We cooperate only with qualified and experienced top world players who participate personally in each event and ready to provide you with the best boosting service and gaming experience in your favorite online games. We ensure that every customer is highly satisfied and 100% positive feedback of our work pretty much sums it up ;) Get the most relevant eu boost and power leveling services from the professional players fast and easy!"
          }
        ]
      },
      {
        "slot": "j",
        "elements": [
          {
            "type": "title",
            "content": "Category Name Slot D",
            "link": "#"
          },
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
        ]
      }
    ]
  }
```
