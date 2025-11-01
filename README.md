# Mediumish Hugo Theme

A Hugo port of the popular Mediumish Jekyll theme - a Medium-styled responsive blog template.

## Features

- Bootstrap 4.x
- Responsive design
- Featured posts
- Categories and tags
- Author profiles
- Pagination
- Search functionality (Lunr.js)
- Disqus comments
- Google Analytics support
- Syntax highlighting
- Star ratings

## Requirements

- Hugo Extended v0.112.0 or later

## Quick Start

### Installation

1. Install Hugo Extended from [Hugo releases](https://github.com/gohugoio/hugo/releases)

2. Clone this repository:
```bash
git clone <repository-url>
cd business.epsilondelta.ai
```

### Development

Run the Hugo development server:
```bash
hugo server -D
```

The site will be available at `http://localhost:1313/`

### Build

Build the static site:
```bash
hugo
```

The generated site will be in the `public/` directory.

## Configuration

Site configuration is in `hugo.toml`. Key settings:

- `baseURL`: Your site's base URL
- `title`: Site title
- `params.name`: Site name
- `params.description`: Site description
- `params.authors`: Author profiles
- `paginate`: Number of posts per page

## Content Structure

- `content/posts/`: Blog posts
- `content/about.md`: About page
- `static/`: Static assets (images, fonts, etc.)
- `layouts/`: Template files
- `assets/`: CSS/SCSS and JS files

## Adding Content

Create a new post:
```bash
hugo new posts/my-new-post.md
```

## Deployment

### GitHub Pages

This site is configured for automatic deployment to GitHub Pages using GitHub Actions.

#### Setup

1. **Enable GitHub Pages** in your repository:
   - Go to Settings → Pages
   - Source: Select "GitHub Actions"
   - Custom domain: `business.epsilondelta.ai` (optional)

2. **DNS Configuration** (for custom domain):
   - Add A records pointing to GitHub Pages IPs:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - Or add a CNAME record pointing to `[username].github.io`

3. **Deploy**:
   ```bash
   git add .
   git commit -m "Your commit message"
   git push origin main
   ```

GitHub Actions will automatically build and deploy your site.

#### Deployment Process

- Workflow file: `.github/workflows/hugo.yml`
- Triggers: Push to `main` branch or manual workflow dispatch
- Build time: ~2-3 minutes
- Hugo version: v0.147.2 Extended

#### Monitoring Deployment

- Check Actions tab in GitHub repository
- View deployment status and logs
- Site URL: https://business.epsilondelta.ai/

#### Local Testing Before Deploy

Always test locally before pushing:
```bash
hugo server -D
# Visit http://localhost:1313
```

## Original Theme

This is a Hugo port of [Mediumish Jekyll Theme](https://github.com/wowthemesnet/mediumish-theme-jekyll) by WowThemes.net.

## License

See LICENSE.txt

