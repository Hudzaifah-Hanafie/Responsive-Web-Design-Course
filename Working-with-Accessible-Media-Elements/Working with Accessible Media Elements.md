# 🌐 Web Accessibility (a11y) Essentials: Images, Links, Media & Keyboards

---

## 1. Image Accessibility & Effective `alt` Text

Alternative text (`alt` text) provides a textual description of an image for screen reader users, search engines, and situations where image files fail to load.

### Bad vs. Good `alt` Text Examples

| Context | Poor `alt` Text | Accessible `alt` Text | Why It's Better |
| :--- | :--- | :--- | :--- |
| **Puppy Image** | `"A cute puppy."` | `"A black and white puppy with an orange collar lies on its belly in the sand, looking off to the side. A bright orange ball rests near its front paws."` | Specific and describes visual key details without fluff. |
| **Resort Image** | `"Resort."` | `"Tropical resort featuring a swimming pool surrounded by palm trees and bungalows."` | Provides enough scene structure to give clear context. |
| **Icon Link (Navigation)** | `"Right arrow."` | `"Go to next page."` | Describes the **action/destination**, not just the visual object. |

### Code Implementations

#### Informational Image
```html
<img 
  src="resort.png" 
  alt="Tropical resort featuring a swimming pool surrounded by palm trees and bungalows." 
/>
```

#### Decorative Image
> [!IMPORTANT] **Decorative Images**
> Images that serve no informational purpose must use an empty `alt=""` attribute (null alt text). This causes screen readers to skip them cleanly. **Never omit the `alt` attribute entirely**, or screen readers may read out the raw filename instead.

```html
<!-- Skips decorative graphic cleanly in screen readers -->
<img src="decorative_divider.png" alt="" />
```

#### Image as a Link
```html
<a href="about.html">
  <img src="arrow-right.png" alt="Go to next page." />
</a>
```

### Best Practices for `alt` Text
* **Be Concise**: Include key details, but avoid overly lengthy descriptions.
* **Avoid Redundancy**: Do **not** prefix text with *"Image of"* or *"Picture of"*. Screen readers already announce image elements.
* **Context Matters**: Tailor the description to the page topic (e.g., focus on dog breed physical characteristics on a veterinary site).
* **Punctuation**: End `alt` text with a period so screen readers pause naturally after reading it.

---

## 2. Accessible Link Text (`<a>`)

Descriptive link text allows screen reader users and visual skimmers to understand where a link leads without reading the surrounding paragraphs.

### Vague vs. Accessible Link Text

| Vague Link Text | Accessible Link Text | Benefit |
| :--- | :--- | :--- |
| `<a href="...">Details</a>` | `<a href="...">Get details about our upcoming webinar</a>` | Specifies the exact topic of the details. |
| `<a href="...">Read more</a>` | `<a href="...">Read our latest blog post on web accessibility</a>` | Eliminates ambiguity when navigating a list of articles. |
| `<a href="...">Click here</a>` | `<a href="...">Learn more about our accessibility efforts</a>` | Focuses on destination rather than input mechanism. |

### Core Rules for Accessible Links
* **Focus on Destination**: Describe *where* the link goes, not the user action (e.g., use *"User behavior results"* instead of *"Click here to view results"*).
* **Keep It Concise**: Target **2–5 words** per link text.
* **Ensure Unique Names**: Do not repeat the same link text on a single page if the links point to different URLs.
* **Visual Distinction**: Ensure links stand out visually using underlines and contrast cues, not relying solely on color.

---

## 3. Accessible Audio & Video Content

Providing accessible media ensures users with visual or hearing impairments—or those in noise-sensitive environments—can consume media content effectively.

### Media Accessibility Formats

| Feature | Primary Audience | Description |
| :--- | :--- | :--- |
| **Captions** | Deaf or hard of hearing users, quiet/noisy environments | Synchronized text of spoken audio **plus** sound effects/non-verbal cues (e.g., `[laughter]`). |
| **Subtitles** | Non-native language speakers | Synchronized translation of spoken dialogue only. |
| **Transcripts** | Deaf users, fast readers, search engines | Plain text document of all spoken content below or alongside the media player. |

### HTML5 `<track>` Element for Media

```html
<video width="400" height="300" controls src="lesson.mp4">
  <track 
    src="captions.vtt" 
    kind="captions" 
    srclang="en" 
    label="English Captions" 
  />
</video>

<audio controls src="podcast.mp3">
  <track 
    src="captions.vtt" 
    kind="captions" 
    srclang="en" 
    label="English Captions" 
  />
</audio>
```

### Displaying Transcripts Below Audio
```html
<audio controls>
  <source src="audio.mp3" type="audio/mpeg" />
  Your browser does not support the audio element.
</audio>

<div class="transcript">
  <h3>Transcript</h3>
  <p><strong>[Speaker 1]:</strong> Welcome to the accessibility tutorial.</p>
  <p><strong>[Speaker 2]:</strong> Today we will cover captions and transcripts.</p>
</div>
```

---

## 4. Keyboard Accessibility & Focus Management

Keyboard navigation is critical for power users, screen reader users, and individuals with motor disabilities who cannot use a mouse.

### The `tabindex` Attribute

| Value | Behavior | Use Case |
| :--- | :--- | :--- |
| `tabindex="0"` | Includes element in natural sequential keyboard navigation (`Tab` key). | Custom interactive controls (e.g., custom buttons, tabs). |
| `tabindex="-1"` | Removes element from natural tab sequence, but makes it **programmatically focusable** via JS. | Modals, notification banners, error messages. |
| `tabindex="1+"` *(Positive)* | Sets explicit focus priority order. | **Avoid using**. Disrupts natural reading order and makes maintenance difficult. |

```html
<!-- Example ofTabIndex Usage -->
<button>First (Natural Focus)</button>
<div tabindex="0">Second (Added to Tab Flow)</div>
<p tabindex="-1" id="error-msg">Programmatically focused error message</p>
```

### Visual Focus Indicators

Never remove the outline from focusable elements (`outline: none`) without replacing it with an accessible focus indicator.

> [!NOTE] **Focus Contrast Requirement**
> Custom focus indicators must maintain a minimum **3:1 color contrast ratio** against the background color behind them.

```css
/* Visible, accessible focus style */
button:focus {
  outline: 2px solid #005fcc;
  outline-offset: 2px;
}
```

### Keyboard Anti-Patterns to Avoid
* **Avoid `accesskey`**: Assigning custom shortcut keys (e.g., `accesskey="s"`) frequently conflicts with screen readers and browser-level keyboard shortcuts.
* **Prevent Focus Traps**: Ensure users can always navigate **into and out of** modal dialogs or sub-menus using standard keyboard shortcuts (`Tab`, `Shift + Tab`, `Escape`).