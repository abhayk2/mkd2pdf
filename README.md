# 📄 Markdown to PDF Converter

A zero-install, client-side web application that converts Markdown text into a professionally styled PDF document using only the browser. No server, no external dependencies at runtime, and no user data leaves the machine.

## 🧠 Technical Theory

### Overview

This tool performs **Markdown-to-PDF** conversion entirely within the browser by chaining two processes:

1. **Markdown → HTML**  
   A JavaScript library (`marked`) parses Markdown syntax and outputs a corresponding HTML string.
2. **HTML → PDF**  
   The browser’s built-in print engine renders the HTML and exports it as a PDF via the “Save as PDF” destination in the print dialog.

The entire process is **client-side static**. The HTML file can be hosted anywhere (GitHub Pages, Netlify, S3) and works without a backend.

---

### 1. Markdown Parsing (Markdown → HTML)

We use **[marked](https://marked.js.org/)**, a low-level, fast, and widely adopted Markdown compiler. It takes a raw Markdown string and produces a complete HTML fragment.

**Example pipeline:**
```javascript
const html = marked.parse('# Hello\n- item 1\n- item 2');
// → '<h1>Hello</h1>\n<ul>\n<li>item 1</li>\n<li>item 2</li>\n</ul>\n'