# 🍳 SousTouch — Touchless Recipe & Cookbook Companion
> **A zero-server, privacy-first kitchen assistant that lets you navigate recipes hands-free using real-time air gestures and text-to-speech.**

[![License: MIT](https://img.shields.io/badge/License-MIT-amber.svg)](LICENSE)
[![MediaPipe](https://img.shields.io/badge/Vision%20ML-MediaPipe%20Hands-emerald.svg)](https://developers.google.com/mediapipe)
[![Web Speech API](https://img.shields.io/badge/Speech-Web%20Speech%20API-blue.svg)](https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API)
[![No Backend Required](https://img.shields.io/badge/Backend-Zero%20Server%20(Static)-purple.svg)](#deployment)

---

## 📖 Overview

Cooking gets messy. Flour on your fingers, oil on your palms, or spices on your knuckles shouldn't mean smudging your laptop trackpad or phone screen.

**SousTouch** is an in-browser utility web app designed specifically for kitchen countertops. Using client-side computer vision (**MediaPipe Tasks Vision**), it tracks 21 hand landmarks in real time directly from your webcam. You can flip through recipe steps, trigger step countdown timers, and listen to step-by-step instructions read aloud—without ever touching a screen or keyboard.

---

## ✨ Key Features

- **100% Client-Side Vision ML**: Runs real-time hand pose estimation in the browser at 30+ FPS via MediaPipe Hands. No video or images ever leave your device.
- **Natural Air Gestures**:
  - ➡️ **Wave Right / Thumb Right**: Advance to the next cooking step.
  - ⬅️ **Wave Left**: Return to the previous step.
  - ✋ **Open Palm (0.4s hold)**: Read instructions aloud or pause narration via the Web Speech API.
  - 👍 **Thumbs Up**: Start or pause the step countdown timer.
- **Smart Gesture Cooldown**: Visual 1.25s debounce cooldown ring prevents accidental multi-step jumps while whisking or chopping.
- **Built-in Resilient Fallbacks**:
  - *Optical Flow Motion Engine*: Works even in offline environments without external CDN access.
  - *On-Screen Simulator & Keyboard Shortcuts*: Complete testability without requiring webcam permissions.
- **High-Contrast Kitchen UI**: Saffron and obsidian dark aesthetic optimized for reading from 3 to 6 feet away on a kitchen counter or tablet stand.
- **Authentic Bengali Heritage Recipes**: Preloaded with detailed timings, ingredient proportions, and chef tips for:
  - *Shorshe Ilish (সর্ষে ইলিশ)*
  - *Kolkata Kosha Mangsho (কষা মাংস)*
  - *Chingri Malai Curry (চিংড়ি মালাই কারি)*
  - *Shahi Bhuna Khichuri (শাহী ভুনা খিচুড়ি)*
- **Interactive Tools**: Built-in countdown timers with synthetic Web Audio chimes and a slide-out pantry ingredient checklist drawer.

---

## 🖐️ Gesture Reference

| Air Gesture | Visual Hint | Action | Fallback Key |
| :--- | :--- | :--- | :--- |
| **Wave Right** | 👉 | Next Recipe Step | `ArrowRight` |
| **Thumb Right** | 👉 | Next Recipe Step | `ArrowRight` |
| **Wave Left** | 👈 | Previous Recipe Step | `ArrowLeft` |
| **Open Palm** (Hold 0.4s) | ✋ | Read Aloud / Pause Speech | `Spacebar` |
| **Thumbs Up** | 👍 | Start / Pause Step Timer | `T` |
| **Fullscreen** | ⛶ | Toggle Fullscreen Counter Mode | `F` |

---

## 🛠️ Tech Stack

- **Computer Vision**: Google MediaPipe Tasks Vision (`@mediapipe/hands`, `@mediapipe/camera_utils`)
- **Speech Synthesis**: Browser Native Web Speech API (`window.speechSynthesis`)
- **Audio Feedback**: Web Audio API (`AudioContext` oscillator synthesis—zero audio asset dependencies)
- **Frontend**: Vanilla HTML5, modern CSS3 (Glassmorphism, CSS Custom Properties), and ES6+ JavaScript
- **Backend**: None (pure client-side static application)

---

## 🚀 Quick Start (Local)

Because SousTouch is a single-file application, you can run it locally with any static HTTP server (required for browser webcam permissions):

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/touchless-recipe-companion.git
cd touchless-recipe-companion

# 2. Start a local server (Python 3)
python3 -m http.server 8000

# 3. Open in your browser
# Navigate to http://localhost:8000/touchless_recipe_companion.html
```

---

## 🌐 Free Production Deployment

Modern browsers require a secure origin (**HTTPS**) to enable webcam access (`navigator.mediaDevices.getUserMedia`).

### Option 1: GitHub Pages
1. Rename `touchless_recipe_companion.html` to `index.html`.
2. Push your code to GitHub.
3. In your repo, go to **Settings** > **Pages** > Set Source branch to `main` (`/root`) > **Save**.
4. Your app is live at `https://<your-username>.github.io/<repo-name>/`.

### Option 2: Netlify Drop
1. Go to [app.netlify.com/drop](https://app.netlify.com/drop).
2. Drag and drop the project folder containing `index.html`.
3. Your app is deployed with free SSL in seconds.

### Option 3: Vercel
```bash
npx vercel
```

---

## 🔒 Privacy & Permissions

- **Webcam Access**: Used exclusively for in-browser landmark calculation. Video frames are processed in volatile memory and are never stored, logged, or transmitted over any network.
- **Offline Capable**: The app contains an internal optical-flow frame-difference fallback engine that operates without active internet connectivity.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
