# Comprehensive Content Review - Round 2

## Executive Summary
This document lists all remaining discrepancies, content inconsistencies, and suggestions for improvement after comparing the resume PDF with the current website.

---

## 1. CRITICAL DISCREPANCIES

### 1.1 DH2i Job Description Mismatch
**Resume says:**
- "Patched DxEnterprise bugs and implemented enhancement features. (centralized logging, near command suggestion..)"

**Website says:**
- No mention of bug patches or enhancement features like centralized logging

**Fix:** Add the missing bullet point about DxEnterprise bug patches and enhancements.

### 1.2 Conative AI Job Title
**Resume says:** "Machine Learning Engineer Intern"
**Website says:** "Machine Learning Engineer Intern" ✓ (Correct)

### 1.3 Conative AI Description
**Resume says:**
- "Developed PyTorch-based time-series models for sales inventory prediction, effectively preventing stock-outs."

**Website says:**
- "Create complete and intepretable Deep Learning pipeline (Pytorch Temporal Fusion Transformer)"
- Typo: "intepretable" should be "interpretable"

**Fix:** Align description with resume and fix typo.

### 1.4 SoftwareOne Description Mismatch
**Resume says:**
- "Built time-series forecasting models (DeepVAR, Prophet) using AWS Redshift and S3 to predict monthly subscription trends."
- "Engineered NLP pipeline (TF-IDF, LDA) to automatically tag and categorize workout XML data, enabling personalized user recommendations."
- "Constructed scalable ML pipelines on Azure Databricks/Spark for credit card fraud detection, managing data versioning via DataLake Gen2."
- "Deployed Azure Bot Framework chatbot integrated with ChatGPT, LangChain, and ChromaDB supporting natural language and SQL queries."
- "Developed Streamlit dashboard to visualize database query results and model predictions for stakeholders."

**Website has 4 projects but missing:**
- Streamlit dashboard project

**Fix:** Add the Streamlit dashboard project.

### 1.5 Katalon Description Mismatch
**Resume says:**
- "Developed graph-based representation of Application Under Test (AUT) to automate test case generation and optimization."
- "Reduced test execution time by 30% while maintaining fault coverage through optimized test set generation."
- "Created interactive GUI for visualizing test results, exposing potential security threats and faults."

**Website says:**
- "Develop state-of-the-art graph representation of AUT from existing human test cases."
- "Generate and optimize test sets to save time while retaining fault coverage."
- "Visualize interactive graph to analyze results."
- "Automate exploration and find new faults."

**Fix:** Align bullet points with resume wording. The 30% metric is important and should be highlighted.

---

## 2. CONTENT INCONSISTENCIES

### 2.1 About Section
**Current:** Generic description about LLM workflows
**Suggestion:** Make it more specific and aligned with the resume's focus areas. Add mention of specific achievements.

### 2.2 Services Section
**Current services:**
- Cloud services
- Query optimization
- AI/ML models
- Algorithm
- Containerization
- Data Engineering

**Suggestion:** These don't directly map to the resume. Consider renaming to better reflect actual expertise:
- LLM Workflow Development
- Cloud Infrastructure (AWS, Azure, GCP)
- Machine Learning Pipelines
- Full-Stack Development
- Data Engineering & Analytics
- AI Chatbot Integration

### 2.3 Education Section Descriptions
**Master's description:** "Deep diving into explaining black-box models, designing cloud infrastructure and networking for AI/ML models."
- This is not in the resume. Consider removing or keeping as supplementary info.

**Bachelor's description:** "Mastering OOP, computer hardware, software engineering concepts and focus on generating optimized test cases from manual test cases."
- This is not in the resume. Consider removing or keeping as supplementary info.

### 2.4 Awards Section
**Resume says:** "MIT App Inventor (Community Award 2018)"
**Website says:** "MIT App Inventor - Community Award" with date "2018"
✓ Correct, but the description is generic. Consider making it more specific.

---

## 3. MISSING CONTENT

### 3.1 LinkedIn Link
**Resume has:** LinkedIn link in header
**Website has:** Social media icons in sidebar but they link to "#" (nowhere)

**Fix:** Add actual LinkedIn profile URL.

### 3.2 Portfolio/GitHub Links
**Resume has:** Portfolio link in header
**Website has:** No GitHub link in sidebar social icons

**Fix:** Add GitHub link to sidebar.

### 3.3 Project Images
**Missing images for:**
- `img-news.jpg` (News Analysis project)
- `img-stock.jpg` (Stock Market Analysis project)

**Suggestion:** Either add placeholder images or use existing images.

---

## 4. TYPOGRAPHY AND GRAMMAR ISSUES

### 4.1 Hero Section
- Line 124: "My expertise lies in building infrastructure and automating sophisticated LLM workflow." → Should be "LLM workflows" (plural)
- Line 124: Closing tag mismatch - `<h2>` has `</a>` inside it (stray anchor close tag)

### 4.2 About Section
- Line 149: "effciency" → "efficiency"
- Line 145: "Hello, I am Viet" → Consider "Hello, I am Viet-Thanh Le" for consistency with resume

### 4.3 Experience Section
- Line 490: "intepretable" → "interpretable"
- Line 489: "Sale inventory" → "Sales inventory"
- Line 653: "comparision" → "comparison"

### 4.4 Services Section
- Line 245: "Algorithm designing and analysis" → Consider "Algorithm Design & Analysis"
- Line 256: "minimalize" → "minimize"

---

## 5. DESIGN AND UX IMPROVEMENTS

### 5.1 Sidebar Navigation
- Missing "Awards" menu item (section exists but not in nav)
- Social media icons point to "#" - should be real links or removed

### 5.2 Meta Tags
- Empty meta description and keywords
- Empty Open Graph tags
- Empty Twitter card tags

**Suggestion:** Fill in proper meta tags for SEO.

### 5.3 Footer
- Copyright says "Made by Colorlib" - template attribution
- Consider customizing or keeping as is (required by license)

### 5.4 Project Section
- Projects without images (News Analysis, Stock Market) will show broken backgrounds
- Consider adding placeholder images or using gradient backgrounds

### 5.5 Consistency
- Job titles use different formats across sections
- Date formats vary (e.g., "May 2025 - Present" vs "September 2023 – March 2025")
- Company names sometimes include location, sometimes don't

---

## 6. RECOMMENDED PRIORITY ORDER

### Phase 1: Critical Fixes
1. Fix typos (intepretable, effciency, comparision, Sale→Sales)
2. Fix HTML errors (stray </a> tag in hero section)
3. Add missing DH2i bullet point (bug patches)
4. Add missing SoftwareOne project (Streamlit dashboard)
5. Align Katalon description with resume (add 30% metric)

### Phase 2: Content Enhancement
1. Update Services section to match actual expertise
2. Add LinkedIn and GitHub links to sidebar
3. Add Awards to navigation menu
4. Fill in meta tags for SEO

### Phase 3: Polish
1. Standardize date formats
2. Standardize company name formats
3. Add placeholder images for missing projects
4. Review and improve About section

---

## 7. CSS COMPATIBILITY

All proposed changes use existing CSS classes:
- `.timeline-entry`, `.projects`, `.title`, `.subtitle` - Already exist
- `.award-entry` - Added in previous round
- `.skills-category` - Added in previous round

No new CSS needed for content changes.

---

## 8. VISUAL IMPROVEMENT SUGGESTIONS

### 8.1 Color Scheme
- Current color scheme is professional and clean
- Consider adding subtle gradient backgrounds to project cards without images

### 8.2 Typography
- Consider adding a subtitle under the name in the sidebar
- Consider adding location to the sidebar (Portland, OR)

### 8.3 Layout
- Consider adding a "Certifications" section if any exist
- Consider adding a "Publications" section if any exist