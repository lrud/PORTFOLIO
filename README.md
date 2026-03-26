# Lukas Rueda - Portfolio Site

A professional portfolio website built with Hugo showcasing quantitative research, trading strategies, and technical projects. Features dynamic content management, responsive design, and production deployment on Proxmox.

## Architecture

- **Static Site Generator**: Hugo
- **CSS Framework**: Tailwind CSS
- **Theme**: hello-friend-ng (customized)
- **Deployment**: Nginx on Proxmox VM
- **CDN/Cache**: Cloudflare
- **Version Control**: Git with GitHub integration

## Project Structure

```
PORTFOLIO_SITE/
├── content/
│   ├── about/           # About page content
│   └── projects/        # Project markdown files
├── layouts/
│   ├── about/           # About page templates
│   ├── _default/        # Custom base layouts
│   └── projects/        # Project-specific templates
├── static/              # Static assets (images, CSS, resume)
├── themes/hello-friend-ng/  # Hugo theme (submodule)
├── hugo.toml            # Hugo configuration
└── .gitignore           # Excludes public/ and generated files
```

## Production Deployment (Proxmox)

### Local to Server Workflow

```bash
# 1. Make changes locally and test
hugo server -D

# 2. Commit and push to GitHub
git add .
git commit -m "Description of changes"
git push origin master

# 3. SSH into server and update
ssh root@your-server-ip
cd /var/www/html/
git pull origin master
hugo --gc --minify
sudo systemctl reload nginx

# 4. Purge Cloudflare cache (important!)
# Go to Cloudflare dashboard → Caching → Configuration → Purge Everything
# Or via API:
curl -X POST "https://api.cloudflare.com/client/v4/zones/YOUR_ZONE_ID/purge_cache" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  --data '{"purge_everything":true}'
```

> **Note:** After deployment, always purge Cloudflare cache. Old CSS/JS will be served otherwise.

## Content Management

### Adding New Projects
1. Create new markdown file in `content/projects/`
2. Use YAML frontmatter for structured data
3. Reference images in `static/images/projects/`

### Project Frontmatter Template
```yaml
---
title: "Project Title"
status: "In Progress"
subtitle: "Project Subtitle"
overview: "Brief project description"
objectives:
  - "First objective"
  - "Second objective"
technologies: "Python, Django, PostgreSQL"
github: "https://github.com/username/repo"
---
```

### Experience Section Updates
Edit `content/about/_index.md` and use bullet points for role descriptions.

## Styling & Layout

### Custom CSS
- Global styles: `static/css/custom.css`
- Layout-specific styles: Embedded in `layouts/` templates

### Key Layout Files
- `layouts/_default/baseof.html` - Base template
- `layouts/about/list.html` - About page layout
- `layouts/projects/list.html` - Projects page layout
- `layouts/_default/single.html` - Individual project pages

## Site Features

- Mobile-responsive design with dark mode
- SEO-optimized structure
- Fast loading with minified assets
- Clickable headshot with modal enlargement
- Project carousels for multi-image displays
- Scrollable education/experience tiles

## Recent Updates

### March 2026
- Added headshot to about page with clickable modal
- Headshot positioned right of name/subtitle with balanced spacing
- Dark mode set as default theme
- Resume button now downloads PDF
- Fixed white flash on page navigation
- Email updated to principlesOS@pm.me

### October 2025
- Projects page features three projects:
  - Master's Thesis: Modeling Bitcoin's Implied Volatility Using Machine Learning (In Progress)
  - Credit Market Volatility Research (Completed)
  - ES Futures VPOC Strategy Backtester (Completed)
- About page redesign with Tailwind CSS
- Education and Experience scrollable tiles with institution logos
- Dark mode support
- Mobile responsive design

---

**Live Site**: https://www.principles0s.com/  
**Repository**: https://github.com/lrud/PORTFOLIO.git
