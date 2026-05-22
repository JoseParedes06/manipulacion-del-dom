# 🧠 DOM Manipulation — JavaScript Learning Series

> A structured, hands-on collection of vanilla JavaScript exercises exploring the fundamentals of DOM manipulation, event handling, and dynamic UI interactions.

---

## 📌 Overview

This repository is organized as a **progressive learning path** through core browser JavaScript concepts. Each module builds on the previous, moving from raw DOM access and element selection all the way to event-driven interactivity and multi-operation logic.

All exercises are written in **pure HTML + CSS + vanilla JavaScript** — no frameworks, no build tools, no dependencies. Just the browser and the fundamentals.

---

## 📁 Project Structure

```
manipulacion-del-dom/
│
├── Main/                          # Core DOM API fundamentals
│   ├── index.html
│   └── script.js
│
├── Interactive JavaScript/        # Inline event handlers & basic input reading
│   ├── index.html
│   └── script.js
│
├── Add Event Listener/            # Refactored with addEventListener + form submit
│   ├── index.html
│   └── script.js
│
├── Desafio Sumar/                 # Challenge: 4-operation calculator with radio buttons
│   ├── index.html
│   └── script.js
│
└── Desafio Add Event Listener/    # Challenge: keypress + mouseover mini-game
    ├── index.html
    ├── script.js
    └── styles.css
```

---

## 🗺️ Learning Progression

The modules are designed to be explored **in order**:

```
Main → Interactive JavaScript → Add Event Listener → Desafio Sumar → Desafio Add Event Listener
  │              │                      │                   │                     │
DOM basics    onclick (inline)    addEventListener     Multi-op calc       keypress + mouseover
querySelector  value reading      event.preventDefault  Number() casting   Random emoji + game
```

---

## 📦 Module Breakdown

---

### 1. `Main` — DOM API Foundations

**Purpose:** A scratchpad for exploring the core DOM API. No UI output — all results visible in the browser console.

**Key Concepts Practiced:**

| Method / Property | What It Does |
|---|---|
| `document.querySelector()` | Select elements by CSS selector |
| `element.innerHTML` | Set HTML content (renders tags) |
| `element.innerText` | Set plain text content (escapes tags) |
| `element.getAttribute()` | Read an attribute value |
| `element.setAttribute()` | Write / overwrite an attribute |
| `element.classList.add/remove` | Manage CSS classes programmatically |
| `document.createElement()` | Dynamically create a new DOM element |
| `element.append()` | Insert a node into the document |

**Notable snippet:**
```js
const img = document.createElement("img");
img.setAttribute("src", "https://...");
pid.append(img);
```
> Creates an image element entirely in JavaScript and injects it into the page — a foundational pattern for dynamic UIs.

---

### 2. `Interactive JavaScript` — Inline Handlers

**Purpose:** First experiment with reading user input and displaying a result — using the older `onclick` inline attribute pattern.

**Key Concepts Practiced:**
- Selecting form inputs with `querySelector`
- Reading `.value` from `<input>` elements
- Updating the DOM with `innerText`
- Wiring a button via the HTML `onclick` attribute

**Known Limitation:**
```js
const sumaInputs = input1.value + input2.value; // ⚠️ String concatenation, not addition
```
> Since `.value` always returns a string, `"3" + "5"` yields `"35"` instead of `8`. This is intentional as a learning artifact — fixed in later modules.

---

### 3. `Add Event Listener` — Event-Driven JavaScript

**Purpose:** Refactors `Interactive JavaScript` using the modern `addEventListener` approach, and adds form submission handling.

**Key Concepts Practiced:**
- `element.addEventListener(type, handler)` — the modern, flexible way to attach events
- Listening to both `'click'` and `'submit'` events
- `event.preventDefault()` — prevents the browser's default form-submit page reload
- The `event` object — inspected via `console.log(event)`

**Core pattern:**
```js
btn.addEventListener('click', sumarInputValues);
form.addEventListener('submit', sumarInputValues);

function sumarInputValues(event) {
    event.preventDefault();
    pResult.innerText = "Resultado: " + (input1.value + input2.value);
}
```

> This is the architectural shift from imperative HTML handlers to a clean separation of structure (HTML) and behavior (JS).

---

### 4. `Desafio Sumar` — 4-Operation Calculator

**Purpose:** A complete challenge that implements a functional calculator supporting addition, subtraction, multiplication, and division using radio buttons.

**Key Concepts Practiced:**
- `<input type="radio">` groups and reading `.checked`
- `Number()` casting to convert string input to numeric values
- Conditional logic (`if / else if / else`) for operation routing
- Dynamic element creation: `document.createElement('h2')` + `body.append(res)`
- Inline `onclick` attribute wiring a globally scoped function

**Core logic:**
```js
function calculate() {
    let value1 = Number(val1.value);
    let value2 = Number(val2.value);
    let resValue = 0;

    if (sum.checked)       resValue = value1 + value2;
    else if (dif.checked)  resValue = value1 - value2;
    else if (pro.checked)  resValue = value1 * value2;
    else                   resValue = value1 / value2;

    res.innerHTML = `The calculated value is: ${resValue}`;
    body.append(res);
}
```

> First module to correctly cast inputs as numbers, resolving the concatenation bug from earlier modules.

---

### 5. `Desafio Add Event Listener` — Interactive Events Challenge

**Purpose:** The most complex module — a creative, game-like page that exercises two distinct event types simultaneously.

**Feature 1 — `keypress` Emoji Randomizer:**
- Every keystroke in an input field triggers a random emoji from an array of 800+ Unicode characters
- Demonstrates event-driven UI updates without form submission

**Feature 2 — `mouseover` Flappy Bird Mini-Game:**
- A Flappy Bird-themed arena using real game assets (pipes, sky background, bird cursor)
- Hovering over pipe obstacles triggers a "PERDISTE" (You Lost) overlay
- A death counter (`dieCount`) increments on each collision
- A reset button re-enables the game and hides the overlay

**Key Concepts Practiced:**
- `'keypress'` event listener on `<input>`
- `'mouseover'` event listener on multiple elements via `.forEach()`
- `Math.random()` + `Math.floor()` for random array indexing
- `element.disabled` toggle for button state management
- `element.style.display` for showing/hiding overlays
- Incremental counter with a closure variable (`let i = 1`)
- CSS `cursor` property with a custom image URL

**Known Bugs (Learning Artifacts):**
```js
// Bug 1 — Typo in variable name (emojiPickl vs emojiPick)
emojiResult.innerHTML = emojiPickl;  // ❌ ReferenceError

// Bug 2 — Wrong selector method for class-based multi-element selection
const pipesHitBox = document.getElementById('.pipeHitBox');  // ❌ Returns null
// Should be: document.querySelectorAll('.pipeHitBox')

// Bug 3 — Typo in style property
message.styke.display = 'flex';  // ❌ TypeError
// Should be: message.style.display
```
> These bugs make this module an excellent debugging exercise. Identifying and fixing them reinforces how JavaScript errors propagate through the DOM.

---

## 🛠️ How to Run

No installation or build step required. Open any module directly in your browser:

```bash
# Clone the repository
git clone https://github.com/your-username/manipulacion-del-dom.git

# Navigate to any module folder and open index.html
open "Add Event Listener/index.html"
```

Or simply drag any `index.html` file into your browser.

> **Recommended:** Use [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) in VS Code for auto-reload on file changes.

---

## 🧪 Debugging Tips

Open your browser's **DevTools** (`F12` or `Cmd+Option+I`) before running any module:

- **Console tab** — Check for `ReferenceError`, `TypeError`, and `console.log()` outputs
- **Elements tab** — Inspect live DOM changes as you interact with the page
- **Sources tab** — Step through JavaScript line by line with breakpoints

---

## 🔑 Core DOM APIs Reference

| API | Description |
|---|---|
| `document.querySelector(sel)` | Returns first matching element |
| `document.querySelectorAll(sel)` | Returns NodeList of all matches |
| `document.getElementById(id)` | Returns element by `id` attribute |
| `document.createElement(tag)` | Creates a new detached element |
| `element.addEventListener(type, fn)` | Attaches an event listener |
| `element.innerHTML` | Gets/sets inner HTML string |
| `element.innerText` | Gets/sets visible text content |
| `element.value` | Gets/sets form input value |
| `element.classList` | Interface to manage CSS classes |
| `element.setAttribute(k, v)` | Sets an attribute |
| `element.append(child)` | Inserts child at end of element |
| `element.style.property` | Directly modifies inline CSS |
| `event.preventDefault()` | Stops default browser behavior |

---

## 🧱 Tech Stack

| Layer | Technology |
|---|---|
| Markup | HTML5 |
| Styling | CSS3 (inline + external sheets) |
| Logic | Vanilla JavaScript (ES6+) |
| Fonts | Google Fonts — Montserrat |
| Assets | Flappy Bird sprite assets (external CDN) |

---

## 📚 Concepts Covered (Summary)

- [x] DOM selection with `querySelector`, `getElementById`, `querySelectorAll`
- [x] Reading and writing element content (`innerHTML`, `innerText`, `.value`)
- [x] Attribute manipulation (`getAttribute`, `setAttribute`, `classList`)
- [x] Dynamic element creation and injection (`createElement`, `append`)
- [x] Inline event handlers (`onclick` attribute)
- [x] `addEventListener` — click, submit, keypress, mouseover
- [x] `event.preventDefault()` for form handling
- [x] Type casting with `Number()`
- [x] Conditional logic for branching behavior
- [x] State management with module-level variables
- [x] Random array indexing with `Math.random()`
- [x] DOM debugging and reading browser errors

---

## 👤 Author

**Jochi** — Computer Science, George Washington University (SEAS), Class of 2029

---

*Built as part of a structured JavaScript fundamentals curriculum. Each module is intentionally isolated so any single exercise can be studied or debugged independently.*
