---
title: "`<bdi>`"
authors:
  - xpleesid
editors:
  - tachisis
keywords:
  - двунаправленный текст
tags:
  - doka
---

## Кратко

Тег `<bdi>` используется, когда нам нужно изолировать часть текста от влияния направления текста родителя. Это полезно, когда в тексте встречается несколько языков с разным направлением чтения, например, когда некоторые читаются слева направо, а другие — справа налево.

## Пример

```html
<p>
  <bdo dir="rtl">
    <bdi>Обычный текст</bdi> |
    Зеркальный текст
  </bdo>
</p>
```

Здесь используется тег [`<bdo>`](/html/bdo/) с атрибутом `dir="rtl"`, поэтому текст в нём будет идти справа налево. Но фраза «Обычный текст» изолирована, и текст идёт слева направо.

<iframe title="Базовый пример работы тега bdi." src="demos/basic/" height="120"></iframe>

## Как понять

_bdi_ означает Bidirectional Isolate — двунаправленная изоляция.

Тег `<bdi>` игнорирует направление текста родителя и для текста внутри устанавливает автоматическое направление. Таким образом создаётся изоляция — контент внутри `<bdi>` не зависит от направления текста снаружи.

## Ещё пример

Предположим, мы разрабатываем международный сайт и хотим вывести список самых активных пользователей. Для этого нам может пригодиться такой подход:

```html
<ul>
  <li>
    Пользователь <bdi>john_smith78</bdi>:
    167 комментариев.
  </li>
  <li>
    Пользователь
    <bdi>superPanda</bdi>:
    152 комментария.
  </li>
  <li>
    Пользователь <bdi>شاب رائع</bdi>:
    133 комментария.
  </li>
</ul>
```

<iframe title="Список пользователей с bdi." src="demos/userlist-bdi/" height="170"></iframe>

Однако если мы заменим `<bdi>` на, скажем, [`<b>`](/html/b/), то мы столкнёмся с неожиданным поведением:

```html
<li>
  Пользователь <b>شاب رائع</b>:
  133 комментария.
</li>
```

<iframe title="Список пользователей с b." src="demos/userlist-b/" height="170"></iframe>

У третьего пользователя логин на арабском языке, поэтому он читается справа налево. Из-за этого браузер считает, что следующие за ним символы также нужно вывести справа налево. Скорее всего, мы бы хотели избавиться от такого непредсказуемого поведения, поэтому в подобных ситуациях стоит изолировать логины или иной генерируемый пользователем контент при помощи тега `<bdi>`.

## Подсказки

💡 Тег `<bdi>` стоит использовать, если мы выводим сгенерированный пользователями контент, такой как логин или комментарий, и мы не уверены, в каком направлении будет идти этот текст. Многие языки имеют направление письменности справа налево, например, арабский, иврит или персидский.