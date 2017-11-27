# Работа с CSS стилями в Java Script

### window.getComputedStyle( element, pseudoelement )
Возвращает скомпилированные стили после применения таблиц стилей и инлайновых стилей. 
В качестве первого параметра принимает ```element```, стили которого нужно рассчитать. Второй аргумент  - строка с 
псеводоэлементом или ```null```.
Возвращает коллекцию ```CSSStyleDeclaration```.

### CSSStyleDeclaration
Коллекция из пар ключ-значение (строка), описывающие скомпилированные стили определенного элемента.

#### CSSStyleDeclaration.cssText
Возвращает строку с содержанием инлайнового стиля элемента (только инлайнового). Может менять инлайновые стили, перезаписывая их.
```html
<p id="test" style="color: red;">Some text.</p>
```
```css
#test {padding: 2em;}
```
```javascript
let el = document.getElementById("test");
el.style.cssText; // color: red
el.style.cssText = 'margin-top: 50px;';
el.style.cssText; // margin-top: 50px
el.style.cssText += 'color: green;';
el.style.cssText; // margin-top: 50px;color: green;
```

#### CSSStyleDeclaration.length
Только чтение. Возвращает количество нлайновых ```style declarations``` указанного элемента. Если использовано сокраженное свойство, указывается количество входящих в него элементарных свойств.
```html
<div id="test" style="padding: 20px;">Lorem ipsum</div>
<div id="test2" style="padding-top: 20px;">Lorem ipsum</div>
```
```javascript
let test = document.getElementById( 'test' ),
    test2 = document.getElementById( 'test2' );
test.style.length; // 4
test2.style.length; // 1
```

#### CSSStyleDeclaration.parentRule


### element.style
Возвращает ```CSSStyleDeclaration```, который содержится в атрибуте ```style``` указанного элемента. С его помощью можно управлять инлайновыми стилями отдельного html-элемента.
```javascript
let el = document.getElementById("test");
el.style.marginTop = "1rem"; // <div id="test" style="margin-top: 1rem;"></div>
```
