Uplink: [[Programming]], [[Web Dasar (HTML, CSS, JS)]]
## Metadata & Search Engine Visibility

### 1. The Meta Description Tag

The `meta` description provides a brief summary of a web page's content. While it is **not visible** on the webpage itself, it appears directly beneath the page title in Search Engine Results Pages (SERPs) as a snippet.

#### Code Implementation

HTML

```
<meta 
  name="description" 
  content="Discover expert tips and techniques for gardening in small spaces, choosing the right plants, and maintaining a thriving garden." 
/>
```

#### Key Mechanics

- **`name="description"`**: Signals to browsers, search engines, and web scrapers how to interpret the metadata.
    
- **`content="..."`**: Holds the actual text description of the page.
    

#### SEO Impact

- **Direct Ranking**: Does **not** directly affect a site's search engine ranking algorithm.
    
- **Indirect Traffic**: A compelling, well-crafted description significantly improves **Click-Through Rates (CTR)**. High CTR signals to search engines that your page is relevant, which can positively influence rankings over time.
    

> [!TIP]
> 
> **Length Matters!**
> 
> Search engines truncate descriptions based on screen layout. Aim for **150–160 characters** to ensure your entire message is visible on both desktop and mobile SERPs without being cut off.

## Social Media Optimization (SMO)

### 2. Open Graph (OG) Protocol

The Open Graph protocol allows you to control exactly how your website's content looks when shared across social media platforms like Facebook, LinkedIn, Twitter/X, and Discord.

Properly configured OG tags transform plain text links into rich, engaging preview cards that entice users to click.

#### The Core Four Essential OG Tags

To create a fully functional preview card, you must include these four core properties in your HTML `<head>`:

| **Property** | **Example Value**                                 | **Purpose**                                                                              |
| ------------ | ------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| `og:title`   | `"freeCodeCamp.org"`                              | The title of your article or page as it should appear in the preview card.               |
| `og:type`    | `"website"`                                       | Defines the type of media (e.g., `website`, `article`, `video.movie`, `music.song`).     |
| `og:image`   | `"https://cdn.freecodecamp.org/.../fcc_meta.png"` | The URL of the preview image displayed on the social card.                               |
| `og:url`     | `"https://www.freecodecamp.org"`                  | The canonical URL for the page, ensuring all social shares consolidate to a single link. |

#### Code Implementation

HTML

```
<meta property="og:title" content="freeCodeCamp.org" />
<meta property="og:type" content="website" />
<meta property="og:url" content="https://www.freecodecamp.org" />
<meta property="og:image" content="https://cdn.freecodecamp.org/platform/universal/fcc_meta_1920X1080-indigo.png" />

<meta property="og:description" content="Learn to code for free together with millions of other people around the world." />
<meta property="og:locale" content="en_US" />
```

> [!NOTE]
> 
> **Image Dimension Best Practices**
> 
> - **Optimal Size:** At least **1200 x 630 pixels** for high-resolution displays (maintains a 1.91:1 aspect ratio).
>     
> - **Minimum Size:** **600 x 315 pixels**. Images smaller than this will render as tiny square thumbnails rather than large, rich cards.
>     

#### SEO & Traffic Impact

- **Engagement Signals:** Beautiful social cards increase user interaction and shares.
    
- **Authority Building:** High click-through rates from social platforms drive massive referral traffic, signaling content relevance and authority back to search engines.

### Additional Essential SEO Tags

#### A. The Title Tag (`<title>`)

The single most important on-page SEO element. It tells search engines exactly what the page is about and serves as the clickable headline in search results.

HTML

```
<title>Gardening Tips for Small Spaces | Thriving Garden</title>
```

- _Best Practice:_ Keep it under **60 characters** and put your primary keyword near the beginning.
    

#### B. The Canonical Tag (`rel="canonical"`)

Prevents duplicate content issues by telling search engines which URL is the "master" or preferred version of a page.

HTML

```
<link rel="canonical" href="https://example.com/gardening-tips" />
```

## Summary Cheat Sheet

- **Search Engine Snippets:** Handled via `<meta name="description">`. Focus on clear, concise summaries (150-160 chars) to boost organic SERP CTR.
    
- **Social Media Cards:** Handled via `<meta property="og:*">`. Focus on high-quality images (1200x630) and accurate titles to drive social media referral traffic.
    

**Tags:** #Programming #Web_Dasar #HTML #CSS #JS #SEO #WebDev