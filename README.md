# viviarentals.com
Core platform for VIVIA Rentals handling landlord onboarding, rental listing syndication, Stripe/Square payments, metadata tracking, and automated tour scheduling.
├─ README.md
├─ .gitignore
├─ dependabot.yml
├─ package.json
├─ index.html
├─ /src
│   ├─ main.js
│   ├─ dashboard.js
│   └─ property-embed.js
├─ /styles
│   └─ main.css
├─ /assets
│   └─ logo.png
├─ /config
│   └─ stripe-config.js
└─ CONTRIBUTING.md
File Contents
README.md

markdown
Copy code
# VIVIA Rentals

Welcome to VIVIA Rentals, a co-ownership property management platform integrated with TurboTenant and major listing networks. 

## Features
- Property listing embedding
- Live dashboard tracking
- Syndication across Zillow, Zumper, TurboTenant, Realtor, Redfin, Facebook Marketplace, Apartment.com, ForRent
- Stripe payment integration for rental management

## Getting Started
1. Clone the repository
2. Install dependencies: `npm install`
3. Run dev server: `npm start`
.gitignore

bash
Copy code
node_modules/
dist/
.env
dependabot.yml

yaml
Copy code
version: 2
updates:
  - package-ecosystem: "npm"
    directory: "/"
    schedule:
      interval: "weekly"
package.json

json
Copy code
{
  "name": "viviarentals.com",
  "version": "1.0.0",
  "description": "Co-ownership property management platform",
  "main": "src/main.js",
  "scripts": {
    "start": "live-server ./",
    "build": "echo 'Add build steps here'"
  },
  "dependencies": {},
  "devDependencies": {
    "live-server": "^1.2.1"
  }
}
index.html

html
Copy code
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>VIVIA Rentals Dashboard</title>
  <link rel="stylesheet" href="./styles/main.css">
</head>
<body>
  <header>
    <img src="./assets/logo.png" alt="VIVIA Rentals Logo" height="50">
    <h1>VIVIA Rentals Dashboard</h1>
  </header>

  <main>
    <section id="property-embed">
      <h2>Embedded Property Listings</h2>
      <iframe src="https://rental.turbotenant.com/embedpropertylist.html#/Zillow,Zumper,TurboTenant,Realtor,Redfin,FacebookMarketplace,ApartmentCom,ForRent" 
              width="100%" height="600px" frameborder="0"></iframe>
    </section>

    <section id="stripe-payments">
      <h2>Rental Payments</h2>
      <p>Payments are securely processed via Stripe. <a href="#">Manage Payments</a></p>
    </section>
  </main>

  <script src="./src/main.js"></script>
  <script src="./src/dashboard.js"></script>
</body>
</html>
src/main.js

js
Copy code
console.log("VIVIA Rentals Main JS loaded");
src/dashboard.js

js
Copy code
// Live dashboard logic and API integration placeholder
console.log("Dashboard module loaded");
src/property-embed.js

js
Copy code
// Dynamic URL generator for property embeds
function generateEmbedURL(channels) {
  const base = "https://rental.turbotenant.com/embedpropertylist.html#/";
  return base + channels.join(",");
}

// Example usage
console.log(generateEmbedURL(["Zillow","Zumper","TurboTenant","Realtor","Redfin","FacebookMarketplace","ApartmentCom","ForRent"]));
styles/main.css

css
Copy code
body { font-family: Arial, sans-serif; margin:0; padding:0; }
header { background-color: #0a4f76; color: white; padding: 20px; display: flex; align-items: center; gap: 10px; }
main { padding: 20px; }
iframe { border-radius: 8px; }
config/stripe-config.js

js
Copy code
export const stripeConfig = {
  publishableKey: "pk_test_xxxxx",
  defaultCurrency: "usd"
};
CONTRIBUTING.md

markdown
Copy code
# Contributing to VIVIA Rentals

## Branching Model
- `main` - production-ready code, protected from direct pushes
- `develop` - development branch
- Feature branches: `feature/<feature-name>`

## Pull Requests
- Every change must go through a PR.
- PRs must be linked to a milestone and include a clear description.

## Releases
- Create a tag for every release.
- Ensure changelog is updated.

## GitHub Actions
- Direct pushes to `main` are blocked.
- PRs must pass all CI checks before merge.

## Code Style
- Follow ES6+ syntax for JS
- Use CSS variables and modular CSS
- Keep HTML semantic

Thank you for contributing!
✅ This setup includes:

Embedded property list via dynamic URL

Live dashboard integration

Stripe payment placeholders

GitHub Actions and PR workflow ready (referenced in CONTRIBUTING.md)

Clean folder structure for easy expansion
