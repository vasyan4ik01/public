DAG в airflow 1, каждый день в 15:00 берет данные за вчера и выполняет следующие преобразования: 

1. В feed_actions (данные о новостной ленте мобильного приложения) для каждого юзера считает число просмотров и лайков контента. В message_actions (данные о входящих и исходящих сообщениях мобильного приложения)  для каждого юзера считает, сколько он получает и отсылает сообщений, скольким людям он пишет, сколько людей пишут ему. Каждая выгрузка в отдельном таске.

2. Объединяет две таблицы в одну.

3. Для этой таблицы считает все эти метрики в разрезе по полу, возрасту и ос. Три разных таска на каждый срез.

4. Финальные данные со всеми метриками записывает в отдельную таблицу в ClickHouse.

5. Каждый день таблица дополняется новыми данными. 

Структура финальной таблицы:

Дата - event_date

Название среза - dimension

Значение среза - dimension_value

Число просмотров - views

Числой лайков - likes

Число полученных сообщений - messages_received

Число отправленных сообщений - messages_sent

От скольких пользователей получили сообщения - users_received

Скольким пользователям отправили сообщение - users_sent

Срез - это os, gender и age