---
title: Техническая документация РФИ Банк 2.0

language_tabs: # must be one of https://git.io/vQNgJ
  - php: PHP
  - java: Java
  - python
  - json: JSON


toc_footers:
  - <a href='https://home.rficb.ru/'>Личный кабинет интернет-эквайринга</a>
  - <a href='https://github.com/RFIBANK/'>Наш репозиторий</a>
  - <a href='https://github.com/lord/slate'>Powered by Slate</a>
  

includes:
  - errors

search: true
---

# Введение

Добро пожаловать на главную страницу технической документации РФИ Банка.
Здесь вы найдете необходимую информаци о взаимодействии сервисов партнера и Банка.

# Личный кабинет интернет-эквайринга

В личном кабинете собраны различные инструменты:
1. this starts a list *with* numbers
+  this will show as number "2"
*  this will show as number "3."
9. any number, +, -, or * will keep the list going.
    * just indent by 4 spaces (or tab) to make a sub-list
        1. keep indenting for more sub lists
    * here i'm back to the second level
* an asterisk starts an unordered list
* and this is another item in the list
+ or you can also use the + character
- or the - character

To start an ordered list, write this:

1. this starts a list *with* numbers
+  this will show as number "2"
*  this will show as number "3."
9. any number, +, -, or * will keep the list going.
    * just indent by 4 spaces (or tab) to make a sub-list
        1. keep indenting for more sub lists
    * here i'm back to the second level

To start a check list, write this:

- [ ] this is not checked
- [ ] this is too
- [x] but this is checked
+ тест
<ul>
<li>создание сервисов
<li>просмотр статистики платежей
<li>создание ссылок/кнопок/QR-кодов для оплаты
<li>инициализация и контроль возвратов
<li>создание и просмотр запросов в техническую поддержку Банка
</ul>
    
Доступ в <a href='https://home.rficb.ru/'>личный кабинет</a> осуществляется по логину и паролю, который вы получите в процессе интеграции

## Создание сервиса

Создание сервиса важный этап интеграции. На одном логине может создано до 10 сервисов. Каждый сервис имеет свои насртойки и набор параметров. 

    <aside class="notice">
        Количество сервисов может быть увеличено по запросу в технчиескую поддержку
    </aside>


> Сервис Вы можете создать в [личном кабинете интернет-эквайринга](https://home.rficb.ru).

<aside class="notice">
Тестовое наполнение <code>meowmeowmeow</code>.
</aside>

# Webhook нотификации

## Стандартные параметры

```php
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```java
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```


> Возвращается JSON:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

Тест-тест-тест.

### HTTP Request

`GET https://partner.rficb.ru `

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

