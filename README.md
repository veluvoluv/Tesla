Repair vs. Lease vs. Buy — 3-Year EV Cost Calculator
A self-contained, single-file calculator that compares the true 3-year cost of ownership across three options for a 2017 Tesla Model X owner with a dead HV battery:

Repair the Model X (battery replacement) and keep driving it
Lease a new Tesla Model Y
Buy (finance) a new Tesla Model Y
What it does
Every slider updates the totals instantly — no backend, no dependencies, no build step. The tool factors in costs that are easy to overlook when making this decision:

Existing perks: Free lifetime Supercharging, included FSD, and included WiFi on the Model X — these are paid subscriptions ($99/mo + $10/mo) on a new Model Y
Supercharging savings: Calculates the dollar value of free Supercharging based on your annual mileage and current Supercharger rates
Repair risk: A yearly set-aside for likely additional repairs on a 9-year-old vehicle (falcon wing doors, air suspension, MCU1)
Buy equity: For the finance option, computes remaining loan balance at the 3-year mark and nets it against estimated resale value
Lease mileage limits: Displays the 10,000 mi/yr cap and $0.25/mi overage fee as a reference

The cheapest option gets a green highlight and the verdict bar explains how much you save versus the next-best alternative.
Hosting
It's a single HTML file with no external dependencies. Host it anywhere that serves static files.

GitHub Pages

# create a repo and push the file

mkdir ev-calculator && cd ev-calculator

cp /path/to/repair-vs-lease-calculator.html index.html

git init && git add . && git commit -m "initial commit"

gh repo create ev-calculator --public --source=. --push

# enable Pages in repo Settings → Pages → Deploy from branch (main)

# site will be live at https://<username>.github.io/ev-calculator/

Netlify (drag and drop)

Go to app.netlify.com/drop, rename the file to index.html, and drag the folder onto the page. You'll get a live URL in seconds.

Vercel

npm i -g vercel

mv repair-vs-lease-calculator.html index.html

vercel --prod

Any static host or your own server

Rename to index.html and drop it into your web root. Apache, Nginx, Caddy, S3 + CloudFront, Firebase Hosting — anything that serves HTML works. No server-side processing needed.
Customization
Everything is self-contained in the single HTML file. The three main areas you might want to change:

Default values — Search for value="..." on the <input type="range"> elements in the HTML. Each slider's min, max, step, and default value are set inline.

Adding or removing cost line items — The calc() function in the <script> block computes all totals. Each cost component is a simple variable (e.g., leaseFsdT = lfsd * months). Add a new slider in the HTML, read it in calc(), and include it in the net total.

Styling — All CSS is in the <style> block at the top. The calculator supports light and dark mode automatically via prefers-color-scheme. Color variables are defined in :root and overridden in the dark media query.
Browser support
Works in all modern browsers (Chrome, Firefox, Safari, Edge). No JavaScript frameworks, no transpilation, no polyfills. Uses only vanilla JS, CSS custom properties, and standard HTML range inputs.
License
MIT — use it however you like.

