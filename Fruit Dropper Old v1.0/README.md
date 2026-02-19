# 🍎 Fruit Dropper Game

A fun and addictive web-based arcade game where you catch falling fruits!

## Quick Shotcut ##
- [Cara Kerja, Fungsi dan Cara Customisasi](DEVELOPER.md)
- [Game Documentation](DOCUMENTATION.md)
- [Setup & Installation Guide](SETUP.md)
- [Cara Bermain](READ_ME_FIRST.txt)
- [Quick Start](START_HERE.txt)
- [More Information](COMPLETE_PACKAGE_INFO.txt)

## 🚀 Quick Start

### Setup (30 seconds)
1. Extract all files from the archive
2. Make sure `asset` folder is in the same directory as `index.html`
3. Open `index.html` in your web browser
4. **Play!** 🎮

### System Requirements
- Modern web browser (Chrome, Firefox, Safari, Edge)
- No installation needed
- Works on mobile, tablet, and desktop

## 🎮 How to Play

### Controls
- **A Key** - Move basket LEFT
- **D Key** - Move basket RIGHT
- **ESC Key** - Pause/Resume game

### Game Objective
Catch falling fruits to earn points and maintain health. Avoid bombs and trash!

## 🎯 Game Features

### 3 Difficulty Levels
- **Easy** - Good for learning the game (3s spawn, 1x speed)
- **Medium** - Moderate challenge (2s spawn, 2x speed)
- **Hard** - Expert only! (1s spawn, 3x speed)

### 5 Fruit Types
| Fruit | Effect | Points |
|-------|--------|--------|
| 🍎 Apple | Basic catch | +1 |
| 🥑 Avocado | Basic catch | +1 |
| ⭐ Golden Apple | Heals & bonus | +3 HP |
| 🗑️ Trash | Penalty | -5 -1HP |
| 💣 Bomb | Game Over | ☠️ |

### Features
✅ Responsive design (works on all devices)  
✅ Custom background colors  
✅ Leaderboard system (top 10 scores)  
✅ Pause & Resume  
✅ Professional UI design  
✅ LocalStorage for score saving  

## 📱 Device Support

| Device | Support |
|--------|---------|
| Desktop | ✅ Full support |
| Tablet | ✅ Full support |
| Mobile Phone | ✅ Full support |
| Landscape | ✅ Fully responsive |
| Portrait | ✅ Fully responsive |

## 📚 Documentation

For detailed documentation, see **[DOCUMENTATION.md](DOCUMENTATION.md)** file which includes:
- Complete game mechanics
- Troubleshooting guide
- Developer customization guide
- Technical architecture
- API reference

## 🛠️ Customization

### Change Colors
Edit CSS variables in `index.html`:
```css
:root {
  --primary-color: #FF6B6B;
  --secondary-color: #4ECDC4;
  --accent-color: #FFE66D;
}
```

### Modify Difficulty
Edit JavaScript constants:
```javascript
const difficultySettings = {
  easy: { spawnRate: 3000, fallSpeed: 1, maxHP: 5 }
};
```

See **DOCUMENTATION.md** for more customization options.

## 🐛 Troubleshooting

**Images not loading?**
- Check if `asset` folder exists
- Verify file names are correct
- Try refreshing the page

**Game lag?**
- Close unnecessary browser tabs
- Update your browser
- Check system resources

**Leaderboard not working?**
- Check browser console for errors
- Verify LocalStorage is enabled
- Try incognito/private mode

For more help, see **[DOCUMENTATION.md](DOCUMENTATION.md)** troubleshooting section.

## 📋 File Structure

```
fruit-dropper/
├── index.html                          (Game - open this file!)
├── DOCUMENTATION.md                    (Full documentation)
├── README.md                           (This file)
└── asset/
    ├── apple.png
    ├── avocado.png
    ├── basket.png
    ├── bomb.png
    ├── golden_apple.png
    └── trash.png
```

## 💾 Data & Storage

Your scores are automatically saved in your browser using LocalStorage. 

**To clear data:**
1. Open browser console (F12)
2. Run: `localStorage.removeItem('fruitDropperScores')`
3. Refresh the page

## ⚡ Performance

- Optimized for 60 FPS gameplay
- Smooth animations on all devices
- Efficient collision detection
- Minimal resource usage

## 🎨 Design

- Modern gradient UI
- Professional color scheme
- Smooth animations & transitions
- Touch-friendly controls
- Fully accessible interface

## 📊 Leaderboard

The game maintains a persistent leaderboard of your top 10 scores:
- Automatically saved in browser storage
- Displays: Rank, Name, Score, Difficulty
- All-time tracking
- Survives browser restart

## 🔒 Privacy

All game data is stored locally in your browser. No data is sent to external servers.

## 📝 License

This game is provided as-is for educational and entertainment purposes. Feel free to modify and customize it!

## 🎓 Learning Resources

This game is built with:
- HTML5 Canvas API
- CSS3 Flexbox & Grid
- Vanilla JavaScript (ES6+)
- LocalStorage API
- No external dependencies

Perfect for learning web development!

---

## 🆘 Need Help?

1. **Game won't start?** Check console (F12) for errors
2. **Images missing?** Verify folder structure
3. **Performance issues?** Close other tabs and refresh
4. **Other issues?** Check [DOCUMENTATION.md](DOCUMENTATION.md)

---

**Have fun playing! 🍎🎮**

**Version:** 1.0.0  
**Made with using Vanilla JavaScript**
