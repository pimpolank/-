## Задача 1
Вывести служебную информацию о пакете matplotlib (Python). Разобрать основные элементы содержимого файла со служебной информацией из пакета. Как получить пакет без менеджера пакетов, прямо из репозитория?
![image](https://github.com/user-attachments/assets/fb4969a8-a5a0-45a3-bb18-41211e6e39c2)

## Задача 2
Вывести служебную информацию о пакете express (JavaScript). Разобрать основные элементы содержимого файла со служебной информацией из пакета. Как получить пакет без менеджера пакетов, прямо из репозитория?
![image](https://github.com/user-attachments/assets/abb76e93-1444-419c-9cd5-97f74d11bec3)


## Задача 3
Сформировать graphviz-код и получить изображения зависимостей matplotlib и express.
```bash
pipdeptree --packages matplotlib --graph-output dot > matplotlib_deps.dot
```
![image](https://github.com/user-attachments/assets/835fc547-7922-4d08-b258-7865b8451a5e)
![express_bdeps](https://github.com/user-attachments/assets/6d066f72-ea2f-4957-b330-b727495460f6)


## Задача 4
Решить на MiniZinc задачу о счастливых билетах. Добавить ограничение на то, что все цифры билета должны быть различными (подсказка: используйте all_different). Найти минимальное решение для суммы 3 цифр.


![image](https://github.com/user-attachments/assets/d6d7b056-58e4-4880-ac80-cc33b6f64786)


## Задача 5

Решить на MiniZinc задачу о зависимостях пакетов для рисунка, приведенного ниже.
![image](https://github.com/user-attachments/assets/0050a54f-b3a1-4ac6-a541-218ae44677fb)


## Задача 6
Решить на MiniZinc задачу о зависимостях пакетов для следующих данных:
```bash
root 1.0.0 зависит от foo ^1.0.0 и target ^2.0.0.
foo 1.1.0 зависит от left ^1.0.0 и right ^1.0.0.
foo 1.0.0 не имеет зависимостей.
left 1.0.0 зависит от shared >=1.0.0.
right 1.0.0 зависит от shared <2.0.0.
shared 2.0.0 не имеет зависимостей.
shared 1.0.0 зависит от target ^1.0.0.
target 2.0.0 и 1.0.0 не имеют зависимостей.
```
![image](https://github.com/user-attachments/assets/517aa58b-05b7-4590-baf3-d5204c227a18)


## Задача 7

![image](https://github.com/user-attachments/assets/17974e48-b647-4ece-b723-b9d1b8c805da)
