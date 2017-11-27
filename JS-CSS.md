# Работа с CSS стилями в Java Script

### window.getComputedStyle( element, pseudoelement )
Возвращает скомпилированные стили после применения таблиц стилей и инлайновых стилей. 
В качестве первого параметра принимает ```element```, стили которого нужно рассчитать. Второй аргумент  - строка с 
псеводоэлементом или ```null```.
Возвращает коллекцию ```CSSStyleDeclaration```.

### CSSStyleDeclaration
Коллекция из пар ключ-значение (строка), описывающие скомпилированные стили определенного элемента.

#### CSSStyleDeclaration.cssText
Возвращает строку с содержанием инлайнового стиля элемента (только инлайнового).
```javascript
// HTML
<p id="test" style="color: red;">Some text.</p>
// CSS
#test {padding: 2em;}
//JS
let el = document.getElementById("test");
el.style.cssText; // color: red
```

#### CSSStyleDeclaration.length

#### CSSStyleDeclaration.parentRule


### element.style
Возвращает ```CSSStyleDeclaration```, который содержится в атрибуте ```style``` указанного элемента. С его помощью можно управлять инлайновыми стилями отдельного html-элемента.
```javascript
let el = document.getElementById("test");
el.style.marginTop = "1rem"; // <div id="test" style="margin-top: 1rem;"></div>
```
