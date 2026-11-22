# Al-Huda: Quranic Guidance & AI Companion
### আল-হুদা: কুরআনিক দিকনির্দেশনা ও ইসলামিক এআই সঙ্গী

A serene, mobile-first Islamic Android application built with **React**, **Vite**, **Tailwind CSS**, **Lucide Icons**, and **Capacitor** for Android APK export.

---

## 🌟 Key Features

### 1. Life Situations & Emotions Hub (হোম স্ক্রিন)
Interactive hub addressing 8 fundamental human emotional states and life circumstances in bilingual (English & Bengali) cards:
- **Sadness / Heartbreak (দুঃখ ও মন খারাপ)** — Solace, ease following hardship (Surah Ash-Sharh, Yusuf, At-Tawbah).
- **Anxiety & Stress (দুশ্চিন্তা ও অস্থিরতা)** — Divine remembrance and mental tranquility (Surah Ar-Ra'd, Al-Imran, At-Talaq).
- **Gratitude & Happiness (খুশি ও শুকরিয়া আদায়)** — Multiplying blessings through Hamd (Surah Ibrahim, An-Nahl, Ar-Rahman).
- **Patience in Hardship (বিপদে ধৈর্য ধারণ)** — Perseverance and trusting divine wisdom (Surah Al-Baqarah, Az-Zumar, Al-Asr).
- **Seeking Forgiveness (তাওবা ও ক্ষমা প্রার্থনা)** — Allah's boundless mercy and repentance (Surah Az-Zumar, Al-Baqarah, An-Nisa).
- **Loneliness & Hopelessness (একাকিত্ব ও হতাশা)** — Realizing Allah is closer than your jugular vein (Surah Qaf, Ad-Duha, Al-Anbiya).
- **Provision & Rizq (রিজিক ও বরকত)** — Unfailing sustenance from unexpected sources (Surah At-Talaq, Hud, Al-Mulk).
- **Anger Management (রাগ নিয়ন্ত্রণ)** — Restraining rage and choosing pardon (Surah Al-Imran, Ash-Shura, Fussilat).

### 2. Authentic Verse Display Card (Strict Vertical Order)
Every verse displays verified text fetched dynamically from the free **AlQuran Cloud API** in strict vertical order:
1. **Exact Arabic Verse** — Large, readable font in Uthmani script (`quran-uthmani`), right-aligned with Surah name and Ayah number badge.
2. **Accurate English Translation** — Clear, authentic translation from Saheeh International (`en.sahih`).
3. **Accurate Bengali Translation** — Precise Bengali translation (`bn.bengali`).
4. **Interactive Controls** —
   - 🔊 **Audio Recitation**: Mishary Rashid Alafasy audio player streaming from the Islamic Network CDN.
   - 📋 **Copy**: Formats and copies Arabic, English, Bangla, and Surah citation to the clipboard with toast feedback.
   - 🔗 **Share**: Web Share API integration with fallback clipboard copy.
   - 🔖 **Bookmark**: Instant toggle to save/unsave verses in device storage (`localStorage`).

### 3. Full Quran Surah Browser & Reader (পবিত্র কুরআন)
- Complete directory of all **114 Surahs** with Arabic typography, English names, Bengali transliteration, revelation place (Meccan / Medinan), and total Ayah count.
- Fast live search by Surah name or number.
- In-depth reader mode featuring verse-by-verse audio and dual translations.

### 4. Gemini AI Islamic Companion (এআই সঙ্গী)
- Integrated with Google's official `@google/genai` SDK using `gemini-2.5-flash`.
- Responds empathetically in Bengali, Banglish, or English to user queries, emotional dilemmas, and questions on Islamic practices.
- Cites authentic Quranic verses with Arabic, English, and Bengali text.
- Formatted with a humble disclaimer reminding users that the assistant provides Quranic reflection and that binding religious rulings (Fatwas) require human scholars.
- Secure in-app Settings modal storing the user's Gemini API key privately on the local device.

### 5. Serene Islamic UI/UX
- Mobile-first glassmorphic dark & light theme.
- Emerald green (`#064e3b`, `#10b981`), deep slate (`#0f172a`), and soft gold (`#f59e0b`) accents.
- Authentic typography using Google Fonts **Amiri** & **Scheherazade New** (Arabic) and **Hind Siliguri** (Bengali).
- Fixed bottom navigation bar with 4 tabs and bookmark count badges.

---

## 📁 Project Architecture

```
al-huda-app/
├── android/                   # Native Android Project (Capacitor)
│   ├── app/
│   │   ├── src/main/
│   │   │   ├── AndroidManifest.xml   # Configured with Internet & Network permissions
│   │   │   └── assets/public/        # Synced web bundle
│   │   └── build.gradle.kts
│   ├── local.properties       # Points to Android SDK
│   └── gradlew.bat
├── src/
│   ├── types/
│   │   └── quran.ts           # TypeScript interfaces for Verses, Emotions, Chat, Bookmarks
│   ├── data/
│   │   ├── emotionsData.ts    # 8 Emotion categories with curated verse references
│   │   └── surahsData.ts      # 114 Surahs metadata (Arabic, English, Bangla)
│   ├── services/
│   │   ├── quranApi.ts        # AlQuran Cloud API fetcher, audio URLs & local cache
│   │   └── geminiService.ts   # @google/genai SDK integration with gemini-2.5-flash
│   ├── components/
│   │   ├── Navbar.tsx         # Serene header with theme toggle & API key modal trigger
│   │   ├── BottomNav.tsx      # 4-tab mobile navigation with badge
│   │   ├── VerseCard.tsx      # Strict 3-tier card (Arabic -> English -> Bangla + Audio)
│   │   ├── EmotionCard.tsx    # Interactive gradient emotion cards
│   │   ├── AudioPlayerBar.tsx # Sticky floating audio player
│   │   ├── ApiKeyModal.tsx    # Secure Gemini API key configuration modal
│   │   └── Toast.tsx          # Feedback toast notifications
│   ├── views/
│   │   ├── HomeView.tsx       # Daily inspiration & emotions hub
│   │   ├── QuranView.tsx      # 114 Surahs browser & full reader
│   │   ├── AiCompanionView.tsx# Gemini 2.5 Flash Islamic AI chat
│   │   └── BookmarksView.tsx  # Saved verses manager with search & audio
│   ├── App.tsx                # Master state controller & tab router
│   ├── main.tsx               # React DOM entry
│   └── index.css              # Tailwind directives & glassmorphic styles
├── capacitor.config.ts        # Capacitor configuration
├── package.json               # Dependencies & build scripts
└── vite.config.ts             # Vite build configuration
```

---

## 🚀 Running and Building

### 1. Run in Development Mode
```bash
npm run dev
```

### 2. Build Web Production Bundle
```bash
npm run build
```

### 3. Sync with Android Project
```bash
npx cap sync android
```

### 4. Open in Android Studio / Build APK
```bash
npx cap open android
```
Inside Android Studio:
- Select **Build > Build Bundle(s) / APK(s) > Build APK(s)** to generate the `.apk` file for physical device installation.
- Or run directly on an Android Emulator or connected physical phone.
