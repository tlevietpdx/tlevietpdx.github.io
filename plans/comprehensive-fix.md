# Comprehensive Portfolio Website Fix Plan

## Overview
This plan outlines all changes needed to align the portfolio website with the resume. Changes are organized by priority and include specific implementation details.

## CSS Compatibility Analysis

**Existing CSS Classes (Compatible):**
- `.timeline-entry`, `.timeline-entry-inner`, `.timeline-icon`, `.timeline-label` - For experience section
- `.panel`, `.panel-heading`, `.panel-body` - For education section
- `.project`, `.desc`, `.con` - For projects section
- `.colorlib-experience`, `.colorlib-skills`, `.colorlib-education`, `.colorlib-work`, `.colorlib-contact` - Section wrappers
- `.animate-box`, `data-animate-effect` - For animations
- `.projects`, `.title`, `.subtitle` - For project descriptions within experience

**New CSS Classes Needed:**
- `.colorlib-awards` - Can reuse `.colorlib-education` styling (add to existing CSS rule at line 414)
- `.award-entry` - Needs new CSS (see CSS additions below)
- `.skills-category` - Needs new CSS (see CSS additions below)

**CSS Additions Required:**
Add to [`css/style.css`](css/style.css) at the end before closing:
```css
/* Awards Section */
.colorlib-awards {
    padding-top: 4em;
    padding-bottom: 4em;
}

.award-entry {
    padding: 20px;
    margin-bottom: 20px;
    border-left: 3px solid #2c98f0;
    background: #f9f9f9;
}

.award-entry h3 {
    margin: 0 0 10px 0;
    color: #000;
}

.award-entry .date {
    color: #727272;
    font-style: italic;
    margin-bottom: 10px;
}

/* Skills Categories */
.skills-category {
    margin-bottom: 30px;
    padding: 20px;
    background: #f9f9f9;
    border-radius: 4px;
}

.skills-category h3 {
    font-size: 18px;
    margin-bottom: 15px;
    color: #000;
    border-bottom: 2px solid #2c98f0;
    padding-bottom: 10px;
}

.skills-category p {
    color: #727272;
    line-height: 1.8;
    margin: 0;
}
```

---

## Phase 1: Critical Fixes (Must Do First)

### 1.1 Add DH2i Current Job Position
**Location:** [`index.html`](index.html:498) - Experience section, before Conative AI entry

**Action:** Insert new timeline entry at the top of the experience section

```html
<article class="timeline-entry animate-box" data-animate-effect="fadeInLeft">
    <div class="timeline-entry-inner">
        <div class="timeline-icon color-1">
            <i class="icon-briefcase3"></i>
        </div>
        <div class="timeline-label">
            <h2><a>Software Development Engineer</a> <span>May 2025 - Present</span></h2>
            <h5>DH2i, Clackamas, Oregon</h5>
            <div class="projects">
                <p class="title">LLM Inference Optimization</p>
                <p class="subtitle">Optimized local LLM inference with vLLM, supporting 32+ concurrent requests and multi-token prediction (MTP).</p>
            </div>
            <div class="projects">
                <p class="title">AI Workflow Integration</p>
                <p class="subtitle">Integrated AI workflows into DxEnterprise, eliminating documentation overhead and accelerating feature deployment.</p>
            </div>
            <div class="projects">
                <p class="title">Vue.js Migration</p>
                <p class="subtitle">Migrated legacy DxAdmin Windows app to Vue.js with enhanced visualization and AI capabilities.</p>
            </div>
            <div class="projects">
                <p class="title">Automated Support Analysis</p>
                <p class="subtitle">Automated support case analysis using Airflow to generate technical diagnoses and reduce manual review time.</p>
            </div>
            <div class="projects">
                <p class="title">MCP Server Implementation</p>
                <p class="subtitle">Implemented Model Context Protocol (MCP) server with code indexing and analysis to centralize codebase repos with 3rd party OAuth for access control.</p>
            </div>
            <div class="projects">
                <p class="title">Resume Review Workflow</p>
                <p class="subtitle">Implemented resume review workflow to grade application based on set criteria and experiences alignment with job description.</p>
            </div>
        </div>
    </div>
</article>
```

### 1.2 Fix Email Address
**Location:** [`index.html:787`](index.html:787)

**Current:** `<a href="mailto:tleviet@pdx.edu">lvthanh1822@gmail.com</a>`
**Fix:** Update to use primary email from resume

```html
<p>
    <a href="mailto:lvthanh1822@gmail.com">lvthanh1822@gmail.com</a><br>
    <a href="mailto:tleviet@pdx.edu">tleviet@pdx.edu</a>
</p>
```

### 1.3 Fix Resume Download Link
**Location:** [`index.html:109`](index.html:109)

**Current:** `href="overleaf_resume.pdf"`
**Fix:** `href="VietThanh_Le_resume.pdf"`

```html
<a class="btn btn-primary btn-learn" href="VietThanh_Le_resume.pdf" download="VietThanhLe_resume.pdf">Download Resumé <i class="icon-download4"></i></a>
```

---

## Phase 2: High Priority Fixes

### 2.1 Fix Bachelor's GPA
**Location:** [`index.html:473`](index.html:473)

**Current:** `GPA: 3.87`
**Fix:** `GPA: 3.78`

### 2.2 Fix Conative AI End Date
**Location:** [`index.html:506`](index.html:506)

**Current:** `<span>October 2024 - Present</span>`
**Fix:** `<span>October 2024 - March 2025</span>`

### 2.3 Fix Katalon Job Title
**Location:** [`index.html:585`](index.html:585)

**Current:** `<h2><a>Research Intern</a>`
**Fix:** `<h2><a>Engineering Research Assistant</a>`

### 2.4 Fix Phone Number Format
**Location:** [`index.html:805`](index.html:805)

**Current:** `<a href="tel://">(+1) 503-544-2906</a>`
**Fix:** `<a href="tel:+15035442906">(503)-544-2906</a>`

---

## Phase 3: Medium Priority - Education Section Enhancement

### 3.1 Add University Names and Dates to Master's Section
**Location:** [`index.html:448-462`](index.html:448)

**Current:**
```html
<a data-toggle="collapse" data-parent="#accordion" href="#collapseOne" aria-expanded="false" aria-controls="collapseOne">Master's in Computer Science</a>
<div class="panel-body">
    <div class="row">
        <div class="col-md-6">
            <p>GPA: 3.93 </p>
            <p>Deep diving into explaining black-box models, designing cloud infrastructure and networking for AI/ML models.</p>
        </div>
    </div>
</div>
```

**Fix:**
```html
<a data-toggle="collapse" data-parent="#accordion" href="#collapseOne" aria-expanded="false" aria-controls="collapseOne">Master's in Computer Science</a>
<div class="panel-body">
    <div class="row">
        <div class="col-md-6">
            <p><strong>Portland State University</strong>, Portland, Oregon</p>
            <p>September 2023 – March 2025</p>
            <p>GPA: 3.93</p>
        </div>
        <div class="col-md-6">
            <p>Deep diving into explaining black-box models, designing cloud infrastructure and networking for AI/ML models.</p>
        </div>
    </div>
</div>
```

### 3.2 Add University Names and Dates to Bachelor's Section
**Location:** [`index.html:467-478`](index.html:467)

**Current:**
```html
<a class="collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapseTwo" aria-expanded="false" aria-controls="collapseTwo">Bachelor of Computer Science</a>
<div id="collapseTwo" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingTwo">
    <div class="panel-body">
        <p>GPA: 3.87</p>
        <p>Mastering OOP, computer hardware, software engineering concepts and focus on generating optimized test cases from manual test cases.</p>
    </div>
</div>
```

**Fix:**
```html
<a class="collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapseTwo" aria-expanded="false" aria-controls="collapseTwo">Bachelor of Computer Science</a>
<div id="collapseTwo" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingTwo">
    <div class="panel-body">
        <div class="row">
            <div class="col-md-6">
                <p><strong>VNUHCM University of Science</strong>, Ho Chi Minh, Vietnam</p>
                <p>September 2018 – July 2022</p>
                <p>GPA: 3.78</p>
            </div>
            <div class="col-md-6">
                <p>Mastering OOP, computer hardware, software engineering concepts and focus on generating optimized test cases from manual test cases.</p>
            </div>
        </div>
    </div>
</div>
```

---

## Phase 4: Low Priority - Enhancements

### 4.1 Add Awards Section
**Location:** After education section, before experience section

**Note:** Requires adding `.colorlib-awards` to existing CSS rule at line 414 in [`css/style.css`](css/style.css:414) and adding new CSS for `.award-entry` (see CSS Additions above)

**Action:** Add new section between education and experience

```html
<section class="colorlib-awards" data-section="awards">
    <div class="colorlib-narrow-content">
        <div class="row">
            <div class="col-md-6 col-md-offset-3 col-md-pull-3 animate-box" data-animate-effect="fadeInLeft">
                <span class="heading-meta">Recognition</span>
                <h2 class="colorlib-heading animate-box">Awards</h2>
            </div>
        </div>
        <div class="row">
            <div class="col-md-12 animate-box" data-animate-effect="fadeInLeft">
                <div class="award-entry">
                    <h3>MIT App Inventor - Community Award</h3>
                    <p class="date">2018</p>
                    <p>Recognized for innovative mobile application development using MIT App Inventor platform.</p>
                </div>
            </div>
        </div>
    </div>
</section>
```

### 4.2 Enhance Technical Skills Section
**Location:** [`index.html:301-430`](index.html:301)

**Note:** Requires adding new CSS for `.skills-category` (see CSS Additions above). This will replace the current progress bars with a cleaner skills listing that matches the resume format.

**Action:** Replace current progress bars with comprehensive skills categories

```html
<section class="colorlib-skills" data-section="skills">
    <div class="colorlib-narrow-content">
        <div class="row">
            <div class="col-md-6 col-md-offset-3 col-md-pull-3 animate-box" data-animate-effect="fadeInLeft">
                <span class="heading-meta">My Specialty</span>
                <h2 class="colorlib-heading animate-box">Technical Skills</h2>
            </div>
        </div>
        <div class="row">
            <div class="col-md-6 animate-box" data-animate-effect="fadeInLeft">
                <div class="skills-category">
                    <h3>Languages</h3>
                    <p>Python, Java, JavaScript, C/C++/C#, SQL, HTML/CSS, R, Rust, Haskell</p>
                </div>
                <div class="skills-category">
                    <h3>AI/LLM Stack</h3>
                    <p>LangChain, LangGraph, vLLM, HuggingFace, PyTorch, TensorFlow, MLFlow, Azure Bot Framework, OpenAI API</p>
                </div>
            </div>
            <div class="col-md-6 animate-box" data-animate-effect="fadeInRight">
                <div class="skills-category">
                    <h3>Frameworks</h3>
                    <p>React, Vue.js, Node.js, Flask, Streamlit, Reflex Python</p>
                </div>
                <div class="skills-category">
                    <h3>Cloud/DevOps</h3>
                    <p>AWS (S3, Redshift), Azure (Databricks, DataLake), GCP (Vertex AI), Docker, Git, Airflow</p>
                </div>
                <div class="skills-category">
                    <h3>Libraries</h3>
                    <p>Pandas, NumPy, Scikit-learn, OpenCV, BeautifulSoup, Selenium</p>
                </div>
            </div>
        </div>
    </div>
</section>
```

### 4.3 Add Missing Projects
**Location:** [`index.html:610-721`](index.html:610) - Work section

**Action:** Add two new project entries for News Analysis and Stock Market Analysis

```html
<div class="col-md-6 animate-box" data-animate-effect="fadeInLeft">
    <div class="project" style="background-image: url(images/img-news.jpg);">
        <div class="desc">
            <div class="con">
                <h3><a href="#">News Analysis and Research</a></h3>
                <span>News analysis platform with CloakBrowser, LangGraph, SQLite, BeautifulSoup4, SMTP, Pinia, Vue.js, MOSS-TTS persona audio generation</span>
                <p class="icon">
                    <span><a><i class="icon-share3"></i></a></span>
                    <span><a><i class="icon-eye"></i>♾️</a></span>
                    <span><a><i class="icon-heart"></i>♾️</a></span>
                </p>
            </div>
        </div>
    </div>
</div>
<div class="col-md-6 animate-box" data-animate-effect="fadeInRight">
    <div class="project" style="background-image: url(images/img-stock.jpg);">
        <div class="desc">
            <div class="con">
                <h3><a href="#">Stock Market Analysis</a></h3>
                <span>Stock market analysis and strategies simulation with CloakBrowser, LangGraph, SQLite, LangSmith, yfinance, FinnHub, AlphaVantage, SMTP</span>
                <p class="icon">
                    <span><a><i class="icon-share3"></i></a></span>
                    <span><a><i class="icon-eye"></i>♾️</a></span>
                    <span><a><i class="icon-heart"></i>♾️</a></span>
                </p>
            </div>
        </div>
    </div>
</div>
```

---

## Implementation Order

1. **Phase 1:** Critical fixes (DH2i job, email, resume link)
2. **Phase 2:** High priority fixes (GPA, dates, job titles)
3. **Phase 3:** Education section enhancements
4. **Phase 4:** Low priority enhancements (awards, skills, projects)

---

## Testing Checklist

- [ ] Verify all links work (resume download, email, phone)
- [ ] Check all dates match resume
- [ ] Verify all job titles match resume
- [ ] Confirm GPA values match resume
- [ ] Test email mailto link
- [ ] Verify phone tel link
- [ ] Check responsive design
- [ ] Test animations still work

---

## Notes

- Keep existing styling and animations intact
- Match existing code style and indentation
- Add new sections following existing patterns
- Ensure all changes are semantic and accessible