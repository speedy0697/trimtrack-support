# TrimTrack — Support & Privacy

> Track every haircut, monitor your grooming spending, and preview new hairstyles with AI.

## About TrimTrack

TrimTrack is a mobile app that helps you keep a detailed history of your haircuts — complete with photos, barber info, spending analytics, and an AI-powered hairstyle previewer.

### Features

* **Haircut Journaling** — Log every cut with photos, price, style, barber, barbershop, rating, and notes
* **AI Stylist** — Upload a selfie and preview new hairstyles before committing
* **Spending Analytics** — Interactive charts and projected spending trends
* **Cloud Sync** — Your data syncs across devices and works offline
* **Secure Authentication** — Sign in with Google, Apple, or email/password

---

## Frequently Asked Questions

**Is TrimTrack free?** Yes! TrimTrack is free to download and use. A Pro subscription unlocks higher AI Stylist generation limits.

**What data do you collect?** Only what you provide: your account email (from Google, Apple, or email sign-up), haircut entries, and uploaded photos. See the Privacy Policy below for full details.

**Can I delete my account and data?** Yes. Go to **Settings → Delete Account** to permanently remove your account and all associated data.

**What devices are supported?** TrimTrack is available on iOS. Android support is planned for a future release.

**Does the AI Stylist store my photos?** Photos you upload for AI styling are processed securely via a server-side function and stored in your private account. They are never shared or made public.

**How do subscriptions work?** TrimTrack Pro is available as an in-app purchase managed through the App Store. You can manage or cancel your subscription at any time via your Apple ID settings.

---

## Privacy Policy

**Last updated:** March 16, 2026

### What We Collect

| Data | Purpose | Storage |
|------|---------|---------|
| Account email and display name | Authentication and account identification | Supabase (encrypted) |
| Haircut entries | Core app functionality (dates, prices, styles, notes, ratings, duration) | Supabase (encrypted) |
| Photos | Haircut journaling and AI Stylist previews | Supabase Storage (private buckets, signed URLs) |
| AI Stylist prompts and results | Hairstyle preview generation and history | Supabase (encrypted) |
| Subscription status | Manage Pro tier access and AI generation limits | RevenueCat and Supabase |

### Device Permissions

TrimTrack may request the following device permissions:

* **Camera** — To take photos for haircut entries or AI Stylist
* **Photo Library** — To select existing photos for haircut entries or AI Stylist
* **Notifications** — To notify you when an AI generation completes (local notifications only; no remote push)

These permissions are requested only when needed and can be revoked at any time in your device settings.

### Third-Party Services

TrimTrack uses the following third-party services to operate:

| Service | Purpose | Data Shared |
|---------|---------|-------------|
| **Supabase** | Database, authentication, and file storage | Account info, haircut data, photos |
| **RevenueCat** | Subscription and in-app purchase management | User ID, entitlement/subscription status |
| **Google Gemini** (via server-side function) | AI hairstyle generation | Uploaded photo and style description (processed server-side; API key never exposed to your device) |
| **Apple Sign-In / Google OAuth** | Authentication | Email and name (per provider's terms) |

### What We Don't Do

* We do **not** sell your data to third parties
* We do **not** share your photos or personal information
* We do **not** serve advertisements
* We do **not** track your location
* We do **not** collect analytics or usage tracking data

### Data Security

* All data is transmitted over HTTPS
* Photos are stored in **private** storage buckets accessible only to your account via time-limited signed URLs
* AI processing is handled via secure server-side functions — no API keys are exposed to your device
* Database access is protected by Row Level Security (each user can only access their own data)
* Authentication sessions are stored securely on-device and automatically refreshed

### Data Retention

Your data is retained as long as your account exists. When you delete your account via **Settings → Delete Account**, all associated data — including your profile, haircut entries, photos, and AI generation history — is permanently removed from our servers.

### Your Rights

You have the right to:

* **Access** your data at any time through the app
* **Delete** your account and all associated data via **Settings → Delete Account**

### Children's Privacy

TrimTrack is not intended for children under 13. We do not knowingly collect data from children under 13.

### Changes to This Policy

We may update this Privacy Policy from time to time. Changes will be reflected on this page with an updated date.

### Contact

For questions, concerns, or data requests, contact us at:

**trimtrack@icloud.com**

---

## Contact & Support

Having issues with TrimTrack? Reach out:

* Email: **trimtrack@icloud.com**

We typically respond within 48 hours.
