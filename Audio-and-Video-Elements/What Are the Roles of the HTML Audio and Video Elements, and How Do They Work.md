# HTML5 Multimedia: Audio and Video Elements

The `<audio>` and `<video>` elements allow you to embed rich, native sound and video content directly into your HTML documents without relying on external plugins.

## Supported Media Formats

Different browsers have varying degrees of native support for multimedia formats. To ensure compatibility, it is essential to understand the formats supported by each element:

|Element|Supported Formats<br><br>MD|Common MIME Types (For Code)|
|---|---|---|
|**`<audio>`**|MP3, WAV, OGG<br><br>MD|`audio/mpeg`, `audio/wav`, `audio/ogg`|
|**`<video>`**|MP4, OGG, WEBM<br><br>MD|`video/mp4`, `video/ogg`, `video/webm`|

## Core Multimedia Attributes

Both elements share a collection of powerful boolean and value-based attributes that control how media behaves on the page.

### 1. The Audio Element (`<audio>`)

By default, simply writing `<audio src="file.mp3"></audio>` will render **nothing** visible on the webpage. To make it functional, you must utilize attributes:
#### Basic Implementation with Controls

HTML

```
<audio src="https://cdn.freecodecamp.org/curriculum/js-music-player/cruising-for-a-musing.mp3" controls></audio>
```

#### Looped and Muted Implementation

HTML

```
<audio
  src="https://cdn.freecodecamp.org/curriculum/js-music-player/can't-stay-down.mp3"
  controls
  loop
  muted
></audio>
```

> [!NOTE] **Attribute Key Mechanics:**
> 
> - **`src`**: Specifies the direct URL or path to the media file.
>     
>     
> - **`controls`**: A boolean attribute that enables the browser's built-in playback interface (play, pause, volume, etc.). If omitted, the player is hidden.
>     
>     
> - **`loop`**: A boolean attribute that forces the audio to replay continuously from the beginning once it ends.
>     
>     
> - **`muted`**: A boolean attribute that forces the audio to start in a muted state.
>     
>     
> - _Browser Quirk:_ Some browsers, like Safari, may omit the volume slider by default even when `controls` is active.
>     
>     MD
>     

### 2. The Video Element (`<video>`)

The `<video>` element supports all the same attributes as the `<audio>` element (`src`, `controls`, `loop`, `muted`), but adds options specifically designed for visual layouts.

#### Advanced Video Implementation

HTML

```
<video
  src="https://archive.org/download/BigBuckBunny_124/Content/big_buck_bunny_720p_surround.mp4"
  width="400"
  controls
  loop
  muted
  autoplay
  poster="https://peach.blender.org/wp-content/uploads/title_anouncement.jpg?x11217"
></video>
```

> [!TIP] **Video-Exclusive Features:**
> 
> - **`width` / `height`**: Sets the display dimensions of the video player directly in HTML.
>     
>     
> - **`autoplay`**: Commands the browser to automatically start playing the video as soon as the page loads.
>     
>     
> - **`poster`**: Unique to the `<video>` element. It specifies an image URL to display as a placeholder while the video is downloading or until the user clicks play.
>     
>     

## Cross-Browser Compatibility: The `<source>` Strategy

Because different browsers prefer different media containers, hardcoding a single `src` attribute can cause your media to fail for certain users.

To build a bulletproof multimedia element, omit the `src` attribute from the primary tag and nest multiple `<source>` elements inside it instead. The browser will read the list from top to bottom and automatically play the **first format it natively understands**.

### Robust Multi-Format Blueprint

HTML

```
<video
  controls
  width="400"
  poster="https://peach.blender.org/wp-content/uploads/title_anouncement.jpg?x11217"
>
  <!-- Best efficiency/quality option first -->
  <source src="video.webm" type="video/webm" />
  <!-- Highly compatible fallback option second -->
  <source src="video.mp4" type="video/mp4" />[cite: 2]
  
  <!-- Fallback Text: Only displays if the browser doesn't support HTML5 video at all -->
  Your browser does not support the HTML5 video tag.[cite: 2]
</video>
```

## Technical Enhancements & Best Practices (Not in Original File)

To make your code production-ready, keep these industry-standard caveats in mind:

### The Modern Autoplay Policy

Modern web browsers (Chrome, Edge, Safari) strictly enforce **Autoplay Policies** to protect user experience.

- **The Rule:** A video or audio file **will not autoplay** if it has sound.
    
- **The Solution:** If you include the `autoplay` attribute, you _must_ pair it with the `muted` attribute. If you don't mute it, the browser will block the autoplay entirely, forcing the user to interact with the page first.
    

### Performance Tip

Always include the `type` attribute on your `<source>` tags (e.g., `type="video/mp4"`)[cite: 2]. This allows the browser to immediately skip a file if it doesn't support the format, preventing it from wasting bandwidth trying to pre-load a broken media stream.

**Tags:** #Programming #Web_Dasar #HTML #Audio #Video #Multimedia #WebDev