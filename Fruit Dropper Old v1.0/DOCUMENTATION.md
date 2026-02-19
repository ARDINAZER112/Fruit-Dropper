# 🍎 FRUIT DROPPER - Game Documentation

**Version:** 1.0.0  
**Last Updated:** February 2026  
**Compatibility:** All Modern Browsers (Chrome, Firefox, Safari, Edge)  
**Resolution:** 400x600px (Responsive for all devices)

---

## 📋 Table of Contents

1. [Overview](#overview)
2. [Game Features](#game-features)
3. [Installation & Setup](#installation--setup)
4. [Game Mechanics](#game-mechanics)
5. [Menu System](#menu-system)
6. [Gameplay Guide](#gameplay-guide)
7. [Difficulty Levels](#difficulty-levels)
8. [Leaderboard System](#leaderboard-system)
9. [Technical Architecture](#technical-architecture)
10. [Responsive Design](#responsive-design)
11. [Troubleshooting](#troubleshooting)
12. [Developer Guide](#developer-guide)

---

## Overview

**Fruit Dropper** adalah sebuah arcade game yang dimainkan di web browser. Pemain harus menangkap buah-buahan yang jatuh dari atas layar menggunakan keranjang di bagian bawah. Game ini menampilkan berbagai jenis buah dengan ability unik, sistem kesulitan yang dapat disesuaikan, dan leaderboard untuk melacak skor tertinggi.

### Core Features:
- ✅ Single HTML file (no external dependencies)
- ✅ Fully responsive (mobile, tablet, desktop)
- ✅ 3 difficulty levels with unique mechanics
- ✅ 5 fruit types dengan ability berbeda
- ✅ Custom background color picker
- ✅ Pause & Resume functionality
- ✅ LocalStorage Leaderboard
- ✅ Professional UI/UX Design
- ✅ Touch & Keyboard support

---

## Game Features

### 1. Main Menu
Menu utama memberikan akses ke semua fitur game:
- **Player Name Input**: Masukkan nama pemain (max 20 karakter)
- **Difficulty Selection**: Pilih antara Easy, Medium, atau Hard
- **Background Color Picker**: Customize warna latar belakang gameplay
- **How to Play**: Panduan singkat tentang cara bermain
- **Leaderboard Button**: Lihat top 10 pemain
- **Play Button**: Mulai game (hanya aktif jika nama terisi)

### 2. Game Display
Saat bermain, tampilan game menunjukkan:
- **Player Name**: Nama pemain yang sedang bermain
- **Score**: Poin kumulatif
- **Health Bar (HP)**: Visual indicator untuk sisa nyawa
- **Game Canvas**: Area bermain dengan keranjang & buah

### 3. Gameplay Elements
- **Basket**: Keranjang yang bergerak dengan tombol A (kiri) & D (kanan)
- **Fruits**: 5 jenis buah dengan efek berbeda
- **Falling Animation**: Buah jatuh dengan kecepatan tergantung difficulty

### 4. Pause & Resume
Tekan **ESC** untuk pause game:
- **Continue**: Lanjut bermain
- **Restart**: Mulai game baru
- **Quit to Menu**: Kembali ke menu utama

### 5. Game Over Screen
Ketika HP mencapai 0:
- Tampilkan final statistics
- Option untuk Restart atau Quit
- Auto-save score ke leaderboard

### 6. Leaderboard
LocalStorage-based leaderboard system:
- Top 10 scores berdasarkan nilai tertinggi
- Menampilkan: Rank, Name, Score, Difficulty
- Persisten across sessions

---

## Installation & Setup

### Requirement:
- Modern web browser (Chrome, Firefox, Safari, Edge)
- Folder structure dengan media files

### File Structure:
```
fruit-dropper/
├── index.html                          (Game file)
└── MODULE_CLIENT_SIDE_MEDIA/
    ├── apple.png
    ├── avocado.png
    ├── basket.png
    ├── bomb.png
    ├── golden_apple.png
    └── trash.png
```

### Setup Steps:
1. **Extract** semua file dari archive
2. **Pastikan** folder `MODULE_CLIENT_SIDE_MEDIA` berada di direktori yang sama dengan `index.html`
3. **Open** `index.html` di web browser (double-click atau drag ke browser)
4. **Game ready to play!** ✅

### Important Notes:
- Tidak perlu server untuk menjalankan game
- File harus dijalankan dari folder yang sama
- Browser harus allow file access ke folder `MODULE_CLIENT_SIDE_MEDIA`

---

## Game Mechanics

### Fruit Types & Effects

#### 1. 🍎 Apple
- **Points**: +1
- **Health**: No change
- **Rarity**: Common
- **Color**: Red

#### 2. 🥑 Avocado
- **Points**: +1
- **Health**: No change
- **Rarity**: Common
- **Color**: Green

#### 3. ⭐ Golden Apple
- **Points**: +3
- **Health**: +1 HP
- **Rarity**: Rare
- **Color**: Golden/Yellow
- **Special**: Heals & gives bonus points

#### 4. 🗑️ Trash
- **Points**: -5
- **Health**: -1 HP
- **Rarity**: Uncommon
- **Penalty**: Double negative (point + health loss)

#### 5. 💣 Bomb
- **Points**: No change
- **Health**: -∞ (Game Over)
- **Rarity**: Rare
- **Special**: Instant game over

### Spawn Probability:
```
Apple (30%) → Avocado (30%) → Golden Apple (15%) 
→ Trash (20%) → Bomb (5%)
```

### Fruit Mechanic:
1. **Spawn**: Buah muncul di posisi random di atas layar
2. **Fall**: Buah jatuh dengan kecepatan sesuai difficulty
3. **Collision**: Jika menyentuh keranjang, buah hilang & effect diterapkan
4. **Miss**: Jika buah jatuh ke bawah tanpa tertangkap, health berkurang 1

---

## Menu System

### Main Menu Structure

```
┌─────────────────────────────────┐
│     🍎 FRUIT DROP (Title)       │
├─────────────────────────────────┤
│  PLAYER NAME                    │
│  [Text Input Field]             │
├─────────────────────────────────┤
│  DIFFICULTY                     │
│  [Easy] [Medium] [Hard]         │
├─────────────────────────────────┤
│  BACKGROUND COLOR               │
│  [Color Picker] Custom BG       │
├─────────────────────────────────┤
│  HOW TO PLAY                    │
│  (Game instructions)            │
├─────────────────────────────────┤
│  [📊 Leaderboard]  [PLAY]       │
└─────────────────────────────────┘
```

### Input Validation:
- Player name tidak boleh kosong
- Play button disabled jika nama kosong
- Difficulty default: Easy
- Background color default: Dark Gray (#2d3436)

### Menu Styling:
- Gradient background (dark blue to purple)
- Animated title dengan bounce effect
- Smooth transitions & hover effects
- Custom color scheme (cyan, coral, yellow)

---

## Gameplay Guide

### How to Play - Step by Step

#### 1. **Start Game**
   - Masukkan nama pemain
   - Pilih difficulty level (Easy untuk pemula)
   - Pilih warna background (optional)
   - Click tombol "PLAY"

#### 2. **Control Basket**
   - Press **A** untuk gerak ke kiri
   - Press **D** untuk gerak ke kanan
   - Basket tidak bisa keluar dari layar

#### 3. **Catch Fruits**
   - Posisikan keranjang untuk menangkap buah
   - Setiap buah punya effect berbeda
   - Monitor score & HP di bagian atas

#### 4. **Manage Health**
   - Start HP tergantung difficulty
   - Miss 1 buah = -1 HP
   - Trash = -1 HP & -5 points
   - Bomb = Game Over
   - Golden Apple = +1 HP & +3 points

#### 5. **Pause Game**
   - Press **ESC** untuk pause
   - Pilih Continue/Restart/Quit
   - Game resume dari posisi terakhir

#### 6. **Game Over**
   - Ketika HP = 0, game berakhir
   - Score otomatis tersimpan
   - Pilih Restart atau Quit

### Tips & Strategies:

✅ **For Easy Mode:**
- Focus on catching commons fruits
- Build score slowly & steadily
- Avoid trash ketika HP masih banyak

✅ **For Medium Mode:**
- Faster reaction time needed
- Prioritize Golden Apples untuk HP
- Balance antara offense & defense

✅ **For Hard Mode:**
- Very fast gameplay
- Spawn rate sangat tinggi
- Setiap miss sangat costly
- Reaction time < 1 second

---

## Difficulty Levels

### Comparison Table

| Aspect | Easy | Medium | Hard |
|--------|------|--------|------|
| **Spawn Rate** | 3 seconds | 2 seconds | 1 second |
| **Fall Speed** | 1x | 2x | 3x |
| **Max HP** | 5 | 4 | 3 |
| **Best For** | Beginners | Intermediate | Advanced |
| **Avg Duration** | 2-3 min | 1-2 min | 30-60 sec |

### Difficulty Mechanics:

**Easy Mode:**
```
- Buah spawn setiap 3 detik
- Kecepatan jatuh normal
- Lebih banyak waktu untuk react
- Good untuk belajar mechanics
- Max score potential: 50-100 points
```

**Medium Mode:**
```
- Buah spawn setiap 2 detik
- Kecepatan jatuh 2x lebih cepat
- Require faster reflexes
- Good untuk practicing
- Max score potential: 100-200 points
```

**Hard Mode:**
```
- Buah spawn setiap 1 detik
- Kecepatan jatuh 3x lebih cepat
- Extreme challenge
- Untuk expert players
- Max score potential: 200+ points
```

---

## Leaderboard System

### Features:
- **Top 10 Scores**: Hanya 10 score tertinggi yang ditampilkan
- **Sorting**: Otomatis sort by score descending
- **Persistence**: Data tersimpan di LocalStorage
- **All-time**: Tidak ada time limit, leaderboard all-time

### What's Stored:
```javascript
{
  name: "Player Name",
  score: 150,
  difficulty: "hard",
  date: "2/18/2026"
}
```

### Access Leaderboard:
1. Click **"📊 Leaderboard"** button di main menu
2. View top 10 players
3. Lihat rank, nama, score, dan difficulty
4. Click **"Close"** untuk kembali ke menu

### Leaderboard Display:
```
🏆 LEADERBOARD 🏆
───────────────────────────
#1  | Player1  | 500 | HARD
#2  | Player2  | 450 | HARD
#3  | Player3  | 420 | MEDIUM
...
#10 | Player10 | 100 | EASY
───────────────────────────
```

### Clear Leaderboard:
To clear leaderboard data, buka browser console (F12) dan jalankan:
```javascript
localStorage.removeItem('fruitDropperScores');
console.log('Leaderboard cleared!');
```

---

## Technical Architecture

### Project Structure

```
Fruit Dropper Game
├── Single HTML File (index.html)
│   ├── HTML Structure
│   │   ├── Canvas Element
│   │   ├── Menu Elements
│   │   ├── Game UI Elements
│   │   ├── Modal Dialogs
│   │   └── Leaderboard
│   ├── CSS Styling
│   │   ├── Root Variables
│   │   ├── Component Styles
│   │   ├── Animation Keyframes
│   │   └── Media Queries
│   └── JavaScript Logic
│       ├── Game State Management
│       ├── Event Handlers
│       ├── Game Loop (RAF)
│       ├── Physics & Collision
│       └── LocalStorage Integration
└── Media Folder (asset/)
    ├── apple.png
    ├── avocado.png
    ├── basket.png
    ├── bomb.png
    ├── golden_apple.png
    └── trash.png
```

### Game State Structure

```javascript
{
  isPlaying: boolean,        // Game running status
  isPaused: boolean,         // Pause status
  playerName: string,        // Current player name
  difficulty: "easy|medium|hard", // Selected difficulty
  score: number,             // Current score
  hp: number,                // Current health points
  maxHP: number,             // Max health (difficulty based)
  backgroundColor: string,   // Custom background color
  gameTime: number,          // Game elapsed time
  spawnRate: number,         // Fruit spawn interval (ms)
  fallSpeed: number,         // Fruit fall multiplier
  fruits: [],                // Active fruits array
  basket: {x, y},            // Basket position
  keys: {}                   // Key press states
}
```

### Key Functions

#### Game Loop:
```javascript
gameLoop() → updateGame() → drawGame() → RAF(gameLoop)
```

#### Update Flow:
1. **updateGame()**: Handle input, update positions, collision detection
2. **drawGame()**: Clear canvas, draw fruits, draw basket
3**updateUI()**: Update score & HP display

#### Collision Detection:
```javascript
// AABB (Axis-Aligned Bounding Box) collision
checkCollision(fruit):
  fruit.x < basket.x + width AND
  fruit.x + width > basket.x AND
  fruit.y < basket.y + height AND
  fruit.y + height > basket.y
```

### Data Persistence

**LocalStorage Key:** `fruitDropperScores`

```javascript
// Storage format
[
  {
    name: "John",
    score: 250,
    difficulty: "hard",
    date: "2/18/2026"
  },
  ...
]
```

### Canvas Resolution

- **Game Canvas**: 400x600px
- **Basket Size**: 60x50px
- **Fruit Size**: 40x40px
- **Game Area**: Full 400x600

---

## Responsive Design

### Device Compatibility

**The game is optimized for ALL devices:**

#### Mobile Phones (320px - 480px)
- Full responsive layout
- Touch-friendly UI
- Optimized font sizes
- Single column layout
- Reduced padding/margins

**Example:** iPhone SE, iPhone 12 Mini

#### Tablets (481px - 768px)
- Medium scaling
- Touch & keyboard support
- Optimized spacing
- Readable text sizes

**Example:** iPad Mini, Samsung Tab S6 Lite

#### Desktop (769px+)
- Full-size game container
- Keyboard controls optimized
- Large interactive elements
- Generous spacing

**Example:** Laptop, Desktop Monitor

#### Landscape Mode
- Game adjusts to viewport
- Reduced vertical padding
- Maintained aspect ratio
- All features accessible

### Responsive Features

1. **Fluid Typography**
   - Uses `clamp()` function untuk responsive fonts
   - Example: `font-size: clamp(12px, 2.5vw, 14px)`
   - Automatic scaling between min & max

2. **Flexible Layouts**
   - Flexbox untuk responsive positioning
   - Max-width containers untuk readability
   - Padding scales dengan viewport

3. **Touch Support**
   - Touch-friendly button sizes (min 44px)
   - Reduced hover effects on touch devices
   - Active states untuk visual feedback

4. **Viewport Optimization**
   - Proper viewport meta tag
   - Aspect ratio maintenance
   - Overflow handling

### Media Query Breakpoints

```css
/* Mobile First - 320px to 480px */
@media (max-width: 480px)

/* Tablet - 481px to 768px */
@media (min-width: 481px) and (max-width: 768px)

/* Landscape Mode */
@media (max-height: 500px)

/* Portrait Mode */
@media (orientation: portrait)

/* Landscape Mode */
@media (orientation: landscape)

/* Desktop - 769px+ */
@media (min-width: 769px)

/* Ultra-wide - 1600px+ */
@media (min-width: 1600px)

/* High DPI */
@media (min-resolution: 2dppx)

/* Touch Devices */
@media (hover: none) and (pointer: coarse)
```

---

## Troubleshooting

### Common Issues & Solutions

#### 1. **Images Not Loading**
**Problem**: Fruits dan basket tidak muncul di game

**Solution**:
- Pastikan folder `asset` ada di directory yang sama dengan `index.html`
- Cek nama file: harus persis seperti di code (lowercase, .png extension)
- Buka browser console (F12) untuk lihat error messages
- Try opening from different browser

#### 2. **Game Not Responsive**
**Problem**: Game display tidak sesuai dengan screen size

**Solution**:
- Refresh page dengan Ctrl+Shift+R (clear cache)
- Check viewport meta tag di HTML
- Try different browser atau device
- Disable browser zoom jika ada

#### 3. **Keyboard Controls Not Working**
**Problem**: Tombol A dan D tidak gerakkan basket

**Solution**:
- Make sure game window is focused (click on game)
- Check jika ada caps lock aktif
- Try dengan lowercase letters
- Buka console untuk debug key events

#### 4. **Leaderboard Not Saving**
**Problem**: Score tidak tersimpan di leaderboard

**Solution**:
- Check browser console untuk LocalStorage errors
- Pastikan LocalStorage tidak disabled di browser
- Try di incognito/private mode
- Clear browser cache & cookies

#### 5. **Performance Issues**
**Problem**: Game lag atau slow

**Solution**:
- Close unnecessary browser tabs
- Update browser ke versi terbaru
- Check system resources (CPU/RAM)
- Try di browser yang berbeda
- Disable browser extensions

#### 6. **Audio Not Working**
**Problem**: Tidak ada sound effects

**Solution**:
- Game ini tidak punya audio (by design)
- Ini bukan bug - feature sudah selesai tanpa audio

### Debug Mode

Buka browser console (F12) untuk lihat game state:

```javascript
// Check game state
console.log(gameState);

// Check if images loaded
Object.keys(images).forEach(key => {
  console.log(`${key}: ${images[key].complete ? 'loaded' : 'pending'}`);
});

// Clear leaderboard (if needed)
localStorage.removeItem('fruitDropperScores');

// View leaderboard data
console.log(JSON.parse(localStorage.getItem('fruitDropperScores')));
```

---

## Developer Guide

### Code Organization

#### HTML Structure
- Semantic markup dengan accessibility
- Single canvas element untuk game rendering
- Modal dialogs untuk menus & popups
- Clear element organization

#### CSS Architecture
- CSS Custom Properties (variables) untuk colors
- Mobile-first responsive design
- BEM-like naming convention
- Organized sections dengan comments

#### JavaScript Logic
- Game state centralized dalam object
- Event-driven architecture
- RequestAnimationFrame untuk smooth animation
- Function-based organization

### Customization Guide

#### Change Color Scheme
Edit CSS variables di `:root`:
```css
:root {
  --primary-color: #FF6B6B;      /* Main color */
  --secondary-color: #4ECDC4;    /* Secondary color */
  --accent-color: #FFE66D;       /* Highlight color */
  --dark-bg: #2D3436;            /* Background */
  --light-text: #F5F6FA;         /* Text color */
}
```

#### Modify Fruit Properties
Edit `fruitTypes` object:
```javascript
const fruitTypes = {
  apple: { points: 1, hp: 0, image: 'apple' },
  // Add new fruit:
  cherry: { points: 2, hp: 0, image: 'cherry' }
};
```

#### Adjust Difficulty Settings
Edit `difficultySettings` object:
```javascript
const difficultySettings = {
  easy: { spawnRate: 3000, fallSpeed: 1, maxHP: 5 },
  // Modify existing:
  hard: { spawnRate: 800, fallSpeed: 4, maxHP: 2 }
};
```

#### Change Game Canvas Size
Modify constants:
```javascript
const GAME_WIDTH = 400;          // Width in pixels
const GAME_HEIGHT = 600;         // Height in pixels
const BASKET_WIDTH = 60;         // Basket width
const BASKET_HEIGHT = 50;        // Basket height
const FRUIT_SIZE = 40;           // Fruit size
```

### Performance Optimization

**Current Optimizations:**
- RequestAnimationFrame untuk smooth 60 FPS
- Efficient collision detection (AABB)
- Image caching untuk reduced memory usage
- LocalStorage untuk persistent data
- CSS transforms untuk hardware acceleration

**Potential Improvements:**
- WebWorker untuk fruit physics
- Canvas offscreen rendering
- Sprite sheet untuk images
- Audio system dengan Web Audio API
- Mobile app wrapper (Cordova/React Native)

### Browser Support

**Fully Supported:**
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

**Partial Support:**
- IE 11 (no CSS Grid, limited flexbox)
- Older mobile browsers

**Features Used:**
- Canvas 2D API
- LocalStorage
- RequestAnimationFrame
- CSS Flexbox
- CSS Grid (for layouts)
- ES6+ JavaScript

### Adding New Features

#### 1. Add New Fruit Type
```javascript
// 1. Add to fruitTypes
const fruitTypes = {
  newFruit: { points: 2, hp: 1, image: 'new_fruit' }
};

// 2. Add image to MODULE_CLIENT_SIDE_MEDIA/new_fruit.png

// 3. Update spawn probability weights
const weights = [30, 30, 15, 20, 5, 10]; // Add weight for new fruit

// 4. Add to types array
const types = ['apple', 'avocado', 'golden_apple', 'trash', 'bomb', 'newFruit'];
```

#### 2. Add New Difficulty
```javascript
// 1. Add to difficultySettings
const difficultySettings = {
  extreme: { spawnRate: 500, fallSpeed: 5, maxHP: 2 }
};

// 2. Add button to HTML menu
<button class="diff-btn" data-difficulty="extreme">Extreme</button>

// 3. Update JavaScript event listener (already handles all data-difficulty)
```

#### 3. Add Sound Effects
```javascript
// Create audio element
const sounds = {
  catch: new Audio('sounds/catch.mp3'),
  gameOver: new Audio('sounds/gameover.mp3')
};

// Play sound when fruit caught
sounds.catch.play();
```

---

## License & Credits

**Game Created:** February 2026  
**Type:** Educational/Arcade Game  
**License:** MIT License (Free to use & modify)

### Assets:
- Graphics: Provided in MODULE_CLIENT_SIDE_MEDIA
- Fonts: Google Fonts (Fredoka, Sour Grape)
- Framework: Vanilla JavaScript (No dependencies)

### Special Thanks:
- Built with best practices for modern web development
- Responsive design for all devices
- Professional UI/UX standards

---

## Support & Contact

### Getting Help:
1. Check Troubleshooting section
2. Review Console for error messages
3. Verify file structure & paths
4. Try different browser/device

### Reporting Issues:
- Check if issue already documented
- Provide detailed description
- Include browser/device info
- Share error messages from console

---

## Version History

### v1.0.0 (Current)
- ✅ Initial release
- ✅ Core game mechanics
- ✅ 3 difficulty levels
- ✅ Leaderboard system
- ✅ Responsive design
- ✅ Complete documentation

---

## Quick Reference

### Controls:
| Action | Key |
|--------|-----|
| Move Left | A |
| Move Right | D |
| Pause | ESC |

### Fruit Effects:
| Fruit | Points | Health | Type |
|-------|--------|--------|------|
| Apple | +1 | 0 | Common |
| Avocado | +1 | 0 | Common |
| Golden Apple | +3 | +1 | Rare |
| Trash | -5 | -1 | Uncommon |
| Bomb | 0 | -∞ | Rare |

### Difficulty Stats:
| Level | Spawn | Speed | MaxHP |
|-------|-------|-------|-------|
| Easy | 3s | 1x | 5 |
| Medium | 2s | 2x | 4 |
| Hard | 1s | 3x | 3 |

---

**Happy Gaming! 🍎🎮**
