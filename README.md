<div align='center'> МИНОБРНАУКИ РОССИИ</div>
<div align='center'>Федеральное государственное бюджетное образовательное учреждение </div>
<div align='center'>высшего образования «Тульский государственный университет»</div>
<div align='center'>Институт прикладной математики и компьютерных наук</div>
<div align='center'>«Кафедра вычислительной техники» </div>
<p> </p>
<div align='center'>Отчёт по лабораторной работе №4</div>
<div align='center'>«Документация кода при помощи Doxygen»</div>
<div align='center'>по дисциплине «Визуальное моделирование и документирование</div>
<div align='center'>программного обеспечения»</div>
<div align='center'>Вариант 10</div>
<p></p>
<div align='center'><pre>Выполнил студент 4 курса группы 220611:           ____________ Картаков В. В.</pre></div>
<p></p>
<div align='center'><pre>Проверил доцент кафедры ВТ:                       ____________    Анцева Н. В.</pre></div>
<p></p>
<div align='center'>Тула 2024</div>
<p></p>




## ВВЕДЕНИЕ

Цель работы – изучить создание документации программ с помощью Doxygen, применение приобретенных навыков для получения документации на конкретную программу.

Задачи: 

1. Получить документацию для любой своей программы, разработанной в рамках дисциплин ВсСИИ либо ИсАС.
 
## ЭТАПЫ ВЫПОЛНЕНИЯ ЗАДАНИЯ

Создадим файл конфигурации файла Doxygen в папке с проектом, в соответствии с рисунком 1.

![Рисунок 1 – Создание файла конфигурации](https://github.com/{username}/{repository}/raw/{branch}/{path}/image.png)

Пропишем необходимые параметры в файле конфигурации:

Параметр        |     Значение    |  Пояснение
---------------:|----------------:|---------------:
PROJECT_NAME    |     "Lab4"      | Название проекта
INPUT           |      l4.py      | Файл на основе которого создается документация
RECURSIVE       |       NO 		    | Обработка только файла указанного в конфигурации
GENERATE_HTML   |       YES	      | Создание HTML-файла
GENERATE_LATEX  |       NO        | Отмена создания Latex файла 
EXTRACT_ALL     |       YES       | включать в документацию все элементы

В качестве кода для формирования документации возьмем 4 лабораторную работу по дисциплине ВвСИИ.

Добавим структуры с пояснениями кода (измененный код представлен в Приложении).

Создадим документацию в соответствии с рисунком 2.
 
![Рисунок 2 – Создание документации](https://github.com/{username}/{repository}/raw/{branch}/{path}/image.png)

Созданная документация представлена в соответствии с рисунками 3-5.
 
![Рисунок 3 – Главная страница документации](https://github.com/{username}/{repository}/raw/{branch}/{path}/image.png)
 
![Рисунок 4 - Документация](https://github.com/{username}/{repository}/raw/{branch}/{path}/image.png)
 
![Рисунок 5 – Методы и переменные программы](https://github.com/{username}/{repository}/raw/{branch}/{path}/image.png)

### Вывод: 

В процессе выполнения лабораторной работы изучено создание документации программ с помощью Doxygen, применены приобретенные навыки для получения документации на конкретную программу.

### Список использованных источников:

1. Doxygen: документация кода [Электронный ресурс]. — URL: https://www.doxygen.nl/manual/index.html
   
3. Как использовать Doxygen для документирования кода [Электронный ресурс]. — URL: https://habr.com/ru/post/350200/
   
5. Doxygen: Простой способ документирования кода [Электронный ресурс]. — URL: https://dev.to/yourusername/documenting-code-with-doxygen-3n0b
   
7. Документирование кода с помощью Doxygen [Электронный ресурс]. — URL: https://www.jetbrains.com/help/idea/doxygen.html.

## ПРИЛОЖЕНИЕ
```python
import numpy as np

def f(x):
    """
    Вычисляет гиперболический тангенс для заданного значения.

    Эта функция принимает одно числовое значение и возвращает 
    гиперболический тангенс этого значения. Гиперболический тангенс 
    определяется как отношение гиперболического синуса к гиперболическому косинусу.

    :param x: Входное значение (float) для вычисления гиперболического тангенса.
    :return: Значение гиперболического тангенса (float).
    """
    return np.tanh(x)  # Используем гиперболический тангенс

def df(x):
    """
    Вычисляет производную функции гиперболического тангенса.

    Эта функция принимает одно числовое значение и возвращает 
    производную гиперболического тангенса, которая равна 
    1 минус квадрат гиперболического тангенса.

    :param x: Входное значение (float) для вычисления производной.
    :return: Производная функции tanh (float).
    """
    return 1 - np.tanh(x)**2  # Производная функции tanh

# Инициализация весов с использованием нормального распределения
np.random.seed(42)  # Устанавливаем начальное значение генератора случайных чисел для воспроизводимости результатов
W1 = np.random.normal(0, 0.5, (2, 4))  # Веса первого слоя: 2 нейрона, 4 входа
W2 = np.random.normal(0, 0.5, 2)  # Веса второго слоя: 2 нейрона на выходе

def go_forward(inp):
    """
    Выполняет прямой проход через нейронную сеть.

    Эта функция принимает входные данные, вычисляет выходы нейронов 
    первого слоя и возвращает выходное значение нейронной сети.

    :param inp: Входные данные (нормализованный массив) для нейронной сети.
    :return: Кортеж, содержащий выходное значение (float) и выходы нейронов первого слоя (numpy array).
    """
    sum = np.dot(W1, inp)  # Вычисляем взвешенную сумму входов для первого слоя
    out = np.array([f(x) for x in sum])  # Применяем активационную функцию к выходам первого слоя
    sum = np.dot(W2, out)  # Вычисляем взвешенную сумму для выходного слоя
    y = f(sum)  # Применяем активационную функцию к выходу сети
    return (y, out)  # Возвращаем выходное значение и выходы первого слоя

def train(epoch):
    """
    Обучает нейронную сеть на заданной выборке.

    Эта функция выполняет обучение нейронной сети, используя 
    алгоритм обратного распространения ошибки.

    :param epoch: Обучающая выборка, состоящая из входных данных и целевых значений.
    """
    global W2, W1  # Объявляем глобальные переменные для весов
    lmd = 0.01  # Шаг обучения
    N = 10000  # Число итераций при обучении
    count = len(epoch)  # Количество примеров в обучающей выборке
    
    for k in range(N):  # Цикл обучения
        x = epoch[np.random.randint(0, count)]  # Случайный выбор примера из обучающей выборки
        y, out = go_forward(x[0:4])  # Прямой проход по НС и вычисление выходных значений нейронов
        e = y - x[-1]  # Вычисляем ошибку
        delta = e * df(y)  # Локальный градиент для выходного слоя
        W2[0] = W2[0] - lmd * delta * out[0]  # Корректировка веса первой связи
        W2[1] = W2[1] - lmd * delta * out[1]  # Корректировка веса второй связи
        
        delta2 = W2 * delta * df(out)  # Вектор локальных градиентов для первого слоя
        # Корректировка весов первого слоя
        W1[0, :] = W1[0, :] - np.array(x[0:4]) * delta2[0 ] * lmd  # Корректировка весов для первого нейрона
        W1[1, :] = W1[1, :] - np.array(x[0:4]) * delta2[1] * lmd  # Корректировка весов для второго нейрона

# Словарь с жанрами
genres_dict = {
    "Комедия": 0,
    "Драма": 1,
    "Экшн": 2,
    "Ужасы": 3,
    "Фантастика": 4
}

def normalize_input(cost, time, place, genre):
    """
    Нормализует входные данные для нейронной сети.

    Эта функция принимает стоимость, время, ряд и жанр, 
    нормализует их и возвращает массив, который можно использовать 
    в нейронной сети.

    :param cost: Стоимость (float).
    :param time: Время (float).
    :param place: Ряд (int).
    :param genre: Жанр (str).
    :return: Нормализованный массив входных данных (numpy array).
    """
    normalized_cost = cost / 1500  # Нормализуем стоимость
    normalized_time = time / 24     # Нормализуем время
    normalized_place = place / 12    # Нормализуем ряд
    normalized_genre = genres_dict[genre] / 4  # Нормализуем жанр (0-4)
    return np.array([normalized_cost, normalized_time, normalized_place, normalized_genre])  # Возвращаем нормализованный массив

# Обучающая выборка (стоимость, время, ряд, жанр, выбор)
epoch = [
    (100, 10, 0, 0, 1),   # Комедия
    (200, 12, 1, 1, -1),  # Драма
    (300, 15, 2, 2, 1),   # Экшн
    (400, 20, 3, 3, -1),  # Ужасы
    (500, 18, 4, 4, 1),   # Фантастика
    (600, 14, 5, 0, -1),  # Комедия
    (700, 16, 6, 1, 1),   # Драма
    (800, 22, 7, 2, -1),  # Экшн
    (900, 19, 8, 3, 1),   # Ужасы
    (1000, 25, 9, 4, -1), # Фантастика
    (1100, 11, 10, 0, 1), # Комедия
    (1200, 13, 11, 1, -1),# Драма
    (1300, 17, 0, 2, 1),  # Экшн
    (1400, 21, 1, 3, -1), # Ужасы
    (1500, 24, 2, 4, 1),  # Фантастика
    (250, 15, 3, 0, -1),  # Комедия
    (350, 12, 4, 1, 1),   # Драма
    (450, 20, 5, 2, -1),  # Экшн
    (550, 18, 6, 3, 1),   # Ужасы
    (650, 14, 7, 4, -1),  # Фантастика
    (750, 16, 8, 0, 1),   # Комедия
    (850, 22, 9, 1, -1),  # Драма
    (950, 19, 10, 2, 1),  # Экшн
    (1050, 25, 11, 3, -1),# Ужасы
    (1150, 12, 0, 4, 1),  # Фантастика
]

train(epoch)  # Запуск обучения сети

# Проверка полученных результатов
while True:
    cost = float(input("Введите стоимость:"))  # Запрос стоимости у пользователя
    time = float(input("Введите время:")[0:2])  # Запрос времени у пользователя
    place = int(input("Введите ряд:"))  # Запрос ряда у пользователя
    genre_input = input ("Введите жанр (Комедия, Драма, Экшн, Ужасы, Фантастика):")  # Запрос жанра у пользователя
    
    if genre_input in genres_dict:  # Проверка, существует ли введенный жанр в словаре
        normalized_input = normalize_input(cost, time, place, genre_input)  # Нормализация входных данных
        y, out = go_forward(normalized_input)  # Прямой проход через нейронную сеть
        if y > 0:  # Проверка, стоит ли покупать
            print("Стоит купить")  # Вывод рекомендации
        else:
            print("Не стоит покупать")  # Вывод рекомендации
    else:
        print("Неверный жанр. Пожалуйста, попробуйте снова.")  # Обработка неверного ввода жанра

```
