# Взаимодействие с DOM

## Загрузка DOM

Способы определить, что DOM загрузиля и можно исполнять скрипт:

**1. window.onload - событие загрузки объекта window**

``` javascript
window.onload = function () {
//commands
};
```

Конструкция используется только один раз. 
Ожидает полной загрузки и отрисовки документа, включая картинки.

**2. Событие DOMContentLoaded**

Приоритетный способ. Событие возникает после того как DOM для страницы будет собран, но не ждет, когда другие ресурсы будут загружены.

``` javascript
window.addEventListener( 'DOMContentLoaded', function( event ){
// commands
});
```

**3. jQuery**

``` javascripr
$(document).ready();
$(window).ready();
```


## Поиск и выбор элементов DOM

### document.querySelector(selectors)

Возвращает первый элемент внутри документа (или элемента, внутри которого производится посик), используется предупорядоченный обход узлов в глубину до первого найденного узла, который совпадает с группой селекторов, установленной в параметрах.

```javascript
let x = document.querySelector(selectors);
```

### document.querySelectorAll(selectors)

Возвращает объект ```NodeList```, содержащий потомков ```el```, подходящих под выборку ```selectors```. Псевдо-селекторы не выбираются (при этом WebKit возвращает <html>, другие движки ничего не возвращают).

``` javascript

let x = document.querySelectorAll( '.some-class' );

```

### document.getElementById()

Возвщает ссылку на найденный по его ID элемент. Параметр id чувствителен к регистру.

```javascript
let x = document.getElementById( 'someId' );

```

### document.getElementsByClassName()

Возвращает псевдо-массив ( ```HTMLCollection``` ) элементов, подходящих условию.

```javascript
let elements = document.getElementsByClassName( 'some-class' ); // или
let elements = rootElement.getElementsByClassName( 'some class' );
```

**Примеры:**

Получить все элементы класса 'test', являющиеся дочерними для элемента с ID 'main':
```javascript
let elements = document.getElementById('main').getElementsByClassName('test');
```

### document.getElementsByTagName()

Возвращает ```HTMLCollection``` элемнетов с указанным именем тега.

```javascript
let elements = document.getElementsByTagName(name);
```

## Создание DOM узлов

### document.createElement()

Создает объект ```node``` - элемент DOM с заданным именем.

``` javascript
let el = document.createElement( 'div' );
```

### document.createTextNode()

Создает текстовый узел.

```javascript
let text = document.createTextNode( 'some text' );
```

### document.createDocumentFragment()

```DocumentFragment``` - обертка для произвольного HTML кода. Представляет собой объект ```DocumentFragment``` и ведет себя как узел DOM. После вставки в DOM обертка исчезает, остаются только DOM - элементы, которые были в ней. 
Свойства documentFragment наследуются от объекта Node.

```DocumentFragment``` хранится в памяти и не является частью основного дерева DOM, поэтому добавление в него дочерних элементов не вызывает reflow, что увеличивает производительность.


``` javascript
let fragment = document.createDocumentFragment();
for ( let i = 0; i < 5; i++  ) {
	let section = document.createElement( 'section' );
	section.classList.add( 'some-class' );
	fragment.appendChild( section );
}
```

### node.cloneNode( true/false )

Клонирует указанный ```node```. Если в параметрах ```true```, то узел клонируется со всем содержимым, если ```false``` - то только сам узел. По умолчанию - ```true```.

```javascript
let el = document.getElementById( 'some' ),
    el2 = el.cloneNode( true );
```


## Добавление узлов в DOM

### element.insertAdjacentHTML(key, code)

Разбирает указанный ```code``` как HTML или XML и вставляет полученные узлы в DOM дерево в указанную в ```key``` позицию. Не переписывает имеющиеся элементы, что предовращает дополнительную сериализацию и поэтому работает быстрее, чем ```innerHTML```.

key может принимать 4 значения: 
* beforeBegin - вставка до element
* afterEnd - вставка после element
* afterBegin - вставка внутрь element (в самое начало)
* beforeEnd - вставка внутрь element (в самый конец)

Визуально: 

``` HTML
<!-- beforeBegin -->
<p>
<!-- afterBegin -->
foo
<!-- beforeEnd -->
</p>
<!-- afterEnd -->
```

```javascript
let code = '<div class = 'some-class'></div>',
el = document.getElementById( 'someid' );
el.insertAdjacentHTML('beforeBegin', code);

```

### element.innerHTML()




## Удаление узлов из DOM


## Управление стилями в DOM

