# Voltix — Electronics & Solar Store

Professional responsive storefront starter built with React, Vite, Tailwind CSS v4 and Firebase. Design direction: modern clean-energy retail with soft sage backgrounds, forest-green accents, strong product photography and responsive layouts.

## Included
- Responsive home page, category tiles, featured products and benefits
- Shop catalogue with category filters, search and sorting
- Product detail pages, specifications and wishlist
- Cart with quantity controls and local persistence
- Firebase email/password sign-in and account creation
- Firestore user profile bootstrap and starter security rules
- Pakistan rupee price display and sample electronics/solar catalogue
- No admin panel

Checkout is intentionally a safe hand-off placeholder. No real payment is taken. Before production, implement trusted server-side order creation, inventory validation and payment gateway verification.

## Run locally
Requirements: Node.js 20.19+ or 22.12+ and npm.

    git clone https://github.com/junaid-developer-coder/E-commerce-website-.git
    cd E-commerce-website-
    npm install
    cp .env.example .env
    npm run dev

Open the local Vite URL, normally http://localhost:5173.

## Firebase setup
1. Create a Firebase project at https://console.firebase.google.com/.
2. Register a Web App in Project settings.
3. Enable Authentication → Sign-in method → Email/Password.
4. Create a Cloud Firestore database.
5. Copy the web config into .env using the variable names in .env.example.
6. Deploy firestore.rules using Firebase CLI: firebase login, firebase init firestore, firebase deploy --only firestore:rules.
7. Restart Vite after editing .env.

Firebase browser config is not a secret. Never put service-account JSON, private keys or Admin SDK credentials in Vite variables or client code. Access control belongs in Authentication and Security Rules.

## Data model
- users/{uid}: user profile (uid, name, email, createdAt)
- products/{productId}: optional public read-only catalogue
- orders/{orderId}: owner-scoped order documents

Sample catalogue data lives in src/data.js so the storefront works before Firestore is populated. For production, manage product catalogue and stock through a trusted server/admin workflow.

## Routes
- / — home
- /shop — catalogue, filters, search, sorting
- /product/:id — product details
- /cart — cart and checkout placeholder
- /wishlist — saved products
- /account — sign in, register and sign out

## Build and deploy
    npm run build
    npm run preview

Deploy dist/ to Firebase Hosting, Vercel, Netlify or another static host. Configure the VITE_FIREBASE_* variables in hosting settings. Configure SPA fallback/rewrite to index.html for deep links.

## Production checklist
- Add a trusted backend or Cloud Functions for order creation and payment verification.
- Calculate totals and validate stock server-side; never trust browser totals.
- Add password reset, email verification, App Check and abuse protection.
- Test Firestore rules with Firebase Emulator Suite.
- Replace sample imagery, prices, contact details and product claims with verified store data.
- Add privacy, terms, shipping, returns and warranty policies.
- Add tests, monitoring, accessibility checks and performance budgets.

## Documentation
See docs/CODING_GUIDE.md, docs/ARCHITECTURE.md and docs/FIREBASE_SECURITY.md.
