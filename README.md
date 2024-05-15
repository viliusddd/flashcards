[![GH Pages Deployment & tests ](https://github.com/viliusddd/mindflip/actions/workflows/deploy.yaml/badge.svg)](https://github.com/viliusddd/mindflip/actions/workflows/deploy.yaml)

# MindFlip

<img align=right width='200px' src="./screenshots/decks.png">

Streamline your learning with flashcards app. Effortlessly create, organize, and study with simple, distraction-free cards. Perfect for focusing on the essentials and boosting your knowledge efficiently.

## Quick Start

1. Create a new deck going to `create a deck`, fill all fields and press `Create Deck`
2. In the newly opened page - press `Import` and import one of the `.CSV` files from the project `examples` directory. It will populate current deck with data.
3. To start reviewing flashcards - go back to `decks` and press `Review` on your deck.
> Optionally check-out `screenshots/` on repo for quick preview of the app.

### Used technologies
[<img src="https://img.shields.io/badge/Vue.js-%2335495e.svg?style=flat&logo=vuedotjs">](https://vuejs.org/)
[<img src="https://shields.io/badge/TypeScript-3178C6?logo=TypeScript&logoColor=FFF&style=flat">](https://www.typescriptlang.org/)
[<img src="https://img.shields.io/badge/-Vite-646CFF?style=flat&logo=vite&logoColor=white">](https://vitejs.dev/)
[<img src="https://img.shields.io/badge/-Vitest-6E9F18?style=flat&logo=vitest&logoColor=white">](https://vitest.dev/)
[<img src="https://img.shields.io/badge/-Playwright-2EAD33?style=flat&logo=playwright&logoColor=white">](https://playwright.dev/)

## Project Setup

```sh
npm install
```


### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Type-Check, Compile and Minify for Production

```sh
npm run build
```

### Run Unit Tests with [Vitest](https://vitest.dev/)

```sh
npm run test:unit
```

### Run End-to-End Tests with [Playwright](https://playwright.dev)

```sh
# Install browsers for the first run
npx playwright install

# When testing on CI, must build the project first
npm run build

# Runs the end-to-end tests
npm run test:e2e
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```
