# Architecture

Vite mounts React in src/main.jsx and wraps the app with BrowserRouter and StoreProvider. App.jsx defines routes and shared navigation/footer.

Pages are implemented as route-level components in App.jsx for this compact starter. Shared product cards and product records use a common data source. StoreProvider owns cart, wishlist and Firebase auth state. Firebase initialization is isolated in src/firebase.js.

Cart and wishlist persist in localStorage. Authentication is observed through Firebase onAuthStateChanged. Firestore stores a basic profile at users/{uid}. The local product catalogue keeps the storefront usable before a database catalogue is configured.

Extension points: move catalogue queries into a product service, add server-backed order creation, implement order history, add loading/error boundaries and split pages into dedicated modules as the codebase grows.
