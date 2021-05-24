# Style guide

## General Rule

>  Always format code by [prettier](https://prettier.io/)

- **Avoid using HTML tags in CSS selectors**

  - E.g. Prefer `.o-modal {}` over `div.o-modal {}`
  - Always prefer using a class over HTML tags (with some exceptions like CSS resets)

- **Don't use ids in selectors**

  - `#header` is overly specific compared to, for example `.header` and is much harder to override

- **Don’t nest more than 3 levels deep**

  - Nesting selectors increases specificity, meaning that overriding any CSS set therein needs to be targeted with an even more specific selector. This quickly becomes a significant maintenance issue.

- **Avoid using nesting for anything other than pseudo selectors and state selectors.**

  - E.g. nesting `:hover`, `:focus`, `::before`, etc. is OK, but nesting selectors inside selectors should be avoided.

- Don't 

  ```
  !important
  ```

  - Ever.
  - **If you must, leave a comment**, and prioritise resolving specificity issues before resorting to `!important`.

- Don’t use

  ```
  margin-top
  ```

  - Vertical margins [collapse](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing). Always prefer `padding-top` or`margin-bottom` on preceding elements

- Avoid shorthand properties (unless you really need them)

  - It can be tempting to use, for instance, `background: #fff` instead of `background-color: #fff`, but doing so overrides other values encapsulated by the shorthand property. (In this case, `background-image` and its associative properties are set to “none.”
  - This applies to all properties with a shorthand: border, margin, padding, font, etc.

- BEM

We recommend a variant of BEM with PascalCased “blocks”, which works particularly well when combined with components (e.g. React). Underscores and dashes are still used for modifiers and children.

```html
// ListingCard.jsx
function ListingCard() {
  return (
    <article class="ListingCard ListingCard--featured">

      <h1 class="ListingCard__title">Adorable 2BR in the sunny Mission</h1>

      <div class="ListingCard__content">
        <p>Vestibulum id ligula porta felis euismod semper.</p>
      </div>

    </article>
  );
}
```

```css
/* ListingCard.css */
.ListingCard { }
.ListingCard--featured { }
.ListingCard__title { }
.ListingCard__content { }
```

Variable

Prefer dash-cased variable names (e.g. `$my-variable`) over camelCased or snake_cased variable names. It is acceptable to prefix variable names that are intended to be used only within the same file with an underscore (e.g. `$_my-variable`).

## Namespace

There are a few reserved namespaces for classes to provide common and globally-available abstractions.

1. `.c-` for CSS components. Components are designed pieces of UI—think buttons, inputs, modals, and banners.
2. `.u-` for helpers and utilities. Utility classes are usually single-purpose and have high priority. Things like floating elements, trimming margins, etc.
3. `.is-, .has-` for stateful classes, a la [SMACSS](https://smacss.com/book/type-state). Use these classes for temporary, optional, or short-lived states and styles.
4. `._` for hacks. Classes with a hack namespace should be used when you need to force a style with `!important` or increasing specificity, should be temporary, and should not be bound onto.
5. `.js-`JavaScript-specific classes for JavaScript hook

## Media Query

1. Put inside selector

```css
$_screen_sm_max: "max-width: 767px";

.selector {
      float: left;

      @media only screen and ($_screen_sm_max) {
        float: none;
      }
}
```

