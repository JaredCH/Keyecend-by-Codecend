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
    <img src="https://img.shields.io/github/downloads/JaredCH/Keyecend-by-Codecend/total?style=for-the-badge&color=brightgreen" alt="Total Downloads">
  </a>
  <a href="https://github.com/JaredCH/Keyecend-by-Codecend/blob/main/LICENSE">
    <img src="https://img.shields.io/github/license/JaredCH/Keyecend-by-Codecend?style=for-the-badge&color=41b883" alt="License">
  </a>
  <a href="https://github.com/JaredCH/Keyecend-by-Codecend/stargazers">
    <img src="https://img.shields.io/github/stars/JaredCH/Keyecend-by-Codecend?style=for-the-badge&logo=startrek&color=f9a825" alt="Stargazers">
  </a>
</div>

---

### **Overview**

Tired of repetitive, manual tasks? **Keyecend** is your solution. It's a sophisticated macro management tool that empowers you to orchestrate complex workflows, automate UI interactions, and integrate external scripts with a simple yet powerful scripting language.

From simple key presses to intelligent, vision-based automation, Keyecend is the engine that drives your productivity. Whether you're a gamer, a data entry professional, or a developer, you can craft scripts to do the work for you.

---

### ✨ **Core Features**

Keyecend comes packed with features that give you complete control over your machine.

* 👁️ **Vision-Based Automation:** Use `WAITFORIMAGEFILE` and `FINDCOLORCLICK` to create intelligent scripts that react to on-screen elements, not just fixed coordinates.
* 🦾 **Human-Like Mouse Movement:** Go beyond robotic `MOVEMOUSE`. With `MOVEMOUSEHUMAN`, your automations become smoother, more natural, and less detectable.
* ⌨️ **Advanced Keystroke Simulation:** The `SEND` command can type text, handle complex keyboard shortcuts (`^c`, `%{F4}`), and even use encrypted text for secure input of sensitive data.
* 🔄 **Powerful Logic and Loops:** Easily repeat actions with `LOOP` or iterate through data with `LOOPLIST` and `SENDLISTITER`. All loops are terminated with `ENDLOOP`.
* ⚙️ **External Script Execution:** Use the `RUN` command to launch `.exe` files, compiled AutoHotkey scripts, or any other program, making Keyecend your central automation hub.
* 🔐 **Built-in Encryption:** Securely store and use sensitive text like passwords or API keys within your scripts with the dead-simple `ENCRYPT` command.
* 🛠️ **Developer Utilities:** Tools like `MEASURE` and interactive overlays make script creation a breeze by giving you instant pixel distances and coordinates.

---

### 🚀 **Getting Started**

1. Go to the [**Releases Page**](https://github.com/JaredCH/Keyecend-by-Codecend/releases).
2. Download the latest `Keyecend.exe` or installer for your operating system.
3. Run the application and start scripting!

---

### ⌨️ **Global Hotkeys**

While a script is running, you can control it globally from any application:
* **`Pause / Break`**: Pauses a running script. Press it again to resume.
* **`End`**: Immediately stops and terminates the current script.

---

### 📚 **Scripting Reference**

Master Keyecend with its straightforward scripting language. Here are the core commands:

#### **Timing & Control Flow**
* **`SLEEP [duration_ms]`**
  * Pauses the script for a fixed duration in milliseconds.
  * `SLEEP 1500`

* **`SLEEPRANDOM [min_ms] [max_ms]`**
  * Pauses for a random duration between the minimum and maximum values. Excellent for mimicking human behavior.
  * `SLEEPRANDOM 800 1200`

* **`LOOP [count|unlimited]`**
  * Repeats a block of commands a specific number of times. Use `unlimited` for an infinite loop (can be stopped with the `End` key). The block must be closed with `ENDLOOP`.
  * ```
    LOOP 5
        # ... your commands here ...
    ENDLOOP
    ```

* **`ENDLOOP`**
  * Marks the end of a `LOOP` or `LOOPLIST` block.
  * `ENDLOOP`

#### **Mouse & Keyboard**
* **`MOVEMOUSE [X] [Y]`** or **`MOVEMOUSE [dynamic_coordinate]`**
  * Instantly moves the cursor to the target coordinates. Also supports [Dynamic Coordinates](#dynamic-coordinates).
  * `MOVEMOUSE 800 600`
  * `MOVEMOUSE foundimage.center`

* **`MOVEMOUSEHUMAN [X] [Y] [duration_ms]`**
  * Smoothly moves the cursor to the target coordinates over a duration, using a Bezier curve to simulate human-like motion.
  * `MOVEMOUSEHUMAN 800 600 50`

* **`CLICKLEFT [X] [Y]`** / **`CLICKRIGHT [X] [Y]`**
  * Performs a mouse click at the specified coordinates. Also supports [Dynamic Coordinates](#dynamic-coordinates).
  * `CLICKLEFT 850 650`
  * `CLICKRIGHT foundimage.offsetxy 10 5`

* **`SEND [text]`**
  * Types the provided text. This is a very powerful command with special syntax:
  * **Special Keys:** Use curly braces `{}` for non-character keys.
    * *Examples:* `{ENTER}`, `{TAB}`, `{F5}`, `{BACKSPACE}`, `{UP 2}` (presses UP key twice).
  * **Modifier Keys:** Use `^` for Ctrl, `+` for Shift, and `%` for Alt.
    * *Examples:* `^c` (Copy), `^v` (Paste), `%{F4}` (Alt+F4).
  * **Encrypted Text:** Safely type sensitive data using the `Enc(...)` syntax.
    * *Example:* `SEND Enc("U0Jbt...==")`
  * **Plain Text:**
    * `SEND Hello World!{ENTER}`

#### **Vision & Color**
* **`WAITFORIMAGEFILE [FileName],[timeout],[actionOffset],[maxAttempts]`**
  * The most powerful conditional command. Waits for a captured image to appear on screen and then alters the script's execution flow.
    * **`FileName`**: The image file (e.g., `button.jpg`) located in the `ScriptImages` folder.
    * **`timeout`**: Time in milliseconds to wait for the image. Use `0` for an unlimited wait.
    * **`actionOffset`**: What to do if the image is **not** found.
      * `0`: Continue to the next line.
      * `> 0`: Jump forward that many lines.
      * `< 0`: Jump backward that many lines (creates a loop until the image is found).
    * **`maxAttempts`**: (Optional) The maximum number of times to try the `actionOffset` loop. `0` means infinite retries.
  * ```
    # Loop until 'login_success.jpg' is found, then continue
    WAITFORIMAGEFILE login_success.jpg,0,-1,0
    ```

* **`WAITFORCOLOR [X] [Y] [hex_color] [timeout_ms]`**
  * Waits until a pixel at a *specific* X,Y location matches the target color (e.g., `#FF33AA`). Use `0` for an unlimited timeout.
  * `WAITFORCOLOR 300 450 #FF33AA 10000`

* **`FINDCOLORCLICK [hex_color] [click_type]`**
  * Finds the *first pixel* of the target color anywhere on screen and performs an action.
    * **`click_type`**: Can be `Left`, `Right`, or `None`.
  * `FINDCOLORCLICK #1A2B3C Left`

#### **Data & Lists**
* **`LOOPLIST [ListName]`**
  * Loops through a user-defined list. For each iteration, the internal iterator for that list advances. Use with `SENDLISTITER` or other commands inside the loop. Must be closed with `ENDLOOP`.
  * ```
    # This example types each line from a list you provide when the script runs.
    LOOPLIST LIVELIST
        SENDLISTITER LIVELIST
        SEND {ENTER}
        SLEEP 500
    ENDLOOP
    ```

* **`SENDLISTITER [ListName]`**
  * Types the *current* item from the specified list based on the loop's progress.
  * `SENDLISTITER MyUserList`

#### **System & Utilities**
* **`RUN [program_path]`**
  * Runs an external program or script. Use quotes for paths with spaces.
  * `RUN "notepad.exe"`
  * `RUN "C:\My Scripts\utility.exe"`

* **`ENCRYPT [text]`**
  * This is a UI-driven command. In the editor, highlight text, click the "Encrypt" button, and it will be replaced with `Enc("...")` for use with the `SEND` command.

* **`MEASURE`**
  * An interactive tool to measure distances. Click two points on the screen, and it will insert commented-out coordinates, distance, and delta values into your script for easy reference.
  * ```
    MEASURE
    # Distance: 100 px
    # First:    X:600, Y:400
    # Second:   X:700, Y:400
    # Delta:    X:100, Y:0
    ```

* **`# [comment]`**
  * Lines starting with `#` are comments and will be ignored by the script runner.
  * `# This is a comment`

---

### **Dynamic Coordinates**

Instead of using fixed X,Y numbers, you can use coordinates relative to the last image found by `WAITFORIMAGEFILE`. This makes your scripts incredibly robust against changes in window position or resolution.

* `foundimage.center`: The center of the found image.
* `foundimage.topleft`: The top-left corner of the found image.
* `foundimage.bottomright`: The bottom-right corner of the found image.
* `foundimage.offsetx [pixels]`: The center of the image, offset horizontally.
* `foundimage.offsety [pixels]`: The center of the image, offset vertically.
* `foundimage.offsetxy [x_pixels] [y_pixels]`: The center, offset by both X and Y.

**Example Usage:**
```
# Wait for the "Username" field to appear on screen
WAITFORIMAGEFILE username_field.jpg,0,-1,0

# Click 200 pixels to the right of the center of that image to select the input box
CLICKLEFT foundimage.offsetx 200

# Send my username
SEND MyUsername
```

---

### 🤝 **Contributing**

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

### 📜 **License**

Distributed under the MIT License. See `LICENSE` for more information.

---

### **Contact**

JaredCH (Codecend) – [@JaredCH](https://github.com/JaredCH) – [www.codecend.com](https://www.codecend.com)

Project Link: [https://github.com/JaredCH/Keyecend-by-Codecend](https://github.com/JaredCH/Keyecend-by-Codecend)
