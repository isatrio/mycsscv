﻿#CSSCV

** CSSCV е прост, субективен стайлшиит за форматиране на семантичен HTML, за да изглежда
като CSS файл. **

## Първи стъпки

Най - лесният начин да започнете с CSSCV е да се гмурнем право в HTML и
да започнете да работите! Няма нищо в Sass, което да не се използва в HTML, така че
файлът `index.html` действа като цялостно реално демо за това, което CSSCV може да прави.

По-долу е представен по-подробен преглед на начина, по който работи CSSCV.

## Субективен?

CSSCV съвпада с моя личен стил на писане на CSS и използва специфична цветова
схема, [<cite>Solarized</ cite>] (http://ethanschoonover.com/solarized). Някои 
други по-субективни черти:

* [Като селектори се допускат само отделни класове] (http://csswizardry.com/2012/05/keep-your-css-selectors-short/)
* [Използва конвенция за наименуване на стил BEM] (http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
* [Наборът от правила е разделен на пет карета) (https://github.com/csswizardry/CSS-Guidelines#section-titles)
* [Квази-вложените правила са индентирани] (https://github.com/csswizardry/CSS-Guidelines#anatomy-of-rulesets)
* [Всички инденти са четири интервала] (https://github.com/csswizardry/CSS-Guidelines#anatomy-of-rulesets)

## Активиране

CSSCV идва с опцията да активира/деактивира стила си. Това е така, за да можете
бързо и лесно да премахне нестандартния външен вид на CSSCV и вместо това да се изложи на показ
нестилизиран HTML в случай, че някога е необходимо да предоставите по-стандартен формат на автобиография
персонал за набиране на персонал или екипи по човешки ресурси. Скучно, но често жизненоважно.За активирането на CSSCV е достатъчно
да се добави клас `.csscv` на елемента `html`; всички стилове на CSSCV са
обхванати в този неймспейс.

## Да работим

Има няколко прости, но строги правила, които да следвате, за да използвате CSSCV.
Наборите от правила се изграждат, като се използват списъци с определения и коментари и селекторите обикновено
са конструирани с използване на заглавия. По-долу е един прост пример, който ще деконструираме:

    <div class = "ruleset">

        <h3 class = "selector"> Me </ h3>

        <dl class = "declarations">

            <dt class = "property"> Име </ dt>
            </ span> </ span> <span class = "string"> Хари Робъртс </ span>

            <dt class = "property"> Работа </ dt>
            <dd class = "value"> <span class = "string"> Консултант Front-end Architect </ span> </ dd>

            <dt class = "property"> Местоположение </ dt>
            <dd class = "value"> <span class = "string"> Лийдс, Великобритания </ span> </ dd>

            <dt class = "property"> Умения </ dt>
            <dd class = "value">
                <ul class = "value-list">
                    <li> <span class = "string"> Архитектура на Front-End </ span> </ li>
                    <Li> Дизайн </ Li>
                    <Li> Разработка </ Li>
                    <Li> OOCSS </ Li>
                    <Li> Производителност </ Li>
                    <li> <span class = "string"> Responsive уеб дизайн </ span> </ li>
                    <Li> Git </ Li>
                    <Li> Vim </ Li>
                    <Li> Agile </ Li>
                </ ul>
            </ dd>

        </ dd>

    </ DIV>

Нека да разгледаме какво прави това:

* Обвиваме всеки набор от правила в контейнер с клас `.ruleset`.
* Заглавието или селекторът на този набор от правила е заглавие, което носи
  `.selector` клас.
* Декларациите, които съставят набора от правила, са маркирани в `dl`, което има
  клас `.declarations`.
* Всяка двойка property / value се маркира съответно с `dt` и `dd`.
  Те, съответно, носят класове на `.property` и `.value`.
* Всички стрингове, които биха се нуждаели от цитиране в CSS (например `"Comic Sans MS"`) могат
  да бъдат обвити в `span` с класа на `string`. Това ги оцветява различно
  и прилага кавички за отваряне и затваряне.
* Списъци със стойности (напр. `font-family: "Comic Sans MS", cursive;`) се маркират
  като наредени или неподредени списъци, които носят клас `.value-list`.

Както можем да видим, наборът от правила се формира от семантични HTML елементи и тежка употреба
на псевдоелементите на CSS се използват за прилагане на CSS-подобен синтаксис (скоби, (полу)
котировки и т.н.).

## Какво правят класовете

### `.csscv`

Този клас се прилага към елемента `html` и активира CSSCV

### `.spaced`

Този клас принуждава всички елементи, които го носят, да има едно разстояние между себе си и следния елемент.

#### `.spaced - large`

Това увеличава разстоянието от една до пет спейса.

### `.indented '

Всичко, което носи този клас, ще бъде индентирано с избрания от вас брой табове
(дефинирани в `$tab-size`).

### `.ruleset`

Този клас се прилага към елемент, който обвива всеки набор от правила. Отделя
наборите от правила един от друг и могат да носят и `.spaced-large` или
`.indentated` класове.

### `.selector`

Този клас се прилага за заглавия, които въвеждат всеки набор от правила. Добавя период
преди, и отваряща скоба след, заглавието на набора от правила.

### `.selector__delimiter`

Този клас се прилага на празен интервал, за да се разделят тирета с няколко типа
селектори. Например:

    <h2 class = "selector"> Относно <span class = "selector__delimiter"> </ span> мен </ h2>

### `.declarations`
Този клас се прилага към списъка с определения, който ще формира тялото на
набор от правила. Добавя затваряща скоба след окончателната декларация.

### `.property`

Този клас се прилага за всеки елемент `dt`, който е собственост на декларацията. То
вмъква декларацията според избрания размер на раздела и добавя последваща запетайка
и пространство.

### `.value`

Това се прилага за всеки елемент `dd`, който става value на декларация. То
добавя последваща точка и запетая.

### `.string`

CSS често има стойности, които съдържат спейсове, които трябва да цитират, да обгръщат тези стрингове
в `span`, който носи класа `.string`.

### `.number`

Този клас просто оцветява всякакви числови стойности (например `34px`, `#f00`).

### `.url`

Всички стойности, подобни на URL, могат да имат класа `.url`, приложен към тях, за да сложат пред него `url(`
и `)` след него.

### `.value-list`

CSS често съдържа списъци със стойности, разделени със запетая. В CSSCV ги отбелязваме
като `ul` и `li`. `Ul` отнема класа `.value-list`.

### `.element` and `.modifier`

Тези два класа ви позволяват да използвате
[Име на стил BEM] (http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
без да замърсявате маркъпа си. За да означите елемент или модификатор, използвайте
съответния клас. Трябва също да използвате атрибута `data-namespace` в
за да сложите отпред клас с правилното име на блока, например:

    <h3 class = "selector"> Работа </ h3>

    ...

    <h4 class = "selector"> <span class = "modifier" data-namespace = "job"> Компания </ span>

### `.comment`, `.comment-block` и `.comment-block__line`

Тези класове, не е изненадващо, стилизират маркъпа да изглежда като коментари. `.comment`
класът дава inline коментар, докато `.comment-block` ни дава коментар със стил DocBlock:

    <p class = "comment-block">
        <span class = "comment-block__line"> Foo </ span>
        <span class = "comment-block__line"> Бар </ span>
        <span class = "comment-block__line"> Baz </ span>
    </ P>

### `.notice`

Това е съобщението, което се показва в долната част на страницата на CSSCV.
Включването на съобщението не е задължително, но е оценено.