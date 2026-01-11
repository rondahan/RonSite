
# Ron Dahan - AI Portfolio & Charlie Assistant

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
