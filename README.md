# gretl-assoc.github.io - Deployment Repository

## What is this repository?

This is the **PRODUCTION DEPLOYMENT REPOSITORY** for the gretl Association website.

**Website**: https://gretl-assoc.github.io/

**Content**: Pre-built HTML, CSS, and JavaScript files generated from the source repository.

**Hosting**: GitHub Pages (automatic serving at gretl-assoc.github.io domain)

### Important Notice

⚠️ **Do not edit files in this repository directly!**

All website changes must be made in the source repository and deployed through the proper workflow.

**Exception**: In emergencies, `.gitignore` or deployment-specific files may be edited, but content changes must always originate from the source repository.

---

## How Updates Happen

### The Deployment Process

```
┌──────────────────────────────────────┐
│   gretl_assoc_website                │
│   (SOURCE REPOSITORY)                │
│                                      │
│   Edit content → npm run build       │
│   Generates: gretl-assoc/public/    │
└──────────────────┬───────────────────┘
                   │
                   │ Manual Copy
                   │ cp -r public/* → here
                   ↓
┌──────────────────────────────────────┐
│   gretl-assoc.github.io              │
│   (THIS REPOSITORY)                  │
│   ├─ de/, en/                        │
│   ├─ css/, js/                       │
│   └─ [HTML files]                    │
│                                      │
│   git push → GitHub Pages           │
└──────────────────┬───────────────────┘
                   │
                   ↓
         https://gretl-assoc.github.io/
         (LIVE WEBSITE)
```

### Key Points

1. **All edits start in source repository**: `gretl_assoc_website`
2. **Build generates output**: `npm run build` creates `public/` directory
3. **Manual deployment**: Files copied from source `public/` → this repo
4. **Single commit per deployment**: All generated files committed together
5. **GitHub Pages serves automatically**: No additional deployment steps needed

---

## Workflow Overview

### Step-by-Step Update Process

#### **Step 1: Edit Content** (in source repository)

```bash
# Edit German or English content
nano gretl_assoc_website/gretl-assoc/content/de/about/_index.md
nano gretl_assoc_website/gretl-assoc/content/en/about/_index.md
```

#### **Step 2: Build for Production** (in source repository)

```bash
cd gretl_assoc_website/gretl-assoc
npm run build
# Generates complete website in public/
```

#### **Step 3: Copy to Deployment Repo** (from source to this repo)

```bash
cp -r gretl_assoc_website/gretl-assoc/public/* gretl-assoc.github.io/
```

#### **Step 4: Commit & Deploy** (in this repository)

```bash
cd gretl-assoc.github.io

# See what changed
git status

# Stage all changes
git add -A

# Commit with description
git commit -m "Update website: [describe your changes]"

# Push to GitHub
git push origin main
```

#### **Step 5: Verify Live**

- GitHub Pages rebuilds automatically (usually within 10-30 seconds)
- Check: https://gretl-assoc.github.io/
- Verify both German (`/de/`) and English (`/en/`) versions

---

## Website Sections

The live website includes these main sections (bilingual German/English):

| Section | Purpose | Languages |
|---------|---------|-----------|
| **About** | Information about gretl Association | DE, EN |
| **About Gretl** | About gretl software project | DE, EN |
| **Get Involved** | Ways to participate in the association | DE, EN |
| &nbsp;&nbsp;├─ **Donate** | Financial support options | DE, EN |
| &nbsp;&nbsp;├─ **Legacy** | Legacy gifts, bequest, testament info | DE, EN |
| &nbsp;&nbsp;└─ **Members** | Membership programs & information | DE, EN |
| **Events** | Conferences, workshops, assemblies | DE, EN |
| **Resources** | Shared documents & materials | DE, EN |

---

## Repository Contents

### Directory Structure

```
gretl-assoc.github.io/
│
├── de/                   ← German website (generated)
│   ├── index.html       ← Homepage redirect
│   ├── about/
│   ├── about-gretl/
│   ├── events/
│   ├── get-involved/
│   │   ├── donate/
│   │   ├── legacy/      ← Legacy/bequest information
│   │   └── members/
│   └── resources/
│
├── en/                   ← English website (generated)
│   ├── index.html       ← Homepage redirect
│   ├── about/
│   ├── about-gretl/
│   ├── events/
│   ├── get-involved/
│   │   ├── donate/
│   │   ├── legacy/      ← Legacy/bequest information
│   │   └── members/
│   └── resources/
│
├── css/                  ← Compiled stylesheets
│   └── *.css            ← All theme & custom CSS
│
├── js/                   ← JavaScript assets
│   └── *.js             ← Theme & interactive scripts
│
├── img/                  ← Website images
│   ├── logo.svg         ← Main logo
│   ├── logo-w.svg       ← White variant
│   ├── logo-b.svg       ← Black variant
│   ├── social-share.png ← Social media preview
│   └── social-icons/    ← Icon set for links
│
├── index.html           ← Root page (language redirect)
├── sitemap.xml          ← SEO sitemap (auto-generated)
├── robots.txt           ← Search engine instructions
├── 404.html             ← Error page
│
├── .gitignore           ← Git ignore rules
└── README.md            ← This file
```

### Generated Files

- **HTML Files**: All website pages (one per section per language)
- **CSS**: Compiled stylesheets from theme + custom branding
- **JavaScript**: Theme scripts and interactive components
- **Images**: Logo variants, social icons, page images
- **Meta Files**: sitemap.xml, robots.txt, 404.html

**Total Files**: ~119 files (auto-generated)

---

## For Website Editors

### How to Edit Content

**All editing happens in the source repository!**

**Source Repository**: https://github.com/gretl-assoc/gretl_assoc_website

**README with full instructions**: 
https://github.com/gretl-assoc/gretl_assoc_website/blob/main/README.md

### Common Tasks

**Edit German content**: 
```
gretl_assoc_website/gretl-assoc/content/de/[section]/_index.md
```

**Edit English content**: 
```
gretl_assoc_website/gretl-assoc/content/en/[section]/_index.md
```

**Update navigation menus**: 
```
gretl_assoc_website/gretl-assoc/config/_default/languages.yaml
```

**Test changes locally**: 
```bash
cd gretl_assoc_website/gretl-assoc
npm run start
# Open http://localhost:1313
```

**Deploy updates**: 
Follow Step-by-Step Update Process above (Steps 1-5)

### Development Workflow Note

⚠️ **Important**: The deployment repository uses `main` branch only.

Feature development happens exclusively in the **source repository**:
- **Source Repo**: https://github.com/gretl-assoc/gretl_assoc_website
- Feature branches created and tested there
- Pull requests reviewed before merge to `main`
- Only final, tested content from `main` is deployed here
- Deployment repo receives built files via manual copy process

**Benefit**: Separation of concerns keeps source code changes separate from deployment artifacts.

---

## Repository Information

| Attribute | Value |
|-----------|-------|
| **Repository Name** | gretl-assoc.github.io |
| **Repository Type** | GitHub Pages deployment |
| **Live Website** | https://gretl-assoc.github.io/ |
| **Hosting** | GitHub Pages (automatic) |
| **Content Type** | Static HTML/CSS/JavaScript |
| **Generated By** | Hugo (source: gretl_assoc_website) |
| **Theme** | Dot-Org Hugo Theme (CNCF) |
| **Languages** | German (de), English (en) |
| **Update Frequency** | Manual (as needed) |

---

## Troubleshooting

### Changes not appearing on live site

1. **Verify push succeeded**: Check GitHub repository
2. **Wait for GitHub Pages**: May take 10-30 seconds
3. **Clear browser cache**: Hard refresh (Ctrl+Shift+R or Cmd+Shift+R)
4. **Check deployment status**: 
   - Go to https://github.com/gretl-assoc/gretl-assoc.github.io
   - Click "Deployments" tab to see GitHub Pages status

### Old content still showing

This likely means the deployment wasn't completed properly:

1. Verify files were copied correctly to `gretl-assoc.github.io/`
2. Check that `git add -A` captured all changes
3. Verify `git push origin main` succeeded
4. Check for any GitHub Pages errors in Actions tab

### 404 errors on specific pages

1. Verify page exists in source repository: `gretl_assoc_website/gretl-assoc/content/de/` or `content/en/`
2. Check page URL matches content directory structure
3. Rebuild from source: `npm run build`
4. Redeploy: Copy `public/` → this repo

---

## Questions & Support

### For Website Editing

→ See **Source Repository**: https://github.com/gretl-assoc/gretl_assoc_website

### For Deployment Issues

1. Check GitHub Pages status: Settings → Pages
2. Review deployment history: Actions tab
3. Verify file permissions and .gitignore settings

### For Content Questions

→ Refer to source repository documentation and content editors

---

## Related Links

- **Source Repository**: https://github.com/gretl-assoc/gretl_assoc_website
- **Live Website**: https://gretl-assoc.github.io/
- **GitHub Pages Docs**: https://docs.github.com/en/pages
- **Hugo Documentation**: https://gohugo.io/

---

*This repository contains the generated output of the gretl Association website build process.*
*Last Updated: August 2026*
