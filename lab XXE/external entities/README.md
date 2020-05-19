## Exploiting XXE using external entities to retrieve files
1. Находим что фича "Check stock" находится на странице товара
2. Смотрим запрос через burp, видим там в теле передачу xml
3. Отправляем запрос в repeater, добавляем в xml `<!DOCTYPE foo [ <!ENTITY xxe SYSTEM "file:///etc/passwd"> ]>` и в поле "productId" пишем `&xxe;`
4. Отправляем запрос. Успех.