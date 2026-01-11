<div align="center">
<img width="1200" height="475" alt="GHBanner" src="https://github.com/user-attachments/assets/0aa67016-6eaf-458a-adb2-6e31a0763ed6" />
</div>

# Ron Dahan - AI Portfolio & RONAI Assistant

Portfolio website built with React, TypeScript, Vite, and Google Gemini AI.

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ installed
- Gemini API key from [Google AI Studio](https://aistudio.google.com/app/apikey)

### Local Development

1. **Install dependencies:**
   ```bash
   npm install
   ```

2. **Create environment file:**
   Create a `.env` file in the root directory:
   ```env
   GEMINI_API_KEY=your_api_key_here
   ```

3. **Run development server:**
   ```bash
   npm run dev
   ```
   The app will be available at `http://localhost:3000`

4. **Build for production:**
   ```bash
   npm run build
   ```

5. **Preview production build:**
   ```bash
   npm run preview
   ```

## 📦 Deployment

### Vercel

1. Push your code to GitHub
2. Import project in Vercel
3. Add environment variable:
   - Name: `GEMINI_API_KEY`
   - Value: Your Gemini API key
4. Deploy!

### Netlify

1. Push your code to GitHub
2. Import project in Netlify
3. Build settings:
   - Build command: `npm run build`
   - Publish directory: `dist`
4. Add environment variable:
   - Key: `GEMINI_API_KEY`
   - Value: Your Gemini API key
5. Deploy!

### GitHub Pages

1. Install `gh-pages`: `npm install --save-dev gh-pages`
2. Add to `package.json`:
   ```json
   "scripts": {
     "predeploy": "npm run build",
     "deploy": "gh-pages -d dist"
   }
   ```
3. Update `vite.config.ts` with `base: '/your-repo-name/'`
4. Run `npm run deploy`

## 🔧 Troubleshooting

### Blank Screen Issues

If you see a blank screen:

1. **Check browser console** for errors
2. **Verify environment variables** are set correctly
3. **Clear browser cache** and hard refresh (Cmd+Shift+R / Ctrl+Shift+R)
4. **Check API key** is valid and has proper permissions

### Module Loading Errors

- Make sure you're running `npm run dev` (not opening `index.html` directly)
- Verify all dependencies are installed: `npm install`

### API Errors

- Verify `GEMINI_API_KEY` is set in `.env` file
- Check API key has access to Gemini models
- Review browser console for specific error messages

## 📁 Project Structure

```
pottfolio/
├── components/       # React components
├── services/         # API services (Gemini)
├── App.tsx          # Main app component
├── index.tsx        # Entry point
├── index.html       # HTML template
├── vite.config.ts   # Vite configuration
└── package.json     # Dependencies
```

## 🛠️ Tech Stack

- **React 19** - UI framework
- **TypeScript** - Type safety
- **Vite** - Build tool
- **Tailwind CSS** - Styling
- **Google Gemini AI** - Chatbot functionality
- **Lucide React** - Icons
