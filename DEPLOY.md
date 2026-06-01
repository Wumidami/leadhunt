# LeadHunt — Deploy Instructions

## Push to GitHub (2 mins)

1. Go to https://github.com/new
2. Name it: `leadhunt` — set to Public — skip README
3. Copy your repo URL (e.g. https://github.com/wumidami/leadhunt)
4. Run in terminal:

```bash
git remote add origin https://github.com/YOUR_USERNAME/leadhunt.git
git push -u origin main
```

## Free Hosting Options (all 1-click after GitHub push)

### 1. GitHub Pages (FREE — github.io URL)
- Go to your repo → Settings → Pages
- Source: Deploy from branch → main → / (root)
- URL: https://YOUR_USERNAME.github.io/leadhunt

### 2. Netlify (FREE — netlify.app URL, best option)
- Go to https://netlify.com → "Add new site" → "Import from Git"
- Connect GitHub → pick leadhunt repo → Deploy
- URL: https://leadhunt-pdified.netlify.app (customizable)

### 3. Cloudflare Pages (FREE — pages.dev URL, fastest CDN)
- Go to https://pages.cloudflare.com
- Connect GitHub → pick repo → Framework: None → Deploy
- URL: https://leadhunt.pages.dev

### 4. Render (FREE — render.com URL)
- Go to https://render.com → New Static Site
- Connect GitHub → Build command: (leave blank) → Publish dir: /
- URL: https://leadhunt.onrender.com

### 5. Surge.sh (FREE — deploy from terminal, no GitHub needed)
```bash
npm install -g surge
cd /path/to/leadhunt
surge . leadhunt-pdified.surge.sh
```

## Recommendation
**Netlify** = best for you. Drag-and-drop deploy (no GitHub needed),
custom domain support, instant HTTPS, and free analytics.
Just go to: https://app.netlify.com/drop and drag the leadhunt.html file.
