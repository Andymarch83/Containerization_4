# Containerization_4
# Контейнеризация (семинары)
## Урок 4. Dockerfile и слои
## Задание: 
необходимо создать Dockerfile, основанный на любом образе (вы в праве выбрать самостоятельно).

В него необходимо поместить приложение, написанное на любом известном вам языке программирования (Python, Java, C, С#, C++).
При запуске контейнера должно запускаться самостоятельно написанное приложение.

Решение:

Создаём директорию для размещения данных для создания образа и самого контейнера:

mkdir HomeWork04

В директорию копируем файл с программой:

cp phonebook.py /home/andrey/HomeWork04

В директории создаём Dockerfile:

nano Dockerfile:

в нём прописываем:

FROM ubuntu:20.04 - /задаём базовый образ/

RUN apt-get update && apt-get install -y python3 - /указываем команды для выполнения в контейнере(обновляем список пакетов и устанавливаем python3)

COPY phonebook.py /app/ - /копируем файл с нашей программой из дирректории с данными для контейнера в указанную директорию в контейнер/

WORKDIR /app - /задаём рабочую директорию в контейнере для выполнения команд по умолчанию/

CMD ["python3", "phonebook.py"] -/определяем исполняемую программу, которая будет запущена/

Проверям наш Dockerfile:

cat Dockerfile

FROM ubuntu:20.04

RUN apt-get update && apt-get install -y python3

COPY phonebook.py /app/

WORKDIR /app

CMD ["python3", "phonebook.py"]

Собираем Docker-образ:

docker build -t phonebook . - /не забываем про точкку, указвающую на нахождение файла в данной директории/


Создаём и запускаем контейнер на его основе:

docker run -it phonebook

Выберите одно из действий:
1 - Вывести инфо на экран
2 - Произвести экпорт данных
3 - Произвести изменение данных
4 - Произвести удаление данных
0 - Выход из программы
Действие: 1

ПП | ФИО | Телефон


Выберите одно из действий:

1 - Вывести инфо на экран

2 - Произвести экпорт данных

3 - Произвести изменение данных

4 - Произвести удаление данных

0 - Выход из программы

Действие: 2

Введите ФИО: Столяр Андрей Николаевич

Введите номер телефона: 8900800700

Добавлена запись : 1 | Столяр Андрей Николаевич | 8900800700


Выберите одно из действий:

1 - Вывести инфо на экран

2 - Произвести экпорт данных

3 - Произвести изменение данных

4 - Произвести удаление данных

0 - Выход из программы

Действие: 1

ПП | ФИО | Телефон

1 | Столяр Андрей Николаевич | 8900800700



Выберите одно из действий:

1 - Вывести инфо на экран

2 - Произвести экпорт данных

3 - Произвести изменение данных

4 - Произвести удаление данных

0 - Выход из программы

Действие: 0

Бдзынь!!!




