# 🎮 Fruit Dropper - Setup & Installation Guide

Complete step-by-step guide to get the game running in minutes.

---

## ✅ Pre-Requirements

Before starting, make sure you have:
- ✅ A modern web browser (Chrome, Firefox, Safari, or Edge)
- ✅ All files extracted from the archive
- ✅ 5 minutes of your time

**That's it! No installation needed. No dependencies. No servers.**

---

## 📦 Step 1: Extract Files

### Windows:
1. Right-click on `fruit-dropper.zip`
2. Select "Extract All..."
3. Choose a location (e.g., Desktop)
4. Click "Extract"

### macOS:
1. Double-click `fruit-dropper.zip`
2. Files automatically extract
3. Check your Downloads folder

### Linux:
```bash
unzip fruit-dropper.zip -d ~/fruit-dropper
cd ~/fruit-dropper
```

---

## 📂 Step 2: Verify File Structure

After extraction, you should have this structure:

```
fruit-dropper/
├── index.html                  ← MAIN GAME FILE
├── README.md
├── DOCUMENTATION.md            ← Full documentation
├── DEVELOPER.md                ← Developer guide
├── SETUP.md                    ← This file
└── MODULE_CLIENT_SIDE_MEDIA/   ← Images folder
    ├── apple.png
    ├── avocado.png
    ├── basket.png
    ├── bomb.png
    ├── golden_apple.png
    └── trash.png
```

**⚠️ Important:** The `MODULE_CLIENT_SIDE_MEDIA` folder MUST be in the same directory as `index.html`

---

## 🚀 Step 3: Play the Game!

### Option A: Double-Click (Easiest)
1. Navigate to the game folder
2. Double-click `index.html`
3. Your browser opens automatically
4. Game is ready to play! 🎮

### Option B: Right-Click > Open With
1. Right-click on `index.html`
2. Select "Open with..."
3. Choose your browser (Chrome, Firefox, Safari, Edge)
4. Click "Open"

### Option C: Drag & Drop
1. Open your browser
2. Drag `index.html` into the browser window
3. Drop it to load the game

### Option D: Command Line (Advanced)
```bash
# macOS
open index.html

# Windows (PowerShell)
Start-Process index.html

# Linux
xdg-open index.html
```

---

## ✨ You're Ready!

Once the game loads:

1. **Enter your name** in the "PLAYER NAME" field
2. **Choose difficulty** (Easy recommended for first time)
3. **Pick a color** if you want (optional)
4. **Click PLAY** button
5. **Enjoy!** 🍎

---

## 🎮 First Game Instructions

### Controls:
| Key | Action |
|-----|--------|
| **A** | Move basket LEFT |
| **D** | Move basket RIGHT |
| **ESC** | Pause game |

### Objective:
- **Catch falling fruits** to earn points
- **Avoid trash** (loses points & health)
- **Dodge bombs** (instant game over)
- **Collect golden apples** (heals & bonus points)

### Your First Game:
1. Watch fruits falling from top
2. Press **A** to move basket left
3. Press **D** to move basket right
4. Catch as many fruits as you can
5. When HP reaches 0, game ends
6. Your score is saved automatically!

---

## 🖥️ Device-Specific Instructions

### Desktop Computer (Windows/Mac/Linux)
✅ **Full support** - Everything works perfectly
- Use keyboard (A & D keys)
- Optimal experience

### Laptop
✅ **Full support** - Everything works perfectly
- Use touchpad (A & D keys)
- Portrait or landscape orientation

### Tablet (iPad/Android Tab)
✅ **Full support** - Responsive design included
- Touch controls work great
- Landscape mode recommended
- Tap area to move basket (or use on-screen arrows)

### Mobile Phone (iPhone/Android)
✅ **Full support** - Fully responsive
- Touch controls optimized for small screens
- Portrait mode works
- Excellent gameplay experience

---

## 🐛 Troubleshooting

### Problem: "Index.html won't open"
**Solution:**
- Make sure file is named exactly `index.html` (lowercase)
- Try right-click > "Open with" > Select browser
- Check file permissions (not read-only)

### Problem: "Game loads but images missing"
**Solution:**
- Verify `MODULE_CLIENT_SIDE_MEDIA` folder exists
- Check folder is in same directory as `index.html`
- All image files should be present (6 .png files)
- Try refreshing page (Ctrl+R or Cmd+R)

### Problem: "Keyboard controls not working"
**Solution:**
- Click on game window to focus it
- Try pressing A and D keys
- Check CAPS LOCK is not on
- Use lowercase letters (a, d not A, D)

### Problem: "Game is very laggy"
**Solution:**
- Close other browser tabs
- Update your browser to latest version
- Check system resources (Task Manager/Activity Monitor)
- Try different browser
- Restart browser

### Problem: "Fruit falls too fast/slow"
**Solution:**
- This is normal! Different difficulties have different speeds
- Easy = slow, Medium = medium, Hard = super fast
- Try Easy mode if too fast

### Problem: "Leaderboard not saving"
**Solution:**
- Check browser console for errors (F12)
- Verify LocalStorage is enabled
- Try incognito/private mode
- Clear browser cache and try again

### Problem: "Browser shows security warning"
**Solution:**
- This is normal for local HTML files
- Click "Allow" or similar button
- Game is 100% safe (no external connections)
- No data is sent to any server

---

## 🌐 Browser Compatibility

### Fully Supported ✅
- Google Chrome 90+
- Mozilla Firefox 88+
- Apple Safari 14+
- Microsoft Edge 90+
- Most modern browsers

### Partially Supported ⚠️
- Internet Explorer 11 (limited styling)
- Very old mobile browsers (may be slow)

### Not Supported ❌
- Very old browsers (pre-2015)
- Text-only browsers

**Recommendation:** Update your browser for best experience!

---

## 📊 System Requirements

### Minimum:
- **Browser:** Any modern browser
- **RAM:** 256 MB
- **Storage:** 1 MB (game folder)
- **Internet:** Not required! Game is offline

### Recommended:
- **Browser:** Latest version of Chrome/Firefox
- **RAM:** 2 GB
- **Internet:** None needed

---

## 🎓 Quick Reference

### Game Files Explained:

| File | Purpose |
|------|---------|
| `index.html` | Main game file (open this!) |
| `README.md` | Quick start guide |
| `DOCUMENTATION.md` | Complete documentation |
| `DEVELOPER.md` | Developer customization guide |
| `SETUP.md` | This setup guide |

### Media Files Explained:

| File | What It Is |
|------|-----------|
| `apple.png` | Red apple sprite |
| `avocado.png` | Green avocado sprite |
| `basket.png` | Player's basket/container |
| `bomb.png` | Dangerous bomb sprite |
| `golden_apple.png` | Special golden apple |
| `trash.png` | Trash/waste sprite |

---

## 💡 Tips for Best Experience

### Performance:
- Close unnecessary browser tabs
- Don't maximize other applications
- Use wired internet if streaming
- Update graphics drivers

### Gameplay:
- Start with Easy difficulty
- Read "How to Play" section
- Check leaderboard for motivation
- Try different difficulties

### Customization:
- Change background color in menu
- Try different difficulty levels
- Customize in DEVELOPER.md

---

## 🎮 Game Modes Quick Reference

### Easy Mode
- Great for learning
- Fruits appear slowly
- More health points
- Perfect for beginners

### Medium Mode
- Good challenge
- Faster gameplay
- Medium health
- Good for practice

### Hard Mode
- Expert challenge
- Very fast spawn
- Little health
- For advanced players

---

## 🔐 Security & Privacy

### Important Notes:
✅ **Completely Offline** - No internet required  
✅ **No Tracking** - No analytics or tracking code  
✅ **No Data Collection** - Your scores stay on YOUR computer  
✅ **100% Safe** - Open-source, auditable code  
✅ **No Ads** - Clean, ad-free experience  

### Data Storage:
- Scores saved in browser LocalStorage
- Persists across sessions
- Only accessible from this game
- Can be cleared anytime

---

## 📞 Getting Help

### If Something Goes Wrong:

1. **Check browser console** (Press F12)
   - Look for red error messages
   - Note any error text

2. **Verify file structure** (folder layout)
   - Make sure `MODULE_CLIENT_SIDE_MEDIA` exists
   - Check all image files are present

3. **Try troubleshooting section** above
   - Most issues have quick fixes
   - Listed common problems

4. **Read documentation**
   - `README.md` - Quick start
   - `DOCUMENTATION.md` - Complete guide
   - `DEVELOPER.md` - Technical details

---

## 🚀 Quick Start (TL;DR)

1. Extract all files
2. Double-click `index.html`
3. Enter player name
4. Click PLAY
5. Press A & D to move
6. Catch fruits, avoid bombs
7. Have fun! 🎮

---

## ✨ Next Steps

### After Setup:

1. **Read README.md** - Game overview (5 min read)
2. **Play the game** - Get comfortable with controls
3. **Check DOCUMENTATION.md** - Learn game mechanics
4. **Try all difficulties** - Easy → Medium → Hard
5. **Check leaderboard** - See top scores
6. **Read DEVELOPER.md** - Learn how to customize

---

## 🎉 Welcome!

You're now ready to enjoy the Fruit Dropper game!

**Remember:**
- 🍎 Catch apples & avocados = +1 point
- ⭐ Catch golden apples = +3 points & +1 HP
- 🗑️ Avoid trash = -5 points & -1 HP
- 💣 Dodge bombs = Game Over
- 📊 Your scores are saved automatically!

---

**Have fun playing! 🍎🎮**

**Need help?** Check the documentation files or review this guide!

---

## Version Info

- **Version:** 1.0.0
- **Updated:** February 2026
- **Status:** Fully Functional ✅

---

**Made with ❤️ using Vanilla JavaScript**
