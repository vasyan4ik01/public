Проект по образовательным курсам:

провести анализ данных и ответить на поставленные задачи:

1. A/B–тестирование

В ходе тестирования одной гипотезы целевой группе была предложена новая механика оплаты услуг на сайте, у контрольной группы оставалась базовая механика. Необходимо проанализировать итоги эксперимента и сделать вывод, стоит ли запускать новую механику оплаты на всех пользователей.

В качестве входных данных Вы имеете 4 csv-файла:

-groups.csv - файл с информацией о принадлежности пользователя к контрольной или экспериментальной группе (А – контроль, B – целевая группа) 
-groups_add.csv - дополнительный файл с пользователями, который вам прислали спустя 2 дня после передачи данных
-active_studs.csv - файл с информацией о пользователях, которые зашли на платформу в дни проведения эксперимента. 
-checks.csv - файл с информацией об оплатах пользователей в дни проведения эксперимента. 

2. SQL
2.1 
Дана таблица default.peas:

Название атрибута	Тип атрибута 	Смысловое значение
st_id	int	ID ученика
timest	timestamp	Время решения карточки
correct	bool	Правильно ли решена горошина?
subject	text	Дисциплина, в которой находится горошина

Необходимо написать оптимальный запрос, который даст информацию о количестве очень усердных студентов.

Под очень усердным студентом мы понимаем студента, который правильно решил 20 задач за текущий месяц.

2.2 
Даны таблицы: 

-default.peas, 
-default.studs:

Название атрибута	Тип атрибута 	Смысловое значение
st_id	int 	ID ученика
test_grp	text 	Метка ученика в данном эксперименте

-default.final_project_check:

Название атрибута	Тип атрибута 	Смысловое значение
st_id	int 	ID ученика
sale_time	timestamp	Время покупки
money	int	Цена, по которой приобрели данный курс
subject	text 	Дисциплина, на которую приобрели полный доступ

Необходимо в одном запросе выгрузить следующую информацию о группах пользователей:

ARPU 
ARPAU 
CR в покупку 
СR активного пользователя в покупку 
CR пользователя из активности по математике (subject = ’math’) в покупку курса по математике
ARPU считается относительно всех пользователей, попавших в группы.

Активным считается пользователь, за все время решивший больше 10 задач правильно в любых дисциплинах.

Активным по математике считается пользователь, за все время решивший 2 или больше задач правильно по математике.

Все данные находятся в табличном виде в Clickhouse

3. Python
3.1
Реализуйте функцию, которая будет автоматически подгружать информацию из дополнительного файла groups_add.csv (заголовки могут отличаться) и на основании дополнительных параметров пересчитывать метрики.
3.2
Реализуйте функцию, которая будет строить графики по получаемым метрикам.