# QQ Bot Website Deployment Guide

## Overview

This is a static website for the QQ Bot project. It's built with semantic HTML5, Tailwind CSS, and vanilla JavaScript. No build step is required.

## Project Structure

```
qq-bot-page/
├── index.html          # Main website file
├── DEPLOY.md          # This deployment guide
└── references/        # Project reference documentation
```

## Deployment Options

### Option 1: GitHub Pages (Recommended)

1. Create a new repository named `qq-bot-page` on GitHub
2. Push this code to the repository:
   ```bash
   git init
   git add index.html DEPLOY.md
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
- **Fast Loading**: Uses CDN for Tailwind CSS and Font Awesome
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

The site uses a gradient theme (purple-blue). Edit the Tailwind config:

```javascript
tailwind.config = {
  theme: {
    extend: {
      colors: {
        primary: {
          // Your custom colors
        }
      }
    }
  }
}
```

## Performance

- Single HTML file with no external dependencies except CDN resources
- Tailwind CSS loaded via CDN (can be self-hosted for production)
- Font Awesome icons via CDN
- Google Fonts (Inter) via CDN
- Intersection Observer for scroll animations
- No JavaScript framework required

## Browser Support

- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

## Local Development

Simply open `index.html` in a browser. No build step or local server required.

For a local server (optional):
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