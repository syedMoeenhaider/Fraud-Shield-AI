# 🛡️ FraudShield AI

**FraudShield AI** ek AI-powered fraud detection mobile app hai jo Pakistani banking users ko financial scams, phishing SMS, aur suspicious links se bachata hai. Yeh app **React Native (Expo)** se bana hai aur saath mein ek **Express API server** bhi hai jo OpenAI ke zariye real-time fraud analysis karta hai.

---

## ✨ Features

- 🔍 **Transaction Analysis** — Har transaction ko automatically scan karta hai aur suspicious activity (large amount, unknown device, foreign location) ke liye risk score deta hai
- 📩 **SMS Scanner** — Phishing keywords aur suspicious links ke liye incoming messages ko analyze karta hai
- 🔗 **Link Checker** — URLs ko real-time check karta hai — suspicious TLDs, URL shorteners, phishing keywords, aur raw IP addresses detect karta hai
- 🤖 **AI-Powered Analysis** — OpenAI GPT ke zariye SMS aur links ka deep analysis karta hai, Urdu aur English dono mein verdict deta hai
- 🔐 **Secure Vault** — Biometric authentication (Face ID / Fingerprint) se protected — cards, passwords, aur notes securely store karta hai
- 📊 **Security Score** — User ki overall security health ek 0–100 score mein dikhata hai
- 🔔 **Background Notifications** — Background mein suspicious activity hone par alert deta hai

---

## 🏗️ Project Structure

```
Fraud-Shield-AI/
├── artifacts/
│   ├── fraudshield/          # React Native (Expo) mobile app
│   │   ├── lib/
│   │   │   ├── data/         # API clients, storage, biometric, notifications
│   │   │   └── domain/       # Pure fraud detection logic (analyzers, URL extractor)
│   │   ├── constants/        # Theme colors
│   │   └── hooks/            # Custom React hooks
│   ├── api-server/           # Express 5 backend
│   │   └── src/
│   │       ├── routes/       # API routes (health, AI analyze)
│   │       └── lib/          # Logger, OpenAI client
│   └── mockup-sandbox/       # UI component preview sandbox
├── lib/
│   ├── api-spec/             # OpenAPI spec + Orval codegen config
│   ├── api-zod/              # Auto-generated Zod validation schemas
│   ├── api-client-react/     # Auto-generated React Query API hooks
│   └── db/                   # PostgreSQL schema (Drizzle ORM)
└── scripts/                  # Helper scripts
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Mobile App | React Native + Expo (SDK 54) |
| Navigation | Expo Router (file-based) |
| Backend | Express 5 + Node.js 24 |
| AI | OpenAI GPT (gpt-5-mini) |
| Database | PostgreSQL + Drizzle ORM |
| Validation | Zod v4 + drizzle-zod |
| API Codegen | Orval (OpenAPI → React Query hooks) |
| Auth | expo-local-authentication (Face ID / Fingerprint) |
| Storage | expo-secure-store + AsyncStorage |
| Package Manager | pnpm workspaces (monorepo) |
| Language | TypeScript 5.9 |

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** v24+
- **pnpm** v9+
- **PostgreSQL** database
- **OpenAI API Key**

### Installation

```bash
# Repository clone karein
git clone <your-repo-url>
cd Fraud-Shield-AI

# Dependencies install karein
pnpm install
```

### Environment Variables

`artifacts/api-server/` mein `.env` file banayein:

```env
OPENAI_API_KEY=your_openai_api_key_here
DATABASE_URL=postgresql://user:password@localhost:5432/fraudshield
PORT=3000
```

### Database Setup

```bash
# Schema push karein (development)
pnpm --filter @workspace/db run push
```

### Development

```bash
# API server start karein
pnpm --filter @workspace/api-server run dev

# Mobile app start karein (alag terminal mein)
pnpm --filter @workspace/fraudshield run dev
```

---

## 📋 Available Commands

```bash
# Poora project typecheck karein
pnpm run typecheck

# Poora project build karein
pnpm run build

# API hooks aur Zod schemas regenerate karein (OpenAPI spec se)
pnpm --filter @workspace/api-spec run codegen

# Database schema push karein (dev only)
pnpm --filter @workspace/db run push

# API server locally chalayein
pnpm --filter @workspace/api-server run dev
```

---

## 🔌 API Endpoints

### `POST /api/ai/analyze`

SMS ya URL ka AI-powered fraud analysis karta hai.

**Request Body:**
```json
{
  "kind": "sms",        // "sms" ya "link"
  "content": "...",     // Analyze karne wala text (max 2000 chars)
  "locale": "en"        // "en" (English) ya "ur" (Urdu)
}
```

**Response:**
```json
{
  "verdict": "danger",
  "riskScore": 85,
  "summary": "This message contains phishing indicators.",
  "reasons": ["Requests OTP", "Contains suspicious link"],
  "recommendation": "Do not click any links or share your OTP."
}
```

### `GET /api/health`

Server health check.

---

## 🧠 Fraud Detection Logic

App do tarah se fraud detect karta hai:

### 1. Rule-Based (Offline, Instant)
- **Transactions:** Amount thresholds, unknown devices, non-trusted locations, high-risk categories (Wire Transfer, Crypto) check karta hai
- **SMS:** Phishing keywords (`otp`, `verify`, `account blocked`, `lucky draw`, etc.) aur URLs scan karta hai
- **Links:** Suspicious TLDs (`.tk`, `.ml`, `.xyz`), URL shorteners, raw IP addresses, phishing hint words check karta hai

### 2. AI-Powered (via OpenAI)
- Deep contextual analysis for ambiguous cases
- Supports Urdu and English responses
- Returns structured JSON verdict with reasons and recommendations

---

## 🌍 Localization

App **English** aur **Urdu** dono languages support karta hai. AI analysis bhi user ki chosen language mein respond karta hai.

---

## 🔒 Security Features

- Biometric authentication (Face ID / Fingerprint / Device PIN)
- Encrypted secure storage for vault items
- Background fraud monitoring with push notifications
- Web fallback for browser-based demo

---

## 📱 Permissions (Android)

```
RECEIVE_SMS, READ_SMS        — SMS scanning ke liye
INTERNET                     — API calls ke liye
POST_NOTIFICATIONS           — Fraud alerts ke liye
FOREGROUND_SERVICE           — Background monitoring ke liye
RECEIVE_BOOT_COMPLETED       — Auto-start on boot ke liye
```

---

## 🤝 Contributing

1. Fork the repository
2. Feature branch banayein (`git checkout -b feature/amazing-feature`)
3. Changes commit karein (`git commit -m 'Add amazing feature'`)
4. Branch push karein (`git push origin feature/amazing-feature`)
5. Pull Request kholen

---

## 📄 License

MIT License — details ke liye [LICENSE](LICENSE) file dekhein.
