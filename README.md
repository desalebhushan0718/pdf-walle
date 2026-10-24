# pdf-walle
Free browser-based PDF toolkit: merge, split, compress, convert, watermark and edit PDFs.
PDF Walle
Every PDF tool. One little Walle.
PDF Walle is a free online PDF toolkit that runs in your browser. Files are processed on the user's device and are never uploaded to a server. A full PDF editor is available as a paid feature (Rs 199 / $2) through Razorpay.
Features
Free tools
Merge PDFs
Split / extract pages
Remove pages
Rotate pages
Add page numbers
Watermark
Compress (choose how much to reduce, in %)
JPG to PDF and PDF to JPG
Paid: PDF Editor
Edit existing text (colour, size and a matching standard font are detected)
Add text, draw, highlight, boxes, circles and lines
Whiteout, insert images, draw a signature
Undo / redo, add or delete pages, zoom
Also included: light and dark mode, animated "file ready" card, Privacy Policy, Terms of Use and Refund Policy pages.
Tech
Plain HTML, CSS and JavaScript in a single index.html
pdf-lib, PDF.js and JSZip loaded from cdnjs
Payments: Razorpay Checkout, verified by a small Cloudflare Worker (worker/worker.js)
Email receipts: Resend (sent from the Worker)
Project structure
index.html            the whole website
worker/worker.js      payment backend (create order, verify payment, email receipt)
worker/wrangler.toml  Cloudflare Worker settings
Run locally
Open index.html in a browser. All free tools work offline-ish (libraries load from the internet).
Deploy the website
Push this repo to GitHub.
Create a project on Cloudflare Pages or Netlify and connect the repo. No build step; the output folder is the repo root.
Add your custom domain.
Connect payments (Razorpay)
Create a Razorpay account and finish KYC. Start in Test mode.
Create a Cloudflare Worker from worker/worker.js.
Set the secrets RZP_KEY_ID, RZP_KEY_SECRET and RESEND_API_KEY, and the variables in wrangler.toml (ALLOWED_ORIGIN, FROM_EMAIL, OWNER_EMAIL).
In index.html set const API='https://your-worker.workers.dev';
Until API is set, the PDF Editor offers a demo mode that adds a "pdf walle" watermark. Remove the demo before launching.
Before going live
Replace your-email@example.com in the Privacy, Terms and Refund sections with a real contact email.
Remove demo mode once Razorpay is connected.
Never commit secret keys. They belong only in Cloudflare secrets.
The editor runs in the browser, so a technical user could bypass the paywall. For strict protection, move the editor's save step to a server.
Known limits
Edited text uses standard fonts (Sans, Serif, Mono), not the exact original font.
Hindi and other non-Latin characters cannot be saved in edited text yet.
Compress turns pages into images, so text is no longer selectable.
PDF to Word/Excel/PowerPoint, OCR, protect/unlock and sign are planned and need a server.
This is a prototype and has not been fully tested in all browsers.
License
No license has been chosen yet. Add one (for example MIT) if you want others to reuse the code.