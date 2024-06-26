---
title: "`.getElementsByTagName()`"
description: "Получаем список элементов с искомым тегом."
authors:
  - nlopin
related:
  - js/dom
  - tools/how-the-browser-creates-pages
  - js/events
tags:
  - doka
---

## Кратко

Метод определён для объекта `document` и любого HTML-элемента ([`Element`](/js/element/)) страницы. Позволяет найти все элементы с заданным тегом среди дочерних. Возвращает похожую на массив [`HTMLCollection`](/js/htmlcollection-and-nodelist/) с найденными элементами. Если элементов не нашлось, то коллекция будет пустая, то есть с размером 0.

## Пример

Метод принимает один параметр — название тега в виде строки. Например, [`<div>`](/html/div/), [`<form>`](/html/form/), [`<h5>`](/html/h1-h6/).

```html
<body>
  <div id="title">
    <h1>Привет, незнакомец!</h1>
    <p>Это параграф, дочерний и для div, и для body</p>
  </div>
  <p>Это параграф, дочерний для body</p>
</body>
```

```js
const pFromBody = document.getElementsByTagName('p')
console.log(pFromBody.length)
// 2

const divEl = document.getElementById('title')
// Ищем параграфы внутри <div>
const pFromDiv = divEl.getElementsByTagName('p')
console.log(pFromDiv.length)
// 1, так как внутри <div> только один <p>

// Ищем несуществующий элемент
const spanFromBody = document.getElementsByTagName('span')
console.log(spanFromBody.length)
// 0
```

Динамический пример, в котором поиск ведётся по кликнутому блоку:

<iframe title="Демонстрация работы метода" src="demos/Lopinopulos-LoZaJp/" height="300"></iframe>

## Как понять

Метод работает с DOM, который связан с HTML-разметкой. Каждый HTML-элемент имеет родительские и дочерние элементы.

- Родительские элементы — это элементы, внутри которых находится элемент. В примере выше у элемента [`<h1>`](/html/h1-h6/) есть два родительских элемента — `<div>` и [`<body>`](/html/body/).
- Дочерние элементы — это элементы, которые содержит текущий элемент. Они могут быть, а могут не быть. Например, для тега `<body>` все элементы страницы дочерние. У `<h1>` дочерний элемент — текст внутри тега.

Если работаете с корнем страницы, объектом `document`, поиск идёт по всем элементам страницы, то есть от `<body>`. Если от конкретного элемента, поиск идёт только по его дочерним элементам.

Так как мы заранее не знаем, сколько элементов с искомым тегом найдётся, метод возвращает коллекцию элементов.
