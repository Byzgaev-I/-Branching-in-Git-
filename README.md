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

**Проверяем изменения в файле**    
cat branching/merge.sh  
После выполнения этих команд содержимое файла merge.sh будет заменено на новое.
**Проверяем изменения, используя команду** 
cat branching/merge.sh.



Шаг 3. Создайте коммит merge: @ instead *, отправьте изменения в репозиторий.  
Шаг 4. Разработчик подумал и решил внести ещё одно изменение в merge.sh:  
```bash
#!/bin/bash
# display command line options

count=1
while [[ -n "$1" ]]; do
    echo "Parameter #$count = $1"
    count=$(( $count + 1 ))
    shift
done
```
### «Решение»

Шаг 5. Создайте коммит merge: use shift и отправьте изменения в репозиторий.  

Выполните следующие шаги в терминале для продолжения работы с файлом merge.sh в ветке git-merge:

*Шаг 3: Создание коммита с сообщением "merge: @ instead ":


**Убеждаемся, что вы находимсся в ветке git-merge**  
git checkout git-merge

**Добавляем изменения в индекс Git и создайте коммит**  
git add branching/merge.sh
git commit -m "merge: @ instead *"

**Отправляем изменения в удаленный репозиторий**    
git push origin git-merge
Шаг 4: Внесение дополнительного изменения в файл merge.sh:  

**Открываем файл merge.sh для редактирования**  
```bash
cat <<EOT > branching/merge.sh
#!/bin/bash
# display command line options

count=1
while [[ -n "\$1" ]]; do
    echo "Parameter #\$count = \$1"
    count=\$(( count + 1 ))
    shift
done
EOT
```
**Проверяем изменения**    
cat branching/merge.sh
Шаг 5: Создание коммита с сообщением "merge: use shift" и отправка изменений в репозиторий:  

**Добавляем изменения в индекс Git и создайте коммит**  
git add branching/merge.sh
git commit -m "merge: use shift"

**Отправляем изменения в удаленный репозиторий**  
git push origin git-merge
После выполнения этих команд вы будете иметь два коммита в ветке git-merge, которые содержат изменения в файле merge.sh, и оба коммита будут отправлены в ваш удаленный репозиторий.

**Изменим main**
Шаг 1. Вернитесь в ветку main. Шаг 2. Предположим, что пока мы работали над веткой git-merge, кто-то изменил main. Для этого изменим содержимое файла rebase.sh на:
```bash
#!/bin/bash
# display command line options

count=1
for param in "$@"; do
    echo "\$@ Parameter #$count = $param"
    count=$(( $count + 1 ))
done

echo "====="
```
**Решение**

**Обновляем содержимое файла rebase.sh с новым кодом**   

```bash
cat <<EOT > branching/rebase.sh
#!/bin/bash
# display command line options

count=1
for param in "\$@"; do
    echo "\$@ Parameter #\$count = \$param"
    count=\$(( count + 1 ))
done

echo "====="
EOT
```

**Проверяем изменения**  
cat branching/rebase.sh

**Добавляем измененный файл в индекс Git и создайте коммит**      
git add branching/rebase.sh
git commit -m "Update rebase.sh to use \$@ instead of \$* and add echo ====="    

**Отправьте изменения в ветку main на удаленный репозиторий**    
git push origin main

**Шаг 3. Отправляем изменённую ветку main в репозиторий.**
Отправьте изменения в ветку main на удаленный репозиторий  
git push origin main

**Подготовка файла rebase.sh**
Шаг 1. Предположим, что теперь другой участник нашей команды не сделал git pull либо просто хотел ответвиться не от последнего коммита в main, а от коммита, когда мы только создали два файла merge.sh и rebase.sh на первом шаге.
Для этого при помощи команды git log найдём хеш коммита prepare for merge and rebase и выполним git checkout на него так: git checkout 8baf217e80ef17ff577883fda90f6487f67bbcea (хеш будет другой). Шаг 2. Создадим ветку git-rebase, основываясь на текущем коммите. Шаг 3. И изменим содержимое файла rebase.sh на следующее, тоже починив скрипт, но немного в другом стиле


Шаг 1. Предположим, что теперь другой участник нашей команды не сделал git pull либо просто хотел ответвиться не от последнего коммита в main, а от коммита, когда мы только создали два файла merge.sh и rebase.sh на первом шаге.
Для этого при помощи команды git log найдём хеш коммита prepare for merge and rebase и выполним git checkout на него так: git checkout 8baf217e80ef17ff577883fda90f6487f67bbcea (хеш будет другой). Шаг 2. Создадим ветку git-rebase, основываясь на текущем коммите. Шаг 3. И изменим содержимое файла rebase.sh на следующее, тоже починив скрипт, но немного в другом стилеШаг 4. Отправим эти изменения в ветку git-rebase с комментарием git-rebase 1.

Шаг 5. И сделаем ещё один коммит git-rebase 2 с пушем, заменив echo "Parameter: $param" на echo "Next parameter: $param".

**Переходим в ветку main для поиска нужного коммита**    
git checkout main

**Находим хеш коммита с сообщением "prepare for merge and rebase" при помощи git log**  
git log --oneline

**После нахождения нужного хеша коммита, выполняем checkout на этот коммит**

**Заменяем 'commit_hash' на найденный хеш коммита**  
git checkout commit_hash

Создание ветки git-rebase:  
Создаем новую ветку git-rebase на основе текущего коммита  
git checkout -b git-rebase

Изменяем содержимого файла rebase.sh:

Проверяем изменения  
cat branching/rebase.sh

Добавляем изменения в индекс и создайте коммит с комментарием "git-rebase 1"  
git add branching/rebase.sh
git commit -m "git-rebase 1"

Отправляем изменения в ветку git-rebase на удаленный репозиторий  
git push -u origin git-rebase

 Создание второго коммита "git-rebase 2":

 Заменяем строку в файле rebase.sh     
sed -i 's/Parameter: /Next parameter: /' branching/rebase.sh  

Заменяем строку в файле rebase.sh  
sed -i 's/Parameter: /Next parameter: /' branching/rebase.sh  

Добавляем изменения в индекс и создайте второй коммит с комментарием "git-rebase 2"  
git add branching/rebase.sh  
git commit -m "git-rebase 2"  

Отпраляем изменения в ветку git-rebase на удаленный репозиторий
git push

![Image](https://github.com/Byzgaev-I/-Branching-in-Git-/blob/main/5.png)


Merge
Сливаем ветку git-merge в main и отправляем изменения в репозиторий, должно получиться без конфликтов:

В результате получаем такую схему:
![Image](https://github.com/Byzgaev-I/-Branching-in-Git-/blob/main/6.png)




