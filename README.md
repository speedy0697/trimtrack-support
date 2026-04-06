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

**What data do you collect?** Your account email, haircut entries, uploaded photos, and anonymized usage analytics. See the Privacy Policy below for full details.

**What devices are supported?** TrimTrack is available on iOS. Android support is planned for a future release.

**What sign-in options are available?** You can sign in with Google, Apple, or email and password.

**Does the AI Stylist store my photos?** Before using the AI Stylist for the first time, you are asked to consent to sharing your photo and style description with Google Gemini AI. Photos are processed securely via a server-side function and stored in your private account. They are never shared or made public beyond the AI processing you consented to.

**How do subscriptions work?** TrimTrack Pro is available as a monthly or annual in-app purchase managed through the App Store. Some plans include a free trial period. You can manage or cancel your subscription at any time via **Settings → Apple ID → Subscriptions** on your device.

**How do I restore a previous purchase?** Go to **Settings → Restore Purchases** inside the app. This reconnects your App Store purchase to your account and restores your Pro access.

**Can I delete my account and data?** Yes. Go to **Settings → Delete Account** to permanently remove your account and all associated data. **Important:** deleting your account does **not** cancel your App Store subscription. You must cancel it separately via your device's **Settings → Apple ID → Subscriptions** to avoid future charges.

**Why am I still being charged after deleting my account?** App Store subscriptions are billed by Apple and are independent of your TrimTrack account. To stop billing, cancel the subscription in your device **Settings → Apple ID → Subscriptions** before or after deleting your account.

---

## Privacy Policy

**Last updated:** April 6, 2026

### What We Collect

| Data | Purpose | Storage |
|------|---------|---------|
| Account email and display name | Authentication and account identification | Supabase (encrypted) |
| Haircut entries | Core app functionality (dates, prices, styles, notes, ratings, duration) | Supabase (encrypted) |
| Photos | Haircut journaling and AI Stylist previews | Supabase Storage (private buckets, signed URLs) |
| AI Stylist photos and prompts | Sent to Google Gemini AI for hairstyle generation (with your explicit consent) and stored in your private history | Google Gemini (processing only, not retained); Supabase (encrypted storage) |
| Subscription status and metadata | Manage Pro tier access and AI generation limits | RevenueCat and Supabase |
| Anonymized usage analytics | Understand feature usage and improve the app | PostHog (no personally identifying information) |

### Device Permissions

TrimTrack may request the following device permissions:

* **Camera** — To take photos for haircut entries or AI Stylist
* **Photo Library** — To select existing photos for haircut entries or AI Stylist
* **Notifications** — To notify you when an AI generation completes (local notifications only; no remote push)

These permissions are requested only when needed and can be revoked at any time in your device settings.

### Analytics & Usage Data

TrimTrack uses **PostHog** to collect anonymized analytics that help us understand how the app is used and identify areas for improvement. Analytics are linked to your account ID (not your email or name) and include:

* App lifecycle events (app opened, became active, went to background)
* Feature interactions (haircut saved, AI generation started/completed, CSV exported)
* Authentication method used (Google, Apple, or email — no credentials)
* Subscription events (paywall viewed, purchase completed, subscription restored)
* Screen navigation

We do **not** send your name, email address, photos, haircut content, or notes to PostHog. Analytics data is used solely to improve the app experience and is never sold or shared with advertisers.

### Face & Photo Data

TrimTrack's **AI Stylist** feature allows you to upload a selfie to preview how different hairstyles might look on you. This section explains exactly how your face and photo data is handled.

#### What Face Data We Collect

When you use the AI Stylist feature, you provide a single selfie photo. The photo is compressed on your device (resized to a maximum of 1024 pixels wide and converted to JPEG format) before being transmitted. **TrimTrack does not extract, store, or process facial landmarks, facial geometry, face embeddings, or any biometric identifiers.** The photo is used solely as a visual reference image.

#### User Consent Before Data Sharing

Before the AI Stylist sends any data to a third-party service, TrimTrack displays a clear consent dialog explaining:

* **What data is sent:** Your photo and hairstyle description.
* **Who it is sent to:** Google Gemini AI.
* **What is not sent:** Your name, email, haircut history, or any other personal data.

You must explicitly agree by tapping **"I Agree"** before any data leaves your device. This consent is requested once; you can continue to use the AI Stylist after agreeing. If you decline, no data is sent and the feature is not used. A persistent disclosure is also displayed on the AI Stylist screen near the Generate button, reminding you that your photo and style description are processed by Google Gemini AI.

#### How Face Data Is Used

Your selfie is sent from your device to a secure server-side function (Supabase Edge Function), which forwards the compressed image to the **Google Gemini API** for hairstyle generation. The Gemini API analyzes the photo only to:

1. **Validate** that a human face is present in the image (if no face is detected, the request is rejected with a user-friendly error message).
2. **Generate** a preview image showing the requested hairstyle applied to your likeness.

No facial recognition, identification, or biometric analysis is performed. The face data is used exclusively for generating a visual hairstyle preview and for no other purpose.

#### Third-Party Processing of Face Data

Your selfie is processed by **Google Gemini API** on Google's servers. The image is transmitted securely (HTTPS) via a server-side function — the Gemini API key is never exposed to your device. Per Google's [Gemini API Terms of Service](https://ai.google.dev/gemini-api/terms), data submitted through the API is **not used to train Google's models** and is **not retained by Google** beyond the duration needed to process your request and generate a response.

No other third party receives your face data. Your photos are never sold, licensed, or shared with advertisers, data brokers, or any other external parties.

#### Where Face Data Is Stored

* **On your device:** A temporary copy of the selfie exists in app memory during upload. Temporary files are cleaned up automatically.
* **On our servers:** Your original selfie and the generated hairstyle image are stored in a **private Supabase Storage bucket** (`ai-generations`). These files are accessible only to your authenticated account via time-limited signed URLs that expire after 1 hour. Row Level Security (RLS) policies ensure that no other user can access your photos.

#### How Long Face Data Is Retained

Your selfie and generated images are retained in your private storage **until you choose to delete them**. You can delete individual AI generations from the AI History screen at any time. If you delete your account via **Settings → Delete Account**, all AI generation data — including selfies and generated images — is **permanently and irreversibly deleted** from our servers. We do not retain backup copies of deleted face data.

#### Your Control Over Face Data

* The AI Stylist feature is entirely optional — you are never required to upload a selfie.
* Camera and Photo Library permissions are requested only when you initiate the AI Stylist and can be revoked at any time in your device settings.
* You can delete any AI generation (including the associated selfie) from the AI History screen.
* You can delete your entire account and all associated data at any time via **Settings → Delete Account**.

### Third-Party Services

TrimTrack uses the following third-party services to operate:

| Service | Purpose | Data Shared |
|---------|---------|-------------|
| **Supabase** | Database, authentication, and file storage | Account info, haircut data, photos |
| **RevenueCat** | Subscription and in-app purchase management | User ID, subscription tier, product ID, purchase and expiry dates |
| **Google Gemini** (via server-side function) | AI hairstyle generation | Uploaded selfie photo and style description only, shared **with your explicit in-app consent** (processed server-side; see [Face & Photo Data](#face--photo-data) for details) |
| **Apple Sign-In / Google OAuth** | Authentication | Email and name (per provider's terms) |
| **PostHog** | Anonymized usage analytics | Account ID and anonymized feature interaction events (no email, name, photos, or content) |

### What We Don't Do

* We do **not** sell your data — including face data — to third parties
* We do **not** perform facial recognition, identification, or biometric analysis
* We do **not** create or store facial landmarks, embeddings, or geometry maps
* We do **not** share your photos or personal information with advertisers or data brokers
* We do **not** serve advertisements
* We do **not** track your location
* We do **not** send your name, email address, or personal content to analytics services

### Data Security

* All data is transmitted over HTTPS
* Photos are stored in **private** storage buckets accessible only to your account via time-limited signed URLs (1-hour expiration)
* AI processing is handled via secure server-side functions — no API keys are exposed to your device
* Database access is protected by Row Level Security (each user can only access their own data)
* Authentication sessions are stored securely on-device and automatically refreshed

### Data Retention

Your data is retained as long as your account exists. When you delete your account via **Settings → Delete Account**, all associated data — including your profile, haircut entries, photos, AI generation history, and selfies — is permanently removed from our servers.

### Your Rights

You have the right to:

* **Access** your data at any time through the app
* **Delete** individual AI generations (including selfies) from the AI History screen
* **Delete** your account and all associated data via **Settings → Delete Account**

For additional data requests (e.g. data export), contact us at **trimtrack.support@proton.me**.

### Children's Privacy

TrimTrack is not intended for children under 13. We do not knowingly collect data from children under 13.

### Changes to This Policy

We may update this Privacy Policy from time to time. Changes will be reflected on this page with an updated date.

### Contact

For questions, concerns, or data requests — including requests related to face data — contact us at:

**trimtrack.support@proton.me**

---

## Terms of Service

**Last updated:** April 6, 2026

By downloading or using TrimTrack, you agree to these Terms of Service. If you do not agree, do not use the app.

### 1. Use of the App

TrimTrack is provided for personal, non-commercial use. You must be at least 13 years old to use the app. You agree not to misuse the app, circumvent its security measures, or use it to harm others.

### 2. Your Account

You are responsible for maintaining the security of your account credentials. You are responsible for all activity that occurs under your account. Notify us at **trimtrack.support@proton.me** if you suspect unauthorized access.

### 3. Subscriptions & Billing

TrimTrack offers a free tier and an optional **Pro** subscription available as a monthly or annual in-app purchase through the App Store.

* Subscriptions automatically renew unless cancelled at least 24 hours before the end of the current period.
* You can manage or cancel your subscription at any time in your device **Settings → Apple ID → Subscriptions**.
* **Deleting your TrimTrack account does not cancel your App Store subscription.** You must cancel it separately to avoid future charges.
* Refunds are subject to Apple's refund policy. Contact Apple Support for billing disputes.

### 4. User Content

You retain ownership of content you upload (photos, haircut notes, etc.). By using TrimTrack, you grant us a limited license to store and process your content solely to provide the service to you. We do not use your personal content for advertising, training AI models, or any other purpose.

### 5. AI Stylist

The AI Stylist feature is provided for entertainment and personal exploration only. AI-generated hairstyle previews are not a substitute for professional styling advice. Results may not accurately represent how a hairstyle will look in person. By using this feature, you consent to your photo and style description being sent to Google Gemini AI as described in our Privacy Policy.

### 6. Acceptable Use

You agree not to:

* Upload content that is illegal, harmful, or violates others' rights
* Attempt to reverse-engineer, modify, or tamper with the app
* Use the app to harass or harm others
* Circumvent rate limits or subscription restrictions

### 7. Termination

We reserve the right to suspend or terminate your account if you violate these Terms. You may delete your account at any time via **Settings → Delete Account**.

### 8. Disclaimers

TrimTrack is provided "as is" without warranties of any kind. We do not guarantee uninterrupted service, and we are not liable for any data loss, service outages, or indirect damages arising from use of the app.

### 9. Changes to Terms

We may update these Terms from time to time. Continued use of the app after changes are posted constitutes acceptance of the updated Terms.

### 10. Contact

**trimtrack.support@proton.me**

---

## Contact & Support

Having issues with TrimTrack? Reach out:

* Email: **trimtrack.support@proton.me**

We typically respond within 48 hours.
