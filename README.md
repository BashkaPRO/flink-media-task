# Тестовое задание от компании Flink-Media на вакансию Node.JS & PHP программист со знанием баз данных (MongoDB, Elasticsearch, MySQL) 

**Написать на NodeJS программу проверки email.**

Программа запускается из командной строки в следующем виде:
```check_email.js myemail@domain.com --proxy=socks://192.168.0.1:2323```

Поддержка прокси - ```socks5```. Если прокси не указан, подключаемся к mail серверу напрямую. Запросы к DNS делаются всегда без прокси.

Список проверок:
- Соответствие введенного email стандарту
- Получение mx записей домена
- Проверка ответа почтового сервера
- Проверка наличия пользователя на сервере
- Проверка наличия несуществующего пользователя на сервере

В консоль должен сформироваться ответ в JSON:
```
{
address: true,
mx_exists: true,
server_is_online: true,
address_exists: true,
wrong_address_accepted: false,

server_helo_response: “220 Mail.Ru ESMTP”,
mx_domains: [“mxs.mail.ru”],
mail_from_response: “250 OK”,
rcpt_to_response: “550 5.1.1 Bad destination mailbox address”,
}
```

Пример работы с сервером SMTP:
```
220 Mail.Ru ESMTP
ehlo pleasefeedme.ru - запрос
250-mx144.mail.ru ready to serve
250-STARTTLS
250-SIZE 73400320
250 8BITMIME
MAIL FROM:<info@pleasefeedme.ru> - запрос
250 OK
RCPT TO:<info@mail.ru> - запрос
250 OK
```