<div align="center">
<img width="1200" height="475" alt="GHBanner" src="https://github.com/user-attachments/assets/0aa67016-6eaf-458a-adb2-6e31a0763ed6" />
</div>

# Ron Dahan Portfolio - AI-Powered Portfolio Website

Portfolio website built with React, TypeScript, Vite, and Google Gemini AI.

---

## 📋 תוכן עניינים / Table of Contents

- [איך Google AI Studio בנתה את זה?](#איך-google-ai-studio-בנתה-את-זה)
- [מה תוקן בקוד?](#מה-תוקן-בקוד)
- [הרצה מקומית (Localhost)](#הרצה-מקומית-localhost)
- [פריסה ל-Vercel](#פריסה-ל-vercel)
- [פריסה ל-Netlify](#פריסה-ל-netlify)

---

## 🔧 איך Google AI Studio בנתה את זה? / How Google AI Studio Built This?

### הטכנולוגיה / Technology Stack:
- **Frontend Framework**: React 19.2.3 עם TypeScript
- **Build Tool**: Vite 6.2.0
- **Styling**: Tailwind CSS (via CDN)
- **AI Integration**: Google Gemini API (@google/genai)
- **Icons**: Lucide React
- **Language Support**: עברית/English (RTL/LTR)

### המבנה / Structure:
```
pottfolio/
├── index.html          # Entry point HTML
├── index.tsx           # React entry point
├── App.tsx             # Main app component
├── components/         # React components
├── services/           # API services (Gemini)
├── constants.tsx       # Translations & data
├── vite.config.ts      # Vite configuration
└── package.json        # Dependencies
```

### הבעיה המקורית / Original Problem:
Google AI Studio יצרה את הפרויקט עם **import maps** ב-`index.html` שמיועדים לסביבת הפיתוח של Google. כשפותחים את `index.html` ישירות או מנסים לפרוס, הקוד לא עובד כי:
1. Import maps מפנים ל-CDN (esm.sh) במקום לקבצים המקומיים
2. TypeScript/JSX לא מקומפל
3. משתני סביבה לא מוזרקים
4. Vite dev server לא רץ

---

## ✅ מה תוקן בקוד? / What Was Fixed?

### 1. תיקון `index.html`
- **הוסר**: Import maps שמיועדים ל-Google AI Studio
- **נוסף**: Script tag שמפנה ל-`/index.tsx` (Vite מטפל בזה אוטומטית)

### 2. קונפיגורציה של Vite
- הקובץ `vite.config.ts` כבר מוגדר נכון
- משתני סביבה מוזרקים דרך `process.env.GEMINI_API_KEY`

---

## 🚀 הרצה מקומית (Localhost) / Run Locally

### דרישות מוקדמות / Prerequisites:
- **Node.js** (גרסה 18 ומעלה)
- **npm** או **yarn**

### שלבים / Steps:

1. **התקנת תלויות / Install Dependencies:**
   ```bash
   npm install
   ```

2. **יצירת קובץ משתני סביבה / Create Environment File:**
   
   צור קובץ `.env.local` בתיקיית הפרויקט:
   ```bash
   touch .env.local
   ```
   
   הוסף את המפתח API שלך:
   ```env
   GEMINI_API_KEY=your_actual_api_key_here
   ```
   
   > 💡 **איך להשיג API Key?**
   > 1. לך ל-[Google AI Studio](https://aistudio.google.com/apikey)
   > 2. צור מפתח API חדש
   > 3. העתק את המפתח לקובץ `.env.local`

3. **הרצת השרת המקומי / Run Dev Server:**
   ```bash
   npm run dev
   ```

4. **פתח בדפדפן:**
   - השרת יעלה על: `http://localhost:3000`
   - Vite יספק Hot Module Replacement (HMR) - שינויים יתעדכנו אוטומטית

### 🔍 פתרון בעיות / Troubleshooting:

**מסך ריק?**
- ודא ש-`npm install` הושלם בהצלחה
- בדוק שיש קובץ `.env.local` עם `GEMINI_API_KEY`
- פתח את Console בדפדפן (F12) ובדוק שגיאות

**שגיאת Port תפוס?**
- שנה את הפורט ב-`vite.config.ts`:
  ```typescript
  server: {
    port: 3001, // במקום 3000
  }
  ```

---

## 🌐 פריסה ל-Vercel / Deploy to Vercel

### שיטה 1: דרך GitHub (מומלץ)

1. **Push את הקוד ל-GitHub:**
   ```bash
   git add .
   git commit -m "Ready for deployment"
   git push origin main
   ```

2. **חבר את הפרויקט ל-Vercel:**
   - לך ל-[vercel.com](https://vercel.com)
   - לחץ על "Add New Project"
   - בחר את ה-repository שלך
   - Vercel יזהה אוטומטית שזה Vite project

3. **הגדר משתני סביבה:**
   - ב-Vercel Dashboard, לך ל-Settings → Environment Variables
   - הוסף:
     - **Name**: `GEMINI_API_KEY`
     - **Value**: המפתח API שלך
   - בחר את כל הסביבות (Production, Preview, Development)

4. **Deploy:**
   - לחץ על "Deploy"
   - Vercel יבנה ויפרס אוטומטית

### שיטה 2: דרך Vercel CLI

1. **התקן Vercel CLI:**
   ```bash
   npm i -g vercel
   ```

2. **Login:**
   ```bash
   vercel login
   ```

3. **Deploy:**
   ```bash
   vercel
   ```
   
   במהלך ה-deployment, Vercel ישאל:
   - האם להוסיף משתני סביבה? → **Yes**
   - `GEMINI_API_KEY` → הכנס את המפתח שלך

### ✅ קובץ `vercel.json` כבר מוגדר נכון!

הקובץ `vercel.json` כולל:
- Build command: `npm run build`
- Output directory: `dist`
- Framework: `vite`
- Rewrites: כל הנתיבים מפנים ל-`index.html` (SPA routing)

---

## 🚢 פריסה ל-Netlify / Deploy to Netlify

### שיטה 1: דרך GitHub (מומלץ)

1. **Push את הקוד ל-GitHub** (אם עדיין לא)

2. **חבר את הפרויקט ל-Netlify:**
   - לך ל-[netlify.com](https://netlify.com)
   - לחץ על "Add new site" → "Import an existing project"
   - בחר את ה-repository שלך

3. **הגדר Build Settings:**
   - **Build command**: `npm run build`
   - **Publish directory**: `dist`
   - Netlify יזהה אוטומטית שזה Vite project

4. **הגדר משתני סביבה:**
   - ב-Netlify Dashboard, לך ל-Site settings → Environment variables
   - הוסף:
     - **Key**: `GEMINI_API_KEY`
     - **Value**: המפתח API שלך

5. **Deploy:**
   - לחץ על "Deploy site"
   - Netlify יבנה ויפרס אוטומטית

### שיטה 2: דרך Netlify CLI

1. **התקן Netlify CLI:**
   ```bash
   npm i -g netlify-cli
   ```

2. **Login:**
   ```bash
   netlify login
   ```

3. **Deploy:**
   ```bash
   netlify deploy --prod
   ```
   
   במהלך ה-deployment:
   - Netlify ישאל אם להוסיף משתני סביבה
   - הוסף `GEMINI_API_KEY` עם המפתח שלך

### ✅ קובץ `netlify.toml` כבר מוגדר נכון!

הקובץ `netlify.toml` כולל:
- Build command: `npm run build`
- Publish directory: `dist`
- Redirects: כל הנתיבים מפנים ל-`index.html` (SPA routing)

---

## 📝 הערות חשובות / Important Notes

### ⚠️ אבטחה / Security:
- **אל תעלה את `.env.local` ל-Git!**
- ודא ש-`.env.local` נמצא ב-`.gitignore`
- השתמש במשתני סביבה בפלטפורמות הפריסה (Vercel/Netlify)

### 🔑 API Key:
- המפתח API שלך נדרש רק עבור ה-Chatbot (Gemini)
- אם אין לך מפתח, ה-Chatbot לא יעבוד, אבל שאר האתר יעבוד

### 🌍 Routing:
- האתר הוא Single Page Application (SPA)
- כל הנתיבים מפנים ל-`index.html` (מוגדר ב-`vercel.json` ו-`netlify.toml`)

---

## 🐛 פתרון בעיות נפוצות / Common Issues

### בעיה: "Blank screen" אחרי deployment
**פתרון:**
1. בדוק ש-`npm run build` עובד מקומית
2. ודא שמשתני הסביבה הוגדרו בפלטפורמת הפריסה
3. בדוק את ה-Logs ב-Vercel/Netlify

### בעיה: Chatbot לא עובד
**פתרון:**
1. ודא ש-`GEMINI_API_KEY` הוגדר נכון
2. בדוק את Console בדפדפן לשגיאות
3. ודא שהמפתח API תקף ולא חרג מהמכסה

### בעיה: Routing לא עובד (404)
**פתרון:**
- Vercel: ודא ש-`vercel.json` קיים עם rewrites
- Netlify: ודא ש-`netlify.toml` קיים עם redirects

---

## 📚 משאבים נוספים / Additional Resources

- [Vite Documentation](https://vitejs.dev/)
- [React Documentation](https://react.dev/)
- [Vercel Documentation](https://vercel.com/docs)
- [Netlify Documentation](https://docs.netlify.com/)
- [Google Gemini API](https://ai.google.dev/)

---

**נבנה עם ❤️ באמצעות Google AI Studio**
