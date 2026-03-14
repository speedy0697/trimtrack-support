# ✂️ TrimTrack — Haircut Tracker & AI Stylist

> Track every haircut, monitor your grooming spending, and preview new hairstyles with AI — all in one app.

## Why This Exists

Remembering what you told your barber, tracking how much you spend on haircuts, and exploring new looks shouldn't require a spreadsheet. TrimTrack is a modern mobile app that turns your grooming routine into organized, visual data you can act on.

## ✨ Features

### 💇‍♂️ Haircut Journaling
- Log detailed entries with style name, price, date, and personal notes
- Attach up to 4 photos per entry — show your barber exactly what you want
- 5-star rating system to remember your best (and worst) cuts
- Filter and sort your full haircut history

### 💈 Barber & Barbershop Tracking
- Track which barbers and barbershops you visit
- Build a personal directory of your go-to spots
- Associate each haircut with a barber and location

### 🤖 AI Stylist
- Upload a selfie and preview yourself with a new hairstyle
- Choose from preset styles or describe your own custom look
- Powered by Google Gemini via a secure server-side Edge Function
- Save AI-generated previews to your gallery
- Rate-limited by tier (daily, weekly, monthly quotas)

### 📊 Spending Analytics
- Interactive charts showing spending trends over time
- Projected spending based on your haircut frequency
- Tap data points to see detailed breakdowns (date, amount, cumulative vs. projected)
- Track total spend, average cost per cut, and days since last visit

### ☁️ Cloud Sync & Offline Support
- Seamless data sync across devices via Supabase
- Offline-first architecture — log entries without connectivity
- Automatic data migration from local storage to cloud on sign-in

### 🔐 Security & Privacy
- Google OAuth sign-in
- All AI processing runs server-side — no API keys exposed to the client
- Row Level Security (RLS) on all database tables
- Input validation and sanitization on all forms
- Private photo storage with scoped access

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Framework** | [React Native](https://reactnative.dev/) via [Expo](https://expo.dev/) (SDK 54) |
| **Routing** | [Expo Router](https://docs.expo.dev/router/introduction/) (file-based) |
| **Backend** | [Supabase](https://supabase.com/) (PostgreSQL, Auth, Edge Functions, Storage) |
| **AI** | [Google Gemini](https://ai.google.dev/) via Supabase Edge Function |
| **UI** | Custom themed components, Dark/Light mode, `react-native-reanimated`, `expo-linear-gradient` |
| **Charts** | `react-native-chart-kit` with `react-native-svg` |

## 🚀 Getting Started

### Prerequisites

- Node.js v18+
- npm
- Expo CLI (`npm install -g expo-cli`)
- Expo Go app on your device (or iOS Simulator / Android Emulator)
- A [Supabase](https://supabase.com/) project
- A [Google Gemini API key](https://ai.google.dev/)

### 1. Clone & Install

```bash
git clone https://github.com/speedy0697/trimtrack.git
cd trimtrack
npm install
```

### 2. Environment Variables

Create a `.env` file in the project root:

```env
# Supabase
EXPO_PUBLIC_SUPABASE_URL=your_supabase_project_url
EXPO_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key

# Google OAuth (for Google Sign-In)
EXPO_PUBLIC_GOOGLE_WEB_CLIENT_ID=your_google_web_client_id
```

> **Note:** The Gemini API key is stored as a Supabase Edge Function secret and is **never** exposed to the client. Set it via:
> ```bash
> supabase secrets set GEMINI_API_KEY=your_key
> ```

### 3. Database Setup

Run the SQL migration scripts in your Supabase SQL editor, in order:

1. `supabase/migrations/001_initial_schema.sql` — Core tables (`profiles`, `haircuts`, `barbershops`, `barbers`, `haircut_photos`), RLS policies, and auto-profile trigger
2. `supabase/migrations/002_add_generation_limits.sql` — AI generation rate limiting and subscription tiers
3. `supabase/migrations/003_add_generation_history.sql` — AI generation history tracking

### 4. Run the App

```bash
npx expo start --clear
```

- Press `i` for iOS Simulator
- Press `a` for Android Emulator
- Scan the QR code with Expo Go on your device

## 📁 Project Structure

```
src/
├── app/                  # Expo Router screens
│   ├── (tabs)/           # Tab navigation (Home, Add, AI Stylist, Analytics, Settings)
│   ├── auth.tsx          # Authentication screen
│   ├── edit/             # Edit haircut flow
│   └── ai-history.tsx    # AI generation history
├── components/           # Reusable UI components
│   ├── EntryForm.tsx     # Multi-step haircut entry form
│   ├── HaircutCard.tsx   # Haircut list item
│   ├── HomeHeader.tsx    # Hero card with days-since-last-cut
│   ├── AIGenerationCard  # AI result display
│   ├── FilterModal.tsx   # Haircut filtering
│   ├── StarRating.tsx    # 5-star rating component
│   ├── Toast.tsx         # Toast notifications
│   ├── ErrorBoundary.tsx # Crash-safe error handling
│   └── LoadingSpinner.tsx
├── constants/            # Theme colors and typography
├── contexts/             # React Context (AuthContext)
├── hooks/                # Custom hooks
├── lib/                  # Supabase client initialization
├── services/             # API layers
│   ├── aiService.ts      # AI Stylist (Gemini via Edge Function)
│   └── database.ts       # Supabase CRUD operations
├── types/                # TypeScript type definitions
└── utils/                # Helpers (storage, validation, logger)
```

## 📄 License

This project is proprietary.
