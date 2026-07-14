# Advanced Text Semantics: Mathematical, Code, Annotation, and Ruby Elements

This document outlines the usage of specialized inline HTML elements for formatting mathematical baselines, displaying computer code, highlighting annotations, and rendering phonetic typography.

## 1. Mathematical Baselines: Superscript and Subscript

HTML provides native inline elements to alter the typographical baseline of text relative to standard prose, which is essential for mathematical and scientific notation.

### A. The Superscript Element (`<sup>`)

- **Definition:** Renders a character or symbol smaller and slightly raised above the baseline.
    
- **Primary Use Cases:** Exponents (e.g., $2^2$), superior lettering (such as abbreviations like $M^{gr}$), and ordinal numbers.
    
- **Stylistic Limitation:** Use `<sup>` only when there is a typographical or semantic reason. For purely decorative raised baselines, use CSS instead.

### B. The Subscript Element (`<sub>`)

- **Definition:** Renders a character or symbol smaller and slightly lowered below the baseline.
    
- **Primary Use Cases:** Chemical formulas (e.g., $\text{CO}_2$), mathematical variable subscripts, and footnotes.

```html
<!-- Exponents and Chemical Formulas -->
<p>2<sup>2</sup> is 4.</p>
<p>Carbon dioxide is written as CO<sub>2</sub>.</p>
```

## 2. Displaying Code: Inline vs. Preformatted Blocks

When writing technical articles or documentation, distinguishing computer-readable text from standard narrative prose is essential for readability.

### A. Inline Code (`<code>`)

- **Purpose:** Represents short, single-line technical terms, CSS properties, or code snippets nested directly within a sentence.
    
- **Default Styling:** Browsers render the content of `<code>` in a monospaced font by default.

### B. Preformatted Text Blocks (`<pre>`)

- **Purpose:** Instructs the browser to display text exactly as written in the source HTML, preserving all spaces, line breaks, and indentations.
    
- **Multi-Line Code Snippets:** To output multi-line code blocks, nest a `<code>` block directly inside a `<pre>` block.

```html
<!-- Multi-Line Code Block Structure -->
<pre>
  <code>
    body {
      color: red;
    }
  </code>
</pre>
```

> [!IMPORTANT] **Indentation Sensitivity** Because the `<pre>` tag is highly sensitive to spacing, any indentation or tabs inside the HTML file will render directly on the user's screen.

## 3. Specialized Typographical Annotations: `<u>`, `<s>`, and `<ruby>`

Modern HTML defines precise semantic purposes for stylistic markings like underlines, strikethroughs, and pronunciation aids.

### A. Unarticulated Annotation (`<u>`)

- **Semantic Meaning:** Represents inline text that has a non-textual annotation, such as highlighting misspelled words.
    
- **Default Styling:** Displays a black underline beneath the target text.
    
- **Strict Rule:** Never use `<u>` for purely decorative underlining (use CSS instead).

### B. Strikethrough (`<s>`)

- **Semantic Meaning:** Represents text that is no longer accurate, valid, or relevant (e.g., a canceled event or outdated pricing).
    
- **Stylistic Limitation:** Do not use `<s>` to show active document edits or revisions. Instead, use the specialized deleted text (`<del>`) and inserted text (`<ins>`) elements.

```html
<!-- Spell Check and Cancellation Examples -->
<p>The system flagged <u>inccccort</u> spelling.</p>
<p><s>The group hike starts at noon.</s> The hike is canceled.</p>
```

### C. Ruby Annotations (`<ruby>`)

- **Purpose:** Used to render small pronunciation guides or translation glosses directly above or below East Asian typographic characters.
    
- **Sub-Components:**
    
    - `<rt>` (Ruby Text): Contains the phonetic guide or translation text itself.
        
    - `<rp>` (Ruby Parentheses): Provides fallback parentheses around the ruby text for older legacy browsers that do not support ruby layout engines.

```html
<!-- Pronunciation Annotation Example -->
<ruby> 明日 <rp>(</rp><rt>Ashita</rt><rp>)</rp> </ruby>
```

**Tags:** #Programming #Web_Dasar #HTML #SemanticHTML #Typography #Superscript #Subscript #CodeBlocks #RubyMarkup #WebDev