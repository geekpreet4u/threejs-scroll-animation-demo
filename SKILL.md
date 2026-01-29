---
name: dk-slides
description: Create stunning, animation-rich HTML presentations with DraftKings/DK Horse branding. Use when you want to build a presentation, convert a PPT/PPTX to web, or create slides for a talk/pitch with the signature DK dark theme and lime green accents.
---

# DK Slides Skill

Create zero-dependency, animation-rich HTML presentations with DraftKings/DK Horse branding. Single HTML files that run entirely in the browser with the signature dark theme and lime green accents.

## Core Philosophy

1. **Zero Dependencies** — Single HTML files with inline CSS/JS. No npm, no build tools.
2. **Show, Don't Tell** — People don't know what they want until they see it. Generate visual previews, not abstract choices.
3. **DK Brand Consistency** — Dark backgrounds, lime green accents, clean modern typography.
4. **Production Quality** — Code should be well-commented, accessible, and performant.

---

## DK Horse Theme Reference

### Color Palette

```css
:root {
    /* Colors - DK Horse Theme */
    --bg-primary: #121212;
    --bg-secondary: #1e1e1e;
    --bg-dark: #000000;
    --text-primary: #ffffff;
    --text-secondary: #b3b3b3;
    --text-light: #666666;
    --accent: #8dc63f;
    --accent-secondary: #8dc63f;
    --accent-light: rgba(141, 198, 63, 0.12);
    --accent-dark: #6ba32d;
    --border: #2d2d2d;
}
```

### Typography

- **Display Font:** 'General Sans' from Fontshare (clean, modern sans-serif)
- **Serif Accent:** 'Zodiak' from Fontshare (for subtitles and quotes)
- **Monospace:** System monospace for code blocks

```html
<link rel="stylesheet" href="https://api.fontshare.com/v2/css?f[]=general-sans@400,500,600,700&f[]=zodiak@400,500&display=swap">
```

### Design Elements

- **Backgrounds:** Pure dark (#121212) with subtle green grid pattern
- **Cards:** Dark secondary (#1e1e1e) with subtle borders (#2d2d2d)
- **Buttons:** Bright lime green (#8dc63f) with black text
- **Hover states:** Green glow effects using rgba(141, 198, 63, 0.15)
- **Accent usage:** Monochromatic green — no secondary colors

---

## Phase 0: Detect Mode

First, determine what the user wants:

**Mode A: New Presentation**
- User wants to create slides from scratch
- Proceed to Phase 1 (Content Discovery)

**Mode B: PPT Conversion**
- User has a PowerPoint file (.ppt, .pptx) to convert
- Proceed to Phase 4 (PPT Extraction)

**Mode C: Existing Presentation Enhancement**
- User has an HTML presentation and wants to improve it
- Read the existing file, understand the structure, then enhance

---

## Phase 1: Content Discovery (New Presentations)

Before designing, understand the content. Ask via AskUserQuestion:

### Step 1.1: Presentation Context

**Question 1: Purpose**
- Header: "Purpose"
- Question: "What is this presentation for?"
- Options:
  - "Pitch deck" — Selling an idea, product, or company to investors/clients
  - "Teaching/Tutorial" — Explaining concepts, how-to guides, educational content
  - "Conference talk" — Speaking at an event, tech talk, keynote
  - "Internal presentation" — Team updates, strategy meetings, company updates

**Question 2: Slide Count**
- Header: "Length"
- Question: "Approximately how many slides?"
- Options:
  - "Short (5-10)" — Quick pitch, lightning talk
  - "Medium (10-20)" — Standard presentation
  - "Long (20+)" — Deep dive, comprehensive talk

**Question 3: Content**
- Header: "Content"
- Question: "Do you have the content ready, or do you need help structuring it?"
- Options:
  - "I have all content ready" — Just need to design the presentation
  - "I have rough notes" — Need help organizing into slides
  - "I have a topic only" — Need help creating the full outline

If user has content, ask them to share it (text, bullet points, images, etc.).

---

## Phase 2: Style Variations (Optional)

Since DK branding is already defined, this phase offers subtle variations within the brand:

### Step 2.1: Layout Preference

**Question: Layout Style**
- Header: "Layout"
- Question: "What layout style do you prefer?"
- Options:
  - "Centered" — Content centered, good for quotes and key messages
  - "Left-aligned" — Content left-aligned, good for lists and detailed info
  - "Mixed" — Varies by slide type (recommended)

### Step 2.2: Animation Intensity

**Question: Animation Level**
- Header: "Motion"
- Question: "How much animation do you want?"
- Options:
  - "Subtle" — Gentle fades and slides, professional feel
  - "Dynamic" — More pronounced entrances, energetic feel
  - "Minimal" — Almost no animation, content-focused

---

## Phase 3: Generate Presentation

Generate the full presentation using the DK Horse theme.

### File Structure

```
presentation.html    # Self-contained presentation
assets/              # Images, if any
```

### HTML Architecture

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Presentation Title</title>

    <!-- Fonts from Fontshare -->
    <link rel="stylesheet" href="https://api.fontshare.com/v2/css?f[]=general-sans@400,500,600,700&f[]=zodiak@400,500&display=swap">

    <style>
        /* ===========================================
           CSS CUSTOM PROPERTIES (DK HORSE THEME)
           =========================================== */
        :root {
            /* Colors - DK Horse Theme */
            --bg-primary: #121212;
            --bg-secondary: #1e1e1e;
            --bg-dark: #000000;
            --text-primary: #ffffff;
            --text-secondary: #b3b3b3;
            --text-light: #666666;
            --accent: #8dc63f;
            --accent-secondary: #8dc63f;
            --accent-light: rgba(141, 198, 63, 0.12);
            --accent-dark: #6ba32d;
            --border: #2d2d2d;

            /* Typography */
            --font-display: 'General Sans', -apple-system, sans-serif;
            --font-serif: 'Zodiak', Georgia, serif;

            /* Spacing */
            --slide-padding: clamp(2rem, 6vw, 5rem);

            /* Animation */
            --ease-out-expo: cubic-bezier(0.16, 1, 0.3, 1);
            --ease-out-back: cubic-bezier(0.34, 1.56, 0.64, 1);
            --duration-normal: 0.7s;
            --duration-fast: 0.4s;
        }

        /* ===========================================
           BASE STYLES
           =========================================== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
            scroll-snap-type: y mandatory;
        }

        body {
            font-family: var(--font-display);
            background: var(--bg-primary);
            color: var(--text-primary);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Subtle grid pattern background */
        body::before {
            content: '';
            position: fixed;
            inset: 0;
            background-image:
                linear-gradient(rgba(141, 198, 63, 0.02) 1px, transparent 1px),
                linear-gradient(90deg, rgba(141, 198, 63, 0.02) 1px, transparent 1px);
            background-size: 60px 60px;
            pointer-events: none;
            z-index: -1;
        }

        /* ===========================================
           SLIDE CONTAINER
           =========================================== */
        .slide {
            min-height: 100vh;
            padding: var(--slide-padding);
            scroll-snap-align: start;
            display: flex;
            flex-direction: column;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        .slide-content {
            max-width: 1000px;
            margin: 0 auto;
            width: 100%;
        }

        /* ===========================================
           TYPOGRAPHY
           =========================================== */
        h1 {
            font-size: clamp(2.5rem, 7vw, 4.5rem);
            font-weight: 600;
            line-height: 1.1;
            letter-spacing: -0.03em;
        }

        h2 {
            font-size: clamp(2rem, 5vw, 3.5rem);
            font-weight: 600;
            line-height: 1.15;
            letter-spacing: -0.02em;
        }

        .subtitle {
            font-family: var(--font-serif);
            font-size: clamp(1.1rem, 2vw, 1.35rem);
            font-weight: 400;
            color: var(--text-secondary);
            line-height: 1.7;
            max-width: 550px;
        }

        .accent {
            color: var(--accent);
        }

        .slide-number {
            font-family: var(--font-serif);
            font-size: 0.9rem;
            color: var(--accent);
            letter-spacing: 0.3em;
            margin-bottom: 2rem;
        }

        /* ===========================================
           ANIMATIONS
           =========================================== */
        .reveal {
            opacity: 0;
            transform: translateY(40px);
            transition:
                opacity var(--duration-normal) var(--ease-out-expo),
                transform var(--duration-normal) var(--ease-out-expo);
        }

        .slide.visible .reveal {
            opacity: 1;
            transform: translateY(0);
        }

        /* Staggered children */
        .slide.visible .reveal:nth-child(1) { transition-delay: 0.1s; }
        .slide.visible .reveal:nth-child(2) { transition-delay: 0.2s; }
        .slide.visible .reveal:nth-child(3) { transition-delay: 0.3s; }
        .slide.visible .reveal:nth-child(4) { transition-delay: 0.4s; }
        .slide.visible .reveal:nth-child(5) { transition-delay: 0.5s; }
        .slide.visible .reveal:nth-child(6) { transition-delay: 0.6s; }

        /* Divider animation */
        .divider {
            width: 60px;
            height: 3px;
            background: var(--accent);
            margin: 1.5rem 0 2rem;
            transform: scaleX(0);
            transform-origin: left;
            transition: transform var(--duration-normal) var(--ease-out-expo);
        }

        .slide.visible .divider {
            transform: scaleX(1);
        }

        /* ===========================================
           COMPONENTS
           =========================================== */

        /* Stat cards */
        .stat-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 2rem;
            margin-top: 3rem;
        }

        .stat-card {
            background: var(--bg-secondary);
            border: 1px solid var(--border);
            border-radius: 16px;
            padding: 2rem;
            text-align: center;
            box-shadow: 0 4px 20px rgba(0,0,0,0.3);
        }

        .stat-number {
            font-size: clamp(2.5rem, 5vw, 3.5rem);
            font-weight: 700;
            color: var(--accent);
            line-height: 1;
            margin-bottom: 0.5rem;
        }

        .stat-label {
            font-size: 0.95rem;
            color: var(--text-secondary);
        }

        /* Feature cards */
        .feature-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 1.5rem;
            margin-top: 2.5rem;
        }

        .feature-card {
            background: var(--bg-secondary);
            border: 1px solid var(--border);
            border-radius: 16px;
            padding: 2rem;
            transition: transform 0.3s var(--ease-out-expo), box-shadow 0.3s ease;
            box-shadow: 0 4px 20px rgba(0,0,0,0.3);
        }

        .feature-card:hover {
            transform: translateY(-4px);
            box-shadow: 0 12px 40px rgba(141, 198, 63, 0.15);
            border-color: var(--accent);
        }

        .feature-icon {
            width: 48px;
            height: 48px;
            border-radius: 12px;
            background: var(--accent-light);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            margin-bottom: 1rem;
        }

        .feature-title {
            font-size: 1.15rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
        }

        .feature-desc {
            font-size: 0.95rem;
            color: var(--text-secondary);
            line-height: 1.6;
        }

        /* Quote block */
        .quote-block {
            background: var(--bg-secondary);
            border-left: 4px solid var(--accent);
            border-radius: 0 16px 16px 0;
            padding: 2.5rem 3rem;
            margin-top: 2rem;
            box-shadow: 0 4px 20px rgba(0,0,0,0.3);
        }

        .quote-text {
            font-family: var(--font-serif);
            font-size: clamp(1.25rem, 2.5vw, 1.75rem);
            line-height: 1.6;
            color: var(--text-primary);
        }

        .quote-author {
            margin-top: 1.5rem;
            font-size: 0.95rem;
            color: var(--text-secondary);
        }

        /* Code block */
        .code-block {
            background: var(--bg-dark);
            border-radius: 16px;
            padding: 2rem;
            margin-top: 2rem;
            font-family: 'SF Mono', 'Fira Code', monospace;
            font-size: 0.9rem;
            color: #e6edf3;
            overflow-x: auto;
        }

        .code-comment { color: #6e7681; }
        .code-keyword { color: #ff7b72; }
        .code-string { color: #a5d6ff; }
        .code-function { color: #d2a8ff; }

        /* Timeline */
        .timeline {
            display: flex;
            justify-content: space-between;
            margin-top: 3rem;
            position: relative;
        }

        .timeline::before {
            content: '';
            position: absolute;
            top: 24px;
            left: 40px;
            right: 40px;
            height: 2px;
            background: var(--border);
        }

        .timeline-item {
            text-align: center;
            position: relative;
            flex: 1;
        }

        .timeline-dot {
            width: 48px;
            height: 48px;
            border-radius: 50%;
            background: var(--bg-secondary);
            border: 2px solid var(--border);
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 1rem;
            font-size: 1.25rem;
            position: relative;
            z-index: 1;
            transition: all 0.3s var(--ease-out-expo);
        }

        .timeline-item:hover .timeline-dot {
            border-color: var(--accent);
            background: var(--accent-light);
        }

        .timeline-label {
            font-weight: 600;
            font-size: 1rem;
            margin-bottom: 0.25rem;
        }

        .timeline-desc {
            font-size: 0.85rem;
            color: var(--text-secondary);
        }

        /* Buttons */
        .btn {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            padding: 1rem 2rem;
            border-radius: 100px;
            font-weight: 600;
            font-size: 1rem;
            text-decoration: none;
            transition: all 0.3s var(--ease-out-expo);
        }

        .btn-primary {
            background: var(--accent);
            color: #000000;
        }

        .btn-primary:hover {
            background: var(--accent-dark);
            transform: translateY(-2px);
            box-shadow: 0 8px 24px rgba(141, 198, 63, 0.3);
        }

        .btn-secondary {
            background: rgba(255,255,255,0.1);
            color: white;
            border: 1px solid rgba(255,255,255,0.2);
        }

        .btn-secondary:hover {
            background: rgba(255,255,255,0.15);
        }

        /* ===========================================
           NAVIGATION
           =========================================== */
        .nav-dots {
            position: fixed;
            right: 2rem;
            top: 50%;
            transform: translateY(-50%);
            display: flex;
            flex-direction: column;
            gap: 0.75rem;
            z-index: 100;
        }

        .nav-dot {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background: rgba(255,255,255,0.2);
            cursor: pointer;
            transition: all 0.3s var(--ease-out-expo);
        }

        .nav-dot:hover {
            background: rgba(255,255,255,0.4);
        }

        .nav-dot.active {
            background: var(--accent);
            transform: scale(1.3);
            box-shadow: 0 0 12px rgba(141, 198, 63, 0.5);
        }

        /* Progress bar */
        .progress-bar {
            position: fixed;
            top: 0;
            left: 0;
            height: 3px;
            background: var(--accent);
            z-index: 100;
            transition: width 0.3s ease;
        }

        /* Keyboard hint */
        .keyboard-hint {
            position: fixed;
            bottom: 2rem;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            align-items: center;
            gap: 0.5rem;
            font-size: 0.8rem;
            color: var(--text-light);
            opacity: 0.6;
        }

        .key {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            min-width: 28px;
            height: 28px;
            padding: 0 8px;
            background: var(--bg-secondary);
            border: 1px solid var(--border);
            border-radius: 6px;
            font-size: 0.75rem;
            font-weight: 500;
            color: var(--text-secondary);
        }

        /* ===========================================
           RESPONSIVE
           =========================================== */
        @media (max-width: 768px) {
            .stat-grid {
                grid-template-columns: 1fr;
                gap: 1rem;
            }

            .feature-grid {
                grid-template-columns: 1fr;
            }

            .timeline {
                flex-direction: column;
                gap: 1.5rem;
            }

            .timeline::before {
                display: none;
            }

            .nav-dots,
            .keyboard-hint {
                display: none;
            }
        }

        /* ===========================================
           REDUCED MOTION
           =========================================== */
        @media (prefers-reduced-motion: reduce) {
            .reveal {
                opacity: 1;
                transform: none;
                transition: none;
            }

            .divider {
                transform: scaleX(1);
                transition: none;
            }

            html {
                scroll-behavior: auto;
            }
        }
    </style>
</head>
<body>
    <!-- Progress bar -->
    <div class="progress-bar" style="width: 0%"></div>

    <!-- Navigation dots -->
    <nav class="nav-dots" aria-label="Slide navigation"></nav>

    <!-- Slides go here -->
    <section class="slide title-slide">
        <div class="slide-content" style="text-align: center;">
            <p class="slide-number reveal">01 / XX</p>
            <h1 class="reveal">Presentation Title</h1>
            <div class="divider" style="margin: 1.5rem auto 2rem; transform-origin: center;"></div>
            <p class="subtitle reveal" style="margin: 0 auto;">Subtitle or tagline goes here</p>
        </div>
    </section>

    <!-- More slides... -->

    <!-- Keyboard hint -->
    <div class="keyboard-hint">
        <span class="key">←</span>
        <span class="key">→</span>
        <span>or</span>
        <span class="key">Space</span>
        <span>to navigate</span>
    </div>

    <script>
        /* ===========================================
           SLIDE PRESENTATION CONTROLLER
           =========================================== */
        class SlidePresentation {
            constructor() {
                this.slides = document.querySelectorAll('.slide');
                this.navDots = document.querySelector('.nav-dots');
                this.progressBar = document.querySelector('.progress-bar');
                this.currentSlide = 0;
                this.totalSlides = this.slides.length;

                this.init();
            }

            init() {
                this.createNavDots();
                this.setupIntersectionObserver();
                this.setupKeyboardNav();
                this.setupTouchNav();
                this.setupWheelNav();
                this.updateProgress();
                this.slides[0].classList.add('visible');
            }

            createNavDots() {
                this.slides.forEach((_, index) => {
                    const dot = document.createElement('button');
                    dot.className = 'nav-dot' + (index === 0 ? ' active' : '');
                    dot.setAttribute('aria-label', `Go to slide ${index + 1}`);
                    dot.addEventListener('click', () => this.goToSlide(index));
                    this.navDots.appendChild(dot);
                });
                this.dots = document.querySelectorAll('.nav-dot');
            }

            setupIntersectionObserver() {
                const observer = new IntersectionObserver((entries) => {
                    entries.forEach(entry => {
                        if (entry.isIntersecting) {
                            entry.target.classList.add('visible');
                            const index = Array.from(this.slides).indexOf(entry.target);
                            this.currentSlide = index;
                            this.updateNavDots();
                            this.updateProgress();
                        }
                    });
                }, { threshold: 0.5 });

                this.slides.forEach(slide => observer.observe(slide));
            }

            setupKeyboardNav() {
                document.addEventListener('keydown', (e) => {
                    if (e.key === 'ArrowDown' || e.key === 'ArrowRight' || e.key === ' ') {
                        e.preventDefault();
                        this.nextSlide();
                    } else if (e.key === 'ArrowUp' || e.key === 'ArrowLeft') {
                        e.preventDefault();
                        this.prevSlide();
                    }
                });
            }

            setupTouchNav() {
                let touchStartY = 0;
                document.addEventListener('touchstart', (e) => {
                    touchStartY = e.changedTouches[0].screenY;
                }, { passive: true });

                document.addEventListener('touchend', (e) => {
                    const diff = touchStartY - e.changedTouches[0].screenY;
                    if (Math.abs(diff) > 50) {
                        diff > 0 ? this.nextSlide() : this.prevSlide();
                    }
                }, { passive: true });
            }

            setupWheelNav() {
                let lastScrollTime = 0;
                document.addEventListener('wheel', (e) => {
                    const now = Date.now();
                    if (now - lastScrollTime < 800) return;
                    if (Math.abs(e.deltaY) > 30) {
                        lastScrollTime = now;
                        e.deltaY > 0 ? this.nextSlide() : this.prevSlide();
                    }
                }, { passive: true });
            }

            goToSlide(index) {
                if (index >= 0 && index < this.totalSlides) {
                    this.slides[index].scrollIntoView({ behavior: 'smooth' });
                }
            }

            nextSlide() {
                if (this.currentSlide < this.totalSlides - 1) {
                    this.goToSlide(this.currentSlide + 1);
                }
            }

            prevSlide() {
                if (this.currentSlide > 0) {
                    this.goToSlide(this.currentSlide - 1);
                }
            }

            updateNavDots() {
                this.dots.forEach((dot, index) => {
                    dot.classList.toggle('active', index === this.currentSlide);
                });
            }

            updateProgress() {
                const progress = ((this.currentSlide + 1) / this.totalSlides) * 100;
                this.progressBar.style.width = `${progress}%`;
            }
        }

        document.addEventListener('DOMContentLoaded', () => {
            new SlidePresentation();
        });
    </script>
</body>
</html>
```

---

## Phase 4: PPT Conversion

When converting PowerPoint files:

### Step 4.1: Extract Content

Use Python with `python-pptx` to extract:

```python
from pptx import Presentation
from pptx.util import Inches, Pt
import json
import os

def extract_pptx(file_path, output_dir):
    """
    Extract all content from a PowerPoint file.
    Returns a JSON structure with slides, text, and images.
    """
    prs = Presentation(file_path)
    slides_data = []

    assets_dir = os.path.join(output_dir, 'assets')
    os.makedirs(assets_dir, exist_ok=True)

    for slide_num, slide in enumerate(prs.slides):
        slide_data = {
            'number': slide_num + 1,
            'title': '',
            'content': [],
            'images': [],
            'notes': ''
        }

        for shape in slide.shapes:
            if shape.has_text_frame:
                if shape == slide.shapes.title:
                    slide_data['title'] = shape.text
                else:
                    slide_data['content'].append({
                        'type': 'text',
                        'content': shape.text
                    })

            if shape.shape_type == 13:  # Picture
                image = shape.image
                image_bytes = image.blob
                image_ext = image.ext
                image_name = f"slide{slide_num + 1}_img{len(slide_data['images']) + 1}.{image_ext}"
                image_path = os.path.join(assets_dir, image_name)

                with open(image_path, 'wb') as f:
                    f.write(image_bytes)

                slide_data['images'].append({
                    'path': f"assets/{image_name}",
                    'width': shape.width,
                    'height': shape.height
                })

        if slide.has_notes_slide:
            slide_data['notes'] = slide.notes_slide.notes_text_frame.text

        slides_data.append(slide_data)

    return slides_data
```

### Step 4.2: Confirm Content Structure

Present the extracted content to the user, then generate using the DK Horse theme.

---

## Phase 5: Delivery

### Final Output

When the presentation is complete:

1. **Open the presentation** — Use `open [filename].html` to launch in browser

2. **Provide summary**
```
Your presentation is ready!

📁 File: [filename].html
🎨 Theme: DK Horse (Dark + Lime Green)
📊 Slides: [count]

**Navigation:**
- Arrow keys (← →) or Space to navigate
- Scroll/swipe also works
- Click the dots on the right to jump to a slide

**To customize:**
- Colors: Look for `:root` CSS variables at the top
- Fonts: Change the Fontshare link
- Animations: Modify `.reveal` class timings

Would you like me to make any adjustments?
```

---

## Component Reference

### Stat Cards
```html
<div class="stat-grid">
    <div class="stat-card reveal">
        <div class="stat-number">42%</div>
        <div class="stat-label">Description here</div>
    </div>
</div>
```

### Feature Cards
```html
<div class="feature-grid">
    <div class="feature-card reveal">
        <div class="feature-icon">🚀</div>
        <div class="feature-title">Feature Title</div>
        <div class="feature-desc">Feature description goes here.</div>
    </div>
</div>
```

### Quote Block
```html
<div class="quote-block reveal">
    <p class="quote-text">"Quote text goes here."</p>
    <p class="quote-author">— Author Name, Title</p>
</div>
```

### Timeline
```html
<div class="timeline reveal">
    <div class="timeline-item">
        <div class="timeline-dot">📋</div>
        <div class="timeline-label">Step</div>
        <div class="timeline-desc">Description</div>
    </div>
</div>
```

### Code Block
```html
<div class="code-block reveal">
    <span class="code-comment"># Comment</span><br>
    <span class="code-keyword">command</span> argument
</div>
```

### Buttons
```html
<div class="cta-buttons reveal">
    <a href="#" class="btn btn-primary">Primary Action →</a>
    <a href="#" class="btn btn-secondary">Secondary Action</a>
</div>
```

---

## Example Session Flow

1. User: "Create a presentation about our Q4 roadmap"
2. Skill asks about purpose (Internal), length (Medium), content readiness
3. User shares bullet points
4. Skill asks about layout preference and animation level
5. Skill generates full DK-branded presentation
6. Skill opens in browser
7. User requests tweaks
8. Final presentation delivered
