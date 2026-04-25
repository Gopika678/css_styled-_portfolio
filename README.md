# Gopika P — Styled Portfolio Website
### Week 2 Project: CSS Styling & Responsive Design

---

## 📌 Project Overview

This project extends the Week 1 HTML portfolio by adding a comprehensive external CSS stylesheet. The goal was to transform a plain HTML document into a visually polished, responsive website using CSS fundamentals — variables, selectors, Flexbox, Grid, animations, hover effects, and media queries.

**Design Direction:** Dark, editorial aesthetic with a deep navy palette, blue-violet accents, and editorial typography (Playfair Display + Outfit). Professional enough for a developer portfolio, distinctive enough to be memorable.

---

## 🚀 Setup Instructions

### Prerequisites
- Any modern web browser (Chrome, Firefox, Edge, Safari)
- [VS Code](https://code.visualstudio.com/) (recommended)
- [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) VS Code extension (optional but helpful)

### Steps

1. **Clone or download this repository**
   ```bash
   git clone https://github.com/yourusername/portfolio-css.git
   cd portfolio-css
   ```

2. **Open in VS Code**
   ```bash
   code .
   ```

3. **Launch in browser**
   - Right-click `index.html` → Open With → Browser
   - **Or** click "Go Live" with Live Server for auto-reload

4. **Add your images** (optional)
   ```
   images/
   ├── profile.jpg       → Replace avatar placeholder in hero
   ├── about.jpg         → Replace placeholder in about section
   └── screenshots/      → Add project screenshots
   ```
   Then uncomment the `<img>` tags in `index.html`.

5. **Customize the design**
   - Open `style.css` and edit the `:root` variables at the top
   - Change `--color-primary` to change the accent color throughout the entire site
   - Change font links in `index.html` `<head>` to swap fonts

---

## 📁 Code Structure

```
portfolio/
│
├── index.html              ← Semantic HTML5 markup (no inline styles)
├── style.css               ← All visual styling (external CSS)
├── README.md               ← This documentation
│
├── images/                 ← Photo assets
│   ├── profile.jpg         ← Profile photo (add yours here)
│   ├── about.jpg           ← About section image
│   └── screenshots/        ← Project screenshots
│       ├── project1.png
│       ├── project2.png
│       ├── project3.png
│       └── project4.png
│
└── screenshots/            ← Portfolio screenshots for submission
    ├── desktop-hero.png
    ├── desktop-skills.png
    ├── mobile-view.png
    └── contact-form.png
```

### style.css Table of Contents

| Section | Lines | Description |
|---------|-------|-------------|
| CSS Custom Properties | 1–60 | Design token variables |
| Reset & Base | 61–110 | Universal reset, body, defaults |
| Typography | 111–140 | Headings, paragraphs, links |
| Utilities | 141–180 | Container, section, eyebrow |
| Buttons | 181–240 | .btn variants and hover states |
| Navigation | 241–330 | Fixed navbar, links, hamburger |
| Hero | 331–460 | Full-viewport hero section |
| About | 461–540 | Two-column about layout |
| Skills | 541–630 | Grid of skill cards with bars |
| Projects | 631–730 | Project cards with overlays |
| Contact | 731–830 | Form and contact info |
| Footer | 831–870 | Footer layout |
| Animations | 871–910 | @keyframes definitions |
| Scroll Reveal | 911–930 | Intersection reveal classes |
| Media Queries | 931–1050 | Responsive breakpoints |

---

## 🎨 CSS Concepts Explained

### 1. CSS Custom Properties (Variables)
```css
:root {
  --color-primary: #4f8ef7;
  --font-body: 'Outfit', sans-serif;
  --space-lg: 1.5rem;
}
/* Used anywhere: */
.btn { background: var(--color-primary); }
```
**Why:** Changing one variable instantly updates the entire site's color scheme. No find-and-replace needed.

---

### 2. CSS Selectors (10+ types used)

| Selector Type | Example | Used For |
|--------------|---------|----------|
| Element | `body`, `h1`, `input` | Base element defaults |
| Class | `.btn`, `.skill-card` | Component styling |
| ID | `#home`, `#contact` | Section identification |
| Descendant | `.nav-links a` | Links inside nav only |
| Child | `.skill-card > h3` | Direct children |
| Pseudo-class | `:hover`, `:focus`, `:nth-child` | State-based styles |
| Pseudo-element | `::before`, `::after` | Decorative elements |
| Attribute | `input[type="email"]` | Specific attributes |
| Universal | `*` | CSS reset |
| Combined | `.skill-card:hover::before` | Chained selectors |

---

### 3. Hover Effects & Transitions

Every interactive element has a smooth hover effect:

```css
/* Button: lift + color change */
.btn-primary:hover {
  background: transparent;
  color: var(--color-primary);
  transform: translateY(-3px);
  box-shadow: 0 12px 40px rgba(79,142,247,0.18);
}

/* Card: lift + border glow */
.skill-card:hover {
  border-color: var(--color-primary-glow);
  transform: translateY(-6px);
}

/* Nav link: sliding underline */
.nav-links a::after {
  width: 0;
  transition: width 250ms ease;
}
.nav-links a:hover::after { width: 100%; }
```

**The `transition` property** smoothly animates CSS changes:
```css
transition: background 250ms ease, transform 250ms ease;
```

---

### 4. CSS Flexbox

Used for one-dimensional layouts (rows or columns):
```css
/* Navigation bar */
.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

/* Hero content row */
.hero {
  display: flex;
  align-items: center;
  gap: 2.5rem;
}

/* Skill tags */
.skill-tags {
  display: flex;
  flex-wrap: wrap;    /* Wraps to next line */
  gap: 0.25rem;
}
```

---

### 5. CSS Grid

Used for two-dimensional layouts:
```css
/* Two-column about section */
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1.3fr;
  gap: 6rem;
}

/* Skills — auto-responsive columns */
.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  /* auto-fit + minmax: creates as many columns as fit, 
     minimum 250px each, without any media queries */
}

/* Contact form — two inputs per row */
.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}
```

---

### 6. Animations

**`@keyframes`** — define animation steps:
```css
@keyframes float {
  0%, 100% { transform: translateY(0px);  }
  50%       { transform: translateY(-8px); }
}
```

**`animation`** property — applies them:
```css
.floating-badge {
  animation: float 3s ease-in-out infinite;
}
```

**CSS gradient text** — for the hero title accent:
```css
.hero-title-accent {
  background: linear-gradient(135deg, #4f8ef7, #a78bfa);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}
```

---

### 7. Responsive Design (Media Queries)

Mobile-first philosophy — styles are written for desktop, then overridden for smaller screens:

```css
/* Tablet (≤ 768px) */
@media (max-width: 768px) {
  .hero { flex-direction: column; }
  .about-grid { grid-template-columns: 1fr; }
  .projects-grid { grid-template-columns: 1fr; }
}

/* Mobile (≤ 480px) */
@media (max-width: 480px) {
  .hero-actions { flex-direction: column; }
  .floating-badge { display: none; }
}
```

**Breakpoints used:**
| Breakpoint | Target |
|-----------|--------|
| `max-width: 1024px` | Tablet landscape |
| `max-width: 768px` | Tablet portrait |
| `max-width: 640px` | Large phones |
| `max-width: 480px` | Small phones |

---

### 8. Custom Fonts (Google Fonts)

```html
<!-- Loaded in HTML <head> -->
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=Outfit:wght@300;400;500;600&display=swap" rel="stylesheet">
```

```css
/* Applied via CSS variables */
:root {
  --font-display: 'Playfair Display', Georgia, serif;
  --font-body: 'Outfit', system-ui, sans-serif;
}

h1, h2, h3 { font-family: var(--font-display); }
body        { font-family: var(--font-body); }
```

---

## 🖼️ Visual Documentation

To add screenshots to this README:

1. Open the site in Chrome
2. Press `F12` → toggle device toolbar for mobile view
3. Right-click the page → "Capture screenshot"
4. Save to `screenshots/` folder

Then add here:
```markdown
### Desktop View
![Desktop Hero](screenshots/desktop-hero.png)
![Desktop Skills](screenshots/desktop-skills.png)

### Mobile View
![Mobile View](screenshots/mobile-view.png)

### Interactive Elements
![Hover Effects](screenshots/hover-effects.png)
![Contact Form](screenshots/contact-form.png)
```

---

## 🔍 Design Decisions

| Decision | Reasoning |
|----------|-----------|
| Dark theme | Reduces eye strain; common in dev portfolios |
| Playfair Display | Adds editorial elegance to contrast tech subject |
| CSS variables system | Single source of truth for colors/spacing |
| Frosted glass navbar | Modern; keeps content visible while scrolling |
| Rotating gradient ring | Eye-catching hero element that uses pure CSS |
| `auto-fit` grid for skills | Responsive without a single media query |
| Overlay on project cards | Reveals action on hover — avoids clutter |

---

## ✅ Testing Evidence

### Device/Browser Testing

| Browser | Desktop | Tablet | Mobile |
|---------|---------|--------|--------|
| Chrome | ✅ | ✅ | ✅ |
| Firefox | ✅ | ✅ | ✅ |
| Safari | ✅ | ✅ | ✅ |
| Edge | ✅ | ✅ | ✅ |

### CSS Validation
- Validate at: [jigsaw.w3.org/css-validator](https://jigsaw.w3.org/css-validator/)
- Result: No errors

### Responsive Design Tests

| Screen Width | Layout | Nav | Hero |
|-------------|--------|-----|------|
| 1440px | ✅ 2-column | Horizontal links | Side by side |
| 1024px | ✅ Adjusted gaps | Horizontal links | Side by side |
| 768px | ✅ 1-column | Hamburger menu | Stacked |
| 480px | ✅ Optimized | Hamburger menu | Stacked |
| 375px | ✅ Full mobile | Hamburger menu | Stacked |

### Interactive Feature Tests

| Feature | Expected | Result |
|---------|----------|--------|
| Nav links hover | Underline slides in | ✅ Pass |
| Skill cards hover | Lift + top border reveals | ✅ Pass |
| Project cards hover | Image scales, overlay appears | ✅ Pass |
| Buttons hover | Color invert + lift | ✅ Pass |
| Form focus | Blue border + glow ring | ✅ Pass |
| Form error | Red border + error message | ✅ Pass |
| Form success | Green success message | ✅ Pass |
| Hamburger menu | Opens/closes on click | ✅ Pass |
| Scroll reveal | Elements fade in on scroll | ✅ Pass |

---

## 💡 Resources Used

- [MDN CSS Reference](https://developer.mozilla.org/en-US/docs/Web/CSS) — Properties reference
- [CSS Tricks Flexbox Guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) — Flexbox reference
- [CSS Tricks Grid Guide](https://css-tricks.com/snippets/css/complete-guide-grid/) — Grid reference
- [W3C CSS Validator](https://jigsaw.w3.org/css-validator/) — Validation
- [Google Fonts](https://fonts.google.com/) — Playfair Display & Outfit typefaces
- [Chrome DevTools](https://developer.chrome.com/docs/devtools/) — Debugging & responsive testing

---

## 📬 Contact

**Gopika P**
- Email: gopika@example.com
- GitHub: [github.com/gopika](https://github.com)
- Location: Palakkad, Kerala, India

---

*Week 2 — Styled Portfolio | Built with HTML5 & CSS3 — Zero frameworks, pure craft.*
