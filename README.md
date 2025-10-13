# Lukas Rueda - Portfolio Site

A professional portfolio website built with Hugo showcasing quantitative research, trading strategies, and technical projects. Features dynamic content management, responsive design, and production deployment on Proxmox.

## 🏗️ Architecture

- **Static Site Generator**: Hugo
- **CSS Framework**: Tailwind CSS
- **Theme**: Modified Blowfish theme with custom layouts
- **Deployment**: Nginx on Proxmox VM
- **Version Control**: Git with GitHub integration

## 📁 Project Structure

```
PORTFOLIO_SITE/
├── content/
│   ├── about/           # About page content
│   └── projects/        # Project markdown files
├── layouts/
│   ├── _default/        # Custom base layouts
│   └── projects/        # Project-specific templates
├── static/              # Static assets (images, CSS, resume)
├── themes/blowfish/     # Hugo theme (submodule)
├── hugo.toml           # Hugo configuration
└── .gitignore          # Excludes public/ and generated files
```

## 🚀 Local Development Setup

### Prerequisites & Initial Setup
```bash
# Install Hugo (if not already installed)
sudo apt install hugo

# Navigate to existing project directory
cd /home/lrud1314/PROJECTS_WORKING/PORTFOLIO_SITE

# Update submodules (if needed)
git submodule update --init --recursive
```

### Development Workflow
```bash
# Start development server (auto-rebuilds on changes)
hugo server -D

# View site at http://localhost:1313
# Server automatically reloads on file changes

# Stop server: Ctrl+C
```

### Making Content Changes
1. **Edit content**: Modify markdown files in `content/`
2. **Update layouts**: Modify templates in `layouts/`
3. **Add assets**: Place files in `static/`
4. **Test locally**: Verify changes at `localhost:1313`

## 🏢 Production Deployment (Proxmox)

### Deployment Workflow

#### 1. Local Development & Push
```bash
# After making changes locally
git add .
git commit -m "Description of changes"
git push origin master
```

#### 2. Server Update
```bash
# SSH into server
ssh root@your-server-ip

# Navigate to site directory
cd /var/www/html/

# Pull latest changes
git pull origin master

# Rebuild site
hugo --minify

# Reload web server
sudo systemctl reload nginx

# Verify deployment
curl -I localhost
```

## 📝 Content Management

### Adding New Projects
1. Create new markdown file in `content/projects/`
2. Use YAML frontmatter for structured data
3. Reference images in `static/images/projects/`

### Project Frontmatter Template
```yaml
---
title: "Project Title"
status: "🟦 In Progress"
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
Edit `content/about/_index.md` and use bullet points for role descriptions:
```markdown
**Role Title** | *Company* | *Dates*
- Achievement or responsibility
- Another key point
- Third accomplishment
```

## 🎨 Styling & Layout

### Custom CSS
- Global styles: `static/css/custom.css`
- Layout-specific styles: Embedded in `layouts/` templates

### Project Tiles Features
- Fixed 500px height with scrolling
- Responsive design with scroll indicators
- Dynamic content from frontmatter
- Professional typography and spacing

### Key Layout Files
- `layouts/_default/baseof.html` - Base template
- `layouts/projects/list.html` - Projects page layout
- `layouts/_default/single.html` - Individual project pages

## 🔧 Troubleshooting

### Common Issues

**Git ownership errors on server:**
```bash
git config --global --add safe.directory /var/www/html
```

**Hugo not found:**
```bash
apt install hugo -y
```

**Network connectivity issues on server:**
```bash
echo "nameserver 8.8.8.8" >> /etc/resolv.conf
```

**Server not reflecting changes:**
```bash
hugo --minify
sudo systemctl reload nginx
```

**Development server issues locally:**
```bash
# Kill any existing Hugo processes
pkill hugo

# Restart development server
hugo server -D
```

### File Permissions (Server)
Ensure proper ownership on server:
```bash
chown -R www-data:www-data /var/www/html/public/
```

## 📊 Site Features

### Dynamic Content
- **Thesis Project**: LSTM Bitcoin volatility forecasting with academic justifications
- **Trading Strategies**: Quantitative analysis with performance metrics
- **Professional Experience**: Structured role descriptions with achievements

### Technical Highlights
- Mobile-responsive design
- SEO-optimized structure
- Fast loading with minified assets
- Clean URLs and navigation
- Professional typography

### Performance
- Static site generation for optimal speed
- CDN-ready asset structure
- Minified CSS and HTML
- Optimized images and resources

## 🔄 Best Practices

### Development
1. Always test changes locally before pushing
2. Use descriptive commit messages
3. Keep frontmatter consistent across projects
4. Optimize images before adding to `static/`

### Deployment
1. Use `hugo --minify` for production builds
2. Always reload nginx after updates
3. Verify site functionality after deployment
4. Monitor server logs for issues

### Content
1. Update resume in `static/images/` when needed
2. Maintain consistent formatting in project descriptions
3. Use proper YAML syntax in frontmatter
4. Keep technology lists current and relevant

---

**Live Site**: Access via your Proxmox server IP  
**Repository**: https://github.com/lrud1314/PORTFOLIO_SITE  
**Local Development**: /home/lrud1314/PROJECTS_WORKING/PORTFOLIO_SITE  
**Last Updated**: October 2025

## Recent Progress
- Projects page now features three projects:
	- Master's Thesis: Modeling Bitcoin's Implied Volatility Using Machine Learning (In Progress)
	- Credit Market Volatility Research (Completed)
	- ES Futures VPOC Strategy Backtester (Completed)
- Each project entry includes:
	- Status flag (emoji) with improved spacing and font size
	- Overview, Objectives, and Technologies Used sections
	- Visually distinct GitHub links for completed projects
- Academic context and subtitle added for thesis project
- Consistent formatting and whitespace across all entries
- Carousel for multi-image projects; modal image enlargement for all
- Custom CSS and inline styles for layout and link styling
- Visual separation between projects using horizontal rules

## About Page Redesign
- Integrated Tailwind CSS for modern utility-first styling
- Centered About Me tile with social icons
- Education and Experience sections now use visually robust, scrollable tiles
- Real education and experience data with institution logos (locally hosted)
- Each education entry is full width, left justified, and visually separated
- Experience entries styled for clarity and consistency
- Vertical scroll enabled for both tiles, with dynamic scroll indicator (← Scroll)
- 

## To Do
- Add more projects and automate image integration
- Further refine mobile responsiveness
- Add analytics or contact options
- Polish visual design and spacing as needed
- Continue About page polish and add new sections as needed

---

See the [Projects](./content/projects/_index.md) page for ongoing work.
