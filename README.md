# Домашнее задание к занятию "`«Ветвления в Git»`"

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

### Задание «Решение»

