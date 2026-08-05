# ♿ Complete Guide to WAI-ARIA & Accessibility Attributes

## 1. Introduction to WAI-ARIA

### What is WAI-ARIA?
**WAI-ARIA** stands for **Web Accessibility Initiative – Accessible Rich Internet Applications**. It is a technical specification that provides additional semantic information to enhance web accessibility for dynamic content and complex interactive UI components.

* **WCAG vs. WAI-ARIA**: WCAG provides general guidelines for web accessibility, while WAI-ARIA offers specific rules for making dynamic and interactive content accessible.
* **Primary Purpose**: To improve accessibility for dynamic content and UI components that do not have native HTML equivalents.

> [!IMPORTANT] **The First Rule of ARIA**
> Always prioritize native HTML elements (such as `<button>`, `<nav>`, or `<dialog>`) over custom ARIA elements. Native elements include built-in keyboard navigation, state management, and accessibility out of the box. Use WAI-ARIA only when standard HTML falls short.

---

## 2. ARIA Roles (`role="..."`)

An **ARIA role** defines the semantic meaning and purpose of an HTML element to assistive technologies like screen readers.

> [!WARNING]
> Setting a role **only provides semantic information**. It does **NOT** add functionality, keyboard support, or behavioral interactivity. Developers must implement expected behaviors manually using CSS and JavaScript.

### Custom Component Example
Assigning `role="button"` to a `<div>` lets screen readers announce it as a button, but keyboard interaction and click handlers must be manually attached:

```html
<div id="custom-btn" role="button" tabindex="0">Click Me</div>
```

```css
#custom-btn {
  display: inline-block;
  padding: 0.4em 1em;
  font-size: 1rem;
  font-family: sans-serif;
  color: buttontext;
  background-color: buttonface;
  border: 1px solid #ccc;
  border-radius: 4px;
  cursor: pointer;
  user-select: none;
  text-align: center;
}

#custom-btn:focus {
  outline: 2px solid Highlight;
  outline-offset: 2px;
} 

#custom-btn:active {
  background-color: #ddd;
}
```

```javascript
const button = document.getElementById("custom-btn");

// Handle click interaction
button.addEventListener("click", () => {
  alert("Button clicked!");
});

// Handle keyboard interaction (Enter / Space keys)
button.addEventListener("keydown", (e) => {
  if (e.key === "Enter" || e.key === " ") {
    e.preventDefault();
    button.click();
  }
});
```

### The 6 Categories of ARIA Roles

| Category | Purpose | Examples | Native HTML Alternative |
| :--- | :--- | :--- | :--- |
| **Document Structure** | Organizes relationships between content sections. | `toolbar`, `tooltip`, `feed`, `math`, `note` | `<article>`, `<figure>`, `<section>` |
| **Widget** | Defines interactive UI widgets. | `scrollbar`, `searchbox`, `slider`, `switch`, `tab` | `<input type="range">`, `<button>` |
| **Landmark** | Categorizes major regions for quick screen reader navigation. | `banner`, `complementary`, `main`, `navigation`, `search` | `<header>`, `<aside>`, `<main>`, `<nav>`, `<search>` |
| **Live Region** | Triggers automated announcements when content changes dynamically. | `alert`, `log`, `marquee`, `status`, `timer` | N/A (Requires ARIA attributes) |
| **Window** | Defines sub-windows and overlays. | `dialog`, `alertdialog` | `<dialog>` |
| **Abstract** | Internal structure used by browsers to build accessibility trees. | *(Internal use only—do not use in code)* | N/A |

---

## 3. Accessible Labeling: `aria-label` vs. `aria-labelledby`

Both attributes provide accessible text labels for elements, but they source their labels differently.

### Feature Comparison

| Feature | `aria-label` | `aria-labelledby` |
| :--- | :--- | :--- |
| **Source** | String defined directly inside the attribute. | References the `id` of existing text element(s) on the page. |
| **Primary Use Case** | Icon-only buttons or controls without visible text. | Inputs, controls, or sections that have visible text on screen. |
| **Translation** | May not be recognized or translated by browser translation tools. | Translates reliably because it references visible DOM text. |
| **Multiple References** | Single text string only. | Can combine multiple `id` values into a single label. |

### Code Examples

#### `aria-label` (Direct Labeling)
Used when no text is visible on screen:

```html
<button aria-label="Search">
  <i class="fa-solid fa-magnifying-glass"></i>
</button>
```

#### `aria-labelledby` (Referenced Labeling)
Links an input field directly to an existing button or heading:

```html
<input type="text" aria-labelledby="search-btn">
<button type="button" id="search-btn">Search</button>
```

Combining multiple element IDs to form one description:

```html
<div>
  <span id="volume-label">Volume</span>
  <span id="volume-details">Adjust the volume level</span>
  <input type="range" min="0" max="100" value="30" aria-labelledby="volume-label volume-details">
</div>
```

> [!NOTE] Precedence Rule
> Do **not** use `aria-label` and `aria-labelledby` on the same element. If both are present, screen readers use `aria-labelledby` and ignore `aria-label` completely.

---

## 4. Hiding Content: `aria-hidden`

The `aria-hidden="true"` attribute removes an element and its children from the **accessibility tree**, making it invisible to screen readers while keeping it visually visible on the page.

### Usage Guidelines

* **When to use**:
  * Purely decorative icons or imagery adjacent to visible text.
  * Duplicated content that would create redundancy for screen readers.
* **When NOT to use**:
  * Keyboard-focusable elements (buttons, inputs, links). Hiding focusable items causes screen readers to focus on invisible elements without announcing them.
  * Content intended to be hidden visually from all users (use CSS `display: none` or the HTML `hidden` attribute instead).

```html
<!-- Correct: Hides decorative gear icon since "Settings" text is already present -->
<button>
  <i class="fa-solid fa-gear" aria-hidden="true"></i>
  <span class="label">Settings</span>
</button>
```

---

## 5. Adding Supplemental Context: `aria-describedby`

The `aria-describedby` attribute connects an element to an **accessible description** (such as instructions, validation rules, or warnings) by referencing another element's `id`.

### Common Applications
* Linking form inputs with error messages or helper text.
* Associating confirmation or warning messages with critical buttons.

```html
<!-- Form Input Description Example -->
<form>
  <label for="password">Password:</label>
  <input type="password" id="password" aria-describedby="password-help" />
  <p id="password-help">Your password must be at least 8 characters long.</p>
</form>

<!-- Warning Message Example -->
<button aria-describedby="delete-message">Delete Account</button>
<p id="delete-message">Warning! All deletions are permanent.</p>
```

---

## 📑 Summary Checklist for Developers

* **Prefer Native HTML**: Always use `<button>`, `<input>`, or `<dialog>` before reaching for ARIA.
* **Explicit Roles**: Adding `role=""` does not provide keyboard interaction; manually build accessibility logic in JS.
* **Visible References**: Prefer `aria-labelledby` over `aria-label` when visible text is present.
* **Decorative Icons**: Apply `aria-hidden="true"` to visual icons alongside readable text.
* **Form Guidance**: Link input instructions and validation messages using `aria-describedby`.