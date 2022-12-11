## Домашнее задание 1

### Сетка дедлайнов:

| дурацкое название | дата             | штраф
| ----------------  | ---------------- | ------------------------------------------------------------------- |
|  основной         | 06 ноября  23:59 | без штрафа, до этого момента получаем полный балл                |
|  1 промежуточный  | 13 ноября  23:59 | все баллы за решения, сданные с этого момента домножаются на 0.7 |
|  2 промежуточный  | 20 ноября  23:59 | все баллы за решения, сданные с этого момента домножаются на 0.5 |
|  3 промежуточный  | 27 ноября  23:59 | все баллы за решения, сданные с этого момента домножаются на 0.3 |
|  фатальный        | 04 декабря 23:59 | с этого момента, увы, не имеет смысла сдавать решения, совсем    |

### 1. Rand (2 балл)

Написать команду, которая будет создавать файл rnd.txt в текущем каталоге.

Размер файла rnd.txt -- случайное число байт.

Файл должен быть полностью заполнен случайными байтами.

Размер можно вычислять заранее, запоминая результат в переменной.

Используйте `dd`, переменную окружения `RANDOM` (`echo $RANDOM`, и см. `bash(1)`),
а также `/dev/urandom`.

### 2. Сумма (1 балл)

Посчитайте сумму значений в третьем столбце файла  `digits.txt`.

Используйте `paste`, чтобы сформировать выражение и `bc`, чтобы его вычислить.
Не забывайте про process subsctitution `$()`

### 3. Посчитаемся (1 балл)

Посчитайте количество регулярных файлов в текущем каталоге,
измененных больше 30 минут и меньше суток назад и имеющих расширение `.txt`.

Для решения используйте `find` и `wc`.

### 4. ping (1 балл)

В файле `ips.txt` записаны IP-адреса (по одному на каждой строчке).

Написать скрипт, считывающий IP-адреса из этого файла, пингует (команда `ping`) 
их и записывает результат в `res.txt`, а ошибки -- в `err.txt`.

Подсказка: 
```bash
while IFS= read -r line; do
    echo "Text read from file: $line"
done < my_filename.txt
```

### 5. Четное-нечетное (1 балл)
Введите целое число и проверьте, является ли оно чётным или нечётным. 
Скрипт должен запрашивать число, и выводить **EVEN** или **ODD** соответственно.

### 6. Палиндром (1 балл)
Написать скрипт, который проверяет, является ли введенная строка палиндромом. 
Скрипт должен запрашивать строку, и выводить **YES** или **NO** соответственно.

### 7. factor (1 балл)

Написать скрипт, который раскладывает на простые множители все числа из 
заданного в первом параметре скрипта файла и записывает результат в другой файл, 
заданный во втором параметре. Каждое число из разложения необходимо вывести 
столько раз, сколько оно там встречается (см. пример для числа 1236).

Пример входных данных:

    123
    15123
    1236
    97

Пример выходных данных:

    123: 3 41
    15123: 3 71 71
    1236: 2 2 3 103
    97: 97

### 8. find (1 балл)

Переименовать все файлы в текущем каталоге (с учетом всех подкаталогов рекурсивно),
имеющие расширение не .sh и измененные не более двух суток назад и не менее суток 
назад, добавив в начало имени файла символ '\_'.

Подсказка:

```
find . -print0 | 
    while IFS= read -r -d '' line 
    do
        echo $line
    done
```


### 9. cal (задача с маленькой звездочкой, 2 балла)

С помощью команд `cal`, `cat` и `grep` вывести текущее число. Выводить месяц и 
год необязательно, но можно.

Выводить весь календарь и утверждать, что условие задания выполнено запрещается.

### 10. Зоопарк (1 балл)

Имеется файл, содержащий сведения о животных в зоопарке:

    id;name;h;strike;color
    1;Chicken;12;0.38;Yellow
    2;Goose;18;0.11;Green
    3;Orca;8;0.81;Yellow
    4;Porcupine;19;0.74;Yellow
    5;Bear;23;0.14;Green
    6;Turtle;4;0.08;Black

Требуется организовать неэтичные бои без правил. Для этого нужно вывести имя 
животного (`name`) и тангенс его ударной силы (`strike`) 
(именно тангенс, не синус и косинус).

При этом интересуют нас только те животные, 
которые не выбыли из турнира, то есть те, перед которыми в списке было нечетное число животных того 
же цвета (`color`);

Пример вывода:

    Orca            1.0505
    Bear            0.1409

Примечания:
* Разрешено использовать только `awk`.
* Тангенс нужно выводить с точностью в четыре знака после запятой.