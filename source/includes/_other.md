## Инициализация платежа
```html
<form method="POST"  class="application"  accept-charset="UTF-8" action="https://partner.rficb.ru/alba/input/">
<input type="hidden" name="key" value="b5/uqup/i/ueWBrRyp9V0n97zyHty5YtV5u/NW27nlk=”/>
<input type="hidden" name="cost" value="1"/>
<input type="hidden" name="name" value="Название услуги или сервиса"/>
<input type="hidden" name="email" value="customer@site.ru" />
<input type="hidden" name="order_id" value="0" />
<input type="image" style="border:0;" src="https://partner.rficb.ru/gui/images/alba_buttons/button_large.png" value="Оплатить" />
</form>
```
Инициализация платежа осуществляется следующим образом

|<center>Параметр | <center>Версия API | <center>Описание | <center>Примечание
|---------|:------------:|----------|-----------
|key | 1.0 | Ключ (идентификатор сервиса), присваиваемый системой при создании кнопки из ЛК | “b5/uqup/i/ueWBrRyp9V0n97zyHty5YtV5u/NW27nlk=
|cost | 1.0<br> 2.0 | Сумма оплаты, в рублях | 100
|name | 1.0<br>2.0 | Описание товара/услуги. Отображается на странице оплаты. Максимальная длина 128 символов. | Заказ №212
|email | 1.0<br>2.0 | Электронная почта плательщика. Поле обязательно для рекуррентных платежей. В иных случаях небходимость обязательного заполнения поля регулируется в настройках сервиса. | customer@site.ru
|phone_number | 1.0<br>2.0 | Номер телефона плательщика. Необходимость обязательного заполнения поля регулируется в настройках сервиса и параметрах платежного канала | 74951234567
|order_id | 1.0<br>2.0 | Цифровое поле (обязательное). Номер заказа в системе партнера, должен быть уникальным. Дважды заказ с одинаковым order_id оплатить не удастся. Если нет необходимости определять каждый заказ, то значение order_id нужно сделать равным 0. | Максимальная длина 64 символа<br>Минимальная длина для реккурентных платежей 6 символов
|comment | 1.0<br>2.0 | Текстовое поле. Можно передавать любую свою информацию. Информация переданная в данном параметре не отображается на странице оплаты и может использоваться для внутренних нужд магазина. | Максимальная длина 512 символов
|invoice_data | 1.0<br>2.0 | Данные в формате **JSON** для фискального чека (см. API для АТОЛ) | htmlspecialchars JSON
|custom_fields | 1.0<br>2.0 | Опциональный параметр. Предназначен для передачи дополнительной информации в различные каналы оплаты | urlencoded словарь JSON
|check | 2.0 | Электронная подпись запроса. | Обязательна передача параметра version=’2.0’ и service_id. Параметр key в данном случае не требуется.
|service_id | 2.0 | Идентификатор сервиса, обязательно для версии 2.0 | 121233
|version | 2.0 | Строка Версия API

Название | Описание | Назначение
---------|----------|-----------
CRM модуль | Встраиваемый модуль | Если ваш сайт использует какую либо CRM систему, используя готовые модули можно подключить оплату в очень короткие сроки
QR код | Ссылка на динамическое графическое изображение (QR код) | Размещение QR кода online на веб сайтах или offline на любых физических носителях
Внешний API | Вебсервис для инициации платежной операции | Данный способ подходит для ТСП формирующих выбор способа оплаты самостоятельно. При использовании данного механизма можно сформировать платежную транзакцию без отображения страниц платежной системы
Всплывающее окно (виджет) | HTML форма + JS | Данное решение полезно, если Вы не хотите, чтобы пользователь уходил с Вашего сайта. Виджет открывается на фоне основного сайта
Кнопка | HTML форма с данными необходимыми для проведения оплаты | Использование на сайтах собственной разработки. В поля HTML формы можно передавать собственные параметры платежа (сумму, назначение и др.)
Ссылка (короткая ссылка) | URL или ShortenURL, после перехода по которой отображается форма выбора способа оплаты. | Отправка ссылок на оплату через любые системы обмена сообщениями. В параметрах URL можно динамически менять параметры платежной транзакции.

### Направление на определенный способ оплаты
> Оплата банковской картой (spg)

```html
<form method="POST"  class="application"  accept-charset="UTF-8" action="https://partner.rficb.ru/alba/input/">
  <input type="hidden" name="key" value="b5/uqup/i/ueWBrRyp9V0n97zyHty5YtV5u/NW27nlk="/>
  <input type="hidden" name="cost" value="1"/>
  <input type="hidden" name="name" value="Название услуги или сервиса"/>
  <input type="hidden" name="phone_number" value="74951234567"/>
  <input type="hidden" name="email" value="customer@site.ru"/>
  <input type="hidden" name="payment_type" value="spg"/>
  <input type="hidden" name="verbose" value="0"/>
  <input type="hidden" name="order_id" value="0"/>
  <input type="image" style="border:0;" src="https://partner.rficb.ru/gui/images/a1lite_buttons/button_large.png" value="Оплатить"/>
</form>
```
Для направления покупателя в интерфейс заранее выбраной платежной системы (минуя окно выбора способа оплаты), к параметрам запроса необходимо добавить дополнительные поля:

Параметр | Значение | Примечание
--------------|----------|-------------------
payment_type | тип оплаты, на который должен быть отправлен плательщик | значения параметра представлены в таблице ниже
phone_number | телефонный номер плательщика | 74951234567
verbose `1/0`| что делать в случае возникновения ошибки, если нет данных о пользователе (e-mail или телефона для способов платежа, где они обязательны) | 1 – показывать ошибку, 0 – показывать страницу выбора способа оплаты
email | электронная почта клиента | поле обязательно для рекуррентных платежей, для остальных вариантов оплаты необходимость ввода регулируется в настройках сервиса

Значения, которые может принимать поле **payment_type**:

| <center>Параметр 	| <center>Значение|
|:--------	|---------------------------------:	|
| spg 	| пластиковые карты 	|
| spg_test 	| пластиковые карты, тестовый канал 	|
| mc 	| мобильная коммерция 	|
| wm 	| WebMoney 	|
| qiwi 	| QIWI терминалы и кошелёк 	|
| ym 	| Яндекс.Деньги 	|
| mtsmoney 	| МТС Деньги 	|

# Webhook нотификации

## Стандартные параметры

# Формирование подписи

## Подпись v2.0
> Пример формирования подписи v2.0

```python
from urllib.parse import urlparse,quote
import hashlib
import urllib
import base64
import hmac
 
def sign(method, url, params, secret_key, exclude=['check', 'mac']):
    """
    Типовой метод для подписи HTTP запросов
    """
    url_parsed = urlparse(url)
    keys = [param for param in params if param not in exclude]
    keys.sort()
 
    result = []
    for key in keys:
        value = quote(
            (params.get(key) or '').encode('utf-8'),
            safe='~'
        )
        result.append('{}={}'.format(key, value))
 
    data = "\n".join([
        method,
        url_parsed.hostname,
        url_parsed.path,
        "&".join(result)
    ])
    secrkey = secret_key.encode('utf-8')
    mesg=data.encode('utf-8')
    print(secrkey,mesg)
    digest = hmac.new(
        secrkey,
        mesg,
        hashlib.sha256
    ).digest()
    signature = base64.b64encode(digest)
    print(signature.decode('utf-8'))
    return signature
//Пример вызова, где $req - массив с параметрами транзакции:
sign("GET", "https://partner.rficb.ru/alba/input/", {'login': 'newlogin~_-.'}, '165165165sd');
```

```java
package ru.rficb.alba;
 
import java.io.UnsupportedEncodingException;
import java.net.URLEncoder;
import java.nio.charset.Charset;
import java.security.InvalidKeyException;
import java.security.NoSuchAlgorithmException;
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.Map;
import java.net.URI;
import java.net.URISyntaxException;
import javax.crypto.Mac;
import javax.crypto.spec.SecretKeySpec;
import javax.xml.bind.DatatypeConverter;

public class AlbaSigner {
 
    public static String sign(String method, String url, Map<String, String> params, String secretKey)
            throws URISyntaxException, UnsupportedEncodingException, NoSuchAlgorithmException, InvalidKeyException {
 
        URI uri = new URI(url);
 
        List keys = new ArrayList<>(params.keySet());
        Collections.sort(keys);
 
        StringBuilder sb = new StringBuilder();
        for (String key: keys) {
            if (sb.length() > 0) {
                sb.append("&");
            }
 
            sb.append(String.format("%s=%s", key, URLEncoder.encode(params.get(key), "UTF-8")));
        }
        String urlParameters = sb.toString();
        String data = method.toUpperCase() + "\n" +
                uri.getHost() + "\n" +
                uri.getPath() + "\n" +
                urlParameters;
 
        Mac hmacInstance = Mac.getInstance("HmacSHA256");
        Charset charSet = Charset.forName("UTF-8");
        SecretKeySpec keySpec = new javax.crypto.spec.SecretKeySpec(charSet.encode(secretKey).array(), "HmacSHA256");
        hmacInstance.init(keySpec);
 
        return DatatypeConverter.printBase64Binary(hmacInstance.doFinal(data.getBytes("UTF-8")));
    }
}
```

```php
<?php
 function http_build_query_rfc_3986($queryData, $argSeparator='&')
    {
        $r = '';
        $queryData = (array) $queryData;
        if(!empty($queryData))
        {
            foreach($queryData as $k=>$queryVar)
            {
                $r .= $argSeparator.$k.'='.rawurlencode($queryVar);
            }
        }
        return trim($r,$argSeparator);
    }
 
    function sign($method, $url, $params, $secretKey, $skipPort=False)
    {
        ksort($params, SORT_LOCALE_STRING);
 
        $urlParsed = parse_url($url);
        $path = $urlParsed['path'];
        $host = isset($urlParsed['host'])? $urlParsed['host']: "";
        if (isset($urlParsed['port']) && $urlParsed['port'] != 80) {
            if (!$skipPort) {
                $host .= ":{$urlParsed['port']}";
            }
        }
 
        $method = strtoupper($method) == 'POST'? 'POST': 'GET';
 
        $data = implode("\n",
            array(
                $method,
                $host,
                $path,
                http_build_query_rfc_3986($params)
            )
        );
 
        $signature = base64_encode(
            hash_hmac("sha256",
                "{$data}",
                "{$secretKey}",
                TRUE
            )
        );
 
        return $signature;
    }
 
// Пример вызова, где $req - массив с параметрами транзакции:
sign("GET", "https://partner.rficb.ru/alba/input/", $req, 'secret');
?>
```

Создать нормализованную строку запроса:

1. Отсортировать параметры по имени в кодировке **Utf-8**, сравнивая побайтово. Параметры берутся из **GET URI** или из тела **POST** запроса (когда **Content-Type: application/x-www-form-urlencoded**)
2. Кодировать имена и значения параметров по следующим правилам:
	* не кодировать определённые в стандарте **RFC 3986** незарезервированные символы. Эти символы: **A-Z**, **a-z**, **0-9**, минус (**-**), подчёркивание (**_**), точка (**.**) и тильда (**~**).
	* все остальные символы должны быть закодированы как **%XY**, где **X** и **Y** это шестнадцатеричные символы от **0** до **9** и от **A** до **F** (заглавные). Расширенные **Utf-8** символы кодируются как **%XY%ZA**.
	* пробел кодируется как **%20** (не как +, как обычно делается в URL).
	* кодированные имена параметров отделяются от кодированных значений знаком равно (=, **ASCII** код 61), даже если параметр имеет пустое значение.
	* пары имя–значение разделяются символом амперсанда (&, **ASCII** код 38).
3. Создать строку для подписи в соответствии со следующей псевдо грамматикой (где “\n” это **ASCII** символ перевода строки), **StringToSign** = :
	* **HTTPVerb** - метод **POST**, **GET**, **PUT** или **DELETE**.'+ "\n" +'
	* **ValueOfHostHeaderInLowercase** - параметр **host** из заголовка **HTTP**-запроса.'+ "\n" +'
	* **HTTPRequestURI** - компонент **URI**, абсолютный путь до (не включая **GET**­-параметров). Для пустого пути ожидается '/'. '+ "\n" +'
	* **CanonicalizedQueryString** (строка из шага 2).
4. Рассчитать **HMAC**, совместимый со стандартом **RFC 2104**, по только что созданной строке *StringToSign*, используя секретный ключ партнёра (*ключ алгоритма*) и **SHA256** (*способ хэширования*).
5. Сконвертировать полученную подпись в **base64**.

Использовать результат как значение **check**.

## Тест

