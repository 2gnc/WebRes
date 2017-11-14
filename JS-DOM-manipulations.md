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

``` javascript
window.addEventListener( 'DOMContentLoaded', function(){
// commands
	});
```

## Выборки

