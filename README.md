# personal-site-template

Created by [Jennifer Isasi](https://jenniferisasi.github.io) for a workshop on personal sites for graduate students. Last updated December 8, 2025.

You can preview the site at: [https://dla-psu.github.io/personal-site-template/](https://dla-psu.github.io/personal-site-template/)

GitHub provides a preview of the files before committing changes. However, if you prefer to work on Markdown and HTML files locally before adding them to your repository, I recommend using [Zettlr](https://www.zettlr.com) or [Visual Studio Code](https://code.visualstudio.com).

---

A template to create simple personal sites with bio, projects and CV. It turns simple markdown files into web pages. No coding required for updates.

The site has four pages:
- About page (homepage) - with optional PhD progress tracker
- Projects page in your main language
- Projects page in an alternative language
- CV/Resume page

## Table of Contents

- [Using This Template](#using-this-template)
- [About Page: Choose Your Version](#about-page-choose-your-version)
  - [Option A: About Page with Progress Tracker](#option-a-simple-about-page-default---currently-active)
  - [Option B: Simple Text-Only About Page](#option-b-simple-text-only-about-page)
- [How to Make Changes](#how-to-make-changes)
- [What's in Each Folder](#whats-in-each-folder)
- [Optional Features](#optional-features)
  - [PhD Progress Tracker](#phd-progress-tracker)
- [Adding a New Project](#adding-a-new-project)
- [Adding Images](#adding-images)
- [Basic Markdown Formatting](#basic-markdown-formatting)
- [Basic HTML Editing](#basic-html-editing)
- [How It Actually Works](#how-it-actually-works)
- [Troubleshooting](#troubleshooting)
- [Want to Change the Design?](#want-to-change-the-design)
- [Want to Add More Project Pages?](#want-to-add-more-project-pages)

## Using This Template

If you want to use this template for your own site:

1. Click the green "Use this template" button at the top of this page
2. Choose "Create a new repository"
3. **Name your repository:** You have two options here:
   - **For a clean URL** (recommended): Name it `your-username.github.io` (replace `your-username` with your actual GitHub username)
     - Your site will be at: `https://your-username.github.io/`
   - **For a project site**: Name it anything you want (like `my-portfolio` or `personal-site`)
     - Your site will be at: `https://your-username.github.io/repository-name/`
4. Make sure it's set to "Public"
5. Click "Create repository"

GitHub will copy all these files to your new repository. Then you can edit them with your own information.

**After copying, you'll need to enable GitHub Pages:**

1. Go to Settings in your new repository
2. Click "Pages" on the left side
3. Under "Source", select "GitHub Actions"
4. Your site will be live in 2-3 minutes!

## About Page: Choose Your Version

This template offers **two options** for your About page (the homepage). Choose the one that fits your needs.

**[👉 View Visual Comparison of Both Options](https://dla-psu.github.io/personal-site-template/about-options.html)**

### Option A: Simple About Page (Default - Currently Active)

**Best for:** Showcasing your journey with a visual timeline and optional PhD progress tracker

**File to edit:** `about.html` (in repository root, not in content folder)

**Features:**
- Profile photo
- Bio sections
- Visual timeline showing your career/education journey
- Optional PhD progress tracker
- Contact information

**How to edit:**
1. Find `about.html` in the root of your repository
2. Click the pencil icon to edit
3. Update your information directly in the HTML
4. The timeline items are easy to copy/paste to add more
5. To enable the PhD progress tracker, find the HTML comment `<!-- OPTIONAL PhD PROGRESS TRACKER` and delete the `<!--` at the start and `-->` at the end

**To customize the footer:**
- Find the footer section near the bottom of `about.html`
- Replace `[Your Name]` with your actual name

### Option B: Simple Text-Only About Page

**Best for:** A clean, simple bio without timeline or progress tracking

**File to edit:** `content/about.md`

**How to switch to this option:**

1. Delete `about.html` from the repository root
2. Open `.github/workflows/deploy.yml`
3. Find the line that says `cp about.html _site/index.html`
4. Replace it with:
```yaml
          # Convert about page (index)
          pandoc content/about.md -o _site/index.html \
            --from markdown+raw_html \
            --template=./template.html \
            --metadata title="About Me" \
            --metadata page="about"
```
5. Commit the changes
6. Edit `content/about.md` with your information using simple Markdown

**Note:** You can keep both `about.html` and `content/about.md` in your repository. Only one will be used based on what's in the workflow file.

## How to Make Changes

### For most pages (Projects, CV):

1. Navigate to the file in the `content` folder (example: `content/projects-main.md`)
2. Click the pencil icon in the top right corner
3. Edit the text using Markdown
4. Scroll to the bottom and click "Commit changes"
5. Wait 2-3 minutes for the site to update

### For the About page (if using Option A with timeline):

1. Navigate to `about.html` in the root folder
2. Click the pencil icon
3. Edit the HTML directly (it's clearly structured with comments)
4. Commit changes

That's it. The website rebuilds itself automatically.

### To Edit the Footer

**Important:** The footer needs to be updated in TWO places to keep it consistent across all pages.

**1. For the About page (if using Option A):**
   - Open `about.html`
   - Find the footer section near the bottom:
   ```html
   <footer>
       <p>&copy; 2024 [Your Name]. All rights reserved.</p>
   </footer>
   ```
   - Replace `[Your Name]` with your actual name

**2. For all other pages (Projects, CV):**
   - Open `template.html`
   - Find the footer section:
   ```html
   <footer>
       <p>&copy; 2024 [Your Name]. All rights reserved.</p>
   </footer>
   ```
   - Replace `[Your Name]` with your actual name

Make sure both footers match exactly so all pages look consistent!

### To Change the Language Labels in Navigation

1. Navigate to `template.html`
2. Find the navigation section
3. Change "Projects" and "Proyectos" to your preferred language labels
4. Example: Change "Proyectos" to "Projets" for French, "Projekte" for German, etc.

If you're using Option A (about.html), also update the navigation in `about.html` to match.

## What's in Each Folder

**Root folder files:**
- `about.html` - About page with timeline (Option A - default)
- `template.html` - The page layout for Markdown pages
- `styles.css` - Colors and fonts for the entire site
- `.github/workflows/deploy.yml` - Instructions for GitHub on how to build the site

**content/** - Markdown files that get converted to pages
- `about.md` - Simple about page (Option B - not used by default)
- `projects-main.md` - Your projects in your primary language
- `projects-alt.md` - Your projects in an alternative language
- `cv.md` - Your resume/CV

**images/** - All pictures and screenshots
- `photo.jpg` - Your profile photo
- Any project screenshots you want to show

## Optional Features

### PhD Progress Tracker

If you're pursuing a PhD or graduate degree, you can enable a progress tracker on your About page (only available with Option A).

**To enable it:**

1. Open `about.html`
2. Find the section marked `<!-- OPTIONAL PhD PROGRESS TRACKER`
3. Delete the line with `<!--` at the beginning of that section
4. Scroll down and delete the line with `-->` at the end
5. Commit your changes

**To customize it:**

Edit the following in `about.html`:
- **Degree title**: Change "PhD in Computer Science"
- **Year progress**: Update "Year 3 of 5"
- **Institution**: Change "University Name"
- **Expected completion**: Update "Expected 2026"
- **Progress percentage**: Change `60%` in two places (the displayed number and `width: 60%`)
- **Milestones**: Add, remove, or edit milestones

**Milestone status:**
- `class="completed"` - Shows green with ✓
- `class="in-progress"` - Shows orange with ⚡
- No class attribute - Shows gray with ◯

### Adding Timeline Items

To add more items to your timeline (if using Option A):

1. Open `about.html`
2. Find the timeline section
3. Copy an existing timeline item block:
```html
<div class="timeline-item">
    <div class="timeline-dot"></div>
    <div class="timeline-content">
        <div class="timeline-date">YEAR - YEAR</div>
        <h3>Position/Degree Title</h3>
        <h4>Company/Institution</h4>
        <p>Description of what you did.</p>
    </div>
</div>
```
4. Paste it where you want it (most recent at top)
5. Update with your information

### Customizing the PhD Progress Tracker Appearance

If you're using the PhD progress tracker, you can customize its colors and styling:

**To change the progress bar color:**
1. Open `styles.css`
2. Find `.progress-fill` (around line 180)
3. Change the `background` color:
```css
.progress-fill {
    background: linear-gradient(90deg, #3498db, #2ecc71);
    /* Change to: background: #your-color-here; */
}
```

**To change milestone status colors:**
1. In `styles.css`, find these sections:
   - `.milestone.completed .milestone-title` - Controls completed items (default: green `#27ae60`)
   - `.milestone.in-progress .milestone-title` - Controls in-progress items (default: orange `#f39c12`)
   - Default milestones without status use gray

2. Change the color values:
```css
.milestone.completed .milestone-title {
    color: #27ae60;  /* Change to your preferred "completed" color */
}

.milestone.in-progress .milestone-title {
    color: #f39c12;  /* Change to your preferred "in-progress" color */
}
```

**To change the progress tracker border:**
1. Find `.phd-progress` in `styles.css`
2. Change `border-left: 4px solid #3498db;` to your preferred color

**Popular color combinations:**
- **Professional Blue:** Progress bar `#2563eb`, completed `#1e40af`
- **Academic Purple:** Progress bar `#8b5cf6`, completed `#6d28d9`
- **Success Green:** Progress bar `#10b981`, completed `#059669`

After making changes, commit the file and your site will update in 2-3 minutes!

## Adding a New Project

1. Open `content/projects-main.md`
2. Find an existing project section
3. Copy everything from one `---` line to the next `---` line
4. Paste it where you want the new project
5. Change the title, date, description, etc.
6. Save by clicking "Commit changes"

Do the same thing in `content/projects-alt.md` for the alternative language version.

## Adding Images

To add a screenshot or photo:

1. Click "Add file" at the top, then "Upload files"
2. Upload your image to the `images` folder
3. In your Markdown file, add this line where you want the image:
```markdown
![Description of image](./images/my-image.jpg)
```
4. Replace `my-image.jpg` with whatever you named the file

## Basic Markdown Formatting

Markdown is just text with some symbols for formatting. Here's what you can use:

```markdown
# Big heading
## Smaller heading
### Even smaller heading

**bold text**
*italic text*

- Bullet point
- Another bullet point

[Link text](https://website.com)

![Image description](./images/photo.jpg)
```

If you want to learn markdown better, I recommend you read: [Getting Started with Markdown](https://programminghistorian.org/en/lessons/getting-started-with-markdown) by Sarah Simpkin

## Basic HTML Editing

If you're using Option A (about.html), you'll be editing HTML directly. Don't worry - HTML is just text with tags that tell the browser how to display things. Here's what you need to know:

```html
<h1>Big heading</h1>
<h2>Smaller heading</h2>
<h3>Even smaller heading</h3>

<p>This is a paragraph of text.</p>

<strong>bold text</strong>
<em>italic text</em>

<a href="https://website.com">Link text</a>

<img src="./images/photo.jpg" alt="Description">
```

The `about.html` file has clear comments showing you exactly what to edit. Look for text between `<!--` and `-->` - those are comments that explain what each section does.

If you want to learn more about HTML, I recommend you read: [Viewing HTML Files](https://programminghistorian.org/en/lessons/viewing-html-files) by William J. Turkel and Adam Crymble

## How It Actually Works

When you save changes, GitHub runs a process in the background to build your website:

**For Markdown files** (Projects, CV):
1. GitHub takes your Markdown files
2. Converts them to HTML web pages using a tool called Pandoc
3. Wraps them in the template (adds the navigation menu, styling, etc.)
4. Publishes everything to the web

**For HTML files** (About page with Option A):
1. GitHub copies the HTML file directly to your site
2. No conversion needed - it's already in HTML
3. This is why the progress tracker and interactive elements work perfectly

**For images and CSS**:
1. These files are copied as-is to your site
2. No processing or conversion happens

This all happens automatically in 2-3 minutes. You never see it or interact with it. You just edit files in GitHub, and the website updates itself!

## Troubleshooting

**My changes aren't showing up**
- Wait 3-5 minutes after saving. The site needs time to rebuild.
- Check the "Actions" tab at the top. If there's a red X, something went wrong. Click it to see what.

**My image isn't appearing**
- Make sure the image is in the `images` folder
- Check that the filename matches exactly (including .jpg or .png)
- Image paths should look like: `./images/filename.jpg`

**The timeline or progress tracker isn't showing correctly**
- Make sure you're using Option A (about.html)
- Check that you have the timeline CSS in `styles.css`
- Verify that HTML comment tags `<!--` and `-->` are properly removed if you want to show the PhD tracker

**I broke something**
- Don't worry! GitHub keeps history of all changes
- Click on the file, then "History" at the top right
- Find the last working version and click the three dots to revert

## Want to Change the Design?

If you want different colors or fonts, you can edit `styles.css`. The main colors in the file are:
- `#3498db` - The blue accent color
- `#2c3e50` - The dark blue/gray navigation bar

To change colors:
1. Visit [color-hex.com/color-palettes](https://www.color-hex.com/color-palettes/) to browse color palette ideas
2. Pick colors you like and copy their hex codes
3. Open `styles.css` in your repository
4. Search for `#3498db` and replace it with your new primary color
5. Search for `#2c3e50` and replace it with your new dark color
6. Commit the changes

Your site will update automatically in 2-3 minutes!

## Want to Add More Project Pages?

If you need a third (or fourth) project page in another language, here's how:

### Step 1: Create the New Markdown File
1. Go to the `content/` folder
2. Click "Add file" → "Create new file"
3. Name it `projects-lang3.md` (or any name you want)
4. Copy content from `projects-main.md` and translate it
5. Commit the file

### Step 2: Update the Workflow
1. Open `.github/workflows/deploy.yml`
2. Find the "Convert Markdown to HTML" section
3. Add these lines before the "Convert CV" part:
```yaml
          # Convert projects (third language)
          pandoc content/projects-lang3.md -o _site/projects-lang3.html \
            --from markdown+raw_html \
            --template=./template.html \
            --metadata title="Projects" \
            --metadata page="projects-lang3"
```
4. Commit changes

### Step 3: Update the Navigation Menu
1. Open `template.html`
2. Find the `<nav>` section
3. Add a new line in the menu:
```html
<li><a href="./projects-lang3.html">项目</a></li>
```
(Replace "项目" with your language label)
4. If using Option A (about.html), also add this line to the navigation in `about.html`
5. Commit changes

Your new project page will appear in the navigation menu and be accessible on your site!
