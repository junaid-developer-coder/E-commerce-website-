# Coding Guide

## Local workflow
Install Node.js 20.19+ or 22.12+, then run npm install, cp .env.example .env, npm run dev. Run npm run build before deploying.

## Structure
- src/App.jsx: routes, page components and shared layout
- src/store.jsx: cart, wishlist, auth state and actions
- src/firebase.js: Firebase initialization
- src/data.js: starter product catalogue and categories
- src/style.css: design system and responsive styling
- firestore.rules: starter Firestore access rules

## Add a product
Add an object to the products array in src/data.js. Each item needs a unique id, name, category, price, image, description, rating, reviews and specs. Product cards, details, cart and wishlist use the same object.

## Add a category
Add the category string to the categories array and use the exact same string in product objects.

## State and persistence
Cart and wishlist are stored in browser localStorage. This is device-local demo persistence, not cross-device account sync. For production, sync user-owned records under users/{uid} and secure them with Firestore rules.

## Authentication flow
The account form calls login or register from the shared store. Firebase Authentication performs credential verification and session management. onAuthStateChanged restores the current user. A basic profile document is created at users/{uid}. Passwords and ID tokens are not manually written to localStorage by this app.

## Styling
Tailwind v4 is enabled with the Vite plugin. The bespoke Voltix layout and breakpoints live in src/style.css. Keep the green palette, spacing and typography consistent.

## Quality checklist
- npm run build succeeds
- Test mobile, tablet and desktop widths
- Test empty cart, wishlist and search states
- Test Firebase auth with a configured project
- Validate rules in Firebase Emulator Suite
- Never expose service-account credentials
- Connect and verify payment processing on a trusted server before launch
