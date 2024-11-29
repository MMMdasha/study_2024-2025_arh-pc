---
## Front matter
title: "Отчёт по лабораторной работе №8"
subtitle: "Программирование
цикла. Обработка аргументов командной строки."
author: "Малкина Дарья Александровна"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Приобретение навыков написания программ с использованием циклов и обработкой
аргументов командной строки.

# Выполнение лабораторной работы

## Реализация циклов в NASM

1. Создаём файл lab8-1.asm и вводим в него текст программы из листинга 8.1, после создаём исполнительный файл и запускаем его:

![Программа lab8-1](image/1.1.png){#fig:001 width=70%}

Замечаем, что программа работает некорректно, вносим изменения:

![Изменение программы lab8-1](image/1.2.png){#fig:002 width=70%}
 
Создаём исполнительный файли запускаем изменённую программу, в результате получаем бесконечный цикл, который возникает из-за отсутсвия условия выхода из цикла loop, так как мы переписываем значение N новым значением ecx, то ecx никогда не достигает 0:
 
![Программа lab8-1 бесконечный цикл](image/1.3.png){#fig:003 width=70%}
 
Снова вносим изменения в текст программы, добавляем стек:

![Добавление стека в программу lab8-1](image/1.4.png){#fig:004 width=70%}
 
Запускаем исправленную программу, теперь вывод верный, программа работает корректно, число проходов цикла соответствует значению 𝑁, введенному с клавиатуры:

![Исправленная программа lab8-1](image/1.5.png){#fig:005 width=70%}

## Обработка аргументов командной строки

2. Создаём файл lab8-2.asm и вводим в него текст программы из листинга 8.2 после создаём исполняемый файл и запускаем его, указав аргументы:

![Программа lab8-2](image/2.1.png){#fig:006 width=70%}

В итоге программой было обработано четыре аргумента.

3. Создаём ещё файл lab8-3.asm и вводим в него текст программы, которая выводит сумму введённых аргументов, после создаём исполняемый файл и запускаем его, указав аргументы:

![Программа lab8-3 сумма аргументов](image/3.1.png){#fig:007 width=70%}

Изменим текст программы так, что бы выводом было произведение введённых аргументов:

![Изменение программы lab8-3](image/3.2.png){#fig:008 width=70%}

Создаём исполнительный файл и запускаем его, указав аргументы:

![Программа lab8-3 произведение аргументов](image/3.3.png){#fig:009 width=70%}

Проверяем, проведя расчёты вручную, и убеждаемся, что программа работает корректно.

# Задание для самостоятельной работы

1. Напишем программу, которая будет находить сумму значений f(x)=4*x+3.
Зададим сообщения, которые будут выводся по окончании работы программы:

![msg1, msg2](image/4.1.png){#fig:010 width=70%}

Пропишем извлечение из стека в ecx количество аргументов и извлечение из стека в edx имя программы, а также переход к следующим аргументам и используем esi для хранения промежуточных результатов:

![Извлечение аргументов из стека и переход к след. аргументам](image/4.2.png){#fig:011 width=70%}

Затем пропишем вычисление, сохраняя результат в esi, и переход к обработке следующего аргумента, если есть ещё аргументы:

![Вычисление](image/4.3.png){#fig:012 width=70%}

Наконец напишем вывод сообщений msg1 и msg2, вывод результата и завершение программы:

![Вывод и выход из программы](image/4.4.png){#fig:013 width=70%}

Создаём исполнительный файл и запускаем его, проверим работу программы с разными аргументами:

![Программа lab8-var5](image/4.5.png){#fig:014 width=70%}

Проверяем, проведя расчёты вручную, и убеждаемся, что программа работает корректно.

# Выводы

В ходе лабораторной работы мы изучили программирование циклов и обработку аргументов командной строки, также попрактиковались работать с циклами, аргументами и ошибками, которые возникают при неверном управлении циклами и стеком.

# Список литературы{.unnumbered}

::: {#refs}
:::
