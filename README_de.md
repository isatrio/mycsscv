#CSSCV

**CSSCV ist ein einfaches, dogmatisches Stylesheet, um semantisches HTML wie CSS eine CSS-Datei aussehen zu lassen.**

## Einstieg

Der schnellste Weg, mit CSSCV einzusteigen, ist, direkt ins HTML einzutauchen und anzupassen! Es gibt nichts im Sass, das nicht auch im HTML genutzt wird. Dadurch dient die `index.html` Datei als eine ausführliche, realitätsnahe Demo, um zu zeigen, was CSSCV bietet.

Unten folgt eine detailliertere Übersicht über CSSCV und wie genau es funktioniert.

## Dogmatisch?

CSSCV trifft meinen eigenen, persönlichen Schreibstil, was CSS angeht und nutzt ein spezielles Farb-Schema, [<cite>Solarized</cite>](http://ethanschoonover.com/solarized), Einige der weiteren dogmatischen Eigenschaften:

* [Nur einzelne Klassen sind als Selektor erlaubt](http://csswizardry.com/2012/05/keep-your-css-selectors-short/)
* [Das Namensschema folgt dem BEM-Stil](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
* [Regeln sind durch fünf Umbrüche getrennt](https://github.com/csswizardry/CSS-Guidelines#selection-titles)
* [Theoretisch geschachtelte Regeln sind eingerückt](https://github.com/csswizardry/CSS-Guidelines#anatomy-of-rulesets)
* [Einrücken entspricht vier Leerzeichen](https://github.com/csswizardry/CSS-Guidelines#anatomy-of-rulesets)

## Aktivieren

CSSCV kommt mit der Option, das Styling zu de/aktivieren. Dadurch lässt sich schnell und einfach das etwas unkonventionelle Aussehen von CSSCV entfernen und unformatiertes HTML ausgeben, wenn das HTML in einem standardkonformeren Format eines Lebenslaufes an Recruiter oder HR Teams übergeben werden muss. Langweilig, aber oftmals wichtig. 
CSSCV aktivieren ist super einfach. Dafür muss nur die Klasse `.csscv` dem `html` Element hinzugefügt werden. Alle Styles von CSSCV sind in diesem Namespace.

## CSSCV zum Laufen bringen

Es gibt ein paar einfache und doch strikte Regeln die einzuhalten sind, um CSSCV zu nutzen.
Regeln setzen sich aus Definitions-Listen und Kommentaren zusammen, Selektoren werden aus Header gebildet:

    <div class="ruleset">

        <h3 class="selector">Me</h3>

        <dl class="declarations">

            <dt class="property">Name</dt>
            <dd class="value"><span class="string">Harry Roberts</span></dd>

            <dt class="property">Job</dt>
            <dd class="value"><span class="string">Consultant Front-end Architect</span></dd>

            <dt class="property">Location</dt>
            <dd class="value"><span class="string">Leeds, UK</span></dd>

            <dt class="property">Skills</dt>
            <dd class="value">
                <ul class="value-list">
                    <li><span class="string">Front-end Architecture</span></li>
                    <li>Design</li>
                    <li>Development</li>
                    <li>OOCSS</li>
                    <li>Performance</li>
                    <li><span class="string">Responsive Web Design</span></li>
                    <li>Git</li>
                    <li>Vim</li>
                    <li>Agile</li>
                </ul>
            </dd>

        </dl>

    </div>

Schauen wir uns das mal genauer an:

* Jede Regel wird in einem Container mit der Klasse `.ruleset` umgeben.
* Der Titel, oder _Selektor_ dieser Regel ist ein Header mit der Klasse `.selector`.
* Die Deklarationen, aus denen sich die Regel zusammensetzt, befinden sich in einem `dl` Element mit der Klasse `.declarations`.
* Jedes Merkmal/Merkmalswert-Paar wird durch ein `dt` und ein `dd` gebildet. Diese haben die Klassen `.property` und `.value` respektive.
* Alle Strings, die in CSS von Anführungszeichen umhüllt werden müssten (z. B. `"Comic Sans MS"`) können von einem `span` Element mit der Klasse `.string` umhüllt werden. Das färbt sie unterschiedlich und fügt öffnende und schließende Anführungszeichen hinzu.
* Werte-Listen (z. B. `font-family: "Comic Sans MS", cursive;`) werden entweder durch geordnete oder ungeordnete Listen dargestelt, die die Klasse `.value-list` tragen.

Wie wir sehen, setzen sich die Regeln aus semantischen HTML Elementen zusammen und setzen stark auf CSS Pseudo-Elemente, um eine CSS-artige Syntax zu schaffen (Klammern, Kommata, Semikola, Anführungszeichen, usw).

## Was die Klassen tun

### `.csscv`

Diese Klasse wird dem `html` Element hinzugefügt und aktiviert CSSCV

### `.spaced`

Diese Klasse führt dazu, dass nach jedem Element, das diese Klasse trägt, ein Zeilenumbruch folgt.

### `.spaced--large`

Statt einem Zeilenumbruch folgen nun fünf Zeilenumbrüche.

### `.indented`

Alles, das diese Klasse träg, wird je nach gewählter Tab-Größe eingerückt (definiert in `$tab-size`).

### `.ruleset`

Diese Klasse wird wird einem Element hinzugefüg, das eine Regel definiert. Es platziert Regeln mit genügend Platz voneinander und kann auch die Klassen `.spaced--large` oder `.indented`.

### `.selector`

Diese Klasse wird jedem Header, der eine Regel beschreibt, hinzugefügt. Sie fügt einen Punkt davor und eine öffnende geschweifte Klammer nach dem Titel der Regel hinzu.

### `.selector__delimeter`

Diese Klasse wird einem leeren Span-Element hinzugefügt, um einem Mehr-Wort-Selektor einen Bindestrich hinzuzufügen. Zum Beispiel:

    <h2 class="selector">About<span class="selector__delimiter"> </span>me</h2>

### `.declarations`

Diese Klasse wird der Definitions-Liste hinzugefügt, die den Körper der Regel darstellt. Sie fügt eine schließende geschweifte Klammer am Ende der Definition hinzu.

### `.property`

Diese Klasse wird jedem `dt` Element hinzugefügt, das sich in der Definitions-Liste befindet. Sie rückt die Zeile um die gewählte Tab-Größe ein und fügt am Ende des Merkmals einen Doppelpunkt und ein Leerzeichen hinzu.

### `.value`

Diese Klasse wird jedem `dd` Element hinzugefüg, das einen Merkmalswert darstellt. Sie fügt am Ende der Zeile ein Semikolon hinzu.

### `.string`

CSS besitzt viele Merkmalswerte, die Leerzeichen beinhalten und dadurch mit Anführungszeichen umhüllt werden müssen. Diese müssen mit einem `span` mit der Klasse `.string` umhüllt werden.

### `.number`

Diese Klasse färbt einfach nur alle Zahl-artigen Merkmalswerte (z. B. `34px`, `#f00`).

### `.url`

Alle URL-artigen Merkmalswere können die `.url` Klasse tragen, um `url(` vorne und `)` hinten angestellt zu bekommen.

### `.value-list`

CSS besitzt viele Komma-getrennten Listen von Merkmalswerten. In CSSCV realisieren wir diese mit `ul`s und `li`s. Diese Elemente tragen die `.value-list` Klasse.

### `.element` und `.modifier`

Diese zwei Klassen erlauben es, eine [Namensgebung im BEM-Stil zu nutzen](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/), ohne das Markup zu verschmutzen. Um ein Element oder Modifizierer zu kennzeichen, wird die passende Klasse genutzt. Es muss außerdem das `data-namespace` genutzt werden, um den korrekten Block Name der Klasse voranzustellen, z. B.:
    <h3 class="selector">Job</h3>

    ...

    <h4 class="selector"><span class="modifier" data-namespace="job">Company</span></h4>

### `.comment`, `.comment-block` und `comment-block__line`

Diese Klassen, wenig überraschend, stylen das Markus wie Kommentare. Die `.comment` Klasse erzeugt ein Inline-Kommentar, während `.comment-block` einen Kommentar-Block erzeugt:

    <p class="comment-block">
        <span class="comment-block__line">Foo</span>
        <span class="comment-block__line">Bar</span>
        <span class="comment-block__line">Baz</span>
    </p>

### `.notice`

Das ist die Erwähnung ganz unten auf der CSSCV Seite.
Die Erwähnung einzufügen ist zwar kein muss, aber natürlich sehr gerne gesehen.
