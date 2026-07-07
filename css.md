# CSS Basics Guide — Your Portfolio

This guide teaches you CSS by styling YOUR actual HTML.
We go step by step, property by property. Keep your Live Server open while you write each step.

---

## What is CSS?

CSS controls how your HTML **looks**.
You write it in `css/style.css` and it targets HTML elements by their tag name or class name.

**Basic syntax:**
```css
selector {
    property: value;
}
```

Example:
```css
h1 {
    color: white;
}
```
This makes every `<h1>` white.

---

## Your HTML Structure (Quick Map)

```
body
 └── header > nav
 └── main
      └── section.hero
           └── div.container
                ├── div.hero-image
                │    └── img.profile_image
                └── div.hero-content
                     ├── h1.title
                     ├── p.sub-title
                     ├── address.hero-location
                     ├── p.hero-status
                     └── p.interests
```

---

## Step 1 — Dark Background on the Page

The `body` is the whole page. Let's make it dark.

**Add to `css/style.css`:**
```css
body {
    background-color: #0b0c0e;
    color: #9ba3b0;
}
```

- `background-color` — sets the background color (`#0b0c0e` is a very dark gray/black)
- `color` — sets the default text color for everything inside `body`

**Save and check Live Server.** The page should go dark.

---

## Step 2 — Style the Card (container)

The `.container` div wraps everything. Let's make it a dark card.

**Add to `css/style.css`:**
```css
.container {
    background-color: #121318;
    border: 1px solid #22252d;
    border-radius: 16px;
    padding: 32px;
    max-width: 750px;
    margin: 40px auto;
}
```

- `background-color` — slightly lighter than body so the card stands out
- `border` — `1px` thin line, `solid` style, dark gray color
- `border-radius` — rounds the corners
- `padding` — space **inside** the card (between border and content)
- `max-width` — card never grows wider than 750px
- `margin: 40px auto` — `40px` top/bottom gap, `auto` centers the card left/right

**Save and check.** You should see a dark rounded card.

---

## Step 3 — Put Image and Content Side by Side

Right now `.hero-image` and `.hero-content` are stacked vertically (on top of each other).
We want them side by side — image on the left, text on the right.

We use **Flexbox** on `.container`. Add `display: flex` and `gap`:

```css
.container {
    background-color: #121318;
    border: 1px solid #22252d;
    border-radius: 16px;
    padding: 32px;
    max-width: 750px;
    margin: 40px auto;
    display: flex;      /* ← makes children line up in a row */
    gap: 28px;          /* ← space between image and text */
}
```

- `display: flex` — the direct children (`.hero-image` and `.hero-content`) now sit side by side automatically
- `gap: 28px` — controls the space between them

**Save and check.** Image and text should be side by side now.

---

## Step 4 — Style the Profile Image

```css
.profile_image {
    width: 130px;
    height: 130px;
    border-radius: 12px;
    object-fit: cover;
}
```

- `width` / `height` — fixed size for the image
- `border-radius` — rounds the corners (try `50%` for a circle shape)
- `object-fit: cover` — crops the image to fit without stretching it

---

## Step 5 — Style the Name

```css
.title {
    font-size: 28px;
    color: #ffffff;
    margin-bottom: 4px;
}
```

- `font-size` — makes the name big
- `color` — white so it stands out from the gray text
- `margin-bottom` — adds a small gap below the name

---

## Step 6 — Style Subtitle, Location, Status

```css
.sub-title {
    font-size: 14px;
    color: #9ba3b0;
    margin-bottom: 8px;
}

.hero-location {
    font-style: normal;
    font-size: 14px;
    color: #9ba3b0;
}

.hero-status {
    font-size: 13px;
    color: #ff3366;
    margin-top: 4px;
}
```

- `.hero-location` needs `font-style: normal` because `<address>` tags are italic by default in browsers
- `.hero-status` uses a red/pink color so "Open to work" stands out

---

## Step 7 — Style the Interests Text

```css
.interests {
    font-size: 15px;
    line-height: 1.6;
    margin-top: 12px;
}
```

- `line-height: 1.6` — adds space between lines, making it easier to read

---

## Complete `css/style.css` — Copy This

```css
/* Page background */
body {
    background-color: #0b0c0e;
    color: #9ba3b0;
}

/* Card */
.container {
    background-color: #121318;
    border: 1px solid #22252d;
    border-radius: 16px;
    padding: 32px;
    max-width: 750px;
    margin: 40px auto;
    display: flex;
    gap: 28px;
}

/* Profile image */
.profile_image {
    width: 130px;
    height: 130px;
    border-radius: 12px;
    object-fit: cover;
}

/* Name */
.title {
    font-size: 28px;
    color: #ffffff;
    margin-bottom: 4px;
}

/* Subtitle */
.sub-title {
    font-size: 14px;
    color: #9ba3b0;
    margin-bottom: 8px;
}

/* Location */
.hero-location {
    font-style: normal;
    font-size: 14px;
    color: #9ba3b0;
}

/* Open to work */
.hero-status {
    font-size: 13px;
    color: #ff3366;
    margin-top: 4px;
}

/* About text */
.interests {
    font-size: 15px;
    line-height: 1.6;
    margin-top: 12px;
}
```

---

## Quick Reference

| Property | What it does |
|---|---|
| `background-color` | Background color of an element |
| `color` | Text color |
| `font-size` | Text size (px) |
| `font-style` | normal, italic |
| `padding` | Space **inside** the element |
| `margin` | Space **outside** the element |
| `border` | Line around the element |
| `border-radius` | Rounds the corners |
| `max-width` | Max width limit |
| `display: flex` | Puts children side by side |
| `gap` | Space between flex children |
| `line-height` | Space between text lines |
| `object-fit: cover` | Crops image without stretching |

---

## Adding an About Me Section (Outside the Flexbox)

The hero section uses `display: flex` to put the image and text side by side.
If you add new content **inside** `.container`, it will also try to sit in that same row.

To avoid that, you add a **new section below** `.container`, outside the flex layout entirely.

---

### Step 1 — Add the HTML

In your `index.html`, add a new `<section>` **after** the closing `</div>` of `.container` but still inside `<main>`:

```html
<main>

    <section class="hero">
        <div class="container">
            <!-- hero content here -->
        </div>
    </section>

    <!-- NEW: About Me section below the hero -->
    <section class="about">
        <h2 class="about-title">About Me</h2>
        <p class="about-text">
            I'm a Computer Science student passionate about building web applications.
            I love working with React, Node.js, and learning new technologies every day.
        </p>
    </section>

</main>
```

**Key point:** It is a sibling of `.hero`, not inside `.container`. So it is completely separate from the flexbox layout.

---

### Step 2 — Add the CSS

```css
.about {
    max-width: 650px;
    margin: 24px auto;
    padding: 32px;
    background-color: #121318;
    border: 1px solid #22252d;
    border-radius: 16px;
}

.about-title {
    font-size: 20px;
    color: #ffffff;
    margin: 0;
    margin-bottom: 12px;
}

.about-text {
    font-size: 15px;
    line-height: 1.7;
    margin: 0;
}
```

- `max-width: 650px` — same width as your hero card so they line up
- `margin: 24px auto` — `24px` gap above it, `auto` centers it horizontally
- The rest is the same card styling as `.container`

---

### Visual Structure

```
<main>
  <section class="hero">       ← flexbox (image + text side by side)
    <div class="container">
      <div class="hero-image">
      <div class="hero-content">
    </div>
  </section>

  <section class="about">      ← NEW, normal block, full width card below
  </section>
</main>
```

Because `<section>` is a **block element**, it automatically goes on its own line below — no extra CSS needed to break out of the flex layout. The flex only affects the children *inside* `.container`.
