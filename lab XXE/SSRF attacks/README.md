## Exploiting XXE to perform SSRF attacks
1. Находим что фича "Check stock" находится на странице товара
2. Смотрим запрос через burp, видим там в теле передачу xml
3. Отправляем запрос в repeater, добавляем в xml `<!DOCTYPE foo [ <!ENTITY xxe SYSTEM "http://169.254.169.254/"> ]> ` и в поле "productId" пишем `&xxe;`
4. В ответ возвращается ошибка: `"Invalid product ID: latest"`
5. "latest" очень похоже на название папки, дописываем в путь, получаем другую ошибку с новым названием папки.
6. Повторяем пока не получим секретные данные. В результате url выглядит как `http://169.254.169.254/latest/meta-data/iam/security-credentials/admin`