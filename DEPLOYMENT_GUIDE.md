# 🚀 מדריך פריסה - Deployment Guide

## 🔍 אבחון הבעיה

### מה הייתה הבעיה?
האתר נבנה ב-Google AI Studio עם **importmap** שמשתמש ב-CDN (esm.sh) לטעינת מודולים. זה עובד בסביבה של Google, אבל לא עובד מחוץ לזה כי:
- אין שרת שיטפל ב-module resolution
- TypeScript לא מתקמפל
- אין build process

### מה תוקן?
1. ✅ הוסר ה-`importmap` מה-`index.html`
2. ✅ נוסף `<script type="module" src="/index.tsx"></script>` לטעינה דרך Vite
3. ✅ נוצרו קבצי config לפריסה (`vercel.json`, `netlify.toml`)
4. ✅ עודכן ה-README עם הוראות מפורטות

---

## 📋 שלב 1: הרצה מקומית (Localhost)

### לפני הכל - בדוק שיש לך:
- ✅ Node.js 18+ מותקן
- ✅ Gemini API Key מ-[Google AI Studio](https://aistudio.google.com/app/apikey)

### הוראות:

1. **התקן dependencies:**
   ```bash
   npm install
   ```

2. **צור קובץ `.env` בתיקיית השורש:**
   ```env
   GEMINI_API_KEY=your_api_key_here
   ```
   ⚠️ **חשוב:** החלף `your_api_key_here` במפתח האמיתי שלך!

3. **הרץ את השרת המקומי:**
   ```bash
   npm run dev
   ```

4. **פתח בדפדפן:**
   ```
   http://localhost:3000
   ```

### אם עדיין רואה מסך ריק:

1. **פתח את Developer Console** (F12) ובדוק שגיאות
2. **ודא ש-`.env` קיים** עם `GEMINI_API_KEY`
3. **נסה לנקות cache:**
   ```bash
   rm -rf node_modules package-lock.json
   npm install
   ```

---

## 🌐 שלב 2: פריסה ל-Vercel

### אופציה 1: דרך GitHub (מומלץ)

1. **Push את הקוד ל-GitHub:**
   ```bash
   git add .
   git commit -m "Fix deployment issues"
   git push
   ```

2. **ב-Vercel:**
   - לך ל-[vercel.com](https://vercel.com)
   - לחץ "Import Project"
   - בחר את ה-repo שלך
   - **הוסף Environment Variable:**
     - Name: `GEMINI_API_KEY`
     - Value: המפתח שלך
   - לחץ "Deploy"

3. **Vercel יזהה אוטומטית:**
   - Framework: Vite
   - Build Command: `npm run build`
   - Output Directory: `dist`

### אופציה 2: דרך Vercel CLI

```bash
npm i -g vercel
vercel
# עקוב אחר ההוראות
# הוסף GEMINI_API_KEY כשמתבקש
```

---

## 🌐 שלב 3: פריסה ל-Netlify

1. **Push את הקוד ל-GitHub**

2. **ב-Netlify:**
   - לך ל-[netlify.com](https://netlify.com)
   - לחץ "Add new site" → "Import an existing project"
   - בחר את ה-repo שלך
   - **הגדר Build settings:**
     - Build command: `npm run build`
     - Publish directory: `dist`
   - **הוסף Environment Variable:**
     - Key: `GEMINI_API_KEY`
     - Value: המפתח שלך
   - לחץ "Deploy site"

3. **Netlify ישתמש ב-`netlify.toml`** שכבר קיים בפרויקט

---

## 🔧 שלב 4: טיפול בשגיאות נפוצות

### שגיאה: "Cannot find module 'react'"
**פתרון:**
```bash
npm install
```

### שגיאה: "process.env.API_KEY is undefined"
**פתרון:**
1. ודא שיש קובץ `.env` עם `GEMINI_API_KEY`
2. ב-Vercel/Netlify - ודא שהוספת את ה-Environment Variable

### שגיאה: "Blank screen" אחרי פריסה
**פתרון:**
1. בדוק את ה-Console בדפדפן (F12)
2. ודא שה-`base` path נכון ב-`vite.config.ts` (אם צריך)
3. נסה hard refresh: Cmd+Shift+R (Mac) או Ctrl+Shift+R (Windows)

### שגיאה: "404 on routes"
**פתרון:**
- Vercel: ה-`vercel.json` כבר מכיל rewrites
- Netlify: ה-`netlify.toml` כבר מכיל redirects

### שגיאה: "CORS error"
**פתרון:**
- זה לא אמור לקרות עם Gemini API
- אם כן, בדוק שה-API key תקין

---

## ✅ Checklist לפני פריסה

- [ ] `npm install` רץ בהצלחה
- [ ] `npm run dev` עובד מקומית
- [ ] קובץ `.env` קיים עם `GEMINI_API_KEY`
- [ ] `npm run build` רץ ללא שגיאות
- [ ] בדקת את ה-build מקומית: `npm run preview`
- [ ] הוספת `GEMINI_API_KEY` ב-Vercel/Netlify
- [ ] בדקת את ה-Console בדפדפן (אין שגיאות אדומות)

---

## 📞 תמיכה

אם עדיין יש בעיות:
1. בדוק את ה-Console בדפדפן (F12)
2. בדוק את ה-Logs ב-Vercel/Netlify
3. ודא שה-API key תקין ופעיל

---

## 🎯 סיכום השינויים

### קבצים ששונו:
- ✅ `index.html` - הוסר importmap, נוסף Vite script
- ✅ `README.md` - עודכן עם הוראות מפורטות
- ✅ `vercel.json` - נוצר (חדש)
- ✅ `netlify.toml` - נוצר (חדש)

### קבצים שצריך ליצור:
- ⚠️ `.env` - צריך ליצור עם `GEMINI_API_KEY`

### פקודות חשובות:
```bash
npm install          # התקנת dependencies
npm run dev         # הרצה מקומית
npm run build       # בניית production
npm run preview     # תצוגה מקדימה של build
```

---

**🎉 עכשיו האתר אמור לעבוד גם מקומית וגם בענן!**
