# Prompts Used - ProdeskiT Landing Page

This file lists the AI prompts I used to build and improve the ProdeskiT landing page (HTML, CSS and JavaScript), and what I learned from each step. I wrote it in simple words so a beginner can follow it.

**Live site:** https://prodesk-landing-page-gules.vercel.app

---

## Prompt 1: Make the website work on all devices (Responsive)

**What "responsive" means:** the website looks good on every screen size: phone, tablet and laptop.

**Prompt used:**

```
Make my landing page responsive for mobile, tablet and desktop using only CSS.
Write the mobile styles first, then use media queries for bigger screens.
Use CSS Grid for the cards and Flexbox for the navbar.
Add a hamburger menu for mobile.
Do not change my content or class names. Give me the full changed file.
```

**What I learned:**
- **Mobile-first:** write the CSS for small screens first, then add extra styles for bigger screens.
- **Media query:** a CSS rule that applies only above or below a certain screen width. Example:

```css
/* Works on every screen */
.card-grid { display: grid; grid-template-columns: 1fr; gap: 1.5rem; }

/* Only when the screen is 900px or wider: show 3 cards in a row */
@media (min-width: 900px) {
  .card-grid { grid-template-columns: repeat(3, 1fr); }
}
```

- **Viewport tag:** `<meta name="viewport" content="width=device-width, initial-scale=1.0">` is needed, otherwise phones show a tiny zoomed-out desktop page.
- **Images:** add `max-width: 100%; height: auto;` so images never go outside the screen.
- **Hamburger menu:** on small screens the links hide behind a menu button, so the navbar does not look crowded.

---

## Prompt 2: Make the website load faster (Performance)

**What "performance" means:** how quickly the page loads and shows content to the user.

**Prompt used:**

```
Improve the performance of my landing page. Preload the CSS and the main image,
lazy-load the images below the fold, use a modern image format, set width and height
on images, and load JavaScript without blocking the page.
Only change what is needed and explain what each change improves.
```

**What I learned (in simple words):**

| Technique | What it means | Why it helps |
|---|---|---|
| Preload | Tell the browser to download important files (CSS, main image) early | The first screen appears sooner |
| Main image: `eager` and `fetchpriority="high"` | Load the biggest top image first, never lazily | The main content shows quickly |
| Lazy loading (`loading="lazy"`) | Load an image only when the user scrolls near it | Less to download at the start |
| AVIF images | A newer image format with much smaller file size | Faster loading, especially on mobile data |
| `width` and `height` on images | Tell the browser the image size in advance | The page does not jump around while images load |
| `srcset` and `sizes` | Offer different image sizes for different screens | Phones download smaller images |
| Inline SVG icons | Put icons directly in the HTML instead of using an icon library | No extra downloads, and the icon color follows the text color |
| `defer` on scripts | Run JavaScript after the page is ready | Scripts do not block the page from showing |

**Small glossary:**
- **LCP (Largest Contentful Paint):** the time until the biggest thing on the first screen (like the hero image) appears.
- **CLS (Cumulative Layout Shift):** how much the page jumps around while loading. Lower is better.

---

## Prompt 3: Make the website easy to use (User-friendly)

**What "user-friendly" means:** everyone can use the website easily, including people who use a keyboard or a screen reader.

**Prompt used:**

```
Make my landing page more user-friendly and accessible. Use semantic HTML tags,
add ARIA attributes on the buttons, make it work with the keyboard, add a dark mode
toggle, and keep the text easy to read. Do not change the design or the content.
```

**What I learned:**
- **Semantic HTML:** use meaningful tags like `header`, `nav`, `main`, `section`, `article` and `footer` instead of only `div`. Screen readers and search engines understand the page better.
- **ARIA attributes:** small labels for assistive tools.
  - `aria-label` tells what a button does (example: "Toggle dark mode").
  - `aria-pressed` and `aria-expanded` tell if a button is on or off.
- **Keyboard support:** real `<button>` elements work with the Tab and Enter keys, so the theme toggle and the menu work without a mouse.
- **Decorative icons:** add `aria-hidden="true"` so screen readers skip them.
- **Dark mode:** the text must stay easy to read in both light and dark themes.
- **Headings:** use one `h1`, then `h2` and `h3` in order. This helps users and SEO.

---

## Summary

| Area | What was done |
|---|---|
| Responsive | Works on phone, tablet and desktop, with a hamburger menu on small screens |
| Performance | Preloaded CSS and main image, AVIF images, lazy loading, image sizes set, inline SVG icons |
| User-friendly | Semantic HTML, ARIA attributes, keyboard-friendly controls, dark mode toggle |

## Tools Used

- AI assistant for code suggestions and explanations
- Chrome DevTools (F12) to test different screen sizes
- Vercel for deployment