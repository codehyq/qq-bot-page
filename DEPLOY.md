# QQ Bot Website Deployment Guide

## Overview

This is a static website for the QQ Bot project. It's built with semantic HTML5, prebuilt Tailwind CSS, and vanilla JavaScript.

## Project Structure

```
qq-bot-page/
├── index.html          # Main website file
├── static/
│   ├── styles.min.css  # Prebuilt Tailwind CSS
│   └── logo.jpg        # Site logo
├── DEPLOY.md           # This deployment guide
└── tailwind.config.js  # Tailwind config (for rebuilding CSS)
```

## Deployment Options

### Option 1: GitHub Pages (Recommended)

1. Create a new repository named `qq-bot-page` on GitHub
2. Push this code to the repository:
   ```bash
   git init
   git add index.html DEPLOY.md static/
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/codehyq/qq-bot-page.git
   git push -u origin main
   ```
3. Go to repository **Settings** > **Pages**
4. Under "Source", select **Deploy from a branch** and choose **main** with **/ (root)**
5. Your site will be available at `https://codehyq.github.io/qq-bot-page/`

### Option 2: Vercel

1. Install Vercel CLI:
   ```bash
   npm i -g vercel
   ```
2. Run in the project directory:
   ```bash
   vercel
   ```
3. Follow the prompts to deploy

### Option 3: Netlify

1. Go to [netlify.com](https://netlify.com)
2. Drag and drop the `index.html` file to deploy
3. Your site will be live instantly

### Option 4: Traditional Web Hosting

Simply upload `index.html` to your web server's document root.

## Features

- **Responsive Design**: Works on desktop, tablet, and mobile devices
- **Dark Mode**: Toggle between light and dark themes
- **Multi-language**: Supports Chinese (zh-CN) and English (en)
- **SEO Optimized**: Includes meta tags, Open Graph, and Twitter cards
- **Fast Loading**: Prebuilt Tailwind CSS (~20KB), non-blocking Font Awesome, optimized font loading
- **Interactive**: Smooth animations and FAQ accordions
- **GitHub Integration**: Links to the main project repository

## Customization

### Changing the GitHub Repository

Search for `codehyq/qq-bot` in `index.html` and replace with your repository URL.

### Adding Languages

Add new translations in the `translations` JavaScript object:

```javascript
const translations = {
  zh: { ... },
  en: { ... },
  ja: { /* Japanese translations */ }
};
```

### Modifying Colors

The site uses a gradient theme (purple-blue). Edit `tailwind.config.js` and rebuild:

```bash
npx tailwindcss@3 build -i <(echo '@tailwind base; @tailwind components; @tailwind utilities;') -o static/styles.min.css --minify --content index.html
```

## Performance

- Prebuilt Tailwind CSS (~20KB minified, replaces ~300KB+ runtime compiler)
- Font Awesome loaded non-blocking via `media="print" onload` pattern
- Google Fonts with reduced weights (400;600;700) and `display=swap`
- Resource hints: `preconnect`, `preload` for critical assets
- `requestAnimationFrame` throttled scroll handler with `passive: true`
- IntersectionObserver with `unobserve` after animation triggers
- DOM element caching to avoid repeated `getElementById` calls
- Event delegation for FAQ accordion and mobile menu
- Image `width`/`height` attributes to prevent layout shift
- No JavaScript framework required

## Browser Support

- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

## Local Development

### Rebuilding CSS (after modifying index.html)

```bash
npx tailwindcss@3 build -i <(echo '@tailwind base; @tailwind components; @tailwind utilities;') -o static/styles.min.css --minify --content index.html
```

### Preview
```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx serve

# Using PHP
php -S localhost:8000
```

Then open `http://localhost:8000` in your browser.

## License

This website is part of the QQ Bot project and is released under the MIT License.