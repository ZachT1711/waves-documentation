# Математические функции

| # | Название | Описание | Сложность |
| :--- | :--- | :--- | :--- |
| 1 | [fraction(Int, Int, Int): Int](#fraction) | Конвертирует произвольно большое знаковое целое число в целое число | 1 |
| 2 | [log(Int, Int, Int, Int, Int, Union): Int](#log)  | Находит логарифм числа | 100 |
| 3 | [pow(Int, Int, Int, Int, Int, Union): Int](#pow) | Возводит число в степень | 100 |

## fraction(Int, Int, Int): Int<a id="fraction"></a>

Конвертирует произвольно большое знаковое целое число в целое число.

```ride
fraction(value: Int, numerator: Int, denominator: Int): Int
```

### Параметры

#### `value`: Int

Произвольно большое знаковое целое число.

#### `numerator`: Int

Числитель дроби.

#### `denominator`: Int

Знаменатель дроби.

### Формула конвертации

Конвертация производится по следущей формуле:

```ride
fraction = value × numerator / denominator
```

### Примеры

```ride
fraction(2,2,3) # Возвращает 1
fraction(3,3,3) # Возвращает 3
fraction(3,2,3) # Возвращает 2
```

## log(Int, Int, Int, Int, Int, Union)<a id="log"></a>

Находит логарифм числа.

``` ride
log(value: Int, ep: Int, base: Int, bp: Int, rp: Int, round: Union): Int
```

### Параметры

#### `value`: Int

Заданное число.

#### `ep`: Int

Количество знаков после запятой у заданного числа.

#### `base`: Int

Основание логарифма.

#### `bp`: Int

Количество знаков после запятой у основания логарифма.

#### `rp`: Int

Количество знаков после запятой результата.

#### `round`: Union

Одна из [функций округлений](#rounding-functions).

В качестве значения по умолчанию может быть использована функция `HalfUp()`.

### Примеры

* log<sub>2</sub>(0) = -Infinity
* log<sub>2</sub>(2) = 0
* log<sub>2</sub>(10.555) = 3.4
* log<sub>2</sub>(16.25) = 4.02

```ride
log(0, 0, 2, 0, 0, HalfUp()) # -Infinity
log(1, 0, 2, 0, 0, HalfDown()) # Возвращает 0
log(10555, 3, 2, 0, 3, HalfEven()) # Возвращает 3400
log(1625, 2, 2, 0, 2, Up()) # Возвращает 403
```

## pow(Int, Int, Int, Int, Int, Union): Int<a id="pow"></a>

Возводит число в степень.

``` ride
pow(base: Int, bp: Int, exponent: Int, ep: Int, rp: Int, round: Union): Int
```

### Параметры

#### `base`: Int

Основание.

#### `bp`: Int

Количество знаков после запятой у основания.

#### `exponent`: Int

Показатель степени.

#### `ep`: Int

Количество знаков после запятой у показателя степени.

#### `rp`: Int

Количество знаков после запятой у результата.

#### `round`: Union

Одна из [функций округления](#rounding-functions).

В качестве значения по умолчанию может быть использована функция `HalfUp()`.

### Примеры

* 1<sup>0</sup> = 1
* 2<sup>4</sup> = 16
* 2.5<sup>2.5</sup> = 9.88
* 3.33<sup>3</sup> = 36.926

```ride
pow(1, 0, 0, 0, 0, Up()) # Возвращает 1
pow(2, 0, 4, 0, 0, HalfUp()) # Возвращает 16
pow(25, 1, 25, 1, 2, Floor()) # Возвращает 988
pow(333, 2, 3, 0, 3, Down()) # Возвращает 36926
```

## Функции округления<a id="rounding-functions"></a>

Функции округления используются _только_ в качестве параметров функций [log](#log) и [pow](#pow), и самостоятельно они не используются.

| Название | Описание |
| :--- | :--- |
| Ceiling(): Int | Округление к положительной бесконечности |
| Down(): Int | Округление к нулю |
| Floor(): Int | Округление к отрицательной бесконечности |
| HalfDown(): Int | Округление вниз до ближайшего целого |
| HalfEven(): Int | Округление к ближайшему четному числу |
| HalfUp(): Int | Округление вверх к ближайшему целому |
| Up(): Int | Округление от нуля |

### Примеры

| | -1,6 | -1,5 | -1,4 | -1,0 | 1,0 | 1,4 | 1,5 | 1,6 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Ceiling | -1 | -1 | -1 | -1 | 1 | 2 | 2 | 2 |
| Down | -1 | -1 | -1 | -1 | 1 | 1 | 1 | 1 |
| Floor | -2 | -2 | -2 | -1 | 1 | 1 | 1 | 1 |
| HalfDown | -2 | -1 | -1 | -1 | 1 | 1 | 1 | 2 |
| HalfEven | -2 | -2 | -1 | -1 | 1 | 1 | 2 | 2 |
| HalfUp | -2 | -2 | -1 | -1 | 1 | 1 | 2 | 2 |
| Up | -2 | -2 | -2 | -1 | 1 | 2 | 2 | 2 |
