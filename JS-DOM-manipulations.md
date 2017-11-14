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

** **


## Создание DOM узлов 

**documentFragment**

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

## Добавление узлов в DOM


## Удаление узлов из DOM