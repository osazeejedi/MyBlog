# Personal Blog

A clean, modern personal blog built with Hugo and the PaperMod theme. Designed for sharing thoughts on technology, programming, and personal growth.

## Features

- 🌙 **Dark theme by default** with light/dark mode toggle
- 📱 **Fully responsive** design for all devices
- ⚡ **Fast loading** with optimized static site generation
- 💬 **Comments system** ready (Disqus integration)
- 🎨 **Custom styling** with enhanced typography and visual elements
- 📊 **SEO optimized** with proper meta tags and structured data
- 🔍 **Search functionality** built-in
- 📝 **Markdown support** with syntax highlighting
- 🏷️ **Tags and categories** for content organization

## Site Structure

```
├── content/
│   ├── _index.md          # Home page
│   ├── about/             # About page
│   ├── posts/             # Blog posts
│   ├── projects/          # Projects showcase
│   └── contact/           # Contact information
├── static/
│   ├── css/
│   │   └── custom.css     # Custom styling
│   └── images/            # Images and media
├── layouts/
│   └── partials/
│       └── extend_head.html # Custom head elements
└── hugo.toml              # Site configuration
```

## Getting Started

### Prerequisites

- [Hugo](https://gohugo.io/installation/) (Extended version)
- [Git](https://git-scm.com/)

### Local Development

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd MyBlog
   ```

2. **Initialize submodules** (for the theme)
   ```bash
   git submodule update --init --recursive
   ```

3. **Start the development server**
   ```bash
   hugo server --buildDrafts
   ```

4. **Open your browser** and visit `http://localhost:1313`

### Creating Content

#### New Blog Post
```bash
hugo new content posts/my-new-post.md
```

#### New Project
```bash
hugo new content projects/my-project.md
```

## Customization

### Personal Information

Update the following files with your personal information:

1. **hugo.toml** - Site configuration
   - Change `title`, `author`, `description`
   - Update `baseURL` for production
   - Replace `disqusShortname` with your Disqus shortname

2. **content/about/index.md** - About page
   - Replace placeholder content with your story
   - Update technology lists and experience
   - Add your actual social media links

3. **content/_index.md** - Home page
   - Update the welcome message
   - Modify the "Currently Working On" section
   - Replace placeholder links

4. **content/contact/index.md** - Contact page
   - Update contact information
   - Replace social media links
   - Update location information

### Images

1. **Profile Photo**
   - Add your photo as `static/images/profile-photo.jpg`
   - Update the image reference in the About page

2. **Favicon**
   - Replace `static/favicon.ico` with your favicon
   - Add other icon sizes in the static directory

### Comments

1. **Set up Disqus**
   - Create a Disqus account
   - Get your shortname
   - Update `disqusShortname` in `hugo.toml`

2. **Alternative: Giscus (GitHub-based)**
   - Follow [Giscus setup guide](https://giscus.app/)
   - Update the comments configuration

### Styling

The site uses custom CSS in `static/css/custom.css`. You can:

- Modify colors and typography
- Adjust spacing and layout
- Add new component styles
- Customize the dark/light theme colors

### Menu Navigation

Update the menu in `hugo.toml`:

```toml
[[menu.main]]
  identifier = "new-page"
  name = "New Page"
  url = "/new-page/"
  weight = 50
```

## Deployment

### GitHub Pages

1. **Create a GitHub repository**
2. **Push your code**
3. **Set up GitHub Actions** for automatic deployment
4. **Configure custom domain** (optional)

### Netlify

1. **Connect your GitHub repository**
2. **Set build command**: `hugo --minify`
3. **Set publish directory**: `public`
4. **Deploy automatically** on git push

### Vercel

1. **Import your GitHub repository**
2. **Framework preset**: Hugo
3. **Deploy automatically** on git push

## Content Guidelines

### Blog Posts

- Use descriptive titles
- Add relevant tags and categories
- Include a brief description
- Use proper markdown formatting
- Add code syntax highlighting when needed

### Projects

- Include project description and tech stack
- Add links to live demos and source code
- Explain what you learned from each project
- Use consistent formatting

## Performance

The site is optimized for performance:

- Static site generation with Hugo
- Minified CSS and JavaScript
- Optimized images (add your own optimization)
- Fast loading fonts
- Minimal external dependencies

## SEO

Built-in SEO features:

- Proper meta tags
- Open Graph and Twitter Card support
- Structured data
- XML sitemap
- RSS feed
- Fast loading times

## Browser Support

- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile browsers
- Progressive enhancement for older browsers

## Contributing

If you find issues or have suggestions:

1. Open an issue
2. Submit a pull request
3. Share feedback

## License

This project is open source. Feel free to use it as a template for your own blog.

## Acknowledgments

- [Hugo](https://gohugo.io/) - Static site generator
- [PaperMod](https://github.com/adityatelange/hugo-PaperMod) - Hugo theme
- [Dennis Irorere](https://denniseirorere.com/) - Design inspiration

---

## Quick Start Checklist

- [ ] Update personal information in all content files
- [ ] Replace placeholder links with your actual social media
- [ ] Add your profile photo
- [ ] Set up Disqus comments
- [ ] Customize colors and styling if desired
- [ ] Write your first blog post
- [ ] Deploy to your preferred hosting platform
- [ ] Set up custom domain (optional)

**Happy blogging! 🚀**
