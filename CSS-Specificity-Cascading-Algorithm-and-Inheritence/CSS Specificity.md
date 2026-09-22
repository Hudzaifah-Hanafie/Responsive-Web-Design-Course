# CSS Specificity

CSS specificity determines **which CSS declaration wins when multiple rules apply to the same element**.

Understanding specificity helps you reason about conflicting CSS rules instead of relying on trial and error.

> **Core idea:** The selector with the higher specificity generally wins when competing declarations target the same property. If specificity is equal, the rule that appears later wins.

---

## 1. Specificity at a Glance

Specificity can be represented as a four-part value:

`(a, b, c, d)`

| Part | What it counts | Example |
| --- | --- | --- |
| `a` | Inline styles | `style="color: red"` |
| `b` | ID selectors | `#unique` |
| `c` | Class selectors, attribute selectors, pseudo-classes | `.button`, `[type="text"]`, `:hover` |
| `d` | Type selectors and pseudo-elements | `p`, `div`, `::before` |

The general order is:

```text
Inline styles
    ↓
ID selectors
    ↓
Class / attribute / pseudo-class selectors
    ↓
Type / pseudo-element selectors
    ↓
Universal selector (*)
```

The universal selector contributes `0` to specificity.

### Important: Internal vs. External CSS

**Internal CSS and external CSS do not have different specificity just because of where they are written.**

Specificity comes from the selectors themselves.

For example:

- An ID selector in internal CSS → `(0, 1, 0, 0)`
- A class selector in external CSS → `(0, 0, 1, 0)`
- A type selector in either location → `(0, 0, 0, 1)`

When competing rules have equal specificity, the rule that appears later wins.

---

## 2. Inline Styles

Inline styles are written directly on an HTML element using the `style` attribute.

They have a specificity value of:

`(1, 0, 0, 0)`

For example:

```html
<p style="color: red;">This text is red.</p>
```

If an external stylesheet contains:

```css
p {
  color: blue;
}
```

the first paragraph will still be red because the inline style has higher specificity than the type selector.

```html
<link rel="stylesheet" href="styles.css">

<p style="color: red;">Red paragraph</p>
<p>Other paragraph</p>
<p>Another paragraph</p>
<p>Yet another paragraph</p>
```

```css
p {
  color: blue;
}
```

### Key point

Inline styles have higher specificity than normal ID, class, and type selectors.

---

## 3. ID Selectors

An ID selector uses `#` followed by an ID name.

IDs should be unique within an HTML document.

```html
<link rel="stylesheet" href="styles.css">

<p id="para-1">Red paragraph</p>
<p>Other paragraph</p>
<p>Another paragraph</p>
<p>Yet another paragraph</p>
```

```css
#para-1 {
  color: red;
}

p {
  color: blue;
}
```

The first paragraph is red because the ID selector has higher specificity than the `p` type selector.

An ID selector has a specificity value of:

`(0, 1, 0, 0)`

### Key point

An ID selector can override class and type selectors, but a normal ID rule can still be overridden by an inline style.

---

## 4. Class, Attribute, and Pseudo-Class Selectors

Class selectors, attribute selectors, and pseudo-classes have the same specificity category.

### Class selectors

A class selector begins with `.`:

```css
.example-para {
  color: green;
}
```

### Attribute selectors

Attribute selectors target elements based on their attributes:

```css
[type="text"] {
  color: green;
}
```

### Pseudo-classes

Pseudo-classes represent a particular state or condition of an element:

```css
button:hover {
  color: green;
}
```

> **Note:** Pseudo-classes are covered in more detail in later lessons.

These selectors contribute to the `c` part of specificity.

For example:

`(0, 0, 1, 0)`

### Example

```html
<link rel="stylesheet" href="styles.css">

<p id="para-1">Example paragraph</p>
<p class="example-para">Other paragraph</p>
<p id="para-3" class="example-para">Another paragraph</p>
<p>Yet another paragraph</p>
```

```css
#para-1 {
  color: red;
}

#para-3 {
  color: purple;
}

.example-para {
  color: green;
}

p {
  color: blue;
}
```

The results are:

- The first paragraph is **red** because the ID selector has higher specificity than the type selector.
- The second paragraph is **green** because the class selector overrides the type selector.
- The third paragraph is **purple** because the ID selector overrides the class selector.
- The remaining paragraph is **blue** because only the type selector matches it.

---

## 5. Type Selectors

Type selectors, also called **element selectors**, target elements by their HTML tag name.

Examples:

```css
p {
  color: blue;
}

div {
  margin: 10px;
}

h1 {
  font-size: 2rem;
}
```

A type selector has a specificity value of:

`(0, 0, 0, 1)`

For example:

```html
<link rel="stylesheet" href="styles.css">

<p>Paragraph one</p>
<p>Paragraph two</p>
<p>Paragraph three</p>
```

```css
p {
  color: blue;
}
```

All `p` elements will have blue text.

### Type selector vs. class selector

Consider:

```html
<link rel="stylesheet" href="styles.css">

<p class="para">I am a paragraph</p>
<p class="para">Here is another paragraph</p>
```

```css
p {
  color: blue;
}

.para {
  color: red;
}
```

Both rules match the paragraphs, but `.para` has higher specificity than `p`.

Therefore, the paragraphs are red.

### Key point

Type selectors have relatively low specificity. They can be overridden by class selectors, ID selectors, and inline styles.

---

## 6. Pseudo-Elements

Pseudo-elements, such as `::before` and `::after`, are in the same low-specificity category as type selectors.

They contribute to the `d` part of the specificity value.

> **Note:** Pseudo-elements are covered in more detail in later lessons.

For example:

```css
p::before {
  content: "Note: ";
}
```

The `p` and `::before` portions both contribute to the selector's specificity.

---

## 7. Universal Selector (`*`)

The universal selector is written as:

```css
*
```

It matches any element.

It is often useful when applying a general style to all elements, such as resetting margins and padding:

```html
<link rel="stylesheet" href="styles.css">

<h1>Heading element</h1>
<p>Example paragraph element</p>
```

```css
* {
  margin: 0;
  padding: 0;
}
```

This applies the declarations to all elements matched by the universal selector.

### Specificity of `*`

The universal selector contributes **zero** to specificity:

`(0, 0, 0, 0)`

It therefore has lower specificity than type selectors, classes, IDs, and inline styles.

### Example: Multiple Specificity Levels

```html
<head>
  <style>
    * {
      color: blue;
    }

    p {
      color: red;
    }

    .highlight {
      color: green;
    }

    #unique {
      color: purple;
    }
  </style>
</head>

<body>
  <p id="unique" class="highlight">This text has multiple styles applied.</p>
</body>
```

All four rules match the paragraph, but they have different specificity:

| Selector | Specificity | Result |
| --- | --- | --- |
| `*` | `(0, 0, 0, 0)` | Lowest |
| `p` | `(0, 0, 0, 1)` | Overrides `*` |
| `.highlight` | `(0, 0, 1, 0)` | Overrides `p` |
| `#unique` | `(0, 1, 0, 0)` | Overrides `.highlight` |

Therefore, the text is **purple**.

---

## 8. Combining Selectors Increases Specificity

Selectors can be combined to target a more specific group of elements.

For example:

```html
<p class="bold-text">Example paragraph</p>
<p class="bold-text">Example paragraph</p>
<p>Another paragraph</p>
<p>Yet another paragraph</p>
```

```css
p.bold-text {
  font-weight: bold;
}
```

The selector `p.bold-text` targets only `p` elements that also have the `bold-text` class.

Its specificity is:

`(0, 0, 1, 1)`

It contains:

- one class selector → `c = 1`
- one type selector → `d = 1`

This is more specific than either `p` alone or `.bold-text` alone.

---

## 9. Internal CSS

Internal CSS is written inside a `<style>` element, usually in the `<head>` of an HTML document.

```html
<head>
  <style>
    #text {
      color: blue;
    }
  </style>
</head>

<body>
  <div id="text">This text is blue.</div>
</body>
```

The selector is `#text`, so its specificity is:

`(0, 1, 0, 0)`

The fact that the rule is inside a `<style>` element does **not** give it a special specificity value.

### Internal CSS vs. external CSS

Internal and external CSS follow the same specificity rules.

For example:

```html
<head>
  <style>
    p {
      color: blue;
    }
  </style>

  <link rel="stylesheet" href="styles.css">
</head>
```

If `styles.css` also contains:

```css
p {
  color: red;
}
```

both selectors have the same specificity:

`(0, 0, 0, 1)`

Because the external rule appears later, it wins.

If the external stylesheet were linked before the `<style>` block, the internal rule would win instead.

> **Remember:** When specificity is equal, **source order matters**.

---

## 10. External CSS

External CSS is written in a separate `.css` file and connected to HTML using a `<link>` element.

```html
<head>
  <link rel="stylesheet" href="styles.css">
</head>

<body>
  <div class="text">This text's color is defined in an external CSS file.</div>
</body>
```

The external stylesheet could contain:

```css
.text {
  color: purple;
}
```

The `.text` selector has a specificity value of:

`(0, 0, 1, 0)`

Like internal CSS, external CSS does not have a special specificity level based on where it is stored.

External stylesheets are especially useful for larger projects because they keep styling separate from HTML and are easier to maintain.

---

## 11. Calculating Specificity

Specificity can be thought of as four separate counts:

```text
(a, b, c, d)
 │  │  │  │
 │  │  │  └─ type selectors + pseudo-elements
 │  │  └──── classes + attributes + pseudo-classes
 │  └─────── IDs
 └────────── inline styles
```

### What each part counts

| Part | Counts | Example |
| --- | --- | --- |
| `a` | Inline styles | `style="color:red"` |
| `b` | IDs | `#header` |
| `c` | Classes, attributes, pseudo-classes | `.card`, `[type="text"]`, `:hover` |
| `d` | Type selectors, pseudo-elements | `p`, `div`, `::before` |

The universal selector `*` contributes nothing.

### Example

Consider:

```css
p.example {
  color: red;
}
```

There is:

- one type selector: `p`
- one class selector: `.example`

So the specificity is:

`(0, 0, 1, 1)`

Consider:

```css
#main .example p {
  color: red;
}
```

There are:

- one ID selector: `#main`
- one class selector: `.example`
- one type selector: `p`

So the specificity is:

`(0, 1, 1, 1)`

---

## 12. Comparing Specificity

When two selectors compete to set the **same property**, compare their specificity from left to right.

For example:

```css
p {
  color: blue;
}

.example {
  color: red;
}
```

Their specificity values are:

```text
p        → (0, 0, 0, 1)
.example → (0, 0, 1, 0)
```

The class selector wins because the `c` value is compared before the `d` value.

So the text becomes red.

### Another example

```css
.example {
  color: red;
}

#unique {
  color: purple;
}
```

Their specificity values are:

```text
.example → (0, 0, 1, 0)
#unique  → (0, 1, 0, 0)
```

The ID selector wins, so the text becomes purple.

> **Mental model:** Compare specificity from **left to right**. A difference in an earlier part outweighs differences in later parts.

---

## 13. The `!important` Keyword

The `!important` keyword gives a declaration higher priority than normal declarations.

For example:

```html
<p class="para" style="background-color: lightblue; color: black;">
  This is a paragraph.
</p>
```

And:

```css
.para {
  background-color: black;
  color: white;
}
```

The inline styles normally win because inline styles have higher specificity than the class selector.

Therefore, the paragraph keeps:

- `background-color: lightblue`
- `color: black`

To override those inline declarations, the stylesheet can use `!important`:

```html
<link rel="stylesheet" href="styles.css">

<p class="para" style="background-color: lightblue; color: black;">
  This is a paragraph.
</p>
```

```css
.para {
  background-color: black !important;
  color: white !important;
}
```

The `!important` keyword is placed **after the value and before the semicolon**:

```css
color: white !important;
```

The `!important` declarations override the normal inline declarations in this example.

### Does `!important` increase specificity?

No.

`!important` does **not** change the selector's specificity value.

For example:

```css
.para {
  color: white !important;
}
```

The selector `.para` still has:

`(0, 0, 1, 0)`

`!important` affects the priority of the declaration rather than changing the selector's specificity.

### When can `!important` be useful?

One appropriate use is overriding styles from a third-party library or framework when you do not control the original CSS.

However, it should generally be used sparingly.

Overusing `!important` can:

- make CSS harder to maintain,
- make debugging more difficult,
- interfere with the natural cascade,
- create unexpected conflicts later.

> **Practical rule:** Use `!important` when there is a clear reason for it, rather than using it as the first solution to a specificity problem.

---

## 14. Inline vs. Internal vs. External CSS

It is important to separate **where CSS is written** from **how specific its selector is**.

| CSS location | Specificity |
| --- | --- |
| Inline | Inline style contributes `(1, 0, 0, 0)` |
| Internal | Determined by its selector |
| External | Determined by its selector |

For example:

```text
Inline style:
(1, 0, 0, 0)

Internal CSS with #id:
(0, 1, 0, 0)

External CSS with .class:
(0, 0, 1, 0)

External CSS with p:
(0, 0, 0, 1)
```

So saying that **"external CSS has lower specificity than internal CSS"** is misleading.

The selector determines specificity.

---

## 15. Practical Specificity Hierarchy

For the selector types covered in this note, the basic hierarchy is:

| Selector / declaration | Specificity |
| --- | --- |
| Inline style | `(1, 0, 0, 0)` |
| ID selector | `(0, 1, 0, 0)` |
| Class selector | `(0, 0, 1, 0)` |
| Attribute selector | `(0, 0, 1, 0)` |
| Pseudo-class | `(0, 0, 1, 0)` |
| Type selector | `(0, 0, 0, 1)` |
| Pseudo-element | `(0, 0, 0, 1)` |
| Universal selector | `(0, 0, 0, 0)` |

This is a useful mental model for understanding the examples in this note.

---

## Summary

### Specificity values

| Selector type | Example | Specificity |
| --- | --- | --- |
| Inline style | `style="color:red"` | `(1, 0, 0, 0)` |
| ID | `#unique` | `(0, 1, 0, 0)` |
| Class | `.highlight` | `(0, 0, 1, 0)` |
| Attribute | `[type="text"]` | `(0, 0, 1, 0)` |
| Pseudo-class | `:hover` | `(0, 0, 1, 0)` |
| Type | `p` | `(0, 0, 0, 1)` |
| Pseudo-element | `::before` | `(0, 0, 0, 1)` |
| Universal | `*` | `(0, 0, 0, 0)` |

### CSS location

- **Inline CSS** contributes the inline-style part of specificity.
- **Internal CSS** gets its specificity from its selectors.
- **External CSS** gets its specificity from its selectors.
- Internal and external CSS can have equal specificity.
- When competing rules have equal specificity, the one that appears later wins.

---

## Key Takeaways

1. **CSS specificity determines which conflicting declaration wins.**
2. Specificity is represented as `(a, b, c, d)`.
3. Inline styles have the highest normal specificity among the selector/declaration types covered here.
4. ID selectors are more specific than classes.
5. Classes, attributes, and pseudo-classes share the same specificity category.
6. Type selectors and pseudo-elements have lower specificity.
7. The universal selector `*` contributes zero specificity.
8. **Internal vs. external CSS does not determine specificity.** The selectors do.
9. If two competing rules have equal specificity, **source order matters**.
10. `!important` increases declaration priority but **does not change the selector's specificity**.
11. Use `!important` sparingly because excessive use makes CSS harder to maintain and debug.

---

## Mental Model

Think of specificity as a comparison of four counters:

```text
                 Specificity
                     │
                     ▼
              ( a , b , c , d )
                │   │   │   │
                │   │   │   └── Type / pseudo-element
                │   │   └─────── Class / attribute / pseudo-class
                │   └─────────── ID
                └─────────────── Inline style

Compare from left → right.

Earlier differences matter more than later differences.
```

A simple way to reason about a conflict is:

```text
1. Do both rules target the same property?
        │
        ▼
2. Compare their specificity.
        │
        ├── One is higher → higher specificity wins
        │
        └── Equal → later rule wins
```

When `!important` is involved, remember that it changes the declaration's priority rather than changing the selector's specificity.

> **The goal is not to memorize isolated examples.** Learn to identify what each selector contains, calculate its specificity, and compare the values from left to right.
