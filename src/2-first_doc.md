# Создание первого документа
---
Чтобы создать первый LaTeX-документ, Вам потребуется создать обычный текстовый файл с расширением _.tex_ в любом текстовом редакторе, или новый документ в TeXMaker (в меню сверху: Файл -> Создать). После этого можно ввести следующий шаблон в наш .tex файл:
```latex
\documentclass{article}
\begin{document}
Text
\end{document}
```
_Вы можете ввести любой текст вместо "Text", но только без использования кириллицы. Далее мы рассмотрим, как включить кириллицу в LaTeX документе._\
\
Теперь попробуйте его скомпилировать. Если Вы используете редактор TeXMaker, Вы можете просто нажать на кнопку "Быстрая сборка" на панели инструментов. Если Вы пишете LaTeX код в текстовом редакторе и хотите компилировать самостоятельно, откройте командную строку или терминал и введите следующее:
```
pdflatex путь_к_файлу
```
Вместо `путь_к_файлу` нужно указать путь к Вашему .tex файлу, который Вы хотите скомпилировать. После успешной компиляции, pdflatex выведет информацию о том, где находится скомпилироуказать путь к Вашему .tex файлу, который Вы хотите скомпилировать. После успешной компиляции, pdflatex выведет информацию о том, где находится скомпилированный .pdf файл.\
![Пример 1](/examples/2_1.png)
Видим, что документ получился красивым и страница пронумерована. Теперь попробуйте заменить "Text" в коде выше на что-то на кириллице:
```latex
\documentclass{article}
\begin{document}
Текст
\end{document}
```
Попробуем скомпилировать данный документ.\
Выходит ошибка:
```
! LaTeX Error: Unicode character Т (U+0422)
               not set up for use with LaTeX.
```
Это происходит потому, что LaTeX по умолчанию не поддерживает русский язык, и чтобы добавить поддержку русского языка нужно включить в документ пакет _babel_, точнее нужные нам поддерживаемые языки оттуда. Для этого после `\documentclass{article}` добавим строку `\usepackage[english,russian]{babel}` и попробуем скомпилировать документ снова.\
![Пример 2](/examples/2_2.png)
Ура! Всё получилось. Теперь давайте попробуем разобраться в синтаксисе шаблона документа:
```latex
\documentclass{article}
\usepackage[english,russian]{babel}
\begin{document}
Текст
\end{document}
```
Можно сразу заметить, что для ввода команд используется символ \. Он также используется, когда в тексте нужно ввести какой-то символ, который относится к спецсимволам в LaTeX (`{}#$%&^~\_`). Например, если Вам нужно ввести знак процента в тексте, его нужно вводить как \%, чтобы % не выполнял ту функцию, которую ему присвоили как спецсимволу.\
Команда `\documentclass{article}` применяет к документу класс _article_, то есть _статья_. Это означает, что наш документ является статьёй и LaTeX применит к нему соответствующий шаблон. Также существуют другие классы, такие как _proc, minimal, report, book, slides_, но в этом учебнике будет использоваться именно article, так как он является наиболее часто используемым.\
С командой `\usepackage[...]{...}` мы уже разобрались. Можно заметить, что здесь также используются квадратные скобки, здесь они используются для применения конкретных настроек из пакета.
`\begin{document}` и `\end{document}` означают начало и завершение кода документа соответственно, как в языке Pascal.
В следующем параграфе будет рассмотрено создание _преамбулы документа_.