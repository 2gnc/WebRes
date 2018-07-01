* [Примитивные типы](https://github.com/2gnc/WebRes/blob/master/typeScript.md#Простые-типы)
* [Типизация массивов](https://github.com/2gnc/WebRes/blob/master/typeScript.md#Типизация-массивов)
* [Типизация переменных](https://github.com/2gnc/WebRes/blob/master/typeScript.md#Типизация-переменных)

## Простые типы
* string
* number
* boolean
* any - любой тип (стараться избегать этого типа). 
* undefined

## Типизация массивов
Указываем, какие типы данных может содержать массив. Количество элементов не ограничивается. 

Массив, содержащий только строки.
```typescript 
const arr: string[] = ['one', 'two']
```
Массив, содержащий только числа.
```typescript 
const arr: string[] = [1, 2]
```
## Кортежи
Указываем порядок элементов, их количество и тип. 

Кортеж из числа и строки. 
```typescript
```

## Типизация переменных
Переменным и константам типы присваиваются при определении, после двоеточия.

```typescript
let someString: string = 'Something';
const NUM: number = 42;
```
