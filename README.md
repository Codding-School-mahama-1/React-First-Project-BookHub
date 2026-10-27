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

### Where things go

| You want to…                       | Put it in                    |
| ---------------------------------- | ---------------------------- |
| Add or edit a component            | `bookhub/src/components/`    |
| Store book objects / data arrays   | `bookhub/src/data/`          |
| Add a shared helper function       | `bookhub/src/utils/`         |
| Change global styles               | `bookhub/src/index.css`      |
| Use a book cover in the app        | copy it into `bookhub/src/assets/` or `bookhub/public/` |

> `node_modules/` and `dist/` are created by npm/Vite and are ignored by git — never commit them.

## Class rules

Read **[`bookhub/README.md`](bookhub/README.md)** before you start. In short, every submission must:

1. Build the UI from **components** (one per file, PascalCase names).
2. Pass data through **props** — no hardcoded content inside components.
3. Model records as **objects** and render collections with `.map()`.
4. **Reuse** anything that appears twice as its own component.
5. Pass `npm run build` and `npm run lint` before you push.
