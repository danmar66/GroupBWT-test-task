# Tasks Daniil Marchenko

## 1) Задан массив целых чисел. Написать функцию нахождения максимального элемента в массиве.

```js
function findMaxNum (array) {  
  let max = array.shift();
    
  for (let i = 0; i < array.length; i++) {  
	  if (array[i] > max) {  
		  max = array[i];  
	  }  
  } 
   
  return max;  
}
```

## 2) Реализовать функцию сортировки пузырьком

```js
function bubbleSort(array) {  
  for (let n = 0; n < array.length; n++) {  
    for (let i = 0; i < array.length - 1 - n; i++) {  
      if (array[i] > array[i + 1]) {  
        const temp = array[i]  
        array[i] = array[i + 1]  
        array[i + 1] = temp  
      }  
    }  
  }  
  
  return array;  
}
```

## 3) Это задача на знание БД и SQL. 

В качестве решения, нарисуйте необходимую структуру БД и напишите SQL запрос в текстовом виде. 

Даны таблицы:
-   products (id, name, price) - продукты в магазине электроники;
-   tags (id, name) - категории товаров к которым может относиться тот или иной продукт.

Как должна выглядеть связь между продуктами и тэгами?

Напишите запрос который найдет продукты с более чем 10-ю тегами.

### Структура таблиц

![diagram](https://ibb.co/f067MVF)

```sql
SELECT `products`.*
FROM `products`
INNER JOIN `products_tags` ON `products_tags`.`product_id` = `products`.`id`
WHERE COUNT(`products_tags`.`tag_id`) > 10
GROUP BY `products`.`id`
```

## 4) Задан упорядоченный по возрастанию массив. Реализовать алгоритм бинарного поиска для нахождения значения в массиве. Вернуть номер элемента или уведомить что такого элемента нет.

```js
function binarySearch(array, value) {  
  let rangeStart = 0;  
  let rangeEnd = array.length - 1;  
  let index = Math.round(rangeEnd / 2);  
  let medianValue = array[index];  
  
  while (medianValue !== value || rangeStart === rangeEnd) {  
    if (value > medianValue) {  
      rangeStart = index + 1;  
    } else {  
      rangeEnd = index - 1;  
    }  
  
    index = Math.round((rangeEnd + rangeStart) / 2);  
    medianValue = array[index];  
  }  
  
  if (medianValue !== value) {  
    return 'Not found';  
  }  
  
  return index;  
}
```

## 5) Реализовать класс 2-х мерный вектор.

Класс должен содержать приватные атрибуты x и y - координаты точки куда направлен вектор, а также публичные методы:
-   сложение векторов (принимает на вход другой объект класса Вектор);
-   вычитание векторов (принимает на вход другой объект класса Вектор);
-   умножение вектора на число (принимает на вход число);
-   вывод вектора на печать (вывод строки содержащей информацию про объект).

```js
class Vector {  
  private x: number;  
  private y: number;  
  
  constructor(x: number, y: number) {  
    this.x = x;  
    this.y = y;  
  }  
  
  getX(): number {  
    return this.x;  
  }  
  
  getY(): number {  
    return this.y;  
  }  
  
  add(vector: Vector): Vector {  
    return new Vector(this.x + vector.getX(), this.y + vector.getY());  
  }  
  
  diff(vector: Vector): Vector {  
    return new Vector(this.x - vector.getX(), this.y - vector.getY());  
  }  
  
  multiplicationByNumber(number: number): Vector {  
    if (number === 0) {  
      return new Vector(0, 0);  
    }  
  
    const x = this.x * number;  
    const y = this.y * number;  
  
    return (number > 0) ? new Vector(x, y) : new Vector(y, x);  
  }  
  
  print(): void {  
    console.log(`Coordinate x: ${this.x}; Coordinate y: ${this.y}`);  
  }  
}
```

## 6) Проверить является ли строка палиндромом.

```js
function isPolindrom(string) {  
  const stringEnd = string.length - 1;  
  
  for (let i = 0; i < Math.round(stringEnd / 2); i++) {  
    if (string[i] !== string[stringEnd - i]) {  
      return false;  
    }
  }
  
  return true;  
}
```
