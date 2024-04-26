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
### «Решение»

Для начала, давайте создадим каталог branching и добавим в него два файла скриптов merge.sh и rebase.sh с одинаковым содержимым, как указано в задании. 
Выполним следующие команды в терминале:

**Перейдем в каталог нашего репозитория**   

Создаем каталог branching  
mkdir branching

**Переходим в каталог branching**      
cd branching

**Создаем файл merge.sh с указанным**       

```bash
echo '#!/bin/bash

# display command line options

count=1
for param in "$*"; do
    echo "\$* Parameter #$count = $param"
    count=$(( $count + 1 ))
done' > merge.sh

**Создайте файл rebase.sh с тем же содержимым
echo '#!/bin/bash
# display command line options

count=1
for param in "$*"; do
    echo "\$* Parameter #$count = $param"
    count=$(( $count + 1 ))
done' > rebase.sh
```

**Делаем файлы скриптов исполняемыми**   
chmod +x merge.sh rebase.sh

**Шаг 2. Создадим коммит с описанием prepare for merge and rebase и отправим его в ветку main.**    

Для того чтобы создать коммит с описанием "prepare for merge and rebase" и отправить его в ветку main, выполняем следующие команды в терминале:

**Убедждаемся, что вы находимся в каталоге нашего репозитория и в ветке main**    
cd devops-netology
git checkout main

**Добавляем новые файлы в индекс Git**    
git add branching/merge.sh branching/rebase.sh

**Создайем коммит с заданным описанием**  
git commit -m "prepare for merge and rebase"

**Отправляем коммит в ветку main на удаленный репозиторий**  
git push origin main

![Image](https://github.com/Byzgaev-I/-Branching-in-Git-/blob/main/1-1.png)

**Подготовка файла merge.sh**
Шаг 1. Создайте ветку git-merge.  
Шаг 2. Замените в ней содержимое файла merge.sh на:  
```bash
#!/bin/bash
# display command line options

count=1
for param in "$@"; do
    echo "\$@ Parameter #$count = $param"
    count=$(( $count + 1 ))
done
```
Чтобы подготовить файл merge.sh в новой ветке git-merge, выполняем следующие команды в терминале:

**Убедитесь, что вы находитесь в каталоге вашего репозитория**  
cd devops-netology

**Создайте новую ветку git-merge и переключитесь на неё**  
git checkout -b git-merge

**Замените содержимое файла merge.sh на новое**  
```bash
echo '#!/bin/bash
display command line options

count=1
for param in "$@"; do
    echo "\$@ Parameter #$count = $param"
    count=$(( $count + 1 ))
done' > branching/merge.sh
```

**Проверьте изменения в файле**  
cat branching/merge.sh
После выполнения этих команд содержимое файла merge.sh будет заменено на новое. Вы можете проверить изменения, используя команду cat branching/merge.sh.
