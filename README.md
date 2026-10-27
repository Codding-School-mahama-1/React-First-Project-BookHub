# React-First-Project-BookHub

React class project: students clone this repo, work in `bookhub/`, and push their changes.

## Getting started

```bash
git clone https://github.com/Codding-School-mahama-1/React-First-Project-BookHub.git
cd React-First-Project-BookHub/bookhub
npm install
npm run dev
```

## Project structure

```
React-First-Project-BookHub/
│
├── README.md                     # This file — overview and structure
│
├── bookhub/                      # ★ The React app — all your work goes here
│   ├── index.html                # Entry HTML, loaded by Vite
│   ├── package.json              # Dependencies + scripts (npm run dev/build/lint)
│   ├── package-lock.json         # Locked dependency versions — do not edit
│   ├── vite.config.js            # Vite + React plugin config
│   ├── eslint.config.js          # Linting rules
│   ├── .gitignore                # Keeps node_modules/ and dist/ out of git
│   ├── README.md                 # ★ Class rules — components, props, objects, reuse
│   │
│   ├── public/                   # Files served as-is at the site root
│   │   └── vite.svg
│   │
│   └── src/                      # ★ Source code you edit
│       ├── main.jsx              # App bootstrap — mounts <App /> to the DOM
│       ├── App.jsx               # Root component — split this into sections
│       ├── App.css               # Styles for App
│       ├── index.css             # Global styles / resets
│       ├── assets/               # Images and other imported assets
│       │   └── react.svg
│       ├── components/           # (create) One reusable component per file
│       │   ├── Navbar.jsx        # The navigation bar — never inline it in App
│       │   ├── Hero.jsx          # Hero / banner section at the top of the page
│       │   ├── Button.jsx        # The one button component everyone reuses
│       │   └── BookCard.jsx
│       ├── data/                 # (create) Book objects and data arrays
│       │   └── books.js
│       └── utils/                # (create) Shared helper functions
│           └── formatRating.js
│
├── book_covers/                  # Book cover images to use in the app
│   ├── atomic_habits_cover.png
│   ├── clean_code_cover.png
│   ├── design_patterns_cover.png
│   ├── dune_cover.png
│   ├── the_5am_club_cover.png
│   └── the_martian_cover.png
│
└── bookhub_output_images/        # UI mockups / design references (not used by the app)
```

Folders marked ★ matter most: your code lives in `bookhub/src/`, the rules live in `bookhub/README.md`.

### What each folder (and file) is for

| Folder / file | What it is for |
| ------------- | -------------- |
| `src/components/` | **Reusable UI pieces.** One component per file: `Navbar`, `Hero`, `Button`, `BookCard`, `Footer`… A component is a function that returns JSX, takes its data through props, and can be dropped anywhere on the page. If you ever write the same JSX twice, it belongs here. |
| `src/data/` | **Your objects and arrays.** The list of books lives here as an array of objects (`[{ id, title, author, rating, cover }]`). Components import it and render it — this keeps content separate from layout, so changing a title never means editing JSX. |
| `src/utils/` | **Helper functions that are not UI.** Formatting a rating (`4.5` → `4.5 ★`), sorting books, filtering a search, building a price string. Pure functions, no JSX, easy to test and reused by many components. |
| `src/assets/` | **Images and files that get bundled.** Logos, covers, icons you `import`. Vite fingerprints the filename, so the browser cache refreshes correctly. |
| `public/` | **Files served as-is at the site root.** Reference them by plain path (`/vite.svg`) with no import — good for `favicon` and images used directly in CSS. |
| `src/App.jsx` | **The root component.** It should mostly *compose*: render `<Navbar />`, `<Hero />`, `<BookList />`, `<Footer />`. Avoid business logic and long markup here. |
| `src/App.css` / `src/index.css` | **Styling.** `index.css` = global reset and base styles for the whole app; `App.css` = styles scoped to `App`. Component-specific styles can live next to their component (`Hero.css`). |
| `src/main.jsx` | **The entry point.** It finds `#root` in `index.html` and mounts `<App />`. You rarely edit it. |
| `index.html` | The single HTML page Vite serves; the React app renders inside `<div id="root">`. |

#### The hero section

The **hero** is the large banner at the top of the landing page — headline, tagline, maybe a search box or a `Get Started` button. It is a **component**, not markup pasted into `App.jsx`:

```jsx
// src/components/Hero.jsx
function Hero({ title, subtitle, actionLabel, onAction }) {
  return (
    <section className="hero">
      <h1>{title}</h1>
      <p>{subtitle}</p>
      <Button label={actionLabel} onClick={onAction} />
    </section>
  );
}

export default Hero;
```

```jsx
// src/App.jsx — only composes
<Hero
  title="Every book, one place"
  subtitle="Browse the BookHub library"
  actionLabel="Browse books"
  onAction={() => setView("all")}
/>
```

Note what it demonstrates: the text arrives as **props** (so the same hero could be reused), the button is the shared `Button` **component**, and the click handler is passed down from the parent.

### Where things go

| You want to…                       | Put it in                    |
| ---------------------------------- | ---------------------------- |
| Add or edit a component            | `bookhub/src/components/`    |
| Store book objects / data arrays   | `bookhub/src/data/`          |
| Add a shared helper function       | `bookhub/src/utils/`          |
| Build the hero / banner section    | `bookhub/src/components/Hero.jsx` |
| Change the navbar or a button      | `bookhub/src/components/`     |
| Change global styles               | `bookhub/src/index.css`      |
| Use a book cover in the app        | copy it into `bookhub/src/assets/` or `bookhub/public/` |

> `node_modules/` and `dist/` are created by npm/Vite and are ignored by git — never commit them.

## Class rules

Read **[`bookhub/README.md`](bookhub/README.md)** before you start. In short, every submission must:

1. Build the UI from **components** (one per file, PascalCase names) — including the **navbar**, the **hero section** and **every button**.
2. Pass data through **props** — no hardcoded content inside components.
3. Model records as **objects** and render collections with `.map()`.
4. **Reuse** anything that appears twice as its own component.
5. Pass `npm run build` and `npm run lint` before you push.
