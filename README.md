# Classic Flash Games Website

A simple static website to play old Flash (.swf) games using Ruffle, a Flash Player emulator.

## ?? Features

- Play 4 classic Flash games in modern browsers
- No Flash Player required - uses Ruffle emulator
- Fully static - no server-side code needed
- Works locally or on any web host
- Responsive design
- Beautiful gradient UI

## ?? File Structure

```
Flash Website/
+-- index.html          # Main website with 4 game slots
+-- test-demo.html      # Test page to verify Ruffle works
+-- games/              # Create this folder for your .swf files
�   +-- game1.swf
�   +-- game2.swf
�   +-- game3.swf
�   +-- game4.swf
+-- README.md          # This file
```

## ?? Quick Start

### Step 1: Test Ruffle
1. Open `test-demo.html` in your browser to verify Ruffle is working.  Adjust line 184 to point to a game file
2. You should see a "Ruffle Ready!" message

### Step 2: Add Your Games
1. Create a folder called `games` in this directory
2. Add your .swf files to the games folder:
   - `game1.swf`
   - `game2.swf`
   - `game3.swf`
   - `game4.swf`

### Step 3: Edit index.html
1. Open `index.html` in a text editor
2. For each game, uncomment the `<ruffle-player>` line and remove the placeholder div
3. Update the game titles and descriptions

**Example for Game 1:**
```html
<!-- BEFORE (placeholder) -->
<div class="game-container">
    <div class="placeholder">
        Place your .swf file at:<br>
        <strong>games/game1.swf</strong>
    </div>
    <!-- <ruffle-player src="games/game1.swf"></ruffle-player> -->
</div>

<!-- AFTER (with game) -->
<div class="game-container">
    <ruffle-player src="games/game1.swf"></ruffle-player>
</div>
```

### Step 4: Open in Browser
Simply open `index.html` in any modern browser (Chrome, Firefox, Edge, Safari)

## ?? Hosting Options

### Local Use
- Just open `index.html` in your browser
- No web server required!

### Host Online
Upload all files to any web host:
- GitHub Pages
- Netlify
- Vercel
- Any traditional web hosting

## ?? Customization

### Change Game Titles
Edit the `<h2 class="game-title">` tags in `index.html`

### Change Descriptions
Edit the `<p class="game-description">` tags

### Change Colors
Modify the CSS in the `<style>` section:
- Background gradient: `background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);`
- Border colors: `border: 3px solid #667eea;`

### Add More Games
Copy and paste a `.game-card` div and update the game number

## ?? Where to Find .swf Games

- Archive.org (Internet Archive)
- Flashpoint Archive
- Your personal collection
- **Note:** Only use games you have permission to distribute

## ? Browser Compatibility

Ruffle works on:
- ? Chrome/Edge (latest)
- ? Firefox (latest)
- ? Safari (latest)
- ? Opera (latest)

Requires WebAssembly support (all modern browsers have this)

## ?? Troubleshooting

**Game doesn't load:**
- Check that the .swf file exists in the `games` folder
- Check that the filename matches exactly (case-sensitive)
- Check browser console for errors (F12)

**Ruffle doesn't load:**
- Ensure you have an internet connection (Ruffle loads from CDN)
- Check browser console for errors
- Try test-demo.html to verify Ruffle works

**Game displays incorrectly:**
- Some complex Flash games may not be fully compatible with Ruffle yet
- Check [Ruffle Compatibility](https://ruffle.rs/compatibility) for known issues

## ?? Resources

- [Ruffle Official Site](https://ruffle.rs/)
- [Ruffle GitHub](https://github.com/ruffle-rs/ruffle)
- [Flashpoint Archive](https://bluemaxima.org/flashpoint/)

## ?? License

This template is free to use. Ruffle is open source (MIT/Apache-2.0).

Make sure you have the rights to use any .swf games you add!
