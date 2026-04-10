# Personal Portfolio Website

A minimalist, single-page portfolio website for Zhengting Tim HE. Built with vanilla HTML5, CSS3 (with CSS variables), and JavaScript. Hosted on GitHub Pages.

## 📋 Table of Contents

- [Quick Start](#quick-start)
- [File Structure](#file-structure)
- [How to Update Content](#how-to-update-content)
- [Technical Architecture](#technical-architecture)
- [Customization Guide](#customization-guide)
- [Deployment to GitHub Pages](#deployment-to-github-pages)
- [Troubleshooting](#troubleshooting)

---

## Quick Start

### Prerequisites
- A text editor (VS Code recommended)
- A GitHub account (for deployment)
- Knowledge of basic HTML

### Local Testing
1. Open `index.html` in your web browser
2. Changes will reflect immediately (no build process needed)
3. Use browser Developer Tools (F12) to debug

---

## File Structure

```
├── index.html              # Main website file (single file with embedded CSS/JS)
├── index (2).html          # Backup/alternative version
├── index (3).html          # Another version
└── README.md               # This file
```

**Why a single HTML file?**
- Simple to deploy to GitHub Pages
- No build process required
- Easy to version control
- Fast loading (no split asset files)

---

## How to Update Content

### 1. Update Personal Information

#### Hero Section (Introduction)
**Location:** Search for `<section id="hero">`

```html
<h1 class="hname">Zhengting Tim HE</h1>
<span class="hcn">何政庭</span>  <!-- Change Chinese name -->
<p class="htag">YOUR NEW TAGLINE HERE</p>
```

**What to change:**
- `hname`: Your full name
- `hcn`: Name in Chinese or another language
- `htag`: Your professional tagline (2-3 sentences max)
- Update email links in buttons: `mailto:YOUR_EMAIL@example.com`
- Update LinkedIn URL
- Update CV PDF link

#### About Section
**Location:** Search for `<section id="about">`

```html
<div class="atxt">
  <p>EDIT YOUR BIO HERE...</p>
  <p>SECOND PARAGRAPH...</p>
  <p>THIRD PARAGRAPH...</p>
</div>
```

**Right column facts:**
```html
<div class="mr"><span class="ml">Location</span><span class="mv">YOUR LOCATION</span></div>
<div class="mr"><span class="ml">Your Field</span><span class="mv">YOUR AREA</span></div>
```

**Tips:**
- Keep paragraphs concise (2-3 sentences each)
- Max 860px content width for readability
- Use simple, clear language

---

### 2. Update Timeline (Education & Experience)

**Location:** Search for `<section id="timeline">`

#### Adding a New Timeline Entry

**Structure:**
```html
<!-- Event name -->
<div class="timeline-row">
  <div class="timeline-side left">
    <div class="timeline-item">
      <p class="timeline-year">START-END DATES</p>
      <h3 class="timeline-title">POSITION TITLE</h3>
      <p class="timeline-org">ORGANIZATION/COMPANY</p>
      <p class="timeline-desc">Brief description of role/achievements</p>
    </div>
  </div>
  <div class="timeline-side right"></div>
  <div class="timeline-marker"></div>
</div>
```

**For side-by-side entries (parallel events):**
```html
<div class="timeline-side right parallel">
  <div class="timeline-item work">
    <!-- First event -->
  </div>
  <div class="timeline-item work" style="margin-top:50px">
    <!-- Second event -->
  </div>
</div>
```

**Marker types:**
- `.timeline-marker` (default): Filled black circle - use for major milestones
- `.timeline-marker.alt` (alternative): Light circle - use for secondary events

**Tips:**
- Keep dates consistent format: "Month Year–Month Year"
- Descriptions should be 1-2 sentences
- Use country emojis for international locations: 🇬🇧 🇮🇪 🇩🇰 🇦🇹
- Add in chronological order from top to bottom

---

### 3. Update Projects Section

**Location:** Search for `<section id="projects">`

#### Adding a New Project

```html
<a href="https://your-project-url.com" class="pc" target="_blank">
  <p class="pt">CATEGORY</p>
  <h3 class="pn">Project Title</h3>
  <p class="pd">Description of the project (2-3 sentences)</p>
  <span class="pa">↗</span>  <!-- Keep this arrow -->
</a>
```

**Project Grid:**
- Automatically displays as 2 columns on desktop, 1 column on mobile
- Maximum 6 projects recommended for performance
- Each project card includes: category, title, description, and link

#### Placeholder for Work-in-Progress

```html
<div class="pc" style="display:flex;align-items:center;justify-content:center;background:var(--g1);cursor:default">
  <div style="text-align:center">
    <p style="font-family:'DM Serif Display',serif;font-size:17px;color:var(--g4);font-style:italic">Work in Progress</p>
    <p style="font-size:12px;color:var(--g4);margin-top:8px;letter-spacing:.04em">Description Here</p>
  </div>
</div>
```

---

### 4. Update Skills Section

**Location:** Search for `<section id="skills">`

**Structure:** 3-column grid (Research Methods, Interests, Technical Skills)

```html
<div>
  <p class="st">CATEGORY TITLE</p>
  <div class="stags">
    <span class="stag">Skill 1</span>
    <span class="stag">Skill 2</span>
    <span class="stag">Skill 3</span>
  </div>
</div>
```

**Tips:**
- Keep skill names short (1-2 words max)
- 5-6 skills per category works best
- Skills automatically wrap to new lines on smaller screens

---

### 5. Update Contact Section

**Location:** Search for `<section id="contact">`

```html
<h2 class="ch">Let's connect.</h2>
<p class="cs">YOUR MESSAGE HERE</p>
<a href="mailto:your-email@example.com" class="btn bp">Email me →</a>
<a href="https://linkedinurl.com" class="btn bs" target="_blank">LinkedIn ↗</a>
```

---

### 6. Update Footer

**Location:** Search for `<footer>`

```html
<span>© 2025 Name Here</span>
```

**Change year and name as needed.**

---

## Technical Architecture

### CSS Variables (Customizable Colors)

**Location:** Top of `<style>` tag

```css
:root {
  --white:#ffffff;           /* Primary background */
  --black:#0a0a0a;           /* Primary text */
  --g1:#f5f5f7;              /* Light gray backgrounds */
  --g2:#e8e8ed;              /* Borders & dividers */
  --g4:#86868b;              /* Secondary text */
  --g6:#515154;              /* Body text */
  
  --fd:'DM Serif Display';    /* Display font (headers) */
  --fb:'DM Sans';             /* Body font */
  --mw:860px;                 /* Max content width */
  --gap:96px;                 /* Section spacing */
}
```

**To change colors:**
1. Find the color code you want to change (e.g., `--white`)
2. Replace the hex value with your new color
3. Changes apply globally throughout the site

### JavaScript Functionality

#### 1. **Season Detection**
- Auto-detects current month and sets seasonal decorations
- Users can override via season picker buttons in footer
- Months: Spring (Feb-Apr), Summer (May-Jul), Autumn (Aug-Oct), Winter (Nov-Jan)

#### 2. **Decorative Flowers**
- 24 fixed-position SVG elements scatter across the page
- Each has unique rotation, scale, position
- Twinkling animation using sine wave (smooth, continuous)
- Middle section (30-70% width) uses lower opacity to avoid content obstruction
- Spring: Sakura blossoms (pink), Autumn: Maple leaves (red/orange), Winter: Snowflakes (blue)
- Summer: Cleared (currently empty)

#### 3. **Season Picker**
- Hover over footer to reveal 4 season buttons
- Clicking regenerates all 24 decorations with new season's graphics
- Button states update to show active season

### Performance Considerations

- **Single file:** ~50KB (all CSS/JS inline)
- **No external dependencies:** Only Google Fonts (preconnected for speed)
- **Animation:** 30ms update interval for smooth 60fps rendering
- **Mobile-optimized:** Responsive breakpoint at 700px
- **Browser support:** Chrome, Firefox, Safari, Edge (modern versions)

---

## Customization Guide

### Change Typography

**Headers (Serif font):**
In CSS, find `.hname`, `.timeline-title`, `.pn`, `.ch` and modify:
```css
.hname {
  font-family: var(--fd);  /* Change --fd in :root */
  font-size: clamp(52px, 8vw, 88px);  /* Min, responsive, max */
}
```

**Body text (Sans-serif font):**
Adjust in `:root` section:
```css
--fb: 'Your Font Name', -apple-system, sans-serif;
```

### Change Accent Colors

Example: Make headings blue instead of black
```css
:root {
  --black: #0066ff;  /* Now blue headings */
}
```

### Adjust Spacing

**Section gaps:**
```css
:root {
  --gap: 96px;  /* Space between sections - increase for more breathing room */
}
```

**Content max-width:**
```css
:root {
  --mw: 860px;  /* Decrease for narrower columns, increase for wider */
}
```

### Customize Season Decorations

**To modify autumn (maple leaf) colors:**

Find `function autumn()` in the JavaScript section:
```javascript
var cs = ['#bf360c','#e64a19','#f4511e','#ff7043','#d84315','#e65100'];
```
Replace with your color palette (hex codes).

**To disable decorations entirely:**

Find section `/* ── 3. Spawn elements */` and change:
```javascript
for (var i = 0; i < 24; i++) {  // Change 24 to 0
```

**To adjust animation speed:**

Find the setInterval function and change the delay:
```javascript
}, 30);  // Currently 30ms - increase for slower updates
```

---

## Deployment to GitHub Pages

### Option 1: Using GitHub Web UI (Easiest)

1. Go to your GitHub repository
2. Click `Add file` → `Upload files`
3. Upload `index.html`
4. Go to repository `Settings` → `Pages`
5. Set Source to `main` branch, `/root` directory
6. Site will be live at `https://YOUR-USERNAME.github.io/REPO-NAME/`

### Option 2: Using Git Command Line

```bash
# Clone your repository
git clone https://github.com/YOUR-USERNAME/REPO-NAME.git
cd REPO-NAME

# Copy index.html to the folder
# Edit and test locally

# Add and commit
git add index.html
git commit -m "Update portfolio website"

# Push to GitHub
git push origin main
```

### Option 3: Using GitHub Pages with Custom Domain

In repository Settings → Pages:
- Select "main" branch as source
- Add custom domain (if you own one)
- Update DNS records accordingly

---

## Troubleshooting

### Issue: Page looks weird/styles missing

**Solution:**
- Clear browser cache (Ctrl+Shift+Delete or Cmd+Shift+Delete)
- Check browser console for errors (F12)
- Verify all HTML tags are properly closed
- Check CSS variable names are spelled correctly

### Issue: Decorative flowers not showing

**Solutions:**
1. Check if season is set correctly (hover footer button)
2. Try clicking a different season button
3. Check console for JavaScript errors (F12 → Console tab)
4. Verify SVG elements are rendering (right-click → Inspect Element)

### Issue: Links aren't working

**Solutions:**
1. Verify URLs are complete with `https://` or `mailto:`
2. Test external links in new tab
3. Check for typos in email addresses
4. Ensure `target="_blank"` is present for external links

### Issue: Mobile layout broken

**Solutions:**
1. Check viewport meta tag is present: `<meta name="viewport"...`
2. Test in browser developer tools (F12 → Toggle device toolbar)
3. Verify mobile breakpoint CSS (look for `@media(max-width:700px)`)

### Issue: Fonts not loading

**Solutions:**
1. Check internet connection
2. Verify Google Fonts link in `<head>`
3. Check browser DevTools → Network tab
4. Add fallback fonts in CSS

---

## Best Practices for Maintenance

### Regular Updates
- **Update timeline:** Add new experiences within 1-2 weeks
- **Refresh projects:** Add new projects at least quarterly
- **Review content:** Annual review of bio and description
- **Check links:** Quarterly verification of external URLs

### Version Control
- Commit changes with descriptive messages
- Keep backups (maintain `index (2).html` as backup)
- Tag releases (e.g., `git tag -a v2.0`)

### Performance
- Keep total file size under 100KB
- Compress project images if embedding (use external links instead)
- Test on various browsers and devices
- Use Lighthouse audit tool (Chrome DevTools) regularly

### SEO Optimization
- Update `<title>` tag descriptively
- Add meta description in `<head>`:
  ```html
  <meta name="description" content="Portfolio of Zhengting Tim HE...">
  ```
- Use semantic HTML (section, article, nav)
- Keep alt text for any images

---

## Additional Resources

- **HTML Reference:** https://developer.mozilla.org/en-US/docs/Web/HTML
- **CSS Variables Guide:** https://developer.mozilla.org/en-US/docs/Web/CSS/--*
- **GitHub Pages:** https://pages.github.com/
- **Color Picker:** https://colorhexa.com/
- **Font Inspiration:** https://fonts.google.com/

---

## Questions or Issues?

If you encounter problems not covered here:
1. Check browser console (F12)
2. Validate HTML at https://validator.w3.org/
3. Review the inline HTML comments in the code
4. Test changes in a copy of the file first

---

**Last Updated:** April 2026  
**Website Status:** Active on GitHub Pages
