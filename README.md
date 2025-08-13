# Osazee's Blog

A modern, responsive personal blog built with Hugo and the PaperMod theme, featuring a dark-focused design with custom styling and mobile optimization.

## 🚀 Live Site

Visit the live blog at: [https://my-blog-osazeejedi.vercel.app/](https://my-blog-osazeejedi.vercel.app/)

## 🛠️ Built With

- **[Hugo](https://gohugo.io/)** - Fast static site generator
- **[PaperMod Theme](https://github.com/adityatelange/hugo-PaperMod)** - Clean, responsive Hugo theme
- **[Vercel](https://vercel.com/)** - Deployment and hosting platform
- **Custom CSS** - Enhanced styling with Jost font family and mobile optimizations

## ✨ Features

### Design & UX
- 🌙 **Dark theme focus** with light mode toggle
- 📱 **Fully responsive** design with mobile-first approach
- 🎨 **Custom hero section** with profile image and modern card design
- 🔤 **Jost font family** for improved typography
- ⚡ **Smooth animations** and hover effects
- 🎯 **Accessible design** with proper focus states

### Content & Navigation
- 📝 **Blog posts** with syntax highlighting and reading time
- 🏷️ **Tag system** for content organization
- 🔍 **Search functionality** (built into PaperMod)
- 📊 **Social sharing** buttons
- 🧭 **Breadcrumb navigation**

### Performance & SEO
- ⚡ **Fast loading** with Hugo's static generation
- 🔍 **SEO optimized** with proper meta tags and Open Graph
- 📱 **Mobile optimized** with responsive images
- 🌐 **Global CDN** delivery via Vercel
- 🤖 **Robots.txt** and sitemap generation

## 🏗️ Project Structure

```
MyBlog/
├── content/                 # Blog content
│   ├── posts/              # Blog posts
│   ├── about/              # About page
│   └── contact/            # Contact page
├── static/                 # Static assets
│   ├── css/               # Custom CSS
│   └── images/            # Images and favicon
├── layouts/               # Custom layouts
│   └── partials/          # Partial templates
├── themes/PaperMod/       # Hugo theme (submodule)
├── hugo.toml              # Hugo configuration
├── vercel.json            # Vercel deployment config
└── README.md              # This file
```

## 🚀 Deployment

This blog is automatically deployed to Vercel with the following configuration:

### Vercel Settings
- **Framework**: Hugo
- **Build Command**: `hugo --minify`
- **Output Directory**: `public`
- **Install Command**: `git submodule update --init --recursive`

### Environment Variables
- `HUGO_VERSION`: 0.147.8

### Automatic Deployment
- ✅ **Auto-deploy** on push to main branch
- ✅ **Preview deployments** for pull requests
- ✅ **Custom domain** support ready
- ✅ **HTTPS** enabled by default

## 🛠️ Local Development

### Prerequisites
- [Hugo Extended](https://gohugo.io/installation/) (v0.147.8 or later)
- [Git](https://git-scm.com/)

### Setup
1. **Clone the repository**
   ```bash
   git clone https://github.com/osazeejedi/MyBlog.git
   cd MyBlog
   ```

2. **Initialize submodules**
   ```bash
   git submodule update --init --recursive
   ```

3. **Start development server**
   ```bash
   hugo server -D
   ```

4. **Open in browser**
   ```
   http://localhost:1313
   ```

### Development Commands
```bash
# Start development server with drafts
hugo server -D

# Build for production
hugo --minify

# Update theme
git submodule update --remote themes/PaperMod
```

## 📝 Content Management

### Adding New Posts
1. Create a new post:
   ```bash
   hugo new posts/my-new-post.md
   ```

2. Edit the post in `content/posts/my-new-post.md`

3. Update the front matter:
   ```yaml
   ---
   title: "My New Post"
   date: 2025-01-01T00:00:00Z
   draft: false
   tags: ["tag1", "tag2"]
   categories: ["category"]
   description: "Post description"
   ---
   ```

### Customizing Design
- **CSS**: Edit `static/css/custom.css`
- **Colors**: Update CSS variables in the `:root` section
- **Fonts**: Modify font imports in `layouts/partials/extend_head.html`
- **Layout**: Customize layouts in `layouts/` directory

## 🎨 Customizations

### Typography
- **Primary Font**: Jost (Google Fonts)
- **Fallback**: Helvetica Neue, Helvetica, Arial, sans-serif
- **Code Font**: SF Mono, Monaco, Inconsolata, Roboto Mono

### Color Scheme
- **Accent**: Indigo (#6366f1)
- **Text**: Gray (#6b7280)
- **Headings**: Light gray in dark mode (#d1d5db)
- **Background**: Theme-based with smooth transitions

### Mobile Optimizations
- **Responsive hero section** with stacked layout
- **Touch-friendly navigation** with proper hamburger menu
- **Optimized images** and typography scaling
- **Improved spacing** and padding for mobile

## 📊 Performance

### Lighthouse Scores (Target)
- **Performance**: 95+
- **Accessibility**: 95+
- **Best Practices**: 95+
- **SEO**: 95+

### Optimizations
- ✅ **Minified CSS/JS**
- ✅ **Optimized images**
- ✅ **Efficient caching**
- ✅ **Fast font loading**
- ✅ **Minimal JavaScript**

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes
4. Commit: `git commit -am 'Add feature'`
5. Push: `git push origin feature-name`
6. Submit a pull request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 👤 Author

**Osazee Oghagbon**
- GitHub: [@osazeejedi](https://github.com/osazeejedi)
- LinkedIn: [osazee-oghagbon](https://www.linkedin.com/in/osazee-oghagbon/)
- Email: helloosaze@gmail.com

## 🙏 Acknowledgments

- [Hugo](https://gohugo.io/) for the amazing static site generator
- [PaperMod](https://github.com/adityatelange/hugo-PaperMod) for the excellent theme
- [Vercel](https://vercel.com/) for seamless deployment and hosting
- [Google Fonts](https://fonts.google.com/) for the Jost font family

---

*Built with ❤️ using Hugo and deployed on Vercel*
