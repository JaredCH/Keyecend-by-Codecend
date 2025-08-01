<div align="center">
  <h1 align="center">⚙️ Keyecend</h1>

  <p align="center">
    <strong>Your Command Center for Desktop Automation.</strong>
    <br />
    A powerful, intuitive, and scriptable macro engine from <a href="https://www.codecend.com" target="_blank"><strong>Codecend</strong></a>.
    <br />
    <br />
    <a href="https://www.codecend.com" target="_blank"><strong>Official Website</strong></a>
    ·
    <a href="https://github.com/JaredCH/Keyecend-by-Codecend/issues">Report Bug</a>
    ·
    <a href="https://github.com/JaredCH/Keyecend-by-Codecend/issues">Request Feature</a>
  </p>

</div>

<div align="center">
  <a href="https://www.codecend.com">
    <img src="https://img.shields.io/badge/Website-Codecend.com-blue?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Website">
  </a>
  <a href="https://github.com/JaredCH/Keyecend-by-Codecend/releases/latest">
    <img src="https://img.shields.io/github/v/release/JaredCH/Keyecend-by-Codecend?style=for-the-badge&color=5d69bf" alt="Latest Release">
  </a>
  <a href="https://github.com/JaredCH/Keyecend-by-Codecend/releases">
    <img src="https://img.shields.io/github/downloads/JaredCH/Keyecend-by-Codecend/total?style=for-the-badge&color=28a745&logo=download" alt="Total Downloads">
  </a>
  <a href="https://github.com/JaredCH/Keyecend-by-Codecend/blob/main/LICENSE">
    <img src="https://img.shields.io/github/license/JaredCH/Keyecend-by-Codecend?style=for-the-badge&color=41b883" alt="License">
  </a>
  <a href="https://github.com/JaredCH/Keyecend-by-Codecend/stargazers">
    <img src="https://img.shields.io/github/stars/JaredCH/Keyecend-by-Codecend?style=for-the-badge&logo=startrek&color=f9a825" alt="Stargazers">
  </a>
</div>

---

## **Overview**

Transform repetitive tasks into automated workflows with **Keyecend**. This sophisticated macro management tool empowers you to orchestrate complex automation, handle UI interactions intelligently, and integrate external scripts—all through an intuitive scripting language.

From simple keystrokes to advanced vision-based automation, Keyecend adapts to your workflow. Perfect for gamers, data professionals, developers, and anyone who values their time.

---

## ✨ **Key Features**

### 🎯 **Smart Automation**
- **Vision-Based Logic**: React to screen changes with `WAITFORIMAGEFILE` and `FINDCOLORCLICK`
- **Human-Like Movement**: Natural mouse paths with `MOVEMOUSEHUMAN` using Bezier curves
- **Dynamic Coordinates**: Script positions relative to found images, not fixed pixels

### ⚡ **Powerful Scripting**
- **Advanced Text Input**: Handle shortcuts, special keys, and encrypted passwords
- **Flexible Loops**: Iterate with counts, lists, or unlimited cycles
- **External Integration**: Launch programs and scripts seamlessly

### 🔒 **Security & Reliability**
- **Built-in Encryption**: Secure storage for sensitive data
- **Global Hotkeys**: Pause/resume/stop scripts from anywhere
- **Developer Tools**: Interactive measurement and coordinate helpers

---

## 🚀 **Quick Start**

1. **Download**: Get the latest version from [Releases](https://github.com/JaredCH/Keyecend-by-Codecend/releases)
2. **Install**: Run `Keyecend.exe` or use the installer
3. **Script**: Create your first automation script
4. **Execute**: Run and control with global hotkeys

### Your First Script
```
# Simple automation example
SLEEP 1000
SEND Hello, World!{ENTER}
CLICKLEFT 500 300
```

---

## ⌨️ **Global Controls**

Control running scripts from any application:
- **`Pause/Break`**: Pause/resume current script
- **`End`**: Stop script immediately

---

## 📖 **Command Reference**

<details>
<summary><strong>⏱️ Timing & Flow Control</strong></summary>

### `SLEEP [duration_ms]`
Pause execution for specified milliseconds.
```
SLEEP 1500
```

### `SLEEPRANDOM [min_ms] [max_ms]`
Random pause duration for human-like behavior.
```
SLEEPRANDOM 800 1200
```

### `LOOP [count|unlimited]` ... `ENDLOOP`
Repeat command blocks.
```
LOOP 5
    SEND Hello{ENTER}
    SLEEP 500
ENDLOOP
```

</details>

<details>
<summary><strong>🖱️ Mouse & Keyboard</strong></summary>

### `MOVEMOUSE [X] [Y]` / `MOVEMOUSE [dynamic_coordinate]`
Instant cursor positioning.
```
MOVEMOUSE 800 600
MOVEMOUSE foundimage.center
```

### `MOVEMOUSEHUMAN [X] [Y] [duration_ms]`
Smooth, natural cursor movement.
```
MOVEMOUSEHUMAN 800 600 500
```

### `CLICKLEFT [X] [Y]` / `CLICKRIGHT [X] [Y]`
Mouse clicks with dynamic coordinate support.
```
CLICKLEFT 850 650
CLICKRIGHT foundimage.offsetxy 10 5
```

### `SEND [text]`
Advanced text input with special syntax:
- **Special keys**: `{ENTER}`, `{TAB}`, `{F5}`, `{UP 2}`
- **Modifiers**: `^c` (Ctrl+C), `+a` (Shift+A), `%{F4}` (Alt+F4)
- **Encrypted text**: `SEND Enc("encrypted_string")`

```
SEND Hello World!{ENTER}
SEND ^c
SEND Enc("U0Jbt...==")
```

</details>

<details>
<summary><strong>👁️ Vision & Color Detection</strong></summary>

### `WAITFORIMAGEFILE [file],[timeout],[actionOffset],[maxAttempts]`
Wait for images and control script flow.
- `file`: Image in `ScriptImages` folder
- `timeout`: Wait time (0 = unlimited)
- `actionOffset`: Lines to jump if not found (negative = loop back)
- `maxAttempts`: Maximum retry attempts (0 = unlimited)

```
# Loop until login button appears
WAITFORIMAGEFILE login_button.jpg,0,-1,0
CLICKLEFT foundimage.center
```

### `WAITFORCOLOR [X] [Y] [hex_color] [timeout_ms]`
Wait for specific pixel color.
```
WAITFORCOLOR 300 450 #FF33AA 10000
```

### `FINDCOLORCLICK [hex_color] [click_type]`
Find and click first matching color pixel.
```
FINDCOLORCLICK #1A2B3C Left
```

</details>

<details>
<summary><strong>📋 Data & Lists</strong></summary>

### `LOOPLIST [ListName]` ... `ENDLOOP`
Iterate through user-defined lists.
```
LOOPLIST USERNAMES
    SENDLISTITER USERNAMES
    SEND {TAB}
    SLEEP 500
ENDLOOP
```

### `SENDLISTITER [ListName]`
Type current list item.
```
SENDLISTITER MyList
```

</details>

<details>
<summary><strong>🛠️ System & Utilities</strong></summary>

### `RUN [program_path]`
Execute external programs.
```
RUN "notepad.exe"
RUN "C:\Scripts\utility.exe"
```

### `ENCRYPT [text]`
UI tool: Select text → Click "Encrypt" button.

### `MEASURE`
Interactive distance measurement tool.
```
MEASURE
# Distance: 100 px
# First:    X:600, Y:400
# Second:   X:700, Y:400
# Delta:    X:100, Y:0
```

### `# [comment]`
Script comments (ignored during execution).
```
# This is a comment
```

</details>

---

## 🎯 **Dynamic Coordinates**

Make scripts resolution-independent by using coordinates relative to found images:

| Coordinate | Description |
|------------|-------------|
| `foundimage.center` | Center of found image |
| `foundimage.topleft` | Top-left corner |
| `foundimage.bottomright` | Bottom-right corner |
| `foundimage.offsetx [pixels]` | Center + horizontal offset |
| `foundimage.offsety [pixels]` | Center + vertical offset |
| `foundimage.offsetxy [x] [y]` | Center + both offsets |

### Example: Adaptive Login Script
```
# Wait for username field
WAITFORIMAGEFILE username_field.jpg,0,-1,0

# Click in the field (200px right of image center)
CLICKLEFT foundimage.offsetx 200

# Enter credentials
SEND MyUsername{TAB}
SEND MyPassword{ENTER}
```

---

## 💡 **Use Cases**

- **Gaming**: Automated resource gathering, repetitive actions
- **Data Entry**: Form filling, batch processing
- **Testing**: UI automation, regression testing  
- **Productivity**: File organization, system maintenance
- **Development**: Build automation, deployment scripts

---

## 🤝 **Contributing**

We welcome contributions! Here's how to get involved:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

### Development Setup
- Windows 10+ required
- .NET Framework 4.7.2+
- Visual Studio 2019+ recommended

---

## 📋 **System Requirements**

- **OS**: Windows 10 or later
- **RAM**: 256MB minimum
- **Storage**: 50MB available space
- **Permissions**: User-level access (Admin for system-wide automation)

---

## ❓ **FAQ**

**Q: Is Keyecend safe to use?**  
A: Yes! Keyecend is digitally signed and contains no malware. It only performs actions you explicitly script.

**Q: Can I use Keyecend for gaming?**  
A: While Keyecend can automate games, always check game terms of service regarding automation tools.

**Q: Does it work with multiple monitors?**  
A: Yes! Keyecend supports multi-monitor setups with full coordinate mapping.

---

## 📜 **License**

Distributed under the MIT License. See [`LICENSE`](LICENSE) for details.

---

## 📞 **Support & Contact**

- **Developer**: JaredCH (Codecend)
- **Website**: [codecend.com](https://www.codecend.com)
- **Issues**: [GitHub Issues](https://github.com/JaredCH/Keyecend-by-Codecend/issues)
- **Discussions**: [GitHub Discussions](https://github.com/JaredCH/Keyecend-by-Codecend/discussions)

---

<div align="center">
  <p><strong>⭐ Star this repo if Keyecend helps automate your workflow!</strong></p>
</div>
