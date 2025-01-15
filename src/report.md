# Part1. News API
- Переходим по ссылке и получаем API KEY.

- Прикладываем API KEY в качестве bearer token в заголовке авторизации.
<br>![apiKey](screenshots/part1/apiKey.png)
<br>*Добавление API KEY*

1. Получаем все новости по теме linux.
<br>![linux](screenshots/part1/linux.png)
<br>*Получение статей про Linux*

2. Получаем все новости по теме «Разработка» на русском языке за последние 15 дней.
<br>![development](screenshots/part1/development1.png)
<br>*Получение статей про разработку*

- Сделаем автоматическое вычисление даты, которая была 15 дней назад, с посощью скрипта на JavaScript.
<br>![development](screenshots/part1/development2.png)
<br>*Вычисление даты*

3. Получаем все новости по теме linux на русском языке на 3 странице, на каждой из которых по 10 новостей.
<br>![linuxPages](screenshots/part1/linuxPages.png)
<br>*Разбивка на страницы*

4. Получаем все заголовки новостей для страны Россия по теме «наука» (science). Для этого устанавливаем `endpoint=top-headlines`.
<br>![newsHeadlines](screenshots/part1/newsHeadlines.png)
<br>*Заголовки новостей*

# Part2. Инструменты разработчика
- Открываем консоль разработчика, выбираем вкладку «network», указываем фильтр на Fetch/XHR и нажимаем на кнопку "Контакты".

- Находим ссылку, начинающуюся с `https://hh.ru/vacancy/`, и открываем заголовки запроса.
<br>![network](screenshots/part2/network.png)
<br>*Запросы, которые посылаются на API hh.ru*

- Переносим запрос и заголовки в Postman.
<br>![contacts](screenshots/part2/contacts.png)
<br>*Получение контактов*

# Part3. Телеграм-бот
- Создаем своего бота.

- Формат, в котором посылаются запросы к боту через api.telegram.org: `https://api.telegram.org/bot<токен>/метод`

- Создаем коллекцию в Postman. Последующие запросы добавляем в неё. Токен сохраняем в variables.

- Получаем информацию о боте (метод `getMe`).
<br>![bot_getMe](screenshots/part3/bot_getMe.png)
<br>*Получение информации о боте*

- Отправляем вручную сообщение боту. Это нужно, чтобы метод `getUpdates` вернул не пустой список, а последние обновления в чате, чтобы взять оттуда `chat.id`.

- Получаем информацию об обновлениях в чате с ботом (метод `getUpdates`).
<br>![bot_getUpdates](screenshots/part3/bot_getUpdates.png)
<br>*Получение обновлений в чате*

- Берем `chat.id` из ответа на предыдущий запрос. Отправляем себе сообщение от имени бота (метод `sendMessage`).
<br>![bot_sendMessage](screenshots/part3/bot_sendMessage.png)
<br>*Отправка сообщения*

- Отправляем фотографию себе от имени бота с помощью метода `sendPhoto` (документация: `https://core.telegram.org/bots/api#sendphoto`).
<br>![bot_sendPhoto1](screenshots/part3/bot_sendPhoto1.png)
<br>*Отправка фотографии*

- Отправляем фотографию с подписью.
<br>![bot_sendPhoto2](screenshots/part3/bot_sendPhoto2.png)
<br>*Отправка фотографии с подписью*

- Отправляем фотографию с подписью над изображением.
<br>![bot_sendPhoto3](screenshots/part3/bot_sendPhoto3.png)
<br>*Отправка фотографии с подписью*

- Отправляем фотографию с защитой от скачивания и пересылки.
<br>![bot_sendPhoto4](screenshots/part3/bot_sendPhoto4.png)
<br>*Отправка фотографии*

- Отправляем файл pdf. От бота приходит его содержание в формате картинки.
<br>![bot_sendPdf1](screenshots/part3/bot_sendPdf1.png)
<br>*Отправка файла pdf*

- При отправке pdf, содержащего текст, также присылается картинка. 
<br>![bot_sendPdf2](screenshots/part3/bot_sendPdf2.png)
<br>*Отправка файла pdf с текстом*

- При отправке файла Docx получаем ошибку `400 Bad Request`. Это связано с работой метода `sendPhoto`: документы с расширением `docx`, `xls` и др. не являются изображениями.
<br>![bot_sendDocx1](screenshots/part3/bot_sendDocx1.png)
<br>*Отправка файла Docx*

- Для отправки документа используем метод `sendDocument`.
<br>![bot_sendDocx2](screenshots/part3/bot_sendDocx2.png)
<br>*Отправка файла Docx*

- Получаем информацию о фотографиях пользователя с помощью метода `getUserProfilePhotos` (документация: `https://core.telegram.org/bots/api#getuserprofilephotos`).
<br>![bot_userInfo](screenshots/part3/bot_userInfo.png)
<br>*Получение информации о фотографиях*

- Из ответа на предыдущий запрос берем `file_id` и добавляем его в параметры нового запроса для получения `file_path` с помощью метода `getFile`.
<br>![bot_filePath](screenshots/part3/bot_filePath.png)
<br>*Получение `file_path`*

- Из ответа на предыдущий запрос берем `file_path` и составляем ссылку для получения изображения (`https://api.telegram.org/file/bot<токен>/photos/file_0.jpg`). Вставляем ссылку в браузер, картинка сохраняется.
<br>![bot_getPicture](screenshots/part3/getPicture.png)
<br>*Переход по ссылке*
