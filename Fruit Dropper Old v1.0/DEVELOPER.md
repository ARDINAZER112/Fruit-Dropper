# 👨‍💻 Fruit Dropper - Developer Setup Guide

Complete guide for developers who want to understand, customize, or extend the game.

---

## 📑 Table of Contents

1. [Project Overview](#project-overview)
2. [File Structure](#file-structure)
3. [Understanding the Code](#understanding-the-code)
4. [Customization Guide](#customization-guide)
5. [Adding Features](#adding-features)
6. [Debugging Tips](#debugging-tips)
7. [Performance Optimization](#performance-optimization)

---

## Project Overview

### Tech Stack
- **Language:** Vanilla JavaScript (ES6+)
- **Rendering:** HTML5 Canvas 2D API
- **Styling:** CSS3 (Flexbox, Grid, Custom Properties)
- **Storage:** Browser LocalStorage API
- **No dependencies:** Pure web technologies

### Architecture Pattern
**State-driven game loop:**
```
Input → State Update → Render → RequestAnimationFrame Loop
```

### Key Concepts
- Single game state object for all data
- RequestAnimationFrame for 60 FPS
- AABB collision detection
- Canvas 2D rendering
- Event-driven architecture

---

## File Structure

### Main Game File: `index.html`

The entire game is contained in a single HTML file with embedded CSS and JavaScript.

```
<html>
  <head>
    <meta tags>
    <style>
      /* All CSS here */
    </style>
  </head>
  <body>
    <!-- HTML Elements -->
    <script>
      /* All JavaScript here */
    </script>
  </body>
</html>
```

### Media Files: `asset/`

```
fruit.png (40x40 pixels each)
├── apple.png          - Red apple (common)
├── avocado.png        - Green avocado (common)
├── basket.png         - Basket sprite (60x50)
├── bomb.png           - Bomb fruit (rare)
├── golden_apple.png   - Golden apple (special)
└── trash.png          - Trash item (uncommon)
```

### Documentation Files

```
├── README.md              - Quick start guide
├── DOCUMENTATION.md       - Complete documentation
└── DEVELOPER.md           - This file
```

---

## Understanding the Code

### 1. Game State Management

The entire game state is stored in one object:

```javascript
let gameState = {
  // Game Status
  isPlaying: false,           // Game running?
  isPaused: false,            // Game paused?
  
  // Player Info
  playerName: '',             // Player's name
  difficulty: 'easy',         // Selected difficulty
  
  // Game Progress
  score: 0,                   // Current score
  hp: 3,                      // Health points
  maxHP: 3,                   // Max health
  gameTime: 0,                // Time elapsed (ms)
  
  // Game Settings
  backgroundColor: '#2d3436', // Custom BG color
  spawnRate: 3000,            // Fruit spawn interval
  fallSpeed: 1,               // Fall speed multiplier
  
  // Game Objects
  fruits: [],                 // Array of fruits
  basket: { x: 170, y: 550 }, // Basket position
  keys: {}                    // Pressed keys state
};
```

### 2. Difficulty Settings

```javascript
const difficultySettings = {
  easy: {
    spawnRate: 3000,   // Spawn every 3 seconds
    fallSpeed: 1,      // Normal speed
    maxHP: 5           // More health
  },
  medium: {
    spawnRate: 2000,   // Spawn every 2 seconds
    fallSpeed: 2,      // 2x faster
    maxHP: 4           // Medium health
  },
  hard: {
    spawnRate: 1000,   // Spawn every 1 second
    fallSpeed: 3,      // 3x faster
    maxHP: 3           // Less health
  }
};
```

### 3. Fruit Types Definition

```javascript
const fruitTypes = {
  apple: {
    points: 1,         // Points awarded
    hp: 0,             // Health change
    image: 'apple'     // Image file (without .png)
  },
  avocado: {
    points: 1,
    hp: 0,
    image: 'avocado'
  },
  golden_apple: {
    points: 3,         // Bonus points!
    hp: 1,             // Heals!
    image: 'golden_apple'
  },
  trash: {
    points: -5,        // Negative points
    hp: -1,            // Damages health
    image: 'trash'
  },
  bomb: {
    points: 0,
    hp: -999,          // Instant game over
    image: 'bomb'
  }
};
```

### 4. Game Loop

```javascript
function gameLoop() {
  // If paused, just loop without updating
  if (gameState.isPaused) {
    requestAnimationFrame(gameLoop);
    return;
  }

  // If not playing, stop
  if (!gameState.isPlaying) {
    return;
  }

  // Update game logic
  updateGame();
  
  // Render to canvas
  drawGame();
  
  // Schedule next frame (~60 FPS)
  requestAnimationFrame(gameLoop);
}
```

### 5. Update Logic

```javascript
function updateGame() {
  // Handle player input
  const moveSpeed = 5;
  if (gameState.keys['a'] && gameState.basket.x > 0) {
    gameState.basket.x -= moveSpeed;
  }
  if (gameState.keys['d'] && gameState.basket.x < GAME_WIDTH - BASKET_WIDTH) {
    gameState.basket.x += moveSpeed;
  }

  // Update all fruits
  gameState.fruits.forEach((fruit, index) => {
    fruit.y += gameState.fallSpeed; // Fall
    
    // Check collision with basket
    if (checkCollision(fruit)) {
      // Apply fruit effect
      const effect = fruitTypes[fruit.type];
      gameState.score += effect.points;
      gameState.hp += effect.hp;
      
      // Remove fruit
      gameState.fruits.splice(index, 1);
      
      // Check game over
      if (gameState.hp <= 0) {
        endGame();
      }
    }
    // Check if fruit missed
    else if (fruit.y > GAME_HEIGHT) {
      gameState.hp -= 1; // Penalty for missing
      gameState.fruits.splice(index, 1);
      
      if (gameState.hp <= 0) {
        endGame();
      }
    }
  });

  // Spawn new fruits based on spawn rate
  gameState.gameTime += 16; // ~60fps = 16ms per frame
  if (gameState.gameTime % gameState.spawnRate < 16) {
    spawnFruit();
  }

  // Update UI
  updateUI();
}
```

### 6. Collision Detection

```javascript
function checkCollision(fruit) {
  // AABB (Axis-Aligned Bounding Box) collision
  return (
    fruit.x < gameState.basket.x + BASKET_WIDTH &&
    fruit.x + fruit.width > gameState.basket.x &&
    fruit.y < gameState.basket.y + BASKET_HEIGHT &&
    fruit.y + fruit.height > gameState.basket.y
  );
}
```

### 7. Rendering

```javascript
function drawGame() {
  const ctx = canvas.getContext('2d');
  
  // Clear canvas with custom background
  ctx.fillStyle = gameState.backgroundColor;
  ctx.fillRect(0, 0, GAME_WIDTH, GAME_HEIGHT);

  // Draw all fruits
  gameState.fruits.forEach(fruit => {
    const image = images[fruitTypes[fruit.type].image];
    if (image.complete) { // Check if loaded
      ctx.drawImage(
        image,
        fruit.x, fruit.y,
        fruit.width, fruit.height
      );
    }
  });

  // Draw basket
  ctx.drawImage(
    images.basket,
    gameState.basket.x, gameState.basket.y,
    BASKET_WIDTH, BASKET_HEIGHT
  );
}
```

---

## Customization Guide

### 1. Change Color Scheme

Edit the CSS variables at the top of `<style>` tag:

```css
:root {
  --primary-color: #FF6B6B;      /* Main/Accent color */
  --secondary-color: #4ECDC4;    /* Secondary color */
  --accent-color: #FFE66D;       /* Highlight color */
  --dark-bg: #2D3436;            /* Dark background */
  --light-text: #F5F6FA;         /* Light text */
  --card-bg: #34495E;            /* Card background */
}
```

**Example - Dark theme:**
```css
:root {
  --primary-color: #E74C3C;      /* Red */
  --secondary-color: #3498DB;    /* Blue */
  --accent-color: #F1C40F;       /* Yellow */
  --dark-bg: #1A1A1A;            /* Very dark */
  --light-text: #ECF0F1;         /* Light gray */
}
```

### 2. Modify Game Canvas Size

Edit constants in JavaScript section:

```javascript
const GAME_WIDTH = 400;          // Change to 500 for wider
const GAME_HEIGHT = 600;         // Change to 700 for taller
const BASKET_WIDTH = 60;
const BASKET_HEIGHT = 50;
const FRUIT_SIZE = 40;
```

**Important:** Also update canvas element dimensions in HTML:
```html
<canvas id="gameCanvas" width="500" height="700"></canvas>
```

### 3. Adjust Basket Speed

Find in `updateGame()` function:

```javascript
const moveSpeed = 5;  // Pixels per frame
// Increase to 8 for faster movement
// Decrease to 3 for slower movement
```

### 4. Customize Fruit Spawn

Find `spawnFruit()` function and modify probability weights:

```javascript
const types = ['apple', 'avocado', 'golden_apple', 'trash', 'bomb'];
const weights = [30, 30, 15, 20, 5];  // Probabilities (%)

// To make bombs more common:
const weights = [25, 25, 15, 20, 15]; // 15% bombs instead of 5%

// To make golden apples rarer:
const weights = [35, 35, 5, 20, 5];   // 5% instead of 15%
```

### 5. Change Difficulty Settings

Modify `difficultySettings`:

```javascript
const difficultySettings = {
  easy: {
    spawnRate: 4000,   // Slower spawn
    fallSpeed: 0.8,    // Slower fall
    maxHP: 6           // More health
  },
  medium: {
    spawnRate: 2000,
    fallSpeed: 2,
    maxHP: 4
  },
  hard: {
    spawnRate: 800,    // Faster spawn
    fallSpeed: 4,      // Faster fall
    maxHP: 2           // Less health
  }
};
```

---

## Adding Features

### Add New Fruit Type

**Step 1:** Add image file to `asset/strawberry.png`

**Step 2:** Define fruit in `fruitTypes`:

```javascript
const fruitTypes = {
  // ... existing fruits ...
  strawberry: {
    points: 2,
    hp: 0,
    image: 'strawberry'
  }
};
```

**Step 3:** Update spawn probability:

```javascript
const types = ['apple', 'avocado', 'golden_apple', 'trash', 'bomb', 'strawberry'];
const weights = [25, 25, 15, 20, 5, 10];  // 10% for strawberry
```

**Step 4:** Update HTML How to Play section:

```html
<div class="how-to-play">
  🍓 Strawberry = +2 points<br>
  <!-- ... rest of instructions ... -->
</div>
```

### Add New Difficulty Level

**Step 1:** Add to `difficultySettings`:

```javascript
const difficultySettings = {
  // ... existing levels ...
  nightmare: {
    spawnRate: 500,    // Every 500ms
    fallSpeed: 5,      // 5x speed
    maxHP: 1           // 1 HP only
  }
};
```

**Step 2:** Add button in HTML menu:

```html
<div class="difficulty-buttons">
  <button class="diff-btn active" data-difficulty="easy">Easy</button>
  <button class="diff-btn" data-difficulty="medium">Medium</button>
  <button class="diff-btn" data-difficulty="hard">Hard</button>
  <button class="diff-btn" data-difficulty="nightmare">Nightmare</button>
</div>
```

Note: Event listeners already handle all `data-difficulty` values automatically!

### Add Sound Effects

**Step 1:** Create `sounds` object:

```javascript
const sounds = {
  catch: new Audio('sounds/catch.mp3'),
  miss: new Audio('sounds/miss.mp3'),
  gameOver: new Audio('sounds/gameover.mp3'),
  trash: new Audio('sounds/trash.mp3'),
  goldenApple: new Audio('sounds/goldenApple.mp3')
};
```

**Step 2:** Play sounds in appropriate places:

```javascript
// When fruit caught
if (checkCollision(fruit)) {
  const effect = fruitTypes[fruit.type];
  
  // Play appropriate sound
  if (fruit.type === 'golden_apple') {
    sounds.goldenApple.play();
  } else if (fruit.type === 'trash') {
    sounds.trash.play();
  } else {
    sounds.catch.play();
  }
  
  // ... rest of code ...
}

// When fruit missed
if (fruit.y > GAME_HEIGHT) {
  sounds.miss.play();
  gameState.hp -= 1;
}

// When game over
if (gameState.hp <= 0) {
  sounds.gameOver.play();
  endGame();
}
```

### Add Score Multiplier

**Step 1:** Add multiplier to game state:

```javascript
let gameState = {
  // ... existing properties ...
  scoreMultiplier: 1,  // 1x, 1.5x, 2x, etc.
  comboCount: 0        // Number of consecutive catches
};
```

**Step 2:** Update score logic:

```javascript
if (checkCollision(fruit)) {
  const effect = fruitTypes[fruit.type];
  const points = effect.points * gameState.scoreMultiplier;
  gameState.score += points;
  gameState.hp += effect.hp;
  
  // Increment combo
  gameState.comboCount++;
  
  // Increase multiplier every 5 catches
  if (gameState.comboCount % 5 === 0) {
    gameState.scoreMultiplier = Math.min(
      gameState.scoreMultiplier + 0.1,
      3.0 // Max 3x
    );
  }
  
  // ... rest of code ...
}
```

### Add Pause On Alt+Tab

```javascript
document.addEventListener('visibilitychange', () => {
  if (document.hidden && gameState.isPlaying && !gameState.isPaused) {
    pause();
  }
});
```

---

## Debugging Tips

### 1. Enable Console Logging

Add debugging to game loop:

```javascript
function gameLoop() {
  if (gameState.isPaused) {
    requestAnimationFrame(gameLoop);
    return;
  }

  if (!gameState.isPlaying) {
    return;
  }

  updateGame();
  drawGame();
  
  // Debug logging
  console.log(`Score: ${gameState.score}, HP: ${gameState.hp}, Fruits: ${gameState.fruits.length}`);
  
  requestAnimationFrame(gameLoop);
}
```

### 2. Inspect Game State

In browser console:

```javascript
// View entire game state
console.log(gameState);

// Monitor score
console.log('Score:', gameState.score);

// Check active fruits
console.log('Fruits:', gameState.fruits);

// Check image loading
Object.keys(images).forEach(key => {
  console.log(`${key}: ${images[key].complete ? '✓' : '✗'}`);
});
```

### 3. Test Collision Detection

Add visual collision box:

```javascript
function drawGame() {
  // ... existing code ...
  
  // Draw collision boxes (debug)
  if (DEBUG_MODE) {
    ctx.strokeStyle = 'red';
    ctx.lineWidth = 2;
    
    // Basket collision box
    ctx.strokeRect(
      gameState.basket.x,
      gameState.basket.y,
      BASKET_WIDTH,
      BASKET_HEIGHT
    );
    
    // Fruit collision boxes
    gameState.fruits.forEach(fruit => {
      ctx.strokeRect(fruit.x, fruit.y, fruit.width, fruit.height);
    });
  }
}
```

Then toggle with:
```javascript
let DEBUG_MODE = false;

// Toggle in console:
DEBUG_MODE = true;  // Enable debug drawing
```

### 4. Slow Motion Testing

Reduce frame rate:

```javascript
// Modify game loop to skip frames
let frameSkip = 0;
function gameLoop() {
  if (frameSkip++ % 6 !== 0) { // Every 6th frame
    requestAnimationFrame(gameLoop);
    return;
  }
  
  // ... rest of game loop ...
}
```

### 5. Freeze Fruit Spawn

```javascript
// In updateGame, comment out spawn logic:
// gameState.gameTime += 16;
// if (gameState.gameTime % gameState.spawnRate < 16) {
//   spawnFruit();
// }

// This freezes spawning for testing other mechanics
```

---

## Performance Optimization

### Current Optimizations

✅ **RequestAnimationFrame** - Syncs with screen refresh rate  
✅ **AABB Collision** - Fast O(n) detection  
✅ **Image Caching** - Preload images once  
✅ **LocalStorage** - Async data persistence  

### Potential Improvements

#### 1. Implement Object Pooling

Instead of creating/destroying fruits:

```javascript
class FruitPool {
  constructor(size = 20) {
    this.pool = [];
    for (let i = 0; i < size; i++) {
      this.pool.push({
        type: 'apple',
        x: 0,
        y: 0,
        width: FRUIT_SIZE,
        height: FRUIT_SIZE,
        active: false
      });
    }
  }

  get() {
    return this.pool.find(f => !f.active) || this.pool[0];
  }

  release(fruit) {
    fruit.active = false;
  }
}
```

#### 2. Spatial Partitioning

For many objects, use quadtree or grid:

```javascript
// Simple grid-based collision check
const gridSize = 100;
function getGridCell(x, y) {
  return {
    x: Math.floor(x / gridSize),
    y: Math.floor(y / gridSize)
  };
}
```

#### 3. Dirty Rectangle Rendering

Only redraw changed areas:

```javascript
let lastFruitCount = 0;
function drawGame() {
  // If fruit count changed, redraw all
  if (gameState.fruits.length !== lastFruitCount) {
    ctx.fillRect(0, 0, GAME_WIDTH, GAME_HEIGHT);
  }
  // ... draw fruits ...
}
```

#### 4. WebWorker for Physics

Move fruit physics to background thread:

```javascript
// main.js
const worker = new Worker('physics.js');

worker.onmessage = (e) => {
  gameState.fruits = e.data; // Updated positions
};

// Send fruits to worker
worker.postMessage({
  fruits: gameState.fruits,
  fallSpeed: gameState.fallSpeed
});
```

---

## Best Practices

### Code Style
- Use `const` by default, `let` for variables
- Single responsibility functions
- Clear naming conventions
- Comments for complex logic

### Performance
- Avoid frequent DOM manipulation
- Use RequestAnimationFrame for animations
- Profile before optimizing
- Test on real devices

### Accessibility
- Keyboard controls
- Color contrast ratios
- Focus indicators
- Error messages

### Testing
- Test on multiple browsers
- Check on different devices
- Verify touch controls work
- Check console for errors

---

## Resources

### JavaScript
- [MDN Canvas API](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)
- [MDN LocalStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)
- [RequestAnimationFrame](https://developer.mozilla.org/en-US/docs/Web/API/window/requestAnimationFrame)

### Game Development
- [Game Programming Patterns](https://gameprogrammingpatterns.com/)
- [2D Game Physics](https://www.gamedev.net/tutorials/programming/general/)

### Web Technologies
- [CSS Variables](https://developer.mozilla.org/en-US/docs/Web/CSS/--*)
- [CSS Grid & Flexbox](https://css-tricks.com/)
- [Responsive Design](https://web.dev/responsive-web-design-basics/)

---

**Happy Playing! 🚀**
