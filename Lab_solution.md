Рабочий скрипт bash:

```
#! /bin/bash

if [ $# -ne 1 ]; then
  echo "Использование файла: $0"
  exit 1
fi

FILE=$1

if [ ! -f "$FILE" ]; then
  echo "Файла $FILE не существует."
  exit 1
fi

lines=$(wc -l < "$FILE")
echo "Количество строк: $lines"

chars=$(wc -m < "$FILE")
echo "Количество символов: $chars"

questions=$(grep -oE "\b.*?\?" "$FILE" | wc -l)
echo "Количество вопросительных предложений: $questions"
# Используем именно \b, чтобы проверять на предложения, ибо если между словом и вопросительным знаком стоит пробел - за предложение не считаем

commas=$(grep -o "," "$FILE" | wc -l)
echo "Количество запятых: $commas"

longest_word=$(grep -oE '\w+' "$FILE" | awk '{ if (length($0) > length(max)) max=$0 } END { print max }')
echo "Самое длинное слово: $longest_word"
# Используем \w+ чтобы определять границы слова
```
Скрипт в sh файле:

![image](https://github.com/user-attachments/assets/09b617ee-ac65-4746-8812-4daf2a7ff3c8)

Запуск скрипта:

![image](https://github.com/user-attachments/assets/d311fb06-72a6-45e1-b741-928cbc53b6de)
