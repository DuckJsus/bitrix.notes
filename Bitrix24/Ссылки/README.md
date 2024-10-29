### Полезные ссылки
***
Общие ссылки

[Документация Rest API](https://apidocs.bitrix24.ru)

***
Бизнес процессы

[Бизнес-процессы в Битрикс24 (памятка)](https://nikaverro.ru/blog/bitrix/buisness-process-bitrix24/)

[Бизнес-процессы - api коробка](https://nikaverro.ru/blog/bitrix/bitriks24-korobka-biznesprotsessy-phpkod/)

Примеры

[Вычисление ID начальника](https://dev.1c-bitrix.ru/learning/course/index.php?COURSE_ID=57&LESSON_ID=2172&LESSON_PATH=5442.4567.4795.2172)

[Вывод в лог](https://dev.1c-bitrix.ru/learning/course/index.php?COURSE_ID=57&LESSON_ID=2906&LESSON_PATH=5442.4567.4795.2906)

***
Работа с файлами

[Диск - api коробка](https://nikaverro.ru/blog/bitrix/api-disk/)

***
Работа с комментариями CRM

[Событие добавления комментария CRM в Rest API ...](https://apidocs.bitrix24.ru/api-reference/crm/timeline/comments/events/on-Crm-Timeline-Comment-Add.html)

[Событие добавления комментария CRM в D7 и ...](https://dev.1c-bitrix.ru/rest_help/crm/timeline/events_timeline/on_Crm_Timeline_Comment_Add.php)

[И работа с Request](https://dev.1c-bitrix.ru/api_d7/bitrix/main/request/index.php)


Пример
>AddEventHandler("crm", "\Bitrix\Crm\Timeline\Entity\Timeline::OnAfterAdd", "GetCommentTime");<br />
function  GetCommentTime() {             
&emsp;    $application = \Bitrix\Main\Application::getInstance();     
&emsp;    $request = $application->getContext()->getRequest(); // получим данные о текущем запросе    
&emsp;    $postList = $request->getPostList()->toArray();<br />
}

***
