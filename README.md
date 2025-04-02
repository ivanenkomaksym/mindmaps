# Mindmap Visualizer with Markmap

This repository provides an automated pipeline for visualizing Markdown-based mindmaps written in Markdown using Markmap on every commit. It converts `.md` files in the `maps/` directory into interactive **Markmap** diagrams and deploys them to **Cloudflare Pages** for easy sharing and access.

🔗 https://mindmaps.ivanenkomak.com

## 🔧 Features

- ✅ Automated Markdown to Markmap conversion – Uses GitHub Actions to generate .html files from Markdown mindmaps.
- ✅ Dynamic Index Page – Generates index.html with links to all visualized mindmaps.
- ✅ Cloudflare Pages Deployment – Publishes all generated mindmaps as a static website.
- ✅ Lightweight & Fast – No server required; everything runs in a static environment.

## 📂 Folder Structure

```
/maps              # Raw Markdown mindmaps  
  ├── azure.md  
  ├── aws.md  
  ├── gcp.md  

/public            # Auto-generated static files  
  ├── maps/        # Contains generated Markmap visualizations  
  │   ├── azure.html  
  │   ├── aws.html  
  │   ├── gcp.html  
  ├── index.html   # Landing page with links to all mindmaps  
```

## 🚀 How It Works

1. Add a new Markdown mindmap to the maps/ folder.
2. Push to GitHub – The workflow automatically:
   - Converts .md files to Markmap HTML
   - Updates public/index.html with new links
   - Deploys to Cloudflare Pages
   - Access your mindmaps online via the Cloudflare Pages URL.

## 🛠️ Local Development

You can manually generate and preview Markmaps using:

```bash
npm install -g markmap-cli
markmap maps/example.md -o public/maps/example.html
```

Then open `public/maps/example.html` in your browser.