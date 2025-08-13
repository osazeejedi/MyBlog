---
title: "Portfolio"
description: "Blockchain Developer, Program Manager and Data Scientist - Showcasing my professional experience and featured projects"
date: 2024-01-01
draft: false
showToc: false
TocOpen: false
hidemeta: false
comments: false
disableHLJS: true
disableShare: false
hideSummary: false
searchHidden: false
ShowReadingTime: false
ShowBreadCrumbs: true
ShowPostNavLinks: false
ShowWordCount: false
ShowRssButtonInSectionTermList: false
UseHugoToc: false
cover:
    image: ""
    alt: ""
    caption: ""
    relative: false
    hidden: true
---

<div class="portfolio-hero">
    <div class="portfolio-intro">
        <h1 class="portfolio-title">{{ .Site.Data.portfolio.personal.name }}</h1>
        <h2 class="portfolio-subtitle">{{ .Site.Data.portfolio.personal.title }}</h2>
        <p class="portfolio-description">{{ .Site.Data.portfolio.personal.description }}</p>
        
        <div class="skills-section">
            <h3>Core Skills</h3>
            <div class="skills-grid">
                {{ range .Site.Data.portfolio.personal.skills }}
                <span class="skill-tag">{{ . }}</span>
                {{ end }}
            </div>
        </div>
        
        <div class="contact-info">
            <a href="mailto:{{ .Site.Data.portfolio.personal.email }}" class="contact-link">
                📧 Get In Touch
            </a>
        </div>
    </div>
</div>

## Professional Experience

<div class="experience-timeline">
    {{ range .Site.Data.portfolio.experience }}
    <div class="experience-item">
        <div class="experience-header">
            <h3 class="experience-title">{{ .title }}</h3>
            <div class="experience-meta">
                <span class="company">{{ .company }}</span>
                <span class="location">{{ .location }}</span>
                <span class="date-range">{{ .range }}</span>
            </div>
        </div>
        <div class="experience-content">
            <ul class="responsibilities">
                {{ range .responsibilities }}
                <li>{{ . }}</li>
                {{ end }}
            </ul>
        </div>
    </div>
    {{ end }}
</div>

## Featured Projects

<div class="projects-grid">
    {{ range .Site.Data.portfolio.featured_projects }}
    {{ if .showInProjects }}
    <div class="project-card">
        <div class="project-image">
            {{ if .image }}
            <img src="/images/portfolio/projects/{{ .image }}" alt="{{ .title }}" loading="lazy">
            {{ else }}
            <div class="project-placeholder">
                <span>🚀</span>
            </div>
            {{ end }}
        </div>
        <div class="project-content">
            <h3 class="project-title">{{ .title }}</h3>
            <p class="project-description">{{ .description }}</p>
            
            <div class="project-tech">
                {{ range .tech }}
                <span class="tech-tag">{{ . }}</span>
                {{ end }}
            </div>
            
            <div class="project-links">
                {{ if .github }}
                <a href="{{ .github }}" target="_blank" rel="noopener noreferrer" class="project-link github-link">
                    <span>GitHub</span>
                </a>
                {{ end }}
                {{ if .external }}
                <a href="{{ .external }}" target="_blank" rel="noopener noreferrer" class="project-link demo-link">
                    <span>Live Demo</span>
                </a>
                {{ end }}
            </div>
        </div>
    </div>
    {{ end }}
    {{ end }}
</div>

## About My Work

{{ .Site.Data.portfolio.personal.bio }}

---

### Currently Exploring

- **Layer 2 Solutions** for Ethereum scaling
- **AI & Blockchain Integration** for innovative applications
- **DeFi Protocols** and decentralized finance innovations
- **Smart Contract Security** and best practices
- **Cross-chain Interoperability** solutions

---

### Let's Connect

I'm always interested in discussing blockchain technology, program management, and innovative projects. Whether you're looking to collaborate on a project, need technical consultation, or just want to chat about the latest in Web3, feel free to reach out!

**Find me here:**
- 💼 [LinkedIn](https://www.linkedin.com/in/osazee-oghagbon/)
- 💻 [GitHub](https://github.com/osazeejedi)
- 📧 [Email](mailto:{{ .Site.Data.portfolio.personal.email }})

---

*"Innovation happens when we combine technical expertise with creative problem-solving and strong execution."*
