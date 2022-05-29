🛠 Если при вёрстке макета вы видите в графическом редакторе межстрочное расстояние, заданное в пикселях, то не стоит переносить его в точности. В случае, если размер шрифта элемента изменится, то абсолютно заданное межстрочное расстояние не подстроится. А хотелось бы больше гибкости.

Используй следующую функцию для расчёта относительного интерлиньяжа:

```
line height / font size = относительный line-height
```

Если размер шрифта в Фотошопе равен 58px, а межстрочное расстояние — 86px, то результат будет таким:

```
86 / 58 = 1.482758621
```

При округлении получим значение `1.5`.

🛠 Если в Фотошопе интерлиньяж не указан (пустое поле), то он равен стандартному значению — 120%. Что аналогично 1.2 для вёрстки.