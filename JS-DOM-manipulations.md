# Взаимодействие с DOM

## Node.nodeType - тип узла
Проверить узел: 
```javascript
    let type = node.nodeType;
```
1. ELEMENT_NODE :zap:
2. ATTRIBUTE_NODE
3. TEXT_NODE :zap:
4. CDATA_SECTION_NODE
5. ENTITY_REFERENCE_NODE
6. ENTITY_NODE
7. PROCESSING_INSTRUCTION_NODE
8. COMMENT_NODE :zap:
9. DOCUMENT_NODE
10. DOCUMENT_TYPE_NODE
11. DOCUMENT_FRAGMENT_NODE :zap:
12.NOTATION_NODE 

Чаще всего применяются типы 1, 3 и 8.
Пример использоватния: если на вход принимается энное количество элеменов, не все из которых язвяютя элементами.
В этом случае можно проверить, что nodeType == 1.  

### Свойства DOM элементов (el.nodeType === 1)

Объект ```element``` наследует свойства от объекта ```node```.

#### element.tagName
Возвращает строку с именем тега, соответствующего элементу. Имя тега всегда заглавными буквами.
```javascript
    let tag = document.getElementById('test').tagName; // "DIV"
```  

#### element.outerHTML
Возвращает HTML узла, включая сам узел. Свойство только для чтения.
```javascript
let el = document.getElementById('test') // <div id="test"><p>some text</p></div>
el.outerHTML; // <div id="test"><p>some text</p></div>
el.innerHTML; // <p>some text</p>
```

#### element.innerText
Нестандартизованное свойство, позволяющее задавать или получать текстовое содержимое элемента.

#### element.textContent
Стандартизированное свойство, позволяющее получать и задавать текствовое содержимое узла. Возвращает null, если узел
является документом. Потребляет гораздо меньше ресурсов, чем ```innerHTML```.

#### node.children
Возвращает живую HTML коллекцию дочерних элементов узла.

#### node.childNodes
Возвращает все дочерние узлы (не только элементы, но еще и текстовые или других типов).

## Загрузка DOM

Способы определить, что DOM загрузилcя и можно исполнять скрипт:

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
## Положение узлов друг относительно друга в DOM

### Node.Contains( otherNode )
Метод определяет, является ли узел Node потомком другого узла otherNode. Возвращает true или false.

### A.compareDocumentPosition( B )
Сравнивает позицию текущего узла ```node``` и другого узла ```other node``` в любом другом документе. Возвращат число 
со следуюущими значениями. Если в результате проерки подошло несколько вариантов, возвращает их сумму.

0. Это одинаковые узлы A === B
1. Узлы в разных документах
2. B предшествует A
4. A предшествует B
8. B содержит узел A
16. A содержит узел B
32. служебное значение

## Создание DOM узлов

### document.createElement()

Создает объект ```node``` - элемент DOM с заданным именем.

``` javascript
let el = document.createElement( 'div' );
```

### element.setAttribute(name, value)

Устанавлиавает для ```element``` атрибут с указанным именем ```name``` и значением ```value``` .

```javascript
let el = document.querySelector( 'button' ); 

el.setAttribute( 'name', 'helloButton' );
el.setAttribute( 'disabled', '' );
```

### element.getAttribute();

Возвращает значение указанного атрибута элемента. Если элемент не содержит данный атрибут, вернется null или пустая строка.

```javascript
let div1 = document.getElementById( 'div1' ),
    align = div1.getAttribute( 'align' );

console.log(align); // отобразит значение атрибута align элемента с id = 'div1'
```

### element.hasAttribute()

Проверяет, есть ли у элемента атрибут с указанным ```name``` , возвращает ```true``` или ```false``` 

### element.attributes
Возвращает ```NamedNodeMap```, содержащий псевдо-массив с атрибутами указанного узла. 

### element.removeAttribute()

Удаляет указанный атрибут у элемента. Попытка удаления аттрибута, которого нет на элементе не вызывает ошибки.

``` javascript
document.getElementById( 'div1' ).removeAttribute( 'align' ); 
```

способ перебрать все атрибуты (перевором), свойство attributes

### document.createTextNode()

Создает текстовый узел.

```javascript
let text = document.createTextNode( 'some text' );
```
 дописать после урока инфу
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

Клонирует указанный ```node```. Если в параметрах ```true```, то узел клонируется со всем содержимым, если ```false``` - то только сам узел.

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

### element.innerHTML(), element.innerHTML

Устанавливает или получает разметку дочерних элементов. В качестве параметра принимает строку.
Нежелательно использовать для вставки текста на страницу, вместо этого использовать ```node.textContent```. 
Если принимает невалидный код, браузер пытается исправить его, запустив анализатор. Из-за этого может работать медленнее.

``` javascript
const content = element.innerHTML;  //сохранили содержимое element в константу content
element.innerHTML = content;  //записали содержимое content в узел element, предыдущее содержимое удаляется
element.innerHTMl = ''; //удалили содержимое element
```

### Node.appendChild()

Добавляет дочерний элемент ```child``` родительскому элементу ```element```. При этом ```child``` становится последним из всех потомков ```element``` . Возвращает ссылку на добавленный элемент.
Если элемент уже существует, он удаляется из текущего родителя и вставляется заново.
Если ```child``` ссылается на уже существующий элемент в документе , тогда ```appendChild``` перемещает элемент с его текущей позиции на новую. Если элемент нужно не перенести, а скопировать, то используется  ```Node.cloneNode``` .

```javascript
let child = element.appendChild();

let p = document.createElement( 'p' );
document.body.appendChild( p );
```

### Node.insertBefore() 

Добавляет элемент в список дочерних элементов родителя перед указанным элементом. Возвращает помещенный элемент. Если родитель пустой или второй аргумент не указант, то ```insertBefore()``` сработает как ```appendChild()``` . 

```javacript

let insertedElement = parentElement.insertBefore(newElement, referenceElement);

```

## Удаление узлов из DOM

### node.removeChild

Удаляет дочерний элемент из DOM. Возвращает удаленный элемент.

```javascript
// если родитель известен
let parent = document.getElementById( 'top' ),
    toDelete = document.getElementById( 'some' ),
    throwawayNode = parent.removeChild( toDelete );

// если родитель неизвестен
let node = document.getElementById( 'toDelete' );
if ( node.parentNode ) {
	node.parentNode.removeChild( node );
};

// удаление всех потомков
let element = document.getElementById( 'top' );
while ( element.firstChild ) {
	element.removeChild(element.firstChild);

// альтернативный вариант удаления 
element.innerHTMl = '';
};
```

## Скрытие DOM элементов
### element.hidden
Возвращает true, если у html тега установлен атрибут hidden. В противном случае false. Позволяет установить атрибут 
HTML элементу. Поддерживается начитая с IE11+.


