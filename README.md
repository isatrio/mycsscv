#CSSCV

**CSSCV est une feuille de style simple et opiniâtre pour le formatage du HTML sémantique pour ressembler à un fichier CSS.**

## Commencer

Le moyen le plus simple pour commencer avec CSSCV est de plonger directement dans le HTML et
obtenir l'édition! Il n'y a rien dans le Sass qui n'est pas utilisé dans le HTML, de sorte que le
Le fichier `index.html` est une démonstration complète et concrète de ce que CSSCV peut faire.


Voici un aperçu plus détaillé des tenants et aboutissants du fonctionnement du CSSCV.

## Opinionated?

Dogmatique?
CSSCV correspond à mon propre style d'écriture CSS, et utilise une couleur spécifique
schéma, [<cite> Solarized </ cite>](http://ethanschoonover.com/solarized). Une partie de
ses autres caractéristiques plus opiniâtres:

* [Only single classes are allowed as selectors](http://csswizardry.com/2012/05/keep-your-css-selectors-short/)
* [It uses a BEM-style naming convention](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
* [Rulesets are spaced by five carriage returns](https://github.com/csswizardry/CSS-Guidelines#section-titles)
* [Quasi-nested rulesets are indented](https://github.com/csswizardry/CSS-Guidelines#anatomy-of-rulesets)
* [All indents are four spaces](https://github.com/csswizardry/CSS-Guidelines#anatomy-of-rulesets)

## Enabling

CSSCV comes with the option to [en|dis]able its styling. This is so that you can
quickly and easily remove CSSCV’s unconventional look, and instead expose
unstyled HTML in case you ever need to provide a more standard format of CV to
recruiters or HR teams. Boring, but often vital. Enabling CSSCV is as simple as
adding a class of `.csscv` the the `html` element; all of CSSCV’s styles are
scoped to this namespace.

## Making stuff work

There are a series of simple yet strict rules to follow in order to use CSSCV.
Rulesets are built using definition lists and comments and selectors are usually
constructed using headings. Below is a simple example that we will deconstruct:

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

Let’s take a look at what this does:

* We wrap each ruleset in a container with a `.ruleset` class.
* The title, or _selector_, of that ruleset is a heading which carries the
  `.selector` class.
* The declarations that make up the ruleset are marked up in a `dl` which has a
  class of `.declarations`.
* Each property/value pair are marked up with `dt`s and `dd`s respectively.
  These, respectively, carry classes of `.property` and `.value`.
* Any strings that would require quoting in CSS (e.g. `"Comic Sans MS"`) can
  be wrapped in a `span` with a class of `string`. This colours them differently
  and applies opening and closing quote marks.
* Lists of values (e.g. `font-family: "Comic Sans MS", cursive;`) are marked up
  as either ordered- or unordered-lists which carry a class of `.value-list`.

As we can see, the rulesets are formed of semantic HTML elements and heavy use
of CSS pseudo-elements are used to apply CSS-like syntax (braces, (semi-)colons,
quotes, etc).

## What the classes do

### `.csscv`

This class gets applied to the `html` element and enables CSSCV

### `.spaced`

This class forces all elements which carry it to have one carriage return’s
space between itself and the following element.

#### `.spaced--large`

This increases the spacing from one to five carriage returns.

### `.indented`

Anything carrying this class will be indented by your chosen tab size amount
(defined in `$tab-size`).

### `.ruleset`

This class is applied to an element which wraps each whole ruleset. It spaces
rulesets apart from each other, and can also carry the `.spaced--large` or
`.indented` classes.

### `.selector`

This class is applied to headings which introduce each ruleset. It adds a period
before, and an opening brace after, the title of the ruleset.

### `.selector__delimiter`

This class is applied to an empty span in order to hyphen-delimit multi-word
selectors. For example:

    <h2 class="selector">About<span class="selector__delimiter"> </span>me</h2>

### `.declarations`

This class is applied to the definition list that will form the body of the
ruleset. It adds a closing brace after the final declaration.

### `.property`

This class is applied to each `dt` element which is a declaration’s property. It
indents the declaration as per your chosen tab size and adds a trailing colon
and space.

### `.value`

This is applied to each `dd` element which becomes a declaration’s value. It
adds a trailing semi-colon.

### `.string`

CSS often has values which contain spaces which need quoting, wrap these strings
in a `span` that carries the `.string` class.

### `.number`

This class simply colours any number-like values (e.g. `34px`, `#f00`).

### `.url`

Any URL-like values can have the `.url` class applied to them to prepend `url(`
and append `)` to it.

### `.value-list`

CSS contient souvent des listes de valeurs séparées par des virgules. En CSSCV, nous les marquons
comme `ul`s et` li`s. Le `ul` prend la classe` .value-list`.
### `.element` and `.modifier`

Ces deux classes vous permettent d'utiliser
[BEM-style naming](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
sans polluer votre balisage. Pour indiquer un élément ou un modificateur, utilisez le
classe correspondante. Vous devez également utiliser l'attribut `data-namespace` dans
afin de préfixer la classe avec le nom de bloc correct, par exemple:
    <h3 class="selector">Job</h3>

    ...

    <h4 class="selector"><span class="modifier" data-namespace="job">Company</span></h4>

### `.comment`, `.comment-block` and `.comment-block__line`


Ces classes, sans surprise, style de balisage pour ressembler à des commentaires. Le `.comment`
class donne un commentaire en ligne, tandis que `.comment-block` nous donne un DocBlock
commentaire de style:

    <p class="comment-block">
        <span class="comment-block__line">Foo</span>
        <span class="comment-block__line">Bar</span>
        <span class="comment-block__line">Baz</span>
    </p>

### `.notice`

C'est le message d'attribution qui apparaît en bas de la page CSSCV.
Y compris le message n'est pas obligatoire, mais est apprécié.
