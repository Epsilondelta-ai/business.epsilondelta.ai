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

## Original Theme

This is a Hugo port of [Mediumish Jekyll Theme](https://github.com/wowthemesnet/mediumish-theme-jekyll) by WowThemes.net.

## License

See LICENSE.txt

