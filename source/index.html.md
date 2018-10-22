---
title: Техническая документация РФИ Банк

language_tabs: # must be one of https://git.io/vQNgJ
  - php: PHP
  - java: Java
  - python
  - json: JSON


toc_footers:
  - <a href='https://home.rficb.ru/'>Личный кабинет интернет-эквайринга</a>
  - <a href='https://github.com/lord/slate'>Powered by Slate</a>

includes:
  - errors

search: true
---

# Введение

Добро пожаловать на главную страницу технчиеской документации РФИ Банка. 

Документация создана при помощи [Slate](https://github.com/lord/slate).

# Создание сервиса

> Для авторизации используйте следующий код:

```php
echo('Hello, world!')
```

```java
('Hello, world')
```

```java
# А что же тут будет написано
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```


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

