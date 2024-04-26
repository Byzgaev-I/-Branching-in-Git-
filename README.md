# Домашнее задание к занятию `«Ветвления в Git»`

---

### Задание «Ветвление, merge и rebase»

Шаг 1. Предположим, что есть задача — написать скрипт, выводящий на экран параметры его запуска. Давайте посмотрим, как будет отличаться работа над этим скриптом с использованием ветвления, merge и rebase.
Создайте в своём репозитории каталог branching и в нём два файла — merge.sh и rebase.sh — с содержимым:

```bash
#!/bin/bash
# display command line options

count=1
for param in "$*"; do
    echo "\$* Parameter #$count = $param"
    count=$(( $count + 1 ))
done
Этот скрипт отображает на экране все параметры одной строкой, а не разделяет их.
```
### Задание «Решение»

Для начала, давайте создадим каталог branching и добавим в него два файла скриптов merge.sh и rebase.sh с одинаковым содержимым, как указано в задании. 
Выполним следующие команды в терминале:

Перейдем в каталог нашего репозитория  
Создаем каталог branching
mkdir branching

Переходим в каталог branching
cd branching

Создаем файл merge.sh с указанным 

```bash
echo '#!/bin/bash

# display command line options

count=1
for param in "$*"; do
    echo "\$* Parameter #$count = $param"
    count=$(( $count + 1 ))
done' > merge.sh

# Создайте файл rebase.sh с тем же содержимым
echo '#!/bin/bash
# display command line options

count=1
for param in "$*"; do
    echo "\$* Parameter #$count = $param"
    count=$(( $count + 1 ))
done' > rebase.sh
```

Делаем файлы скриптов исполняемыми
chmod +x merge.sh rebase.sh
