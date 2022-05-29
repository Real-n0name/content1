---
title: "`console.log()`"
authors:
  - doka-dog
contributors:
  - nlopin
  - corocoto
tags:
  - doka
---

## Кратко

`console.log();` — это метод, предназначенный для вывода в консоль браузера.

При написании скриптов порой требуется увидеть какой-либо промежуточный результат прямо в консоли браузера — это просто, удобно и не требует никакой дополнительной логики для отображения.

## Как пишется

Синтаксис написания крайне прост. `console.log()` выведет в консоль все переданные параметры:

```js
console.log("hello") // выведет "hello"
console.log(true, { a: true }, 100) // выведет true {a: true} 100
```

## Как это понять

⚡️ В момент разработки все действия кажутся долгими, поэтому можно воспользоваться молниеносным выводом в консоль.

Почему консоль разработчика, а не `alert`?

Открой консоль и сравни:

```js
let a = { id: 1, value: "one text" }
alert(a)
```

Вывод при таком подходе не отражает содержимого объекта `а`. Помимо этого приходится каждый раз закрывать диалоговое окно, что раздражает.

Другое дело если совершать эти действия в консоли:

```js
let a = { id: 1, value: "one text" }
console.log(a)
```

Результат представлен в виде древа, которое удобно раскрывается — видны все параметры.

💡 Если хочется вывести отладочное сообщение на страницу, то придётся воспользоваться или `alert` или создавать специальный `textarea`, чтобы записать туда свои вычисления. Также нужно будет перевести всё это в строку — проще будет читать.

## Особенность работы в браузере

В браузере с помощью `console.log` можно проверить мутацию [ссылочного типа](/js/ref-type-vs-value-type/). Этого можно добиться, раскрыв выведенное значение в консоли. Всё что нам нужно сделать — нажать на ►.

В качестве примера создадим массив с героями диснеевских мультфильмов. Изначально в нем будет располагаться только Микки Маус, а после вызова `console.log`, добавим и Плуто.

```js
const disneyCharacters = [{ name: 'Mickey Mouse', type: 'mouse' }]
console.log(disneyCharacters)
disneyCharacters.push({name: 'Pluto', type: 'dog' })
```

Нажмём на ► в консоли и увидим результат вывода:

![В консоли отображается массив с обоими героями](images/track-mutation.png)
В консоли выводится итоговый вид массива с добавленным Плуто

Причина в том, что значение ссылочного типа читается браузером только при его первом раскрытии. Этот процесс также называют _ленивым чтением (lazy-read)_.

<aside>

💡 Google Chrome при этом показывает информационную иконку, при наведении на которую отобразится подсказка с текстом: "This value was evaluated upon first expanding. It may have changed since then."

</aside>