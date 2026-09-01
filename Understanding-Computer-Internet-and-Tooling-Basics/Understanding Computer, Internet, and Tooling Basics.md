# 💻 Computer Fundamentals: Hardware, Ergonomics, Security, & Developer Tools

---

## 1. Core Hardware Components
Computers execute tasks ranging from document writing to running complex applications. Understanding the core hardware architecture is essential for developers.

### Key Components Overview

| Component | Full Name | Primary Function | Key Details / Metrics |
| :--- | :--- | :--- | :--- |
| **Motherboard** | Main Circuit Board | Connects and holds all internal components and sockets. | Serves as the foundational circuit board. |
| **CPU** | Central Processing Unit | Executes program instructions and performs calculations. | Referred to as the "brain"; speed measured in MHz (millions/sec) and GHz (billions/sec). |
| **RAM** | Random Access Memory | Provides fast, temporary short-term storage for active CPU tasks. | Volatile memory; having adequate RAM prevents system slowdowns during multitasking. |
| **HDD** | Hard Disk Drive | Stores permanent files and software using a mechanical platter and arm. | Non-volatile storage; offers higher capacity at lower costs. |
| **SSD** | Solid State Drive | Non-volatile flash storage alternative to traditional hard drives. | Faster boot times and smaller footprint than HDDs. |
| **PSU** | Power Supply Unit | Converts wall outlet AC electricity into regulated DC power. | Distributes power to the motherboard, CPU, and peripherals. |
| **GPU / Expansion Cards** | Graphics Processing Unit | Renders visual output on the display screen. | Fits into motherboard expansion slots alongside sound and network cards. |

> [!NOTE] **Volatile vs. Non-Volatile Storage**
> * **RAM is Volatile**: Data is completely erased when the computer powers off. Work must be saved to permanent storage.
> * **HDDs & SSDs are Non-Volatile**: Files, operating systems, and applications remain saved permanently regardless of power state.

---

## 2. Ergonomics & Workplace Health

Prolonged computer usage without proper technique can result in strain injuries and long-term health issues.

### Physical Ergonomics Checklist
* **Mouse Grip**: Maintain a relaxed, gentle hold on the mouse rather than gripping tightly during focused work or gaming.
* **Height Alignment**: Keep the mouse at the exact same height as the keyboard to avoid straining wrist and arm muscles.
* **Dynamic Posture**: Avoid remaining in a rigid or slouched position for extended periods. Practice dynamic sitting, take regular breaks, and change positions to facilitate blood circulation and spine health.
* **Ergonomic Hardware**: Utilize specialized ergonomic keyboards and mice designed to keep wrists in neutral positions.
* **Keyboard Shortcuts**: Incorporate hotkeys for web browsing, OS navigation, and code editing to decrease repetitive mouse movements.

---

## 3. Internet Service Providers (ISPs) & Connection Types

An **Internet Service Provider (ISP)** is a company that sells access to the global internet infrastructure.

### ISP Structure Tiers
1. **Tier 1 (Conglomerates)**: Own extensive infrastructure capable of handling network traffic independently.
2. **Tier 2 (National Providers)**: Large regional providers that may lease access from Tier 1 backbones.
3. **Tier 3 (Local Providers)**: Small local providers supplying consumer access via leased larger networks.

### Connection Technologies Comparison

| Technology | Underlying Infrastructure | Performance & Features |
| :--- | :--- | :--- |
| **Fiber Optic** | Glass or plastic fibers transmitting light signals | Delivers extremely high data exchange speeds. |
| **Cable** | Coaxial cable television networks | High availability across residential areas. |
| **DSL** | Traditional landline telephone wiring | Widely accessible in non-cable regions; generally slower connection speeds. |
| **Dial-Up** | Standard telephone lines | Legacy technology; locks telephone line usage during active connections. |
| **Satellite** | Orbital satellite constellations | Connects remote locations across global coverage zones. |
| **5G Home** | Cellular tower networks | Supplies home internet wirelessly through cellular data networks. |

---

## 4. System Authentication & Account Security

Protecting local operating system accounts prevents unauthorized system access.

### Security Configuration Steps

#### Password Best Practices
* Use long passwords combining uppercase letters, lowercase letters, numbers, and special symbols.
* Avoid common strings like `12345` or `password`.
* Do not base credentials on easily discoverable personal information (names, birthdates, addresses).
* Enable **Two-Factor Authentication (2FA)** for supplemental verification security.

#### Biometric Authentication Options
* **Windows Hello**: Enables facial recognition or fingerprint scanning as alternatives to typed passwords.
* **Mac Touch ID**: Allows quick, secure fingerprint login on supported Apple hardware.

#### Operating System Setup Paths
* **Windows**: Open `Start` $\rightarrow$ `Settings` $\rightarrow$ `Accounts` $\rightarrow$ `Sign-in options`.
* **macOS**: Open `Apple Menu` $\rightarrow$ `System Settings` $\rightarrow$ `Users & Groups`.

---

## 5. Professional Developer Toolset

Software engineering workflows depend on standard development tools across hardware, software editing, version control, and testing.

| Tool Category | Purpose | Examples |
| :--- | :--- | :--- |
| **Hardware & OS** | Base execution environment requiring high RAM and CPU performance. | Windows, macOS, Linux. |
| **Code Editors & IDEs** | Applications providing syntax highlighting, auto-completion, debugging, and terminal integration. | VS Code, Visual Studio, IntelliJ IDEA, PyCharm, Sublime Text, Notepad++. |
| **Version Control (VCS)** | System for tracking code changes, managing feature branches, and merging updates. | Git (Core VCS), GitHub, GitLab, Bitbucket (Cloud Hosting). |
| **Package Managers** | Tools for installing, updating, and removing external libraries and dependencies. | npm, Yarn, pnpm (JS); pip (Python); Composer (PHP); Maven (Java). |
| **Testing Frameworks** | Tools for executing automated test suites to ensure application reliability. | Cypress, Playwright, Selenium; Jest (JS); pytest (Python); PHPUnit (PHP); JUnit (Java). |
| **Browser DevTools** | Environment for inspecting visual layout (HTML/CSS), debugging scripts, and profiling web performance. | Google Chrome, Mozilla Firefox, Microsoft Edge, Apple Safari. |