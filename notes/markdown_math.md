Got it — thanks for the clarification.
This is the key point, so I’ll be very precise and honest with you 👇

---

## 🔴 Short, direct answer (no sugar-coating)

> **You cannot make**

```markdown
[
math
]
```

> **render as math in standard Markdown without modifying the content.**

There is **no Markdown setting, no VS Code option, no MathJax/KaTeX switch** that will interpret bare square brackets as math delimiters.

This is not a limitation of VS Code — it’s a **syntax collision by design**.

---

## 🧠 Why this is fundamentally impossible

### 1️⃣ `[` is already owned by Markdown

In Markdown:

```markdown
[text](url)
```

So when the parser sees:

```markdown
[
something
]
```

It assumes:

* a **link label**
* or malformed Markdown

👉 Math engines are **never invoked**.

---

### 2️⃣ Math engines only activate inside math delimiters

MathJax / KaTeX **only parse math** when they see:

* `$ … $`
* `$$ … $$`
* `\( … \)`
* `\[ … \]`

They **do not scan raw text** looking for math.

So this will *never* work:

```markdown
[
-\frac12
]
```

because math mode was never entered.

---

## ✅ What *can* be done (realistic options)

Since you said **“I don’t want to modify `[` to `$$`”**, here are the **only viable workarounds**, from most to least practical.

---

## 🟢 Option 1 (BEST): Render with Pandoc + custom extension

If you control the **rendering pipeline** (Pandoc, academic workflow):

```bash
pandoc --lua-filter=bracket-math.lua input.md
```

Where the filter converts:

```
[
math
]
```

→ internally to:

```
\[
math
\]
```

📌 The source file stays unchanged
📌 Rendering is correct
📌 This is how publishers handle legacy content

⚠️ VS Code preview **cannot do this**

---

## 🟡 Option 2: Use a Markdown flavor that redefines syntax (rare)

Some **non-standard editors** (not VS Code, not GitHub) allow:

* Typora (custom syntax plugins)
* Obsidian (community plugins)

But:

* ❌ Not portable
* ❌ Not standard Markdown
* ❌ Will break elsewhere

---

## 🔴 Option 3: VS Code preview hacks (NOT possible)

There is **no way** to tell:

* VS Code Markdown preview
* Markdown-It
* MathJax

to reinterpret `[` as math **without preprocessing**.

Extensions cannot intercept raw Markdown AST **before** parsing.

---

## 🔑 The unavoidable truth

> **Rendering math requires entering math mode.**
> **`[` is not a math-mode delimiter.**

So **one of these must happen**:

1. The content is **preprocessed**
2. The content is **converted**
3. The renderer is **non-standard**

If *none* of those are allowed → it **cannot be rendered as math**

---

## ✅ Practical recommendation (least invasive)

If you’re pasting legacy content:

* Keep the source unchanged
* Add **one preprocessing step** (script, Pandoc filter, build hook)

That’s how this is handled in:

* academic publishing
* LaTeX → Markdown pipelines
* math-heavy note systems

---

## 🧩 If you want, I can give you:

* a **Pandoc Lua filter**
* a **regex-based preprocessor**
* an **Obsidian plugin workaround**
* a **VS Code task that renders correctly without touching files**

Just tell me **where you preview/render**:

* VS Code preview
* GitHub
* Pandoc
* Typora
* Obsidian

and I’ll tailor the exact solution.
