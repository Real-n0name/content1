---
title: "`@import`"
authors:
  - solarrust
editors:
  - tachisis
keywords:
  - import
  - директива
  - импорт
tags:
  - doka
---

## Кратко

При помощи директивы `@import` можно импортировать один файл со стилями в другой файл со стилями.

## Пример

Предположим, в проекте для удобства стили разделены на несколько файлов:

1. _fonts.css_ — файл с подключением шрифтов и стилями.
1. _buttons.css_ — файл со стилями для кнопок.
1. _main.css_ — основной файл стилей с остальным CSS-кодом.

Нам нужно, чтобы все стили загружались при открытии страницы. Для этого импортируем отдельные файлы в наш основной файл _main.css_:

```css
@import "fonts.css";
@import "buttons.css";

/*  Остальной CSS-код */
```

## Как пишется

<aside>

☝️ Начнём с важного: все директивы импорта должны быть в самом верху CSS-файла, до всего остального кода. Иначе не сработает.

</aside>

Равнозначные варианты импорта:

```css
@import "file.css";
@import url("file.css");
```

Технической разницы между этими двумя вариантами нет. Файлы будут импортироваться одинаково в обоих случаях. Путь до файла может быть как абсолютным, так и относительным.

Можно указать, для каких типов устройств должны применяться стили из импортируемого файла:

```css
@import "print-styles.css" print;
@import "screen-styles.css" screen;
```

В этом примере стили из файла, импортируемого в первой строке, будут применяться только при печати. А стили из файла, импортируемого во второй строке, будут применяться для отображения на экране.

Допустимо указывать несколько медиавыражений после пути:

```css
@import "file.css" (min-width: 481px) and (max-width: 768px);
@import "file.css" screen and (orientation: landscape);
```

Можно проверить, поддерживается ли какое-то конкретное правило или выражение в браузере пользователя, и загрузить для него конкретные стили. Для этого используется правило `supports`:

```css
@import "file.css" supports(not (display: flex));

/* Остальной CSS-код */
```

В этом примере для браузеров, которые не поддерживают флексбоксы, будет загружена _запасная_ таблица стилей. Для всех остальных будут использованы стили, написанные ниже правила импорта.

## Как это понять

Во время загрузки страницы браузер пройдёт по всем указанным в импортах путям и загрузит таблицы стилей. Затем прочитает правила ниже импортов и отрисует страницу на основании комбинации всего CSS.

## Подсказки

💡 Желательно не злоупотреблять импортами. Потенциально это может замедлить загрузку страницы.

💡 Все импорты всегда должны быть в начале CSS-файла.

💡 Поскольку браузер читает медиавыражения, указанные после пути до файла в импорте в последнюю очередь, то он в любом случае сходит по ссылке _почитать_ стили и только потом определит, нужно ли их применять. Эту особенность стоит держать в голове.