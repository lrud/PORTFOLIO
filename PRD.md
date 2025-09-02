# Personal Portfolio Site PRD

## Project Overview
- **Goal:** Build a minimal personal portfolio website using Hugo, hosted on your existing server infrastructure.
- **Purpose:** Present yourself and your projects in a clear, accessible format.

## Core Features
- **Navigation:**  
  - Static top navigation bar, always visible.
  - Toggle menu for switching between: About Me (landing page), Projects.

- **Pages/Sections:**  
  - **About Me / Overview:**  
    - Landing page with brief introduction, high-level overview of experience, and profile image (optional).
    - Social media links for GitHub and LinkedIn.
  - **Projects:**  
    - List of projects with titles, short descriptions, and links (if available).
    - Support for images/screenshots and external links for each project.

- **Design:**  
  - Clean, simple layout.
  - Responsive (works on desktop and mobile).
  - Use prebuilt Hugo themes/components as much as possible.

## Technical Requirements
- **Framework:** Hugo static site generator.
- **Theme:** Use the open-source [hello-friend-ng](https://github.com/rhazdon/hugo-theme-hello-friend-ng) Hugo theme for a minimalist, responsive design.
- **Hosting:** Self-hosted on your existing server.
- **Content Management:** Markdown files for each section.
- **Navigation:** Static menu using theme's built-in navigation.
- **Accessibility:** Basic accessibility (readable fonts, contrast, keyboard navigation).
- **Exposure:** Use Cloudflared Zero Trust Tunnel to securely expose the site to the internet.
- **Traffic:** Designed for low traffic, personal use.
- **Security:** No dynamic backend; access managed via Cloudflare Zero Trust policies.

## Non-Functional Requirements
- **Performance:** Fast load times (static HTML).
- **Maintainability:** Easy to update content via Markdown.
- **Security:** No direct exposure of server IP; access managed through Cloudflare.

## Codebase Design Aspects
- Codebase should be simple and not overly complex.
- Each script or component should be no more than 300-400 lines of code.
- Minimal comments throughout the codebase; code should be self-explanatory.
- All code and content should be tracked with Git for easy backup and collaboration.
- Project should follow a clear, logical directory structure (e.g., separating content, static assets, and configuration).
- Codebase should allow for easy addition of new sections or features in the future (extensibility).
- Use only well-maintained, open-source dependencies; keep them minimal.
- Site configuration should be centralized (e.g., in `config.toml` for Hugo).
- Build and deployment process should be simple and documented (e.g., a short README).

## Milestones
1. Select and set up Hugo theme.
2. Configure navigation/menu.
3. Create and populate About Me and Projects sections.
4. Test responsiveness and accessibility.
5. Deploy to local server and expose via Cloudflared Tunnel.

## Success Criteria
- Both sections are accessible via the static top menu.
- Content is clear, readable, and easy to update.
- Site loads quickly and works on all devices.
- Uses prebuilt solutions wherever possible.
- Securely exposed to the internet via Cloudflared Zero Trust.
