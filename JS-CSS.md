# Работа с CSS стилями в Java Script

## [Скомпилированные стили](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#windowgetcomputedstyle-element-pseudoelement-)

[window.getComputedStyle()](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#windowgetcomputedstyle-element-pseudoelement-)

## [Инлайновые стили](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#elementstyle)

[element.style](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#elementstyle) | [style.cssText](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#elstylecsstext) | [style.length](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#elstylelength) | [style.parentRule](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#elstyleparentrule) | [style.getPropertyValue()](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#elstylegetpropertyvalueproperty) | [style.getPropertyPriority()](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#elstylegetpropertypriorityproperty) | [style.item()](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#elstyleitemindex) | [style.removeProperty()](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#elstyleremovepropertyproperty) | [style.setProperty()](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#elstylesetpropertypropertyname-value-priority)

## [Таблицы стилей](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#cssstylesheet)

[document.styleSheets](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#documentstylesheets) | [CSSStyleSheet](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#cssstylesheet) | [CSSStyleSheet.cssRules](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#cssstylesheetcssrules) | [CSSStyleSheet.deleteRule()](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#cssstylesheetdeleteruleindex) | [CSSStyleSheet.insertRule()](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#cssstylesheetinsertrulerule-index) | [CSSRule.cssText](https://github.com/2gnc/WebRes/blob/master/JS-CSS.md#cssrulecsstext)

### window.getComputedStyle( element, pseudoelement )
Возвращает скомпилированные стили после применения таблиц стилей и инлайновых стилей. 
В качестве первого параметра принимает ```element```, стили которого нужно рассчитать. Второй аргумент  - строка с 
псеводоэлементом или ```null```.
Возвращает коллекцию ```CSSStyleDeclaration```.

### CSSStyleDeclaration
Коллекция из пар ключ-значение (строка), описывающие все скомпилированные стили определенного элемента (в том числе унаследованные и по умолчанию).

### element.style
Возвращает ```CSSStyleDeclaration```, который содержится в атрибуте ```style``` указанного элемента. С его помощью можно управлять инлайновыми стилями отдельного html-элемента.
```javascript
let el = document.getElementById("test");
el.style.marginTop = "1rem"; // <div id="test" style="margin-top: 1rem;"></div>
```
#### el.style.cssText
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

#### el.style.length
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

#### el.style.parentRule
Возвращает родительские стили.

```javascript
var declaration = document.styleSheets[0].rules[0].style;
var rule = declaration.parentRule;
```

#### el.style.getPropertyValue(property)
Возвращает строку с значением указанного стиля (из инлайновых стилей).
```html
<div id="test" style="padding: 20px;">Lorem ipsum</div>
```
```javascript
let test = document.getElementById( 'test' );
test.style.getPropertyValue(padding); // 20px
```

#### el.style.getPropertyPriority(property)
Возвращает приоритет свойства (!important), если указано, или пустую строку.

#### el.style.item(index)
Возвращает имя свойства (по порядку, отсчет с 0).
```html
<div id="test" style="padding: 20px;">Lorem ipsum</div>
```
```javascript
let el = document.getElementById( 'test' ),
    prop = '';
for (let i =0; i < el.style.length; i++) {
	prop += el.style.item( i ) + '; '
};
console.log( prop ); // padding-top; padding-right; padding-bottom; padding-left;
```

#### el.style.removeProperty(property);
Удаляет указанное свойство.
```html
<div id="test" style="color: white; padding-top: 20px;">Lorem ipsum</div>
```
```javascript
let el = document.getElementById( 'test' );
console.log(el.style.cssText); // color: white; padding-top: 20px;
el.style.removeProperty('color');
console.log(el.style.cssText); // padding-top: 20px;
```

#### el.style.setProperty(propertyName, value, priority);
Устанавливает указанному свойству указанное значение и приоритет.
```html
<div id="test">Lorem ipsum</div>
```
```javascript
let el = document.getElementById( 'test' );
console.log( el.style.cssText ); // 
el.style.setProperty( 'color', 'red' );
console.log( el.style.cssText ); // color: red;
```

## document.styleSheets
Свойство, доступное только для чтения, возвращает объект псевдо-массив ```StyleSheetList```, содержащий объекты ```CSSStyleSheet ```.
```javascript
// на примере lenta.ru
let styleSheetList = document.styleSheets; // StyleSheetList {0: CSSStyleSheet, 1: CSSStyleSheet, 2: CSSStyleSheet, 3: CSSStyleSheet, 4: CSSStyleSheet, 5: CSSStyleSheet, 6: CSSStyleSheet, 7: CSSStyleSheet, length: 8}
```

### CSSStyleSheet

Объект ```CSSStyleSheet``` представляет собой один файл css-стилей, подключенный к странице. Наследуется от ```StyleSheet```. Содержит в себе css-правила ```CSSRule``` (объекты). Входит в состав ```document.styleSheets```

#### CSSStyleSheet.cssRules
Возвращает живую коллекцию ``` CSSRuleList``` CSS - правил, содержащихся в ```document.styleSheets[index]```.

#### CSSStyleSheet.deleteRule(index)
Удаляет указанное правило.

#### CSSStyleSheet.insertRule(rule, index)
Добавляет указанное правило, где rule - строка.

#### CSSRule.cssText
Строка, содержащая в себе одно правило из таблицы стилей. Например, ```body { background-color: darkblue; }```.


