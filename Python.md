# 📚 ПОЛНЫЙ КУРС PYTHON ДЛЯ НАЧИНАЮЩИХ (С НУЛЯ ДО ML)

## ОГЛАВЛЕНИЕ
1. Переменные и типы данных
2. Строки
3. Списки
4. Кортежи
5. Множества
6. Словари
7. Условия
8. Циклы
9. Функции
10. Lambda-функции
11. Map, Filter, Reduce
12. List Comprehensions и Generators
13. Обработка ошибок (try/except)
14. Работа с файлами и JSON
15. ООП — Классы и объекты
16. Декораторы
17. Collections (Counter, defaultdict, namedtuple, deque)
18. Itertools
19. NumPy для начинающих
20. Контекстные менеджеры
21. Аннотации типов (typing)
22. Виртуальные окружения и Git
23. Итоговая шпаргалка

---

# 1. ПЕРЕМЕННЫЕ И ТИПЫ ДАННЫХ

```python
# ==========================================
# БАЗОВЫЕ ТИПЫ
# ==========================================

name = "Алексей"          # str — строка
age = 25                   # int — целое число
salary = 75000.50          # float — дробное число
is_employed = True         # bool — логический (True/False)
nothing = None             # NoneType — отсутствие значения

# Проверка типа
print(type(name))          # <class 'str'>
print(type(age))           # <class 'int'>
print(type(salary))        # <class 'float'>
print(type(is_employed))   # <class 'bool'>

# ==========================================
# ПРЕОБРАЗОВАНИЕ ТИПОВ
# ==========================================

x = int("25")              # строку → число       25
y = float("3.14")          # строку → дробное     3.14
z = str(100)               # число → строку       "100"
b = bool(0)                # число → bool         False

# Falsy значения (считаются False):
# None, 0, 0.0, "", [], {}, set(), False

# ==========================================
# АННОТАЦИИ ТИПОВ (Type Hints)
# ==========================================
# Это подсказки — Python их НЕ проверяет автоматически
# Нужны для читаемости и IDE

name: str = "Анна"
age: int = 25
salary: float = 90000.0

def greet(name: str) -> str:          # принимает str, возвращает str
    return f"Привет, {name}"

def add(a: int, b: int) -> int:       # принимает int, возвращает int
    return a + b

def get_users() -> list:              # возвращает список
    return ["Анна", "Борис"]

def get_config() -> dict:             # возвращает словарь
    return {"host": "localhost"}

# Как читать:
# weight: float   → параметр должен быть float
# -> float        → функция возвращает float
```

---

# 2. СТРОКИ

```python
text = "Data Engineering"

# ==========================================
# ИНДЕКСАЦИЯ И СРЕЗЫ
# ==========================================

print(text[0])             # 'D'       — первый символ
print(text[-1])            # 'g'       — последний символ
print(text[0:4])           # 'Data'    — срез от 0 до 4 (не включая)
print(text[5:])            # 'Engineering'
print(text[:4])            # 'Data'
print(text[::2])           # 'Dt niern' — каждый 2-й символ
print(text[::-1])          # 'gnireenignE ataD' — разворот

# ==========================================
# ОСНОВНЫЕ МЕТОДЫ
# ==========================================

print(text.upper())        # 'DATA ENGINEERING'
print(text.lower())        # 'data engineering'
print(text.strip())        # убирает пробелы по краям
print(text.split(" "))     # ['Data', 'Engineering']
print(text.replace("Data", "Software"))  # 'Software Engineering'
print(text.startswith("Data"))  # True
print(text.endswith("ing"))     # True
print(text.find("Eng"))         # 5 — индекс начала
print(text.count("n"))          # 3 — количество вхождений
print(" ".join(["a", "b", "c"]))  # 'a b c'

# ==========================================
# F-STRINGS — форматирование (рекомендуется)
# ==========================================

name = "Анна"
age = 30
salary = 85000.567

print(f"Имя: {name}, Возраст: {age}")       # Имя: Анна, Возраст: 30
print(f"Зарплата: {salary:.2f}")            # Зарплата: 85000.57
print(f"{'=' * 20}")                         # ====================
print(f"{age:>10}")                          #         30  (выравнивание)
print(f"{age:0>5}")                          # 00030       (заполнение нулями)
```

---

# 3. СПИСКИ

```python
fruits = ["яблоко", "банан", "вишня", "дыня"]

# ==========================================
# ИНДЕКСАЦИЯ И СРЕЗЫ
# ==========================================

print(fruits[0])           # 'яблоко'
print(fruits[-1])          # 'дыня'
print(fruits[1:3])         # ['банан', 'вишня']
print(fruits[::-1])        # развёрнутый список

# ==========================================
# ИЗМЕНЕНИЕ
# ==========================================

fruits.append("ежевика")          # добавить в конец
fruits.insert(1, "груша")         # вставить на позицию 1
fruits.extend(["киви", "манго"])  # добавить несколько
fruits.remove("банан")            # удалить по значению
popped = fruits.pop()             # удалить последний и вернуть
popped2 = fruits.pop(0)          # удалить по индексу
del fruits[0]                     # удалить без возврата

# ==========================================
# ПОЛЕЗНЫЕ МЕТОДЫ
# ==========================================

nums = [3, 1, 4, 1, 5, 9, 2, 6]

print(len(nums))           # 8
print(min(nums))           # 1
print(max(nums))           # 9
print(sum(nums))           # 31
print(nums.count(1))       # 2
print(nums.index(5))       # 4

nums.sort()                # сортировка на месте
nums.sort(reverse=True)    # по убыванию
sorted_new = sorted(nums)  # новый список, исходный не меняется

print(5 in nums)           # True
print(100 not in nums)     # True

# ==========================================
# КОПИРОВАНИЕ (важно!)
# ==========================================

original = [1, 2, 3]

wrong = original           # НЕ копия — это ссылка!
wrong.append(4)
print(original)            # [1, 2, 3, 4] — оригинал изменился!

copy1 = original.copy()    # правильная копия
copy2 = original[:]        # правильная копия
copy3 = list(original)     # правильная копия

# Вложенные списки — нужен deepcopy
import copy
nested = [[1, 2], [3, 4]]
deep = copy.deepcopy(nested)
```

---

# 4. КОРТЕЖИ

```python
# Кортеж — неизменяемый список
coordinates = (55.7558, 37.6173)
single = (42,)             # кортеж из одного элемента — запятая обязательна!

print(coordinates[0])      # 55.7558
# coordinates[0] = 100    # TypeError — нельзя изменить!

# Распаковка
lat, lon = coordinates
print(f"Широта: {lat}, Долгота: {lon}")

first, *rest = (1, 2, 3, 4, 5)
print(first)               # 1
print(rest)                # [2, 3, 4, 5]

# Зачем кортежи:
# 1. Быстрее списков
# 2. Могут быть ключами словаря
# 3. Защита от случайного изменения
```

---

# 5. МНОЖЕСТВА

```python
colors = {"red", "green", "blue"}

# Удаление дубликатов из списка
names = ["Аня", "Боря", "Аня", "Витя"]
unique = set(names)        # {'Аня', 'Боря', 'Витя'}

colors.add("yellow")       # добавить
colors.remove("red")       # удалить (ошибка если нет)
colors.discard("purple")   # удалить (без ошибки)

# ==========================================
# ОПЕРАЦИИ С МНОЖЕСТВАМИ
# ==========================================

frontend = {"HTML", "CSS", "JavaScript", "Python"}
backend = {"Python", "Java", "SQL"}

print(frontend & backend)  # {'Python'}       — пересечение
print(frontend | backend)  # все элементы     — объединение
print(frontend - backend)  # {'HTML', 'CSS', 'JavaScript'} — разность
print(frontend ^ backend)  # всё кроме общего — симметричная разность
```

---

# 6. СЛОВАРИ

```python
person = {
    "name": "Алексей",
    "age": 28,
    "skills": ["Python", "SQL"],
}

# ==========================================
# ДОСТУП К ДАННЫМ
# ==========================================

print(person["name"])               # 'Алексей'
print(person.get("salary"))         # None (безопасный доступ)
print(person.get("salary", 0))      # 0 (значение по умолчанию)

# ==========================================
# ИЗМЕНЕНИЕ
# ==========================================

person["age"] = 29                  # изменить
person["city"] = "Москва"          # добавить
del person["city"]                  # удалить
salary = person.pop("age")         # удалить и вернуть

# ==========================================
# ПЕРЕБОР
# ==========================================

for key in person:     # keys
    print(key)

for value in person.values():
    print(value)

for key, value in person.items():
    print(f"{key}: {value}")

# ==========================================
# ОБЪЕДИНЕНИЕ СЛОВАРЕЙ
# ==========================================

d1 = {"a": 1, "b": 2}
d2 = {"b": 3, "c": 4}

merged = {**d1, **d2}          # {"a": 1, "b": 3, "c": 4}
merged = d1 | d2               # то же самое (Python 3.9+)
```

---

# 7. УСЛОВИЯ

```python
age = 25

if age < 18:
    print("Несовершеннолетний")
elif age < 65:
    print("Взрослый")
else:
    print("Пенсионер")

# ==========================================
# ОПЕРАТОРЫ СРАВНЕНИЯ И ЛОГИКИ
# ==========================================

# ==  равно          !=  не равно
# >   больше         <   меньше
# >=  больше/равно   <=  меньше/равно

# and — оба True
# or  — хотя бы одно True
# not — инвертирование

if age > 20 and age < 60:
    print("Работоспособный")

if age < 18 or age > 65:
    print("Льготы")

# ==========================================
# ТЕРНАРНЫЙ ОПЕРАТОР
# ==========================================

status = "взрослый" if age >= 18 else "ребёнок"
print(status)                       # 'взрослый'

# ==========================================
# ПРОВЕРКИ
# ==========================================

value = None
if value is None:
    print("Нет данных")

if isinstance(age, int):
    print("Это целое число")

items = []
if not items:                       # пустой список = False
    print("Список пуст")
```

---

# 8. ЦИКЛЫ

```python
# ==========================================
# ЦИКЛ FOR
# ==========================================

fruits = ["яблоко", "банан", "вишня"]
for fruit in fruits:
    print(fruit)

# range()
for i in range(5):          # 0, 1, 2, 3, 4
    print(i)

for i in range(2, 10):      # 2, 3, ..., 9
    print(i)

for i in range(0, 20, 3):   # 0, 3, 6, 9, 12, 15, 18
    print(i)

# enumerate() — индекс + значение
for i, fruit in enumerate(fruits):
    print(f"{i}: {fruit}")

for i, fruit in enumerate(fruits, start=1):  # нумерация с 1
    print(f"{i}: {fruit}")

# zip() — параллельный перебор
names = ["Аня", "Боря"]
ages = [25, 30]
for name, age in zip(names, ages):
    print(f"{name} — {age} лет")

# ==========================================
# ЦИКЛ WHILE
# ==========================================

count = 0
while count < 5:
    print(count)
    count += 1

# ==========================================
# BREAK, CONTINUE, ELSE
# ==========================================

# break — выход из цикла
for num in range(10):
    if num == 5:
        break
    print(num)              # 0, 1, 2, 3, 4

# continue — пропустить итерацию
for num in range(10):
    if num % 2 == 0:
        continue
    print(num)              # 1, 3, 5, 7, 9

# else — выполняется если цикл не прерван break
for num in range(5):
    if num == 100:
        break
else:
    print("Цикл завершился нормально")  # выполнится
```

---

# 9. ФУНКЦИИ

```python
# ==========================================
# БАЗОВАЯ СТРУКТУРА
# ==========================================

def имя_функции(параметры):
    """Docstring — описание"""
    # тело
    return результат

# ==========================================
# ВИДЫ ФУНКЦИЙ
# ==========================================

# Без параметров
def say_hello():
    print("Привет!")

say_hello()                 # Привет!

# С параметрами
def greet(name):
    print(f"Привет, {name}!")

greet("Анна")               # Привет, Анна!

# С возвратом значения
def add(a, b):
    return a + b

result = add(3, 5)
print(result)               # 8

# ==========================================
# RETURN
# ==========================================

# БЕЗ return → функция возвращает None
def no_return(a, b):
    result = a + b          # вычисляет, но не возвращает

x = no_return(3, 5)
print(x)                    # None

# Return завершает функцию немедленно
def check_age(age):
    if age < 0:
        return "Ошибка"     # выходим здесь
    if age < 18:
        return "Ребёнок"    # или здесь
    return "Взрослый"       # или здесь

print(check_age(-1))        # Ошибка
print(check_age(10))        # Ребёнок
print(check_age(25))        # Взрослый

# Возврат НЕСКОЛЬКИХ значений (кортеж)
def min_max(numbers):
    return min(numbers), max(numbers)

result = min_max([3, 1, 9, 4])
print(result)               # (1, 9)
print(type(result))         # <class 'tuple'>

# Распаковка
minimum, maximum = min_max([3, 1, 9, 4])
print(f"Мин: {minimum}, Макс: {maximum}")  # Мин: 1, Макс: 9

# ==========================================
# ПАРАМЕТРЫ ПО УМОЛЧАНИЮ
# ==========================================

def connect(host="localhost", port=5432, database="postgres"):
    print(f"Подключение: {host}:{port}/{database}")

connect()                               # localhost:5432/postgres
connect("192.168.1.1")                  # 192.168.1.1:5432/postgres
connect(port=5433, database="mydb")     # localhost:5433/mydb

# ⚠️ ЛОВУШКА — изменяемый объект как умолчание
def bad(item, lst=[]):          # список создаётся ОДИН РАЗ!
    lst.append(item)
    return lst

print(bad(1))                   # [1]
print(bad(2))                   # [1, 2] — не сбросился!

def good(item, lst=None):       # ПРАВИЛЬНО
    if lst is None:
        lst = []
    lst.append(item)
    return lst

print(good(1))                  # [1]
print(good(2))                  # [2] — свежий список

# ==========================================
# ПОЗИЦИОННЫЕ И ИМЕНОВАННЫЕ АРГУМЕНТЫ
# ==========================================

def describe(name, age, city):
    print(f"{name}, {age} лет, {city}")

# Позиционные — порядок важен
describe("Анна", 25, "Москва")

# Именованные — порядок не важен
describe(age=25, city="Москва", name="Анна")

# Смешанные — позиционные ВСЕГДА первыми
describe("Борис", city="Питер", age=30)

# ==========================================
# *args — переменное число позиционных аргументов
# ==========================================
# *args собирает в КОРТЕЖ

def sum_all(*args):
    print(f"Тип: {type(args)}")     # <class 'tuple'>
    print(f"Значения: {args}")
    return sum(args)

print(sum_all(1, 2, 3))             # 6
print(sum_all(10, 20, 30, 40, 50)) # 150

# Комбинация с обычными параметрами
def greet_many(greeting, *names):
    for name in names:
        print(f"{greeting}, {name}!")

greet_many("Привет", "Анна", "Борис", "Витя")
# Привет, Анна!
# Привет, Борис!
# Привет, Витя!

# Распаковка списка при вызове
numbers = [1, 2, 3, 4, 5]
print(sum_all(*numbers))            # * распаковывает список

# ==========================================
# **kwargs — переменное число именованных аргументов
# ==========================================
# **kwargs собирает в СЛОВАРЬ

def create_user(**kwargs):
    print(f"Тип: {type(kwargs)}")   # <class 'dict'>
    for key, value in kwargs.items():
        print(f"  {key}: {value}")

create_user(name="Анна", age=25, role="admin")
# name: Анна
# age: 25
# role: admin

# Распаковка словаря при вызове
params = {"n_estimators": 100, "max_depth": 5}

def train(n_estimators, max_depth):
    print(f"n_estimators={n_estimators}, max_depth={max_depth}")

train(**params)             # ** распаковывает словарь

# ==========================================
# ПРАВИЛЬНЫЙ ПОРЯДОК ПАРАМЕТРОВ
# ==========================================
# 1. Обычные параметры
# 2. *args
# 3. **kwargs

def full(a, b, *args, **kwargs):
    print(f"a={a}, b={b}")
    print(f"args={args}")
    print(f"kwargs={kwargs}")

full(1, 2, 3, 4, 5, name="Анна", age=25)
# a=1, b=2
# args=(3, 4, 5)
# kwargs={'name': 'Анна', 'age': 25}

# ==========================================
# АННОТАЦИИ ТИПОВ (Type Hints)
# ==========================================
# Python НЕ проверяет их автоматически
# Это подсказки для разработчика и IDE

def calculate_bmi(weight: float, height: float) -> float:
    return weight / (height ** 2)

# Читается:
# weight: float  → ожидается float
# height: float  → ожидается float
# -> float       → возвращает float

result = calculate_bmi(70, 1.75)
print(f"BMI: {result:.1f}")     # BMI: 22.9

# ==========================================
# DOCSTRING — документация функции
# ==========================================

def process(filepath: str, sep: str = ",") -> list:
    """
    Обрабатывает данные из файла.

    Args:
        filepath: Путь к файлу
        sep: Разделитель полей

    Returns:
        Список обработанных строк

    Raises:
        FileNotFoundError: Если файл не найден
    """
    pass

help(process)   # выводит документацию

# ==========================================
# ОБЛАСТЬ ВИДИМОСТИ (SCOPE)
# ==========================================

x = 10                      # глобальная переменная

def show():
    y = 20                  # локальная переменная
    print(f"x={x}, y={y}")  # x видна — читаем глобальную

show()                      # x=10, y=20
print(x)                    # 10
# print(y)                  # NameError — y не существует снаружи!

# Функция НЕ изменяет глобальную (создаёт локальную копию)
x = 10

def try_change():
    x = 99                  # НОВАЯ локальная x
    print(f"Внутри: {x}")

try_change()                # Внутри: 99
print(f"Снаружи: {x}")     # Снаружи: 10  — не изменилась!

# global — изменить глобальную (используй редко)
counter = 0

def increment():
    global counter
    counter += 1

increment()
increment()
print(counter)              # 2

# ==========================================
# ФУНКЦИИ КАК ОБЪЕКТЫ
# ==========================================

def square(x):
    return x ** 2

# Присвоить переменной
my_func = square
print(my_func(5))           # 25

# Передать как аргумент
def apply(func, value):
    return func(value)

print(apply(square, 4))     # 16

# Список функций
operations = [square, abs, str]
for op in operations:
    print(f"{op.__name__}(-3) = {op(-3)}")
# square(-3) = 9
# abs(-3) = 3
# str(-3) = -3

# ==========================================
# ВЛОЖЕННЫЕ ФУНКЦИИ И ЗАМЫКАНИЯ
# ==========================================

def outer(x):
    def inner(y):
        return x + y        # inner помнит x из outer
    return inner

add_5 = outer(5)
add_10 = outer(10)

print(add_5(3))             # 8   (5 + 3)
print(add_10(3))            # 13  (10 + 3)

# Реальный пример — фабрика функций
def make_multiplier(factor):
    def multiply(x):
        return x * factor
    return multiply

double = make_multiplier(2)
triple = make_multiplier(3)

print(double(5))            # 10
print(triple(5))            # 15
```

---

# 10. LAMBDA-ФУНКЦИИ

```python
# lambda — анонимная однострочная функция
# lambda аргументы: выражение

# Обычная функция
def square(x):
    return x ** 2

# Lambda-эквивалент
square = lambda x: x ** 2
print(square(5))            # 25

# Несколько аргументов
add = lambda a, b: a + b
print(add(3, 5))            # 8

# С условием
classify = lambda x: "+" if x > 0 else "-" if x < 0 else "0"
print(classify(5))          # +
print(classify(-3))         # -
print(classify(0))          # 0

# ==========================================
# LAMBDA + SORTED (самое частое применение)
# ==========================================

students = [("Анна", 85), ("Борис", 92), ("Витя", 78)]
by_grade = sorted(students, key=lambda x: x[1])
print(by_grade)
# [('Витя', 78), ('Анна', 85), ('Борис', 92)]

employees = [
    {"name": "Анна", "salary": 90000},
    {"name": "Борис", "salary": 85000},
    {"name": "Витя", "salary": 95000},
]
by_salary = sorted(employees, key=lambda e: e["salary"], reverse=True)
print(by_salary[0]["name"])  # Витя
```

---

# 11. MAP, FILTER, REDUCE

```python
from functools import reduce

numbers = [1, 2, 3, 4, 5]

# ==========================================
# MAP — применяет функцию к каждому элементу
# ==========================================

squares = list(map(lambda x: x ** 2, numbers))
print(squares)              # [1, 4, 9, 16, 25]

# Преобразование типов
strings = ["1", "2", "3"]
ints = list(map(int, strings))
print(ints)                 # [1, 2, 3]

# ==========================================
# FILTER — отбирает элементы по условию
# ==========================================

positive = list(filter(lambda x: x > 0, [1, -2, 3, -4, 5]))
print(positive)             # [1, 3, 5]

# Фильтрация непустых строк
data = ["hello", "", "world", "", "python"]
non_empty = list(filter(None, data))
print(non_empty)            # ['hello', 'world', 'python']

# ==========================================
# REDUCE — свёртка к одному значению
# ==========================================

total = reduce(lambda acc, x: acc + x, numbers)
print(total)                # 15

product = reduce(lambda acc, x: acc * x, numbers)
print(product)              # 120

# ==========================================
# MAP vs LIST COMPREHENSION
# ==========================================

# Одно и то же:
result1 = list(map(lambda x: x ** 2, numbers))
result2 = [x ** 2 for x in numbers]

# List comprehension обычно читается лучше
# map удобен когда уже есть готовая функция:
result3 = list(map(str, numbers))   # проще чем [str(x) for x in numbers]
```

---

# 12. LIST COMPREHENSIONS И GENERATORS

```python
# ==========================================
# LIST COMPREHENSION — создаёт список в памяти
# ==========================================

# [выражение for элемент in итерируемый]
squares = [x ** 2 for x in range(10)]
print(squares)
# [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# [выражение for элемент in итерируемый if условие]
even_squares = [x ** 2 for x in range(10) if x % 2 == 0]
print(even_squares)
# [0, 4, 16, 36, 64]

# [выр_если_true if условие else выр_если_false for элемент in ...]
labels = ["чётное" if x % 2 == 0 else "нечётное" for x in range(6)]
print(labels)
# ['чётное', 'нечётное', 'чётное', 'нечётное', 'чётное', 'нечётное']

# ==========================================
# ВЛОЖЕННЫЕ ЦИКЛЫ
# ==========================================

pairs = [(x, y) for x in range(3) for y in range(3)]
print(pairs)
# [(0,0), (0,1), (0,2), (1,0), (1,1), (1,2), (2,0), (2,1), (2,2)]

# Flatten — раскрытие вложенного списка
nested = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flat = [num for sublist in nested for num in sublist]
print(flat)
# [1, 2, 3, 4, 5, 6, 7, 8, 9]

# ==========================================
# DICT COMPREHENSION
# ==========================================

names = ["Анна", "Борис", "Витя"]
lengths = {name: len(name) for name in names}
print(lengths)
# {'Анна': 4, 'Борис': 5, 'Витя': 4}

# Инвертирование словаря
original = {"a": 1, "b": 2, "c": 3}
inverted = {v: k for k, v in original.items()}
print(inverted)
# {1: 'a', 2: 'b', 3: 'c'}

# Фильтрация словаря
prices = {"apple": 100, "banana": 50, "cherry": 200}
expensive = {k: v for k, v in prices.items() if v > 80}
print(expensive)
# {'apple': 100, 'cherry': 200}

# ==========================================
# SET COMPREHENSION
# ==========================================

words = ["hello", "HELLO", "Hello", "world"]
unique_lower = {w.lower() for w in words}
print(unique_lower)
# {'hello', 'world'}

# ==========================================
# GENERATOR EXPRESSION — экономит память
# ==========================================

# List comprehension — создаёт список сразу в памяти
big_list = [x ** 2 for x in range(1000000)]  # много памяти!

# Generator — вычисляет по одному элементу
big_gen = (x ** 2 for x in range(1000000))   # мало памяти (112 байт)

# Удобно в функциях
total = sum(x ** 2 for x in range(1000000))  # без создания списка

# ==========================================
# ГЛАВНОЕ ОТЛИЧИЕ
# ==========================================

# List comprehension — все данные в памяти
lst = [x for x in range(5)]
print(lst[0])    # можно по индексу
print(len(lst))  # можно узнать длину

# Generator — данные по одному
gen = (x for x in range(5))
# print(gen[0])  # TypeError!
# print(len(gen))  # TypeError!

for val in gen:  # можно только один раз пройти
    print(val)
# второй проход — пусто!
```

---

# 13. ОБРАБОТКА ОШИБОК (TRY/EXCEPT)

```python
# ==========================================
# TRY / EXCEPT — ПЕРЕХВАТ ОШИБОК
# ==========================================

# Без try/except программа упадёт
# number = int("hello")  # ValueError!

# С try/except — программа продолжает работу
try:
    number = int("hello")
except ValueError:
    number = 0
print(number)  # 0

# ==========================================
# КОНКРЕТНЫЕ ТИПЫ ОШИБОК
# ==========================================

try:
    result = 10 / 0
except ZeroDivisionError:
    print("Деление на ноль!")
    result = 0

# Несколько типов ошибок
try:
    number = int("hello")
except ValueError:
    print("Невозможно преобразовать")
except TypeError:
    print("Неверный тип")
except Exception as e:          # ловит всё остальное
    print(f"Неизвестная ошибка: {e}")

# ==========================================
# ПОЛНАЯ КОНСТРУКЦИЯ
# ==========================================

try:
    file = open("data.csv", "r")
    content = file.read()
except FileNotFoundError:
    print("Файл не найден!")
    content = ""
else:
    print("Файл прочитан успешно")  # если ошибок НЕ было
finally:
    print("Выполняется всегда")     # всегда, для очистки
    if 'file' in locals():
        file.close()

# ==========================================
# СОЗДАНИЕ СВОИХ ИСКЛЮЧЕНИЙ
# ==========================================

class DataValidationError(Exception):
    """Своё исключение для валидации данных"""
    pass

def validate_age(age):
    if age < 0 or age > 150:
        raise DataValidationError(f"Недопустимый возраст: {age}")
    return True

try:
    validate_age(200)
except DataValidationError as e:
    print(f"Ошибка валидации: {e}")

# ==========================================
# ПРАКТИЧЕСКИЙ ПРИМЕР
# ==========================================

def safe_divide(a, b):
    try:
        return a / b
    except ZeroDivisionError:
        print("Ошибка: деление на ноль")
        return None
    except TypeError:
        print("Ошибка: оба аргумента должны быть числами")
        return None

print(safe_divide(10, 2))   # 5.0
print(safe_divide(10, 0))   # Ошибка: деление на ноль \n None
print(safe_divide(10, "2")) # Ошибка: оба аргумента должны быть числами \n None
```

---

# 14. РАБОТА С ФАЙЛАМИ И JSON

```python
import json
from pathlib import Path

# ==========================================
# РАБОТА С ФАЙЛАМИ (TXT)
# ==========================================

# Запись
with open("output.txt", "w", encoding="utf-8") as f:
    f.write("Первая строка\n")
    f.write("Вторая строка\n")

# Чтение целиком
with open("output.txt", "r", encoding="utf-8") as f:
    content = f.read()
    print(content)

# Чтение построчно
with open("output.txt", "r", encoding="utf-8") as f:
    for line in f:
        print(line.strip())  # strip() убирает \n

# Добавление в конец
with open("output.txt", "a", encoding="utf-8") as f:
    f.write("Третья строка\n")

# Режимы:
# "r"  — чтение
# "w"  — запись (перезаписывает!)
# "a"  — добавление в конец
# "rb" — чтение бинарного файла
# "wb" — запись бинарного файла

# ==========================================
# JSON (JavaScript Object Notation)
# ==========================================

data = {
    "name": "Анна",
    "age": 25,
    "skills": ["Python", "SQL"],
    "is_active": True
}

# Словарь → JSON строка
json_string = json.dumps(data, ensure_ascii=False, indent=2)
print(json_string)

# JSON строка → словарь
parsed = json.loads(json_string)
print(parsed["name"])           # Анна
print(parsed["skills"][0])      # Python

# Запись в файл
with open("data.json", "w", encoding="utf-8") as f:
    json.dump(data, f, ensure_ascii=False, indent=2)

# Чтение из файла
with open("data.json", "r", encoding="utf-8") as f:
    loaded = json.load(f)

print(loaded["age"])  # 25

# ==========================================
# PATHLIB — СОВРЕМЕННАЯ РАБОТА С ПУТЯМИ
# ==========================================

from pathlib import Path

# Создание путей
base_dir = Path("my_project")
data_dir = base_dir / "data"      # объединение через /
results_dir = base_dir / "results"

# Создание директорий
base_dir.mkdir(exist_ok=True)
data_dir.mkdir(exist_ok=True)
results_dir.mkdir(exist_ok=True)

# Проверка существования
print(base_dir.exists())    # True
print(base_dir.is_dir())    # True

# Поиск файлов
for file in data_dir.glob("*.json"):
    print(f"Найден JSON: {file.name}")

# Информация о файле
file_path = Path("data.json")
print(file_path.stem)       # data (имя без расширения)
print(file_path.suffix)     # .json
print(file_path.parent)     # . (родительская директория)
```

---

# 15. ООП — КЛАССЫ И ОБЪЕКТЫ

```python
# ==========================================
# ЧТО ТАКОЕ КЛАСС? (ПРОСТОЕ ОБЪЯСНЕНИЕ)
# ==========================================
# Класс — это чертёж. Объект — это конкретная вещь по чертежу.

class Car:
    def __init__(self, brand, color):  # конструктор
        self.brand = brand              # атрибут
        self.color = color
    
    def drive(self):                    # метод
        return f"{self.color} {self.brand} едет!"

# Создаём объекты
car1 = Car("Toyota", "red")
car2 = Car("BMW", "black")

print(car1.brand)      # Toyota
print(car2.drive())    # black BMW едет!

# ==========================================
# МАГИЧЕСКИЕ МЕТОДЫ
# ==========================================

class Book:
    def __init__(self, title, author, year):
        self.title = title
        self.author = author
        self.year = year
    
    # Для пользователей (красиво)
    def __str__(self):
        return f"'{self.title}' от {self.author}"
    
    # Для разработчиков (подробно)
    def __repr__(self):
        return f"Book(title='{self.title}', author='{self.author}', year={self.year})"
    
    # Сравнение
    def __eq__(self, other):
        return self.title == other.title and self.author == other.author
    
    # Длина
    def __len__(self):
        return len(self.title)

book = Book("1984", "Оруэлл", 1949)
print(str(book))   # '1984' от Оруэлл
print(repr(book))  # Book(title='1984', author='Оруэлл', year=1949)

# ==========================================
# @property — КОНТРОЛЬ ДОСТУПА
# ==========================================

class BankAccount:
    def __init__(self, owner, balance):
        self.owner = owner
        self._balance = balance  # _ означает "защищённое"
    
    @property
    def balance(self):           # геттер
        print(f"Запрос баланса для {self.owner}")
        return self._balance
    
    @balance.setter
    def balance(self, value):    # сеттер с проверкой
        if value < 0:
            raise ValueError("Баланс не может быть отрицательным!")
        self._balance = value
    
    @property
    def is_rich(self):           # вычисляемое свойство
        return self._balance > 1_000_000

account = BankAccount("Анна", 5000)
print(account.balance)   # Запрос баланса... 5000
account.balance = 10000
print(account.is_rich)   # False

# ==========================================
# НАСЛЕДОВАНИЕ
# ==========================================

class Animal:
    def __init__(self, name):
        self.name = name
    
    def speak(self):
        raise NotImplementedError("Реализуй в дочернем классе")

class Dog(Animal):              # наследуем Animal
    def speak(self):
        return f"{self.name}: Гав!"
    
    def fetch(self):
        return f"{self.name} принёс мяч"

class Cat(Animal):
    def speak(self):
        return f"{self.name}: Мяу!"

dog = Dog("Бобик")
cat = Cat("Мурка")

print(dog.speak())   # Бобик: Гав!
print(cat.speak())   # Мурка: Мяу!
print(dog.fetch())   # Бобик принёс мяч

# super() — вызов метода родителя
class Puppy(Dog):
    def __init__(self, name, age):
        super().__init__(name)  # вызываем конструктор Dog
        self.age = age
    
    def speak(self):
        parent_speak = super().speak()  # вызываем метод Dog
        return f"{parent_speak} (щенок)"

puppy = Puppy("Малыш", 1)
print(puppy.speak())  # Малыш: Гав! (щенок)

# Проверка типа
print(isinstance(dog, Dog))     # True
print(isinstance(dog, Animal))  # True
print(isinstance(dog, Cat))     # False
```

---

# 16. ДЕКОРАТОРЫ

```python
import time
import functools

# ==========================================
# КАК РАБОТАЕТ ДЕКОРАТОР
# ==========================================
# Декоратор — обёртка, которая добавляет функциональность

def my_decorator(func):
    @functools.wraps(func)  # сохраняет имя функции
    def wrapper(*args, **kwargs):
        print("До вызова")
        result = func(*args, **kwargs)
        print("После вызова")
        return result
    return wrapper

@my_decorator
def say_hello():
    print("Привет!")

say_hello()
# До вызова
# Привет!
# После вызова

# ==========================================
# @timer — ИЗМЕРЕНИЕ ВРЕМЕНИ
# ==========================================

def timer(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        elapsed = time.time() - start
        print(f"⏱ {func.__name__}: {elapsed:.4f} сек")
        return result
    return wrapper

@timer
def slow_function(n):
    return sum(range(n))

slow_function(1_000_000)  # ⏱ slow_function: 0.0456 сек

# ==========================================
# @retry — ПОВТОР ПРИ ОШИБКЕ
# ==========================================

def retry(n=3, delay=1):
    def decorator(func):
        @functools.wraps(func)
        def wrapper(*args, **kwargs):
            for attempt in range(1, n + 1):
                try:
                    return func(*args, **kwargs)
                except Exception as e:
                    print(f"Попытка {attempt}/{n} провалилась: {e}")
                    if attempt < n:
                        time.sleep(delay)
                    else:
                        raise
        return wrapper
    return decorator

@retry(n=3, delay=0.5)
def unstable_function():
    import random
    if random.random() < 0.7:
        raise ConnectionError("Сервер недоступен")
    return "Данные получены"

# ==========================================
# @lru_cache — КЭШИРОВАНИЕ (ускоряет рекурсию)
# ==========================================

from functools import lru_cache

@lru_cache(maxsize=128)
def fibonacci(n):
    if n < 2:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

print(fibonacci(50))  # быстро! 12586269025
```

---

# 17. COLLECTIONS (COUNTER, DEFAULTDICT, NAMEDTUPLE, DEQUE)

```python
from collections import Counter, defaultdict, namedtuple, deque

# ==========================================
# COUNTER — ПОДСЧЁТ ЧАСТОТ
# ==========================================

words = ["python", "java", "python", "go", "python", "java"]
count = Counter(words)
print(count)  # Counter({'python': 3, 'java': 2, 'go': 1})
print(count.most_common(2))  # [('python', 3), ('java', 2)]

# Подсчёт букв в строке
text = "hello world"
letter_count = Counter(text)
print(letter_count['l'])  # 3

# ==========================================
# DEFAULTDICT — СЛОВАРЬ СО ЗНАЧЕНИЕМ ПО УМОЛЧАНИЮ
# ==========================================

# Проблема: обычный словарь даёт KeyError
d = {}
# d["new_key"] += 1  # KeyError!

# Решение: defaultdict
from collections import defaultdict

# Список по умолчанию
groups = defaultdict(list)
groups["fruit"].append("apple")
groups["fruit"].append("banana")
groups["veg"].append("carrot")
print(dict(groups))  # {'fruit': ['apple', 'banana'], 'veg': ['carrot']}

# Число по умолчанию (0)
count = defaultdict(int)
for char in "hello":
    count[char] += 1
print(dict(count))  # {'h': 1, 'e': 1, 'l': 2, 'o': 1}

# ==========================================
# NAMEDTUPLE — ИМЕНОВАННЫЕ КОРТЕЖИ
# ==========================================

# Обычный кортеж — только по индексу
point = (10, 20)
print(point[0])  # 10

# NamedTuple — можно по имени
from collections import namedtuple
Point = namedtuple("Point", ["x", "y"])
p = Point(10, 20)
print(p.x)       # 10
print(p.y)       # 20
print(p[0])      # 10 (всё ещё можно по индексу)

# Удобно для конфигов
Config = namedtuple("Config", ["learning_rate", "batch_size", "epochs"])
config = Config(0.001, 32, 100)
print(config.learning_rate)  # 0.001

# ==========================================
# DEQUE — ДВУСТОРОННЯЯ ОЧЕРЕДЬ (БЫСТРЫЙ APPEND/POP)
# ==========================================

from collections import deque

# Обычный список: медленный pop(0) — O(n)
# Deque: быстрый pop/popleft — O(1)

queue = deque()
queue.append("a")      # добавить справа
queue.appendleft("b")  # добавить слева
queue.pop()            # удалить справа
queue.popleft()        # удалить слева

# Ограниченная длина (хранит последние N элементов)
recent = deque(maxlen=3)
for i in range(10):
    recent.append(i)
print(recent)  # deque([7, 8, 9]) — только последние 3
```

---

# 18. ITERTOOLS

```python
import itertools

# ==========================================
# КОМБИНАТОРНЫЕ ФУНКЦИИ
# ==========================================

# product — декартово произведение
colors = ["red", "green"]
sizes = ["S", "M"]
combos = list(itertools.product(colors, sizes))
print(combos)  # [('red', 'S'), ('red', 'M'), ('green', 'S'), ('green', 'M')]

# combinations — комбинации (порядок НЕ важен)
teams = list(itertools.combinations(["A", "B", "C", "D"], r=2))
print(teams)  # [('A','B'), ('A','C'), ('A','D'), ('B','C'), ('B','D'), ('C','D')]

# permutations — перестановки (порядок важен)
perms = list(itertools.permutations([1, 2, 3], r=2))
print(perms)  # [(1,2), (1,3), (2,1), (2,3), (3,1), (3,2)]

# ==========================================
# ПОЛЕЗНЫЕ ФУНКЦИИ ДЛЯ ИТЕРАЦИИ
# ==========================================

# chain — объединение нескольких итераторов
result = list(itertools.chain([1, 2], [3, 4], [5, 6]))
print(result)  # [1, 2, 3, 4, 5, 6]

# chain.from_iterable — из списка списков
nested = [[1, 2], [3, 4], [5, 6]]
flat = list(itertools.chain.from_iterable(nested))
print(flat)  # [1, 2, 3, 4, 5, 6]

# compress — фильтрация по маске
data = ["a", "b", "c", "d"]
mask = [True, False, True, False]
result = list(itertools.compress(data, mask))
print(result)  # ['a', 'c']

# takewhile — берём пока условие True
nums = [2, 4, 6, 7, 8, 10]
taken = list(itertools.takewhile(lambda x: x % 2 == 0, nums))
print(taken)  # [2, 4, 6] (7 нечётное — останов)

# accumulate — накопительные операции
running_sum = list(itertools.accumulate([1, 2, 3, 4, 5]))
print(running_sum)  # [1, 3, 6, 10, 15]

# islice — срез итератора (без создания списка)
first_five = list(itertools.islice(range(100), 5))
print(first_five)  # [0, 1, 2, 3, 4]
```

---

# 19. КОНТЕКСТНЫЕ МЕНЕДЖЕРЫ (CONTEXT MANAGERS)

```python
# ==========================================
# ЧТО ТАКОЕ КОНТЕКСТНЫЙ МЕНЕДЖЕР?
# ==========================================
# Управляет ресурсами: открыл → сделал → закрыл
# Самый частый пример: with open(...)

# Без контекстного менеджера (нужно закрывать вручную)
f = open("file.txt", "w")
f.write("hello")
f.close()  # если забыть — утечка ресурсов

# С контекстным менеджером (закроется автоматически)
with open("file.txt", "w") as f:
    f.write("hello")
# файл закрыт автоматически

# ==========================================
# КОНТЕКСТНЫЙ МЕНЕДЖЕР ЧЕРЕЗ КЛАСС
# ==========================================

class Timer:
    """Замеряет время выполнения блока кода"""
    def __enter__(self):
        self.start = time.time()
        return self
    
    def __exit__(self, exc_type, exc_val, exc_tb):
        self.end = time.time()
        print(f"⏱ Время выполнения: {self.end - self.start:.3f} сек")
        return False  # False — не подавляем исключения

# Использование
with Timer():
    time.sleep(1)
    print("Делаем работу")
# ⏱ Время выполнения: 1.001 сек

# ==========================================
# КОНТЕКСТНЫЙ МЕНЕДЖЕР ЧЕРЕЗ @contextmanager
# ==========================================

from contextlib import contextmanager

@contextmanager
def timer_context(name):
    print(f"⏱ Начинаем: {name}")
    start = time.time()
    try:
        yield  # здесь выполняется код внутри with
    finally:
        end = time.time()
        print(f"⏱ {name} заняло: {end - start:.2f} сек")

# Использование
with timer_context("загрузка данных"):
    time.sleep(0.5)
    print("Данные загружены")

# ==========================================
# КОНТЕКСТНЫЙ МЕНЕДЖЕР ДЛЯ ЛОГИРОВАНИЯ
# ==========================================

@contextmanager
def log_context(operation_name, log_file="app.log"):
    from datetime import datetime
    with open(log_file, 'a') as f:
        f.write(f"[{datetime.now()}] START: {operation_name}\n")
    try:
        yield
    except Exception as e:
        with open(log_file, 'a') as f:
            f.write(f"[{datetime.now()}] ERROR: {operation_name} - {e}\n")
        raise
    else:
        with open(log_file, 'a') as f:
            f.write(f"[{datetime.now()}] END: {operation_name}\n")

# Использование
with log_context("processing user data"):
    result = 10 / 2
    print("Данные обработаны")
```

---

# 20. АННОТАЦИИ ТИПОВ (TYPING)

```python
from typing import List, Dict, Tuple, Optional, Union, Callable, Any

# ==========================================
# БАЗОВЫЕ АННОТАЦИИ
# ==========================================

# Простые типы
name: str = "Анна"
age: int = 25
salary: float = 90000.0
is_active: bool = True
data: None = None

# Функции с аннотациями
def greet(name: str) -> str:
    return f"Привет, {name}!"

def add(a: int, b: int) -> int:
    return a + b

def divide(a: float, b: float) -> float:
    return a / b

# ==========================================
# КОЛЛЕКЦИИ
# ==========================================

# Список целых чисел
numbers: List[int] = [1, 2, 3, 4, 5]

# Словарь: str → float
prices: Dict[str, float] = {"apple": 1.2, "banana": 0.8}

# Кортеж из трёх элементов разных типов
person: Tuple[str, int, bool] = ("Анна", 25, True)

# ==========================================
# OPTIONAL — МОЖЕТ БЫТЬ None
# ==========================================

def find_user(user_id: int) -> Optional[Dict[str, Any]]:
    # Возвращает либо словарь, либо None
    if user_id == 1:
        return {"name": "Анна", "age": 25}
    return None

# ==========================================
# UNION — НЕСКОЛЬКО ТИПОВ
# ==========================================

def to_number(value: Union[str, int]) -> float:
    """Принимает строку или число, возвращает float"""
    return float(value)

# Альтернативная запись (Python 3.10+):
# def to_number(value: str | int) -> float:

# ==========================================
# CALLABLE — ФУНКЦИЯ КАК АРГУМЕНТ
# ==========================================

def apply_operation(
    x: float, 
    y: float, 
    operation: Callable[[float, float], float]
) -> float:
    return operation(x, y)

result = apply_operation(5, 3, lambda a, b: a + b)  # 8
result = apply_operation(5, 3, lambda a, b: a * b)  # 15

# ==========================================
# ПОЛЕЗНЫЕ ПРИМЕРЫ В ML
# ==========================================

import numpy as np

def train_model(
    X: np.ndarray,
    y: np.ndarray,
    learning_rate: float = 0.001,
    epochs: int = 100,
    verbose: bool = True
) -> Dict[str, List[float]]:
    """
    Обучает модель.
    
    Args:
        X: Признаки (n_samples, n_features)
        y: Целевая переменная (n_samples,)
        learning_rate: Скорость обучения
        epochs: Количество эпох
        verbose: Печатать прогресс
    
    Returns:
        Словарь с историей обучения
    """
    history: Dict[str, List[float]] = {"loss": [], "accuracy": []}
    # ... обучение
    return history

# ==========================================
# dataclasses — УПРОЩЁННОЕ СОЗДАНИЕ КЛАССОВ
# ==========================================

from dataclasses import dataclass

@dataclass
class ModelConfig:
    """Конфигурация модели машинного обучения"""
    learning_rate: float = 0.001
    batch_size: int = 32
    epochs: int = 100
    dropout_rate: float = 0.5
    model_name: str = "baseline"

# Автоматически создаёт __init__, __repr__, __eq__
config = ModelConfig(learning_rate=0.01, batch_size=64)
print(config)  # ModelConfig(learning_rate=0.01, batch_size=64, epochs=100, dropout_rate=0.5, model_name='baseline')
```

---

# 21. ВИРТУАЛЬНЫЕ ОКРУЖЕНИЯ И GIT

```bash
# ==========================================
# ВИРТУАЛЬНЫЕ ОКРУЖЕНИЯ
# ==========================================

# СОЗДАНИЕ
# Windows
python -m venv venv
venv\Scripts\activate

# Mac/Linux
python3 -m venv venv
source venv/bin/activate

# УСТАНОВКА ПАКЕТОВ
pip install numpy pandas matplotlib scikit-learn
pip install jupyter notebook
pip install black flake8 mypy

# СОХРАНЕНИЕ ЗАВИСИМОСТЕЙ
pip freeze > requirements.txt

# УСТАНОВКА ИЗ ФАЙЛА
pip install -r requirements.txt

# ВЫХОД ИЗ ОКРУЖЕНИЯ
deactivate

# ==========================================
# .gitignore — ЧТО НЕ ПУШИТЬ В GIT
# ==========================================
```

```gitignore
# Виртуальное окружение
venv/
env/
ENV/

# Python
__pycache__/
*.pyc
*.pyo
*.pyd
.Python

# Jupyter
.ipynb_checkpoints/
*.ipynb

# Данные (могут быть большими)
*.csv
*.json
*.pkl
*.h5
*.pb

# Логи
*.log
logs/

# IDE
.vscode/
.idea/
*.swp

# OS
.DS_Store
Thumbs.db

# ML модели (большие файлы)
*.h5
*.pth
*.pt
*.onnx
*.joblib

# Переменные окружения
.env
```

```bash
# ==========================================
# GIT БАЗОВЫЕ КОМАНДЫ
# ==========================================

# НАСТРОЙКА (один раз)
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

# СОЗДАНИЕ РЕПОЗИТОРИЯ
git init
git add .
git commit -m "Initial commit"

# РАБОТА С УДАЛЁННЫМ РЕПО (GitHub)
git remote add origin https://github.com/username/repo.git
git branch -M main
git push -u origin main

# ОСНОВНЫЕ КОМАНДЫ
git status              # Показать изменения
git add file.py         # Добавить файл
git add .               # Добавить все файлы
git commit -m "message" # Создать коммит
git push                # Отправить на GitHub
git pull                # Скачать изменения
git log --oneline       # История коммитов

# РАБОТА С ВЕТКАМИ
git branch              # Показать ветки
git branch feature      # Создать ветку
git checkout feature    # Переключиться на ветку
git merge feature       # Слить ветку в текущую
git branch -d feature   # Удалить ветку

# ОТКАТ ИЗМЕНЕНИЙ
git checkout -- file.py   # Отменить изменения в файле
git reset HEAD file.py    # Убрать из staging
git reset --soft HEAD~1   # Отменить последний коммит (оставить изменения)
git reset --hard HEAD~1   # Отменить последний коммит (удалить изменения)
```

---

# 22. ПРИМЕР СТРУКТУРЫ ML ПРОЕКТА

```
my_ml_project/
├── .gitignore
├── README.md
├── requirements.txt
├── setup.py
├── configs/
│   └── config.yaml
├── data/
│   ├── raw/
│   ├── processed/
│   └── external/
├── notebooks/
│   ├── 01_eda.ipynb
│   └── 02_model.ipynb
├── src/
│   ├── __init__.py
│   ├── data_processor.py
│   ├── features.py
│   ├── model.py
│   └── utils.py
├── tests/
│   ├── test_data_processor.py
│   └── test_model.py
└── models/
    └── saved_models/
```

---

# 23. ИТОГОВАЯ МЕГА-ШПАРГАЛКА

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                         PYTHON — ПОЛНАЯ ШПАРГАЛКА                            ║
╠══════════════════════════════════════════════════════════════════════════════╣
║                                                                              ║
║  📌 ТИПЫ ДАННЫХ                                                              ║
║    str, int, float, bool, None                                               ║
║    int("5"), float("3.14"), str(100), bool(0)                                ║
║    type(x), isinstance(x, int)                                               ║
║                                                                              ║
║  📌 СТРОКИ                                                                   ║
║    s[0], s[-1], s[1:4], s[::-1]                                              ║
║    .upper(), .lower(), .strip(), .split(), .join()                           ║
║    .replace(), .find(), .startswith(), .count()                              ║
║    f"Привет, {name}!", f"{value:.2f}"                                        ║
║                                                                              ║
║  📌 СПИСКИ                                                                   ║
║    lst[0], lst[-1], lst[1:3], lst[::-1]                                      ║
║    .append(), .insert(), .extend(), .remove(), .pop()                        ║
║    .sort(), sorted(lst), len(), min(), max(), sum()                          ║
║    x in lst, copy = lst.copy()                                               ║
║                                                                              ║
║  📌 СЛОВАРИ                                                                  ║
║    d["key"], d.get("key", default)                                           ║
║    .keys(), .values(), .items()                                              ║
║    for k, v in d.items(): ...                                                ║
║    merged = {**d1, **d2}                                                     ║
║                                                                              ║
║  📌 УСЛОВИЯ                                                                  ║
║    if x > 0 and x < 10: ...                                                  ║
║    result = "yes" if x > 0 else "no"                                         ║
║    x is None, isinstance(x, int)                                             ║
║                                                                              ║
║  📌 ЦИКЛЫ                                                                    ║
║    for i in range(10): ...                                                   ║
║    for i, v in enumerate(lst): ...                                           ║
║    for a, b in zip(lst1, lst2): ...                                          ║
║    break, continue, else                                                     ║
║                                                                              ║
║  📌 ФУНКЦИИ                                                                  ║
║    def f(a, b=10, *args, **kwargs): ...                                      ║
║    return x, y  →  a, b = f()                                                ║
║    f(**dict), f(*list)                                                       ║
║    ⚠️  def f(lst=None):  не def f(lst=[])!                                   ║
║                                                                              ║
║  📌 LAMBDA                                                                   ║
║    f = lambda x: x ** 2                                                      ║
║    sorted(lst, key=lambda x: x["age"])                                       ║
║                                                                              ║
║  📌 COMPREHENSIONS                                                           ║
║    [x**2 for x in range(10)]                                                 ║
║    [x for x in lst if x > 0]                                                 ║
║    [a if x>0 else b for x in lst]                                            ║
║    {k: v for k, v in d.items()}                                              ║
║    (x**2 for x in range(10))  ← generator                                    ║
║                                                                              ║
║  📌 MAP/FILTER/REDUCE                                                        ║
║    list(map(lambda x: x*2, lst))                                             ║
║    list(filter(lambda x: x>0, lst))                                          ║
║    reduce(lambda acc, x: acc+x, lst)                                         ║
║                                                                              ║
║  📌 ОШИБКИ                                                                   ║
║    try: ... except ValueError: ... else: ... finally: ...                    ║
║    raise ValueError("сообщение")                                             ║
║                                                                              ║
║  📌 ООП                                                                      ║
║    class Dog(Animal):                                                        ║
║        def __init__(self, name):                                             ║
║            super().__init__(name)                                            ║
║        def speak(self): ...                                                  ║
║    @property, @setter, @staticmethod, @classmethod                           ║
║    __str__, __repr__, __add__, __len__, __eq__                               ║
║                                                                              ║
║  📌 ДЕКОРАТОРЫ                                                               ║
║    @timer, @logger, @retry, @lru_cache                                       ║
║    @functools.wraps(func)  — сохраняет метаданные                           ║
║                                                                              ║
║  📌 COLLECTIONS                                                              ║
║    Counter(lst)           — частоты                                          ║
║    defaultdict(list)      — словарь с умолчанием                            ║
║    namedtuple("N", [...]) — лёгкий класс                                    ║
║    deque(maxlen=N)        — очередь с ограничением                          ║
║                                                                              ║
║  📌 КОНТЕКСТНЫЕ МЕНЕДЖЕРЫ                                                    ║
║    with open("file.txt") as f: ...                                           ║
║    @contextmanager def timer(): ...                                          ║
║                                                                              ║
║  📌 АННОТАЦИИ ТИПОВ                                                          ║
║    from typing import List, Dict, Optional, Union, Callable                  ║
║    def f(x: int) -> str: ...                                                 ║
║    @dataclass class Config: ...                                              ║
║                                                                              ║
║  📌 NUMPY                                                                    ║
║    np.array([1,2,3]), np.zeros((3,4))                                        ║
║    X.shape, X.dtype, X.reshape(-1, 1)                                        ║
║    X[0], X[:, 0], X[X > 0]                                                   ║
║    A @ B, np.mean(X, axis=0), np.argmax(X, axis=1)                          ║
║    np.where(x > 0, x, 0), np.vstack, np.hstack                              ║
║                                                                              ║
║  📌 GIT                                                                      ║
║    git init, git add ., git commit -m "msg"                                  ║
║    git push, git pull, git status                                            ║
║    git branch, git checkout, git merge                                       ║
║                                                                              ║
║  📌 ВИРТУАЛЬНОЕ ОКРУЖЕНИЕ                                                    ║
║    python -m venv venv                                                       ║
║    source venv/bin/activate  (Mac/Linux)                                     ║
║    venv\Scripts\activate      (Windows)                                      ║
║    pip freeze > requirements.txt                                             ║
║    pip install -r requirements.txt                                           ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```
