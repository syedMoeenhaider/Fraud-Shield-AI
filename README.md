# 🛡️ FraudShield AI

> AI-Powered Fraud Detection Mobile App — Protecting Pakistani banking users from financial scams, phishing SMS, and suspicious links.

---

## 🖼️ App Screenshots

| Home Screen | SMS Scanner | Link Checker |
|:---:|:---:|:---:|
| ![Home](screenshots/home_screen.jpg) | ![SMS](screenshots/sms_scanner.jpg) | ![Link](screenshots/link_checker.jpg) |

| Secure Vault | Emergency Freeze | Account Frozen | Settings |
|:---:|:---:|:---:|:---:|
| ![Vault](screenshots/secure_vault.jpg) | ![Freeze](screenshots/emergency_freeze.jpg) | ![Frozen](screenshots/account_frozen.jpg) | ![Settings](screenshots/settings.jpg) |

---

## 🎬 Demo Video

[![Watch Demo Video](https://img.shields.io/badge/▶️_Watch_Demo-Google_Drive-blue?style=for-the-badge&logo=google-drive)](https://drive.google.com/file/d/1BLFkettfymQqYb3LBAvJUdkhsJBN0kAT/view?usp=drivesdk)

---

## 📲 Download APK

[![Download APK](https://img.shields.io/badge/⬇️_Download_APK-FraudShieldAI-green?style=for-the-badge&logo=android)](apk/FraudShieldAI.apk)

> **Installation:** Download APK → Open file → Allow unknown sources → Install → Run

---

## ✨ Features

- 🏠 **Home Dashboard** — Security score (0–100), alerts, activity overview, and quick action buttons
- 📩 **SMS Scanner** — AI-powered phishing detection, classifies messages as Safe, Suspicious, or Dangerous
- 🔗 **Link Checker** — Paste any URL to instantly detect phishing, malware, and scam sites
- 🔐 **Secure Vault** — Biometric-protected storage for Bank PIN, ATM Card, Email Password, and Recovery Codes
- 🚨 **Emergency Freeze** — Instantly block all financial activity if fraud is suspected or card is lost/stolen
- ⚙️ **Settings** — SMS Monitoring, Auto-Scan Links, Fraud Alerts, Biometric Lock, Dark Mode, Language (EN/اردو)

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
| Auth | expo-local-authentication (Face ID / Fingerprint) |
| Storage | expo-secure-store + AsyncStorage |
| Package Manager | pnpm workspaces (monorepo) |
| Language | TypeScript 5.9 |

---

## 🏗️ Project Structure

```
Fraud-Shield-AI/
├── app/                          ← Complete source code
│   ├── artifacts/
│   │   ├── fraudshield/          ← React Native (Expo) mobile app
│   │   └── api-server/           ← Express 5 backend
│   └── lib/                      ← Shared libraries
├── screenshots/                  ← App screenshots
├── apk/
│   └── FraudShieldAI.apk         ← Android APK file
├── docs/
│   └── user_manual.pdf           ← User Manual
├── README.md
└── LICENSE
```

---

## 🚀 How to Install APK

1. Download `FraudShieldAI.apk` from the `apk/` folder above
2. Open the APK file on your Android phone
3. Tap **"Allow from this source"** if prompted
4. Tap **"Install"** and wait for installation
5. Open **FraudShield AI** from your home screen

---

## 🧠 Fraud Detection Logic

The app uses two layers of fraud detection:

### 1. Rule-Based (Offline, Instant)
- **SMS:** Scans for phishing keywords (`otp`, `verify`, `account blocked`, `lucky draw`, etc.)
- **Links:** Detects suspicious TLDs (`.tk`, `.ml`, `.xyz`), URL shorteners, raw IP addresses

### 2. AI-Powered (via OpenAI)
- Deep contextual analysis for complex cases
- Supports **English** and **Urdu** responses
- Returns verdict with specific reasons and recommendations

---

## 🔒 Security Features

- Biometric authentication (Face ID / Fingerprint / Device PIN)
- Encrypted secure storage for vault items
- Emergency account freeze with one tap
- Background fraud monitoring with push notifications
- Auto-scan incoming SMS and clipboard URLs

---

## 📱 Android Permissions

| Permission | Purpose |
|---|---|
| `RECEIVE_SMS, READ_SMS` | For SMS scanning |
| `INTERNET` | For AI-powered analysis |
| `POST_NOTIFICATIONS` | For fraud alerts |
| `FOREGROUND_SERVICE` | For background monitoring |
| `RECEIVE_BOOT_COMPLETED` | For auto-start on device boot |

---

## 🔌 API Endpoints

### `POST /api/ai/analyze`
```json
Request:
{
  "kind": "sms",
  "content": "Your OTP is 1234, click here to verify",
  "locale": "en"
}

Response:
{
  "verdict": "danger",
  "riskScore": 85,
  "summary": "This message contains phishing indicators.",
  "reasons": ["Requests OTP", "Contains suspicious link"],
  "recommendation": "Do not click any links or share your OTP."
}
```

### `GET /api/health`
Server health check endpoint.

---

## 📄 Documentation

- 📘 [User Manual](docs/user_manual.pdf)
- 📜 [License](LICENSE)

---

## 🔮 Future Enhancements

- Add more fraud detection patterns
- Improve UI design
- Add admin panel
- Add database reports
- Multi-language support expansion

---

## 👨‍💻 Developed By

**Student Name:** Syed Moeen Haider
**GitHub:** [syedMoeenhaider](https://github.com/syedMoeenhaider)

---

## 📄 License

MIT License — see the [LICENSE](LICENSE) file for details.

---

<div align="center">
  <b>🛡️ FraudShield AI — Protecting Your Financial Future</b>
</div>
