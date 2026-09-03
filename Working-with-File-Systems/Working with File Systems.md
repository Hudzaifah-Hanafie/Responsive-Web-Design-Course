# 📁 Operating System File Management, Project Architecture, & Web File Formats

---

## 1. Operating System File Managers: Windows File Explorer vs. macOS Finder

File management applications provide built-in tools to store, organize, edit, and locate digital assets.

### Core Feature Comparison

| Feature / Action | Windows File Explorer | macOS Finder |
| :--- | :--- | :--- |
| **Default Launch Path** | Open via the Start menu or press the **Windows Key**. | Click the Finder icon located in the System Dock. |
| **Folder Organization** | Pin folders via right-click → **Pin**. | Access favorite folders in the left sidebar. |
| **Categorization Tools** | Folder hierarchies and local paths. | Custom colored **Tags** and criteria-based **Smart Folders**. |
| **Searching Saved Tags** | N/A | Click colored tags in the sidebar or search by tag color name. |

> [!NOTE] **Smart Folders**
> Smart Folders in macOS Finder automatically collect and group files according to criteria defined by the user, such as file type, creation date, or search keywords.

---

## 2. Web Application File Naming & Directory Architecture

Organizing and naming files cleanly ensures projects remain readable, predictable, and easy for teams to maintain.

### File Naming Best Practices
* **Use Descriptive Names**: Standardize on meaningful names like `about-us.html` rather than ambiguous identifiers like `index1234.html`.
* **Avoid Spaces and Special Characters**: Separate words with hyphens (`-`) instead of spaces. Avoid complex characters (e.g., `file-1!@.html`) and stick strictly to standard letters and dashes.
* **The Root Entry Point**: Always name the main homepage `index.html`, as web servers load this file by default.
* **Adhere to Team Guidelines**: Consult language documentation and internal team style guides to ensure team-wide consistency.

### Standard Web Project Directory Layout

```bash
.                       # Root directory (top-level starting point)
├── /assets             # Project static assets directory
│   ├── /images         # Raster and vector image files
│   │   ├── logo.png
│   │   ├── banner.jpg
│   │   └── icons.svg
│   ├── /fonts          # Custom web typography files
│   │   ├── custom-font.woff
│   │   └── custom-font.woff2
├── /css                # Stylesheet directory
│   ├── main.css
│   ├── about.css
│   └── contact.css
├── index.html          # Main application homepage
├── about.html          # About page
├── contact.html        # Contact page
└── README.md           # Project documentation in Markdown format
```

---

## 3. File & Folder Operations across Platforms

Basic file operations differ between Windows and macOS due to native system workflows.

### Execution Methods

| Operation | Windows File Explorer Method | macOS Finder Method |
| :--- | :--- | :--- |
| **Create File** | Select **New** → choose file type directly in Explorer. | Create and save files within dedicated applications (e.g., TextEdit via `Cmd + S`). |
| **Create Folder** | Select **New** → **Folder** or right-click empty space → **New** → **Folder**. | Right-click empty space → select **New Folder**. |
| **Move Item** | Drag and drop, or select **Cut** and then **Paste** in the destination folder. | Drag to sidebar/tabs, or copy item (`Cmd + C`) and move via `Cmd + Option + V`. |
| **Delete Item** | Select item and click the **Trash icon** or right-click → **Delete**. | Right-click → **Move to trash**, or drag item to the Dock Trash icon. |

### Key File Management Shortcuts

| Action | Operating System | Keyboard Shortcut |
| :--- | :--- | :--- |
| **Rename File / Folder** | Windows | `F2` |
| **Save File** | macOS | `Command` + `S` |
| **Move File / Folder (Cut/Move)** | macOS | `Command` + `C`, then `Command` + `Option` + `V` |

---

## 4. Searching Files & Folders

Both operating systems provide scoped search utilities to quickly locate project assets.

### Windows Search Options
* **Taskbar Search**: Searches keywords across the local PC and connected OneDrive accounts. Results can be filtered using the **Documents**, **Apps**, or **Web** tabs.
* **File Explorer Search Bar**:
  * **Home**: Searches local PC files and cloud drives quickly.
  * **Current Folder**: Restricts search results strictly to the active folder.
  * **This PC**: Executes a thorough, in-depth system scan.

### macOS Search Options
* **Spotlight**: Opened using `Command + Spacebar` or the magnifying glass icon in the menu bar. Displays categorized results (Folders, Presentations, Photos, Documents) with expanded view options.
* **Finder Recents**: Selecting **Recents** in the Finder sidebar shows a list of all recently viewed files.

---

## 5. Web Application File Types & Extensions

File extensions identify file types and inform operating systems and software how to process content.

### Web Core & Markup Formats
* **`.html`**: Defines structural markup and webpage content.
* **`.css`**: Handles formatting, layout design, and presentation styles.
* **`.js`**: Implements dynamic behavior, interactions, and complex web logic.
* **`.md` / `.markdown`**: Stores documentation files (such as project `README` files) formatted in lightweight Markdown markup.

### Media Formats (Image, Audio, & Video)

| Extension / Format | Type | Compression | Best Use Cases & Features |
| :--- | :--- | :--- | :--- |
| **JPEG** | Image | Lossy | Photographs; trades minor visual quality for smaller file sizes. |
| **PNG** | Image | Lossless | High quality, sharp edges, logos, and icons; supports transparency. |
| **GIF** | Image | Lossy / Palette Limited | Animated graphics; supports transparency with a limited color palette. |
| **SVG** | Image | Vector | Resolution-independent graphic scaling without quality loss. |
| **MP3** | Audio | Lossy | Standard compressed audio delivery. |
| **WAV** | Audio | Lossless | Uncompressed, full original quality audio files. |
| **MP4** | Video | Compressed | Broad video playback; supports multiple codecs, audio tracks, metadata, and subtitles. |
| **MOV** | Video | Native Apple | QuickTime multimedia video format developed by Apple. |
| **WebM** | Video | Open-Source | High-quality, open-source web video format. |

### Typography & Archive Formats
* **TTF (TrueType Font)**: Standard, cross-platform typography format.
* **WOFF (Web Open Font Format)**: Web-optimized font format featuring compressed sizes and licensing metadata support.
* **WOFF2**: Advanced successor to WOFF offering higher compression efficiency and performance.
* **ZIP**: Standard archive format using lossless compression to bundle multiple files and folders together.