* [Простые типы](https://github.com/2gnc/WebRes/blob/master/typeScript.md#Простые-типы)
* [Массивы](https://github.com/2gnc/WebRes/blob/master/typeScript.md#Массивы)
* [Tuples](https://github.com/2gnc/WebRes/blob/master/typeScript.md#tuples)
* [Enums](https://github.com/2gnc/WebRes/blob/master/typeScript.md#enum)
* [Типизация переменных](https://github.com/2gnc/WebRes/blob/master/typeScript.md#Типизация-переменных)

## Простые типы
* string
* number
* boolean
* any - любой тип (стараться избегать этого типа). 
* undefined

## Массивы
Указываем, какие типы данных может содержать массив. Количество элементов не ограничивается. 

Массив, содержащий только строки.
```typescript 
const arr: string[] = ['one', 'two']
```
Массив, содержащий только числа.
```typescript 
const arr: string[] = [1, 2]
```
## Tuples
Указываем порядок элементов, их количество и тип. 

Кортеж (tuple) из одного числа и одной строки. 
```typescript
const data: [number, string] = [42, 'ansver'];
```

## Enum
Перечисление - для присвоения понятных имен числовым значениям.
```typescript 

```

## Типизация переменных
Переменным и константам типы присваиваются при определении, после двоеточия.

```typescript
let someString: string = 'Something';
const NUM: number = 42;
```
