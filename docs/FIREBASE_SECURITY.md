# Firebase Security

Firebase web config is public project identification, not a private credential. Do not commit service-account files, private keys or Admin SDK secrets.

Firebase Authentication handles password verification and token/session lifecycle. The client subscribes to onAuthStateChanged and does not persist raw passwords or manually manage ID tokens.

The included rules restrict user documents to the matching authenticated UID, permit public read-only product documents, and scope order creation/read to the owner. These are starter rules: validate fields and types, enforce immutable ownership, validate state transitions on trusted server code and test with Firebase Emulator Suite.

Never trust client-calculated totals or client-side payment status. Use a payment provider and verify payment webhooks on a trusted backend. Do not store card details in Firestore.
