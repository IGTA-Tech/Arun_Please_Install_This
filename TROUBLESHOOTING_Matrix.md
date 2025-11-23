# 🔧 Troubleshooting Matrix - WordPress Content System

## Quick Diagnostic Guide

Use this matrix to quickly diagnose and fix common issues.

---

## 🚨 Critical Errors (System Won't Run)

### Error: "Missing required configuration"

**Symptoms:**
- Script fails immediately
- Error log shows missing configuration
- No articles generated

**Diagnosis:**
```
✓ Check Script Properties (Project Settings → Script Properties)
✓ Verify all 5 properties exist
✓ Confirm no typos in property names
```

**Fix:**
1. Open Apps Script editor
2. Click ⚙️ (Project Settings)
3. Scroll to "Script Properties"
4. Verify these exist:
   ```
   CLAUDE_API_KEY
   OPENAI_API_KEY
   WP_SITE_URL
   WP_USERNAME
   WP_APP_PASSWORD
   ```
5. If missing, add them
6. Ensure no extra spaces in values

**Verification:**
- Run `🚀 Content System` → `▶️ Generate & Publish Now`
- Should proceed past configuration phase

---

### Error: "WordPress publish failed: 401 Unauthorized"

**Symptoms:**
- Articles generate successfully
- Publishing to WordPress fails
- Error log shows 401 error

**Diagnosis:**
```
✓ WordPress Application Password incorrect
✓ WordPress username incorrect
✓ Authentication headers malformed
```

**Fix:**

**Option A: Regenerate Application Password**
1. Log into WordPress: `https://innovativeautomations.dev/wp-admin`
2. Go to Users → Your Profile
3. Scroll to "Application Passwords"
4. Delete existing "Content System" password
5. Create new one:
   - Name: `Content System v2`
   - Click `Add New Application Password`
6. Copy password (remove ALL spaces)
7. Update Script Properties:
   - `WP_APP_PASSWORD` = new password (no spaces, 24 chars)

**Option B: Verify Username**
1. In WordPress, check your username (Users → Your Profile)
2. Update Script Properties:
   - `WP_USERNAME` = exact username (case-sensitive)

**Option C: Check WordPress URL**
1. Verify Script Properties:
   - `WP_SITE_URL` = `https://innovativeautomations.dev`
   - NO trailing slash
   - MUST start with `https://`

**Verification:**
- Run manual generation
- Check for successful WordPress publish
- Verify posts appear in WordPress admin

---

### Error: "Claude API error: 401"

**Symptoms:**
- Content generation fails
- Error mentions Anthropic or Claude
- HTTP 401 status code

**Diagnosis:**
```
✓ Anthropic API key invalid
✓ API key revoked
✓ Account suspended
```

**Fix:**
1. **Verify API Key:**
   - Go to https://console.anthropic.com
   - Navigate to API Keys
   - Check key status (active/revoked)

2. **If Revoked:**
   - Create new API key
   - Copy new key
   - Update Script Properties:
     - `CLAUDE_API_KEY` = new key (starts with `sk-ant-`)

3. **Check Account Status:**
   - Verify billing info is current
   - Ensure account has credits
   - Check for any restrictions

**Verification:**
- Run: `🚀 Content System` → `▶️ Generate & Publish Now`
- Should successfully generate articles

---

### Error: "DALL-E API error: insufficient_quota"

**Symptoms:**
- Articles generate successfully
- Thumbnail generation fails
- Publishing may fail or proceed without images

**Diagnosis:**
```
✓ OpenAI account has no credits
✓ Billing issue
✓ API key invalid
```

**Fix:**
1. **Add Credits:**
   - Go to https://platform.openai.com
   - Click Settings → Billing
   - Add $10+ in credits

2. **Check API Key:**
   - Navigate to API Keys
   - Verify key is active
   - If revoked, create new key

3. **Update Script Properties:**
   - `OPENAI_API_KEY` = valid key (starts with `sk-`)

**Verification:**
- Run manual generation
- Confirm thumbnails are created
- Check WordPress media library for images

---

## ⚠️ Warning Issues (System Runs But Problems Exist)

### Warning: "Knowledge base folder not found"

**Symptoms:**
- Script runs but uses no knowledge base content
- Articles seem generic or lack specific details
- Warning in logs about missing folder

**Diagnosis:**
```
✓ Knowledge base folder not created
✓ KNOWLEDGE_BASE_FOLDER_ID not set
✓ Folder ID incorrect
```

**Fix:**
1. **Create Folder Structure:**
   - Run: `🚀 Content System` → `📁 Create Knowledge Base Folders`
   - Note the folder ID in toast message

2. **Verify Creation:**
   - Open Google Drive
   - Search for "Innovative_Automations_Knowledge_Base"
   - Open folder and verify subfolder structure

3. **Manual Fix (if needed):**
   - Find folder in Google Drive
   - Copy folder ID from URL (between `/folders/` and end)
   - Add to Script Properties:
     - Key: `KNOWLEDGE_BASE_FOLDER_ID`
     - Value: (folder ID)

**Verification:**
- Run manual generation
- Check logs for file count (should be > 0)
- Articles should reference knowledge base content

---

### Warning: Articles have low confidence scores

**Symptoms:**
- Confidence consistently below 92%
- Articles may be rejected by verification
- Quality seems subpar

**Diagnosis:**
```
✓ Insufficient knowledge base content
✓ Few or no inspiration sources
✓ Threshold too high for early generations
```

**Fix:**

**Short-term:**
1. **Lower Threshold (temporarily):**
   - Open Config sheet
   - Find `CONFIDENCE_THRESHOLD` row
   - Change value from 92 to 85
   - Allow system to build baseline

**Long-term:**
1. **Add More Knowledge Base Files:**
   - Open Drive folder
   - Add 5+ Google Docs to each category:
     - Success_Stories/
     - News_Updates/
     - Case_Studies/
   - Include specific examples, data, case studies

2. **Add Inspiration Sources:**
   - Open Inspiration_Sources sheet
   - Add competitor blogs:
     - Name: "Zapier Blog"
     - URL: "https://zapier.com/blog"
     - Type: "Website"
     - Active: TRUE

3. **Wait for Self-Learning:**
   - System improves after Generation 6
   - Confidence increases naturally over time
   - Target: 95%+ by Generation 20

**Verification:**
- Monitor Self_Learning_Database sheet
- Track average confidence over generations
- Should see upward trend

---

### Warning: Execution timeout / Takes too long

**Symptoms:**
- Script times out before completing
- Execution exceeds 6 minutes (Apps Script limit)
- Partial success or complete failure

**Diagnosis:**
```
✓ Too many knowledge base files
✓ Files too large (PDFs especially)
✓ Slow API responses
✓ Network issues
```

**Fix:**

**Reduce Knowledge Base Size:**
1. Open Drive folder
2. Check file sizes (aim for <5 MB each)
3. Remove or compress large PDFs
4. Limit to 20 files total per category
5. Move old/unused files to Archive

**Optimize Word Counts:**
1. Open Config sheet
2. Reduce target length:
   - `MAX_WORD_COUNT` = 2000 (from 2500)
   - `MIN_WORD_COUNT` = 1000 (from 1200)

**Split Execution (Advanced):**
1. Generate 1 article per run instead of 2
2. Run twice daily (8 AM, 4 PM)
3. Modify `determineContentStrategy()` to return only 1 article

**Verification:**
- Check Apps Script Executions log
- Execution should complete in <6 minutes
- Monitor for consistent success

---

### Warning: No email notifications received

**Symptoms:**
- System runs successfully
- WordPress posts publish
- No email received

**Diagnosis:**
```
✓ EMAIL_RECIPIENTS not configured
✓ Email in spam folder
✓ Apps Script can't send to external email
```

**Fix:**

**Configure Email:**
1. Open Config sheet
2. Find `EMAIL_RECIPIENTS` row (or add it)
3. Add email address: `your.email@example.com`
4. For multiple: `email1@example.com,email2@example.com`

**Check Spam:**
1. Search email for "Content Generation Complete"
2. Check spam/junk folder
3. Mark as "Not Spam" if found
4. Add sender to safe list

**Gmail Users:**
1. Emails from Apps Script may be filtered
2. Create filter:
   - From: (your Google account email)
   - Subject: "Content Generation"
   - Never send to spam

**Alternative Notifications:**
1. Use Slack webhook (modify script)
2. Check Content_Archive sheet directly
3. Monitor Apps Script Executions log

**Verification:**
- Run manual generation
- Check email within 1 minute of completion
- Verify email contains article links

---

## 🐛 Quality Issues (Content Problems)

### Issue: Articles too generic / not specific enough

**Symptoms:**
- Content lacks specific examples
- No reference to company services
- Generic industry information

**Diagnosis:**
```
✓ Knowledge base has generic content
✓ Not enough company-specific information
✓ Inspiration sources too broad
```

**Fix:**

**Enhance Knowledge Base:**
1. Add specific company information:
   - Service descriptions
   - Client case studies
   - Unique methodologies
   - Proprietary frameworks
   - Team expertise areas

2. Create detailed Google Docs:
   - "Company_Services_Overview.gdoc"
   - "Client_Success_Stories.gdoc"
   - "Technical_Capabilities.gdoc"
   - "Differentiators.gdoc"

3. Add to Success_Stories folder:
   - Specific client wins with names (if permissible)
   - ROI examples
   - Before/after scenarios

**Update Inspiration Sources:**
1. Remove generic industry sites
2. Add direct competitors for style
3. Focus on similar company sizes/markets

**Verification:**
- Generate new article
- Review for company-specific details
- Check if services are mentioned
- Verify examples are relevant

---

### Issue: SEO metadata not optimal

**Symptoms:**
- Meta descriptions not exactly 155 characters
- Titles too long or too short
- Missing keywords in content

**Diagnosis:**
```
✓ Verification layer not strict enough
✓ Claude not following exact requirements
✓ Prompt needs reinforcement
```

**Fix:**

**Immediate:**
1. Check Error_Log for verification failures
2. If meta descriptions aren't exactly 155 chars:
   - Verification should catch this
   - Check logs for "meta description" warnings

**Adjust Verification:**
1. Open script in Apps Script editor
2. Find `comprehensiveVerification()` function
3. Verify strict meta description check exists:
   ```javascript
   if (article.metaDescription.length !== 155) {
     errors.push(`Meta description must be EXACTLY 155 chars`);
   }
   ```

**Reinforce Prompt:**
1. Find `buildMasterPrompt()` function
2. Ensure it emphasizes:
   ```
   Meta description: EXACTLY 155 characters - count carefully
   Title: 50-60 characters
   Primary keyword in title and first paragraph
   ```

**Manual Post-Processing:**
1. Review first 10 articles in WordPress
2. Manually optimize if needed
3. System will learn from edits (if updated in WP)

**Verification:**
- Check Yoast SEO score in WordPress
- Aim for green "Good" rating
- Verify meta descriptions in Google search

---

### Issue: Thumbnails don't match brand style

**Symptoms:**
- Images look generic
- Colors don't match brand
- Style inconsistent

**Diagnosis:**
```
✓ DALL-E prompt not specific enough
✓ Brand guidelines not clear in prompt
✓ Image prompts in articles too vague
```

**Fix:**

**Update Brand Guidelines:**
1. Open script in Apps Script editor
2. Find `buildEnhancedDallePrompt()` function
3. Verify brand color codes:
   ```javascript
   Color palette: Professional blues (#2563eb, #1e40af)
   ```
4. Add more specific brand requirements:
   - Logo placement preference
   - Photography style
   - Graphic style
   - Mood/atmosphere

**Enhance Article Image Prompts:**
1. Knowledge base should include:
   - "Brand_Visual_Guidelines.gdoc"
   - Examples of preferred thumbnail styles
   - Links to visual inspiration

2. Update inspiration sources:
   - Add "Visual_Inspiration" folder
   - Include example images
   - Reference in image prompts

**Manual Review Process:**
1. Set `DEFAULT_POST_STATUS` to `draft`
2. Review thumbnails before publishing
3. Regenerate if needed (WordPress Media Library)
4. Provide feedback in knowledge base docs

**Verification:**
- Generate test article
- Review thumbnail for brand consistency
- Check color palette accuracy
- Verify professional appearance

---

## 🔄 Performance Issues

### Issue: Self-learning not activating

**Symptoms:**
- System past Generation 5
- Still shows "Building Baseline"
- No performance improvement

**Diagnosis:**
```
✓ MIN_GENERATIONS_FOR_LEARNING set too high
✓ Self-learning database not updating
✓ Content archive missing data
```

**Fix:**

**Check Generation Count:**
1. Open Self_Learning_Database sheet
2. Count rows (excluding header)
3. Should increment with each run
4. If not updating, check archive function

**Verify Threshold:**
1. Open Config sheet
2. Check `MIN_GENERATIONS_FOR_LEARNING`
3. Default: 5
4. If higher, reduce to 5

**Manual Reset (if needed):**
1. If database corrupted:
   - Backup current sheets
   - Delete Self_Learning_Database sheet
   - Run: `🚀 Content System` → `🏗️ Initialize All Sheets`
   - Manually add historical data if needed

**Verification:**
- Run generation #6 manually
- Check logs for "Self-Learning: ACTIVE"
- Verify email badge shows "🧠 Self-Learning Active"
- Review metadata in response

---

### Issue: Confidence scores not improving over time

**Symptoms:**
- Self-learning is active
- Confidence stuck at 88-92%
- No upward trend visible

**Diagnosis:**
```
✓ Knowledge base hasn't improved
✓ Self-learning weight too low
✓ WordPress has no posts to learn from
✓ System needs more time
```

**Fix:**

**Enhance Learning Weight:**
1. Open Config sheet
2. Find `SELF_CONTENT_WEIGHT`
3. Increase from 0.3 to 0.4 or 0.5
4. Allows more self-optimization

**Improve Knowledge Base:**
1. Add more high-quality content
2. Include successful article examples
3. Update with current information
4. Add more inspiration sources

**WordPress Style Learning:**
1. Manually publish 3-5 high-quality articles
2. System will learn from these
3. Ensure they match desired style

**Be Patient:**
1. Real improvement takes 15-20 generations
2. Track trend, not individual scores
3. Check Self_Learning_Database for patterns
4. Look for gradual 1-2% improvements

**Verification:**
- Create chart of confidence over time
- Calculate moving average
- Trend should be upward
- Target: 95% by Generation 30

---

## 🆘 Emergency Recovery

### Complete System Failure / Corruption

**Symptoms:**
- Multiple errors
- Can't run at all
- Sheets corrupted
- Unknown state

**Nuclear Option - Complete Rebuild:**

1. **Backup Current Data:**
   - File → Download → Microsoft Excel (.xlsx)
   - Save all sheets
   - Note Script Properties

2. **Create Fresh Google Sheet:**
   - New blank spreadsheet
   - Name: `Innovative Automations Content System v2`

3. **Re-add Script:**
   - Extensions → Apps Script
   - Copy fresh code from `Innovative_Automations_WordPress_Content_System.gs`
   - Save project

4. **Re-configure Script Properties:**
   - Add all 5 properties from backup notes

5. **Initialize Clean System:**
   - `🚀 Content System` → `🏗️ Initialize All Sheets`
   - `🚀 Content System` → `🏷️ Setup WordPress Categories`

6. **Restore Historical Data (optional):**
   - Manually copy Content_Archive from backup
   - Manually copy Self_Learning_Database from backup

7. **Test:**
   - Run manual generation
   - Verify success
   - Re-enable daily trigger

**Verification:**
- System runs without errors
- Fresh start with clean data
- Historical data preserved

---

## 📊 Diagnostic Checklist

Use this checklist when troubleshooting:

### Initial Diagnostics

- [ ] Check Error_Log sheet for recent errors
- [ ] Review Apps Script Executions log
- [ ] Verify all 5 Script Properties are set
- [ ] Confirm WordPress is accessible
- [ ] Check Anthropic account has credits
- [ ] Check OpenAI account has credits
- [ ] Verify knowledge base folder exists
- [ ] Confirm email is in Config sheet

### Configuration Verification

- [ ] `CLAUDE_API_KEY` starts with `sk-ant-`
- [ ] `OPENAI_API_KEY` starts with `sk-`
- [ ] `WP_SITE_URL` has no trailing slash
- [ ] `WP_SITE_URL` starts with `https://`
- [ ] `WP_APP_PASSWORD` is 24 characters (no spaces)
- [ ] `WP_USERNAME` is correct (case-sensitive)

### System Health

- [ ] Last execution completed successfully
- [ ] Content_Archive has recent entries
- [ ] Self_Learning_Database updating
- [ ] Email notifications received
- [ ] WordPress posts publishing
- [ ] Thumbnails uploading
- [ ] No errors in last 5 executions

### Performance Checks

- [ ] Confidence scores ≥ 92%
- [ ] Word counts in range (1200-2500)
- [ ] Execution time < 8 minutes
- [ ] Success rate > 95%
- [ ] API costs within budget
- [ ] Knowledge base files loading

---

## 🎯 When to Contact Support

**Self-Service First:**
1. Review this troubleshooting guide
2. Check Error_Log and Executions log
3. Verify all configuration
4. Try manual generation to isolate issue
5. Consult SETUP_GUIDE for detailed instructions

**Contact Support If:**
- Tried all troubleshooting steps
- Error persists after fixes
- System completely non-functional
- Data loss or corruption
- Security concerns
- Billing issues with APIs

**What to Include:**
1. Execution ID from error
2. Error message from Error_Log
3. Screenshot of error
4. What you've tried
5. When it started
6. System configuration (Config sheet values)

---

## 📖 Additional Resources

- **Setup Guide:** `SETUP_GUIDE_WordPress_Content_System.md`
- **Quick Start:** `QUICK_START_WordPress_Content_System.md`
- **System Overview:** `README_WordPress_Content_System.md`
- **Script Code:** `Innovative_Automations_WordPress_Content_System.gs`

**External Documentation:**
- [Google Apps Script Troubleshooting](https://developers.google.com/apps-script/guides/support)
- [WordPress REST API](https://developer.wordpress.org/rest-api/)
- [Anthropic API Status](https://status.anthropic.com/)
- [OpenAI API Status](https://status.openai.com/)

---

**Last Updated:** 2025-01-22
**Version:** 1.0.0
**Compatibility:** Google Apps Script, WordPress 5.6+, Claude Sonnet 4, DALL-E 3
