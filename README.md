# Phone Navigation App

A small, open-source Phone Navigation App built with plain HTML, CSS, and JavaScript. This repository demonstrates a lightweight, accessible navigation UI intended for phones and small screens. You are free to fork and modify it — I only ask that you credit the original author (Connor). Dev site: https://connorssite.rf.gd/

## Overview

This project is a simple, mobile-focused navigation example. It shows how to build a responsive navigation UI for phone-sized viewports using minimal dependencies.

This README has been expanded to:
- Provide a clear project structure
- Explain why and how to split JavaScript into its own file
- Offer step-by-step instructions to extract inline scripts into `js/app.js`
- Give basic best practices, running instructions, and contribution notes

## Project structure (recommended)

- index.html        — main HTML file (no inline scripts)
- css/
  - styles.css      — stylesheet
- js/
  - app.js          — JavaScript (moved out of HTML)
- assets/           — images, icons, fonts, etc.

If your repo currently has inline scripts inside `index.html`, follow the steps below to separate them into `js/app.js`.

## Why separate JS from HTML

- Cleaner, easier-to-read HTML.
- Better caching and performance.
- Easier to unit-test and reuse code.
- Simpler collaboration and code reviews.

## Steps to separate JavaScript from HTML

1) Create the folder and file

   - Create a `js` directory at the project root and add a file named `app.js`.

   Example:
   - `mkdir js`
   - `touch js/app.js`

2) Move inline script contents to `js/app.js`

   - If `index.html` has a `<script>` block (for example at the end of `<body>`), cut everything between `<script>` and `</script>` and paste it into `js/app.js`.

   - Wrap initialization code so it runs after the DOM is ready. For example, in `js/app.js`:

```javascript
// js/app.js

// Initialization to run after the DOM is loaded
document.addEventListener('DOMContentLoaded', () => {
  // paste the code you removed from index.html here
  // e.g. event listeners, DOM queries, initial state setup
});
```

3) Link the external JS file from `index.html`

   - Remove the inline `<script>` block from `index.html` and add a script tag that references the new file. Place it before the closing `</body>` tag or use the `defer` attribute in the head.

Example (before `</body>`):

```html
<script src="js/app.js"></script>
</body>
```

Or (in `<head>`) with `defer`:

```html
<head>
  <!-- other tags -->
  <script src="js/app.js" defer></script>
</head>
```

4) Test the app

   - Open `index.html` in the browser (or run a local static server) and verify the functionality is unchanged.
   - Use browser devtools console to see errors and fix any missing references (IDs/classes/variables that changed when moving code).

## Example: small index.html snippet

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Phone Navigation App</title>
  <link rel="stylesheet" href="css/styles.css">
  <script src="js/app.js" defer></script>
</head>
<body>
  <nav class="phone-nav" aria-label="Primary">
    <button id="menuBtn" aria-expanded="false">Menu</button>
    <ul id="menu" hidden>
      <li><a href="#home">Home</a></li>
      <li><a href="#features">Features</a></li>
      <li><a href="#about">About</a></li>
    </ul>
  </nav>

  <main id="content">
    <h1>Welcome</h1>
    <p>Resize to a mobile width to see the navigation behavior.</p>
  </main>
</body>
</html>
```

And the companion JS (move any inline script into this file):

```javascript
// js/app.js

document.addEventListener('DOMContentLoaded', () => {
  const menuBtn = document.getElementById('menuBtn');
  const menu = document.getElementById('menu');

  menuBtn.addEventListener('click', () => {
    const expanded = menuBtn.getAttribute('aria-expanded') === 'true';
    menuBtn.setAttribute('aria-expanded', String(!expanded));
    if (expanded) {
      menu.hidden = true;
    } else {
      menu.hidden = false;
      menu.querySelector('a')?.focus();
    }
  });

  // close menu when focus moves away
  document.addEventListener('click', (e) => {
    if (!menu.contains(e.target) && e.target !== menuBtn) {
      menu.hidden = true;
      menuBtn.setAttribute('aria-expanded', 'false');
    }
  });
});
```

## Recommended JavaScript best practices

- Use `const` and `let` (avoid `var`).
- Keep DOM queries and event listeners inside the DOMContentLoaded handler or use `defer`.
- Encapsulate logic into functions and modules where possible.
- Avoid polluting the global scope—use an IIFE or ES module (`type="module"`) for larger projects.

Example using ES modules:

```html
<script type="module" src="js/app.js"></script>
```

```javascript
// js/app.js
import { initNav } from './nav.js';

document.addEventListener('DOMContentLoaded', () => {
  initNav();
});
```

## Installation & usage

1. Clone the repo:

   git clone https://github.com/htmlfan123/Phone-Navigation-App.git

2. Open `index.html` in your browser, or serve with a simple static server:

   - Python 3: `python -m http.server 8000`
   - Node (http-server): `npx http-server -c-1`

3. Visit `http://localhost:8000` (or open the file directly) and test on a mobile viewport.

## Contributing

Contributions are welcome. Please open issues for bugs and feature requests and submit pull requests for fixes or improvements. If you reuse or adapt this project, please credit the original author.

## License

Add a license file (e.g., `LICENSE`) if you want to clarify reuse terms. If you don't add one, the repository defaults to "all rights reserved." A permissive choice is the MIT License.

---

If you'd like, I can also:

- Create `js/app.js` with the extracted inline script from your current `index.html` (if you point me to it),
- Create `css/styles.css` with a minimal mobile-first stylesheet, or
- Submit a PR that moves the inline script into `js/app.js` and updates `index.html`.
