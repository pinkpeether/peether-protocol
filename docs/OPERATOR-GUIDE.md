---

### File: `OPERATOR-GUIDE.md`

```markdown
# Peether Operator Guide

## What You're Getting

Peether is a **modular settlement protocol** for ride-hailing networks. You deploy it, customize it,
operate it independently.

## Architecture

**Layer 1 (Global):** PTDT smart contracts on BSC
- Immutable
- Used by all operators worldwide
- No fees to deploy or use

**Layer 2 (Your Instance):** Peether Settlement API
- Deploy to your servers
- Customize for your country
- Connect to your payment processors

**Layer 3 (Your Business):** Pink Taxi (Your Country)
- Your app
- Your drivers
- Your riders


## Getting Started

### 1. Clone the Repository
```bash

git clone https://github.com/pinkpeether/peether-protocol.git
cd peether-protocol


2. Install Dependencies
```bash

npm install


3. Configure Environment
```bash

cp .env.example .env


Edit .env with your details:

```text

OPERATOR_ID=pink-taxi-your-country
CURRENCY_CODE=PKR
PTDT_TOKEN_ADDRESS=0x66c6Fc5E7F99272134a52DF9E88D94eD83E89278
SUPABASE_URL=your-supabase-url
SUPABASE_ANON_KEY=your-anon-key


4. Set Up Database
```bash

npm run migrate

This creates:
• quotes table
• payments table
• payouts table


5. Start Development Server
```bash

npm run dev
API runs on http://localhost:3000


6. Test with Postman
Import postman/Peether-Settlement-API.postman_collection.json and test all endpoints.


Integration with Your App
Quote Flow
```text

1. User enters ride amount (e.g., 1000 PKR)
2. Your app calls: POST /api/peether/quote
3. Peether returns: Quote ID + PTDT equivalent + price
4. Your app shows: "Driver earns 23.42 PTDT (~6750 PKR)"


Payment Flow
```text

1. Rider confirms ride
2. Your app calls: POST /api/peether/pay
3. Peether executes: PTDT transfer to driver
4. Your app confirms: Payment successful


Payout Flow

```text
1. Driver requests withdrawal
2. Your app calls: POST /api/peether/payout
3. Peether processes: Converts PTDT → PKR (via JazzCash)
4. Driver receives: Fiat in 24 hours

Customization

Change Fiat Processor
Edit config.ts:

typescript

FIAT_ADAPTER: 'jazzCash' // → 'flutterwave', 'pix', or custom


Adjust Fees
typescript

PROTOCOL_FEE_BPS: 50       // 0.5% protocol fee
OPERATOR_MARGIN_PERCENT: 2 // 2% operator margin


Add Custom KYC
Create src/adapters/kyc/your-country.ts:

typescript
export async function verifyKYC(wallet: string, data: any) {
  // Your KYC logic
}


Compliance
Each operator is responsible for local regulation, for example:
- Nigeria: Comply with SEC rules
- Brazil: Comply with CVM rules
- Pakistan: Comply with PVARA rules

Peether doesn't enforce compliance—you do.

Support:
GitHub Issues: Report bugs
Email: support@ptdt.taxi
Discord: Join the community


### File: `tsconfig.json`

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "commonjs",
    "lib": ["ES2020"],
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "resolveJsonModule": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules"]
}


File: .gitignore
text

node_modules/
dist/
.env
.env.local
.env.*.local
*.log
npm-debug.log*
.DS_Store
.idea/
.vscode/
*.swp
*.swo


Setup Instructions

Step 1: Clone & Install
```bash

git clone https://github.com/pinkpeether/peether-protocol.git
cd peether-protocol
npm install


Step 2: Configure
```bash

cp .env.example .env
# Edit .env with your Supabase credentials


Step 3: Migrate Database
```bash

npm run migrate


Step 4: Run Dev Server
```bash

npm run dev


Step 5: Test
```text

Import Postman collection
Test all 3 endpoints
Verify responses


Step 6: Deploy
```bash

npm run build
git push to your repo
FastComet auto-deploys
