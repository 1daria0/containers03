# Лабораторная работа 3: Первый контейнер.

## Цель работы.

Целью лабораторной работы является изучение основ контейнеризации и подготовка рабочего окружения для выполнения следующих лабораторных заданий.

### Подготовка.
До этого у нас уже был скачан Docker Desktop.

### Выполнение. 

* Создала репозиторий *containers03* и склонировали себе его на компьютер.

```
git clone https://github.com/1daria0/containers03.git
```

* Создала в папке *containers03* файл *Dockerfile* со следующих содержимым.

```
notepad Dockerfile
```

```
FROM debian:latest
COPY ./site/ /var/www/html/
CMD ["sh", "-c", "echo hello from $HOSTNAME"]
```

* В той же папке создаем папку *site*. В новой папке создала файл *index.html* с произвольным содержимым.

```
echo ^<!DOCTYPE html^>^<html^>^<head^>^<title^>Привет, Docker!^</title^>^</head^>^<body^>^<h1^>Моя первая лабораторная работа^</h1^>^</body^>^</html^> > index.html
```

### Запуск и тестирование.

* Открываю терминал в папке *containers03* и выполняю команду:

```
 docker build -t containers03 .
```

* Образ создавался: **Building 97.1s**

* Выполнила команду для запуска контейнера:

```
docker run --name containers03 containers03
```

* В консоле было выведено: *hello from 60838855d510*

* Удалила контейнер и запустила снова, выполнив команды:

```
docker rm containers03
docker run -ti --name containers03 containers03 bash
```

* В открывшемся окне выполнила команды:

```
cd /var/www/html/
ls -l
```

* На экране выводиться: *total 4
-rwxr-xr-x 1 root root 126 Feb 25 20:19 index.html*. Закрыли окно комадной *exit*.

### Используемые источники.

1. https://elearning.usm.md/mod/assign/view.php?id=282116

2. https://chat.deepseek.com
