# Why Are Default Link Styles Important for Usability on the Web?

Default link styles are an important part of **web usability and accessibility**.

Most browsers traditionally display:

- **Unvisited links** in blue and underlined.
- **Visited links** in purple and underlined.

These styles have become familiar conventions that users recognize when navigating websites. The important idea is not that every website must use exactly blue and purple, but that links should provide **clear and consistent visual cues**.

---

## 1. The Purpose of Link Styles

The main purpose of link styling is to help users quickly distinguish between:

- **Interactive elements** — things they can click.
- **Non-interactive elements** — ordinary text or other content.

This distinction makes a webpage easier to scan and helps users understand how they can interact with the page.

> **Core idea:** Link styles should make it immediately clear that text is clickable.

A clear visual distinction contributes to a more **intuitive, usable, and accessible browsing experience**.

---

## 2. The Basic Default Link Styles

A simple HTML document might contain a link like this:

```html
<link rel="stylesheet" href="styles.css">

<a href="/">Example link</a>
```

The corresponding CSS can define the typical unvisited and visited states:

```css
a:link {
  color: blue;
  text-decoration: underline;
}

a:visited {
  color: purple;
}
```

### What These Selectors Mean

| Selector | Purpose |
|---|---|
| `a:link` | Styles an unvisited link |
| `a:visited` | Styles a link the user has already visited |

The browser can then use different visual styles to communicate the link's state.

---

## 3. Why Blue Links Are Easy to Recognize

The traditional blue color for unvisited links provides a strong visual cue.

It helps links stand out from ordinary text, making them easier to find when users scan a webpage for:

- Navigation options
- Additional information
- Related content
- Other clickable elements

This is especially useful on pages containing a lot of text.

### Why the Underline Matters

The underline provides a second visual cue that the text is clickable.

This is important because **color alone should not be the only way to communicate that something is a link**.

For example, a user who has difficulty distinguishing certain colors may still be able to recognize an underlined link.

> **Important:** Using multiple visual cues makes links easier for a wider range of users to identify.

---

## 4. Why Visited Links Change Color

Visited links are commonly displayed in purple.

The change in color tells the user:

> **"You have already visited this page."**

This provides useful feedback about the user's browsing history.

For example, imagine researching a topic across a website containing dozens of pages. A different color for visited links helps you recognize which pages you have already opened.

This can help prevent accidentally revisiting the same pages and makes it easier to continue exploring unfamiliar content.

### Example

```html
<p>
  Learn more about
  <a href="https://www.example.com/cats">cats</a>
  and
  <a href="https://www.example.com/dogs">dogs</a>.
</p>
```

Without custom CSS, most browsers will typically display these links with a blue color and an underline.

After visiting one of the links, the browser can display that link in a different color, such as purple.

This gives the user immediate visual feedback about their browsing history.

---

## 5. Customizing Default Link Styles

Web designers often change the default appearance of links to match a website's visual design.

This is perfectly possible, but customization should **not remove the usability principles behind the default styles**.

When changing link styles, make sure that:

1. Links are clearly distinguishable from ordinary text.
2. Visited and unvisited links have a visible difference when that distinction is useful.
3. The chosen colors have sufficient contrast with the background.
4. Users can still recognize links quickly while scanning the page.

> **The appearance can change; the usability principles should remain.**

---

## 6. Example: Replacing the Underline

For example, a designer could remove the traditional underline and use a bottom border instead:

```html
<link rel="stylesheet" href="styles.css">

<a href="/">Example link</a>
```

```css
a:link {
  color: blue;
  text-decoration: none;
  border-bottom: 1px solid blue;
}

a:visited {
  color: purple;
  border-bottom: 1px solid purple;
}
```

Here, the underline has been replaced with a `border-bottom`.

The result keeps the familiar **blue/purple distinction** while using a different visual treatment for the link.

This demonstrates an important principle:

**You can customize the appearance of links without removing the visual cues that make them understandable.**

---

## 7. Link Interaction States

Links have more states than simply "visited" and "unvisited."

Two additional states are commonly used:

- `:hover` — when the user points at the link.
- `:active` — while the link is being activated.

For example:

```html
<link rel="stylesheet" href="styles.css">

<a href="/">Example link</a>
```

```css
a:hover {
  color: red;
}

a:active {
  color: darkorange;
}
```

### What These States Do

| State | Selector | Meaning |
|---|---|---|
| Unvisited | `:link` | The user has not visited the link yet |
| Visited | `:visited` | The user has already visited the link |
| Hover | `:hover` | The pointer is currently over the link |
| Active | `:active` | The link is currently being activated |

These different states provide **immediate feedback** as users interact with links.

---

## 8. A Simple Mental Model

Think of link styling as a small visual communication system:

```text
                    LINK
                      │
          ┌───────────┴───────────┐
          │                       │
     Unvisited                 Visited
          │                       │
       Blue +                  Purple +
      underline                underline
          │                       │
          └───────────┬───────────┘
                      │
               User interacts
                      │
             ┌────────┴────────┐
             │                 │
           Hover             Active
             │                 │
        Visual feedback   Visual feedback
```

The goal is not simply to make links look attractive.

The goal is to communicate **what is clickable and what has already been visited**.

---

## 9. Practical Design Principles

When designing link styles, keep these principles in mind:

### Make Links Easy to Identify

Users should not have to guess whether a piece of text is clickable.

### Do Not Rely Only on Color

Use additional visual cues, such as an underline or another clear distinction, so that links remain identifiable even when color differences are difficult to perceive.

### Preserve Visited-State Feedback

When appropriate, give users a visible difference between visited and unvisited links so they can keep track of where they have already been.

### Maintain Sufficient Contrast

Link colors should remain sufficiently distinct from the background so that the text is easy to see.

### Customize Carefully

A website does not necessarily need to use the browser's traditional blue-and-purple appearance. However, customization should preserve the underlying usability principles.

---

## Summary

| Concept | Why It Matters |
|---|---|
| **Blue unvisited links** | Makes links easy to identify |
| **Underlined links** | Provides a visual cue that text is clickable |
| **Purple visited links** | Shows which pages the user has already visited |
| **Hover state** | Provides feedback when the pointer is over a link |
| **Active state** | Provides feedback while a link is being activated |
| **Sufficient contrast** | Keeps links readable and distinguishable |
| **Consistent visual cues** | Makes navigation more intuitive |

---

## Key Takeaways

- **Default link styles exist for usability, not just appearance.**
- Blue unvisited links and purple visited links are familiar conventions that help users navigate.
- Underlines provide an additional cue that text is clickable.
- Visited-link styling helps users remember where they have already been.
- Link styles can be customized, but the underlying usability principles should remain.
- Links should remain visually distinguishable from ordinary text.
- **Color should not be the only cue** used to identify links.
- Hover and active states provide additional interaction feedback.
- The overall goal is **clarity and a usable, accessible browsing experience**.
