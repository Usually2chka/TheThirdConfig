# configuration-management-homework3
Домашки по конфигурационному управлению (номер 3!)
## Вариант 10
### Задание 3

Разработать инструмент командной строки для учебного конфигурационного
языка, синтаксис которого приведен далее. Этот инструмент преобразует текст из
входного формата в выходной. Синтаксические ошибки выявляются с выдачей
сообщений.

Входной текст на **учебном конфигурационном языке** принимается из
стандартного ввода. Выходной текст на **языке yaml** попадает в стандартный
вывод.

Однострочные комментарии:
```
" Это однострочный комментарий
```

Словари:
```
{
 имя = значение;
 имя = значение;
 имя = значение;
 ...
}
```

Имена:
```
[_a-z]+
```

Значения:
```
• Числа.
• Словари.
```

Объявление константы на этапе трансляции:
```
имя := значение;
```

Вычисление константного выражения на этапе трансляции (постфиксная
форма), пример:
```
[имя 1 +]
```

Результатом вычисления константного выражения является значение.
Для константных вычислений определены операции и функции:
```
1. Сложение.
2. mod().
```
   
Все конструкции учебного конфигурационного языка (с учетом их
возможной вложенности) должны быть покрыты тестами. Необходимо показать 3
примера описания конфигураций из разных предметных областей.

#### Общее описание проекта

Этот проект представляет собой парсер для учебного конфигурационного языка, который преобразует текст в формате конфигурации в формат YAML. Входные данные могут содержать объявления констант, словари и постфиксные выражения, которые обрабатываются и сохраняются в результирующем словаре. Конфигурация поддерживает числовые значения, строки и вложенные словари, а также позволяет вычислять константы на основе выражений с операциями сложения и взятия остатка (mod). Парсер также поддерживает построчную обработку и вывод данных в формате YAML.

#### Описание функций

1. `__init__`
  - Описание: Инициализирует объект парсера и создает контейнер для хранения констант.
  - Аргументы: Нет.
  - Возвращает: Нет.

2. `parse(text)`
 - Описание: Основной метод парсинга, который обрабатывает текст, извлекает константы и словари, а также вычисляет значения для выражений.
 - Аргументы: text — Входной текст в формате конфигурации.
 - Возвращает: Словарь, который содержит все константы и данные, преобразованные из входного текста, включая обработанные выражения и вложенные словари.
 
3. `_parse_constant(line)`
 - Описание: Обрабатывает строку, которая объявляет новую константу с заданным значением. Поддерживает как прямые числовые значения, так и вычисления через постфиксные выражения.
 - Аргументы: line — Строка, которая объявляет константу в формате имя := значение.
 - Возвращает: Кортеж, содержащий имя константы и ее значение (может быть числом или результатом вычисления выражения).

4. `_evaluate_expression(expr)`
 - Описание: Оценка постфиксного выражения. Применяется для вычисления значений констант, которые содержат операции сложения и взятия остатка (mod).
 - Аргументы: expr — Строка, представляющая постфиксное выражение (например, "80 10 +" или "port 50 mod").
 - Возвращает: Результат вычисления выражения (целое число).

5. `_parse_dictionary(line)`
 - Описание: Обрабатывает строку, которая представляет запись внутри словаря конфигурации. Преобразует строку в пару ключ-значение.
 - Аргументы: line — Строка в формате ключ = значение;, где значение может быть числом, строкой или константой.
 - Возвращает: Кортеж из ключа и обработанного значения (число, строка или ссылка на константу).

6. `main()`
 - Описание: Главная функция для запуска парсера. Читает входные данные из стандартного ввода, парсит их, а затем выводит результат в формате YAML.
 - Аргументы: Нет.
 - Возвращает: Нет.

#### Тест 1

##### Файл `input.txt` для быстрого ввода кода на учебном конфигурационном языке
![image](https://github.com/user-attachments/assets/00c8e98a-05cf-4e6b-a312-9f85e379bac5)
##### Результат работы программы с данным файлом
![image](https://github.com/user-attachments/assets/0b64c83b-66c3-4603-ad49-470934125547)



#### Тест 2

##### Файл `input_2.txt` для быстрого ввода кода на учебном конфигурационном языке
![image](https://github.com/user-attachments/assets/281609de-3130-463d-b834-939086f2fd1a)
##### Результат работы программы с данным файлом
![image](https://github.com/user-attachments/assets/662a07d0-2a8e-4808-8db2-a3ebd57b409b)



