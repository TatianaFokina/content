---
title: "`ArrayBuffer`"
description: "Объект с бинарными данными с фиксированной длинной."
authors:
  - doka-dog
keywords:
  - typed array
  - indexed collection
  - javascript collection
related:
  - js/arrays
  - js/typedarray
  - js/dataview
tags:
  - doka
  - placeholder
---

## Кратко

Объект, который содержит бинарные данные с фиксированной длинной и помогает с ними работать. Является частью типизированного массива [`TypedArray`](/js/typedarray/).

Типизированные массивы упрощают работу с тяжёлыми данными, например, видео, аудио и анимациями. Их часто используют с различными API — WebGL, Canvas 2D, XMLHttpRequest2 и так далее.

## Пример

```js
const buffer = new ArrayBuffer(3)
const view = new Int8Array(buffer)

console.log(view)
// Int8Array(3) [0, 0, 0, buffer: ArrayBuffer(3),
// byteLength: 3, byteOffset: 0, length: 3,
// Symbol(Symbol.toStringTag): 'Int8Array']
```

## Как пишется

Элементами из `ArrayBuffer` нельзя манипулировать без представления. По сути это просто ссылка на часть памяти, в которой хранятся байты информации.

У `ArrayBuffer` есть длина, которую указывают к скобках. К примеру, этот буфер содержит 8 байтов данных:

```js
new ArrayBuffer(8)
```

Представление можно создать при помощи объектов `TypedArray` или [`DataView`](/js/dataview/). Они отображают данные из буфера в нужном вам формате и дают доступ к записи и чтению его содержимого.

`ArrayBuffer` не возвращает запись о завершении, а его изначальное значение равно `0`.

### Свойства

- `ArrayBuffer.length` — длина `ArrayBuffer` в байтах. По умолчанию равна 1.
- `ArrayBuffer.prototype.byteLength` — размер `ArrayBuffer` в байтах, если для буфера используется метод `ArrayBuffer.prototype.resize()`.
- `ArrayBuffer.prototype.maxByteLength` — максимальный размер `ArrayBuffer` в байтах, до которого может быть увеличен буфер.
- `ArrayBuffer.prototype.resizable` — увеличивается ли размер буфера. Возвращает `true` или `false`.
- `ArrayBuffer.prototype.detached` — был ли отсоединён новый массив от старого. Возвращает `true` или `false`.

### Методы

- `ArrayBuffer.isView()` — возвращает представление буфера. Это может быть `true` или `false`.
- `ArrayBuffer.prototype.resize()` — увеличивает размер `ArrayBuffer` в байтах до указанного числа.
- `ArrayBuffer.prototype.slice()` — возвращает новый `ArrayBuffer`, который содержит копию старого.
- `ArrayBuffer.transfer()` — возвращает новый `ArrayBuffer`, который в том числе содержит данные из старого.
- `ArrayBuffer.prototype.transferToFixedLength()` — создаёт новый `ArrayBuffer` с неизменяемым размером и отсоединяет его от старого.

## Как понять

Буфер — пространство в памяти, где хранятся бинарные данные. Про память подробнее узнаете из статьи «[Как устроена память](/tools/trivial-memory-model/)».
