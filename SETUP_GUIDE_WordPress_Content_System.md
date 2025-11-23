# Innovative Automations - WordPress Content System Setup Guide

## 🎯 Complete Setup Instructions

This guide will walk you through setting up your fully autonomous, self-learning WordPress content generation system.

---

## 📋 Prerequisites Checklist

Before starting, ensure you have:

- [ ] Google Account with access to Google Drive and Google Sheets
- [ ] WordPress site at `innovativeautomations.dev` with admin access
- [ ] Anthropic Claude API key (sign up at https://console.anthropic.com)
- [ ] OpenAI API key (sign up at https://platform.openai.com)
- [ ] Basic familiarity with Google Apps Script

---

## 🚀 Step-by-Step Setup

### Step 1: Create Google Sheet and Apps Script Project

1. **Create New Google Sheet:**
   - Go to https://sheets.google.com
   - Create a new blank spreadsheet
   - Name it: `Innovative Automations Content System`

2. **Open Apps Script Editor:**
   - In Google Sheet, click `Extensions` → `Apps Script`
   - Delete any default code in `Code.gs`
   - Copy the ENTIRE contents of `Innovative_Automations_WordPress_Content_System.gs`
   - Paste into the Apps Script editor
   - Click `Save` (disk icon)
   - Name the project: `IA Content System`

---

### Step 2: Configure WordPress Application Password

**WordPress Application Passwords** provide secure API access without exposing your main password.

#### Creating the Application Password:

1. **Log into WordPress:**
   - Navigate to: `https://innovativeautomations.dev/wp-admin`
   - Log in with your admin credentials

2. **Navigate to Your Profile:**
   - Click on `Users` in the left sidebar
   - Click `Your Profile` or click your username at the top right

3. **Find Application Passwords Section:**
   - Scroll down to the **"Application Passwords"** section
   - (If you don't see this, your WordPress version may need updating - requires WP 5.6+)

4. **Create New Application Password:**
   - In the "New Application Password Name" field, enter:
     ```
     Innovative Automations Content System
     ```
   - Click `Add New Application Password`

5. **Copy the Generated Password:**
   - WordPress will display a password like: `xxxx xxxx xxxx xxxx xxxx xxxx`
   - **IMPORTANT:** Copy this IMMEDIATELY - it will only be shown once!
   - Remove all spaces when saving (should be 24 characters)
   - Example: `xxxxxxxxxxxxxxxxxxxxxx`

6. **Store Securely:**
   - Save this password - you'll need it in Step 3

#### Troubleshooting:
- **Don't see Application Passwords?**
  - Ensure WordPress is version 5.6 or higher
  - Check that your site uses HTTPS (required for security)
  - If on shared hosting, contact your host to enable it

---

### Step 3: Configure Script Properties (API Keys)

**Script Properties** securely store your API keys and credentials.

1. **Open Script Properties:**
   - In Apps Script editor, click the **gear icon** (⚙️) on the left sidebar
   - Or click `Project Settings` in the left menu
   - Scroll down to **"Script Properties"** section

2. **Add Each Property:**
   - Click `+ Add script property` for each of the following:

   | Property Name | Value | Where to Get It |
   |--------------|-------|-----------------|
   | `CLAUDE_API_KEY` | `sk-ant-api03-...` | https://console.anthropic.com → API Keys |
   | `OPENAI_API_KEY` | `sk-proj-...` | https://platform.openai.com → API Keys |
   | `WP_SITE_URL` | `https://innovativeautomations.dev` | Your WordPress URL (NO trailing slash) |
   | `WP_USERNAME` | Your WordPress admin username | Your WP login username |
   | `WP_APP_PASSWORD` | (24-char password from Step 2) | Application Password created above |

3. **Verify All Properties:**
   - You should have exactly 5 Script Properties
   - Double-check all keys are correct (no extra spaces)
   - Click `Save script project settings` if prompted

#### Getting API Keys:

**Anthropic Claude API Key:**
1. Go to https://console.anthropic.com
2. Sign up or log in
3. Navigate to API Keys section
4. Create a new API key
5. Copy the key (starts with `sk-ant-`)
6. Note: You'll need to add billing info and credits (~$10 recommended for testing)

**OpenAI API Key:**
1. Go to https://platform.openai.com
2. Sign up or log in
3. Click your profile → View API Keys
4. Create new secret key
5. Copy the key (starts with `sk-`)
6. Note: You'll need to add billing info and credits (~$10 recommended)

---

### Step 4: Initialize System Sheets

1. **Return to Google Sheet:**
   - Close Apps Script editor
   - Go back to your Google Sheet

2. **Refresh to Load Menu:**
   - Refresh the page (F5 or Cmd+R)
   - You should see a new menu: **🚀 Content System**
   - (If not, wait 10 seconds and refresh again)

3. **Initialize All Sheets:**
   - Click `🚀 Content System` → `🏗️ Initialize All Sheets`
   - Grant permissions when prompted (click "Allow")
   - Wait for confirmation toast: "All sheets have been created successfully!"

4. **Verify Sheet Creation:**
   - You should now have 5 tabs at the bottom:
     - `Config` - System configuration
     - `Content_Archive` - All generated articles
     - `Self_Learning_Database` - Performance tracking
     - `Error_Log` - Error tracking
     - `Inspiration_Sources` - External content sources

---

### Step 5: Configure Email Notifications

1. **Open Config Sheet:**
   - Click the `Config` tab

2. **Add Your Email:**
   - Find the row with Key: `EMAIL_RECIPIENTS` (or add it)
   - In the `Value` column, enter your email address
   - For multiple recipients: `email1@example.com,email2@example.com`

3. **Review Default Settings:**
   - The Config sheet contains all customizable parameters
   - Default values are already optimal for most cases
   - You can adjust later if needed:
     - `CONFIDENCE_THRESHOLD` (default: 92)
     - `MIN_WORD_COUNT` (default: 1200)
     - `MAX_WORD_COUNT` (default: 2500)

---

### Step 6: Create Google Drive Knowledge Base

1. **Create Folder Structure:**
   - In Google Sheet, click `🚀 Content System` → `📁 Create Knowledge Base Folders`
   - Wait for confirmation with folder ID
   - Click the link in the toast notification to open the folder

2. **Verify Folder Structure:**
   ```
   Innovative_Automations_Knowledge_Base/
   ├── Success_Stories/
   │   ├── Client_Wins/
   │   └── Case_Examples/
   ├── News_Updates/
   │   ├── Industry_Trends/
   │   └── Company_News/
   ├── Case_Studies/
   │   ├── Technical_Deep_Dives/
   │   └── Implementation_Guides/
   └── _Inspiration_Sources/
       ├── Competitor_Blogs/
       ├── Industry_Leaders/
       ├── Writing_Guides/
       └── Visual_Inspiration/
   ```

3. **Add Initial Content:**
   - Create at least 2-3 Google Docs in each category folder
   - Content examples:
     - **Success_Stories:** Client testimonials, project wins, transformation stories
     - **News_Updates:** Industry news summaries, company announcements
     - **Case_Studies:** Technical implementation details, methodology explanations
     - **_Inspiration_Sources:** Competitor blog URLs, industry reports, style guides

4. **Supported File Types:**
   - Google Docs (`.gdoc`) - **Recommended**
   - PDFs (`.pdf`)
   - Word documents (`.docx`)
   - Plain text (`.txt`, `.md`)

---

### Step 7: Setup WordPress Categories

1. **Verify WordPress Categories Exist:**
   - Log into WordPress
   - Go to `Posts` → `Categories`
   - Ensure these three categories exist:
     - `Success Stories`
     - `News & Updates`
     - `Case Studies`
   - (If they don't exist, the script will create them automatically)

2. **Auto-Detect Category IDs:**
   - In Google Sheet, click `🚀 Content System` → `🏷️ Setup WordPress Categories`
   - The script will:
     - Find or create the three categories
     - Store their WordPress IDs in the Config sheet
   - Verify in Config sheet:
     - `WP_CATEGORY_SUCCESS_STORIES`: (number)
     - `WP_CATEGORY_NEWS_UPDATES`: (number)
     - `WP_CATEGORY_CASE_STUDIES`: (number)

---

### Step 8: Test Run (Critical!)

**Before setting up automation, test the system manually.**

1. **Run Manual Generation:**
   - Click `🚀 Content System` → `▶️ Generate & Publish Now`
   - First run will ask for permissions:
     - Click "Review Permissions"
     - Select your Google account
     - Click "Advanced" → "Go to IA Content System (unsafe)"
     - Click "Allow" to grant all permissions
   - **This may take 5-8 minutes** - be patient!

2. **Monitor Execution:**
   - Go to `Extensions` → `Apps Script`
   - Click `Executions` in left sidebar
   - Watch the execution log in real-time
   - Look for any errors

3. **Verify Success:**
   - Check your email for notification
   - Log into WordPress and verify 2 new posts were published
   - Review Content_Archive sheet for entries
   - Check Self_Learning_Database sheet for Generation #1

4. **Troubleshooting First Run:**
   - **Error: "Missing required configuration"**
     - Verify all Script Properties are set correctly
   - **Error: "WordPress publish failed"**
     - Check WordPress Application Password is correct
     - Ensure WordPress site is accessible
   - **Error: "Claude API error"**
     - Verify Anthropic API key is correct
     - Check your Anthropic account has credits
   - **Error: "DALL-E API error"**
     - Verify OpenAI API key is correct
     - Check your OpenAI account has credits

---

### Step 9: Setup Daily Automation

**Once testing is successful, enable daily automation.**

1. **Create Daily Trigger:**
   - Click `🚀 Content System` → `⏰ Setup Daily 4AM Trigger`
   - Confirm: "Daily trigger set for 4:00 AM"

2. **Verify Trigger:**
   - Go to `Extensions` → `Apps Script`
   - Click `Triggers` in left sidebar (⏰ icon)
   - You should see:
     - Function: `generateAndPublishDailyContent`
     - Event: Time-driven, Day timer, 4AM-5AM

3. **Trigger Settings:**
   - The system will run every day at 4:00 AM (your timezone)
   - Execution takes 5-8 minutes
   - You'll receive email notification after each run
   - No manual intervention required

---

### Step 10: Add Inspiration Sources (Optional)

To enhance content quality with competitor insights:

1. **Open Inspiration_Sources Sheet:**
   - Click the `Inspiration_Sources` tab

2. **Add External Sources:**
   | Source Name | URL/File ID | Type | Category | Quality Rating | Last Used | Active | Notes |
   |-------------|-------------|------|----------|----------------|-----------|--------|-------|
   | Zapier Blog | https://zapier.com/blog | Website | Competitor | 9 | | TRUE | Great storytelling examples |
   | Make.com Blog | https://www.make.com/en/blog | Website | Competitor | 8 | | TRUE | Technical depth |

3. **Add Google Docs as Sources:**
   - Create Google Docs with inspiration content
   - Copy the file ID from the URL
   - Add to Inspiration_Sources sheet with Type: `Google Doc`

4. **Activate Sources:**
   - Set `Active` column to `TRUE` for sources you want to use
   - The system will automatically reference these during content generation

---

## 🎓 Understanding the System

### How Self-Learning Works

**Generations 1-5: Building Baseline**
- System focuses on competitor content and best practices
- Establishes consistent writing style
- Builds foundation for future learning
- Typical confidence: 85-90%

**Generation 6+: Self-Learning Active**
- Analyzes performance of previous 10 articles
- Identifies successful patterns (word count, structure, topics)
- Blends WordPress style (70%) with learned optimizations (30%)
- Typical confidence: 92-97%

**Generation 20+: Fully Optimized**
- Highly refined understanding of what works
- Consistently high confidence scores (95%+)
- Minimal manual intervention needed

### Content Generation Process

Each run generates 2 articles through this 9-phase process:

1. **Configuration** - Load settings, validate API keys
2. **Strategy** - Determine which categories to write about (smart rotation)
3. **Knowledge Assembly** - Gather all Drive files, inspiration sources
4. **Style Analysis** - Analyze WordPress posts + self-generated content
5. **Content Generation** - Call Claude API with comprehensive prompt
6. **Verification** - 6-layer quality check (confidence, word count, HTML, SEO)
7. **Thumbnails** - Generate professional images with DALL-E 3
8. **Publishing** - Upload to WordPress with full metadata
9. **Learning** - Update performance database for continuous improvement

### Smart Category Rotation

The system ensures balanced content by:
- Tracking last 20 articles by category
- Selecting 2 least-used categories each run
- Preventing repetitive content on the same topics

Example:
- Day 1: Success Stories + News & Updates
- Day 2: Case Studies + Success Stories
- Day 3: News & Updates + Case Studies
- (Continues rotating for balanced coverage)

---

## 📊 Monitoring & Maintenance

### Daily Monitoring

**Email Notifications:**
- Sent after each run
- Shows success rate, confidence scores
- Direct links to published articles
- Alerts if any errors occurred

**Content_Archive Sheet:**
- Complete history of all generated articles
- Track: Date, Category, Title, Word Count, Confidence, Status
- Use for analysis and reporting

**Self_Learning_Database Sheet:**
- Performance metrics over time
- Generation count, success rate, average confidence
- Shows when self-learning activated
- Track improvement trends

### Error Handling

**Error_Log Sheet:**
- Automatic error logging
- Timestamp, execution ID, error details
- Use for troubleshooting

**Automatic Retry:**
- System retries up to 3 times on failure
- 5-second delay between attempts
- If one article fails, the other still publishes
- Detailed error emails sent

### Maintenance Tasks

**Weekly:**
- Review Content_Archive for quality
- Check Error_Log for recurring issues
- Add new knowledge base files to Drive

**Monthly:**
- Review Self_Learning_Database trends
- Update inspiration sources
- Adjust Config settings if needed
- Check API usage/costs

**Quarterly:**
- Full system review
- Update WordPress plugins
- Rotate API keys for security
- Archive old content

---

## 🔧 Configuration Reference

### Config Sheet Parameters

| Parameter | Default | Description |
|-----------|---------|-------------|
| `EMAIL_RECIPIENTS` | (empty) | Comma-separated email addresses |
| `CONFIDENCE_THRESHOLD` | 92 | Minimum confidence to publish (0-100) |
| `MIN_WORD_COUNT` | 1200 | Minimum article length |
| `MAX_WORD_COUNT` | 2500 | Maximum article length |
| `LEARNING_SAMPLE_SIZE` | 10 | Number of past articles to analyze |
| `MIN_GENERATIONS_FOR_LEARNING` | 5 | Generations before self-learning activates |
| `SELF_CONTENT_WEIGHT` | 0.3 | How much to weight own content (0-1) |
| `DEFAULT_POST_STATUS` | publish | WordPress post status (`publish` or `draft`) |

### Customization Examples

**More Conservative Publishing:**
- Set `DEFAULT_POST_STATUS` to `draft`
- Review drafts manually before publishing
- Once confident, change to `publish`

**Longer Articles:**
- Increase `MIN_WORD_COUNT` to 1500
- Increase `MAX_WORD_COUNT` to 3000

**Faster Self-Learning:**
- Reduce `MIN_GENERATIONS_FOR_LEARNING` to 3
- Increase `SELF_CONTENT_WEIGHT` to 0.4

---

## 💰 Cost Estimation

### API Costs per Article

**Claude API (Anthropic):**
- Model: Claude Sonnet 4
- ~8,000 tokens input + ~4,000 tokens output per 2 articles
- Cost: ~$0.15-0.20 per run (2 articles)

**DALL-E 3 (OpenAI):**
- Quality: HD
- Size: 1792x1024
- Cost: ~$0.04 per image × 2 images = $0.08 per run

**Total Daily Cost:**
- ~$0.23-0.28 per day
- ~$7-8.50 per month
- ~$84-100 per year

### Cost Optimization

**To reduce costs:**
- Set `DEFAULT_POST_STATUS` to `draft` - review before publishing
- Reduce `MAX_WORD_COUNT` to 2000
- Run every other day instead of daily
- Use standard quality DALL-E images (edit script)

---

## 🔒 Security Best Practices

### Protecting Your API Keys

1. **Never Share Script Properties:**
   - API keys stored in Script Properties are private
   - Never share your Apps Script project with untrusted users

2. **Restrict API Key Permissions:**
   - In Anthropic Console, set spending limits
   - In OpenAI dashboard, set usage limits
   - Monitor API usage regularly

3. **WordPress Security:**
   - Use Application Passwords (not main password)
   - Revoke old Application Passwords periodically
   - Use strong, unique WordPress admin password

4. **Google Sheet Access:**
   - Limit sharing to necessary collaborators only
   - Use "Viewer" or "Commenter" access for non-admins
   - Keep "Editor" access restricted

### Monitoring for Suspicious Activity

- Check Apps Script Executions log weekly
- Review WordPress posts for unexpected content
- Monitor API usage in Anthropic/OpenAI dashboards
- Set up billing alerts in both API platforms

---

## 🆘 Troubleshooting Guide

### Common Issues & Solutions

#### "Missing required configuration"
**Cause:** Script Properties not set correctly
**Solution:**
- Verify all 5 Script Properties are present
- Check for typos in property names
- Ensure no extra spaces in values

#### "WordPress publish failed: 401 Unauthorized"
**Cause:** Authentication issue
**Solution:**
- Regenerate WordPress Application Password
- Ensure no spaces in Application Password
- Verify WordPress username is correct
- Check WordPress URL has no trailing slash

#### "Claude API error: 401"
**Cause:** Invalid Anthropic API key
**Solution:**
- Verify API key in Script Properties
- Check API key hasn't been revoked
- Ensure Anthropic account has credits

#### "DALL-E API error: insufficient_quota"
**Cause:** No OpenAI credits
**Solution:**
- Add credits to OpenAI account
- Check billing settings

#### "Knowledge base folder not found"
**Cause:** Folder ID not set or incorrect
**Solution:**
- Run: Content System → Create Knowledge Base Folders
- Check KNOWLEDGE_BASE_FOLDER_ID in Script Properties

#### Execution times out
**Cause:** Too much content or slow API responses
**Solution:**
- Reduce number of knowledge base files
- Decrease MAX_WORD_COUNT
- Check internet connection

#### Articles have low confidence scores
**Cause:** Insufficient knowledge base content
**Solution:**
- Add more Google Docs to category folders
- Populate Inspiration_Sources sheet
- Wait for self-learning to activate (Gen 6+)

#### No email notifications received
**Cause:** Email address not configured
**Solution:**
- Add email to Config sheet: EMAIL_RECIPIENTS
- Check spam folder
- Verify Apps Script can send email (check Executions log)

---

## 📚 Additional Resources

### WordPress REST API Documentation
- https://developer.wordpress.org/rest-api/

### Anthropic Claude API Documentation
- https://docs.anthropic.com/claude/reference/

### OpenAI DALL-E Documentation
- https://platform.openai.com/docs/guides/images

### Google Apps Script Documentation
- https://developers.google.com/apps-script

---

## 🎉 You're Ready!

Your self-learning WordPress content system is now fully configured and operational.

**What Happens Next:**
1. System runs automatically at 4 AM daily
2. Generates 2 high-quality, SEO-optimized articles
3. Creates professional thumbnails
4. Publishes to WordPress automatically
5. Sends you email confirmation
6. Continuously learns and improves

**Expected Timeline:**
- **Week 1:** Building baseline, establishing style
- **Week 2-3:** Self-learning activates, quality improves
- **Month 2+:** Fully optimized, minimal oversight needed

---

## 💡 Pro Tips

1. **Start with drafts:** Set `DEFAULT_POST_STATUS` to `draft` initially, review quality, then switch to `publish`

2. **Populate knowledge base:** The more content in your Drive folders, the better the articles

3. **Use inspiration sources:** Add competitor blogs to Inspiration_Sources sheet for style guidance

4. **Monitor trends:** Check Self_Learning_Database monthly to see improvement

5. **Adjust as needed:** Tweak Config parameters based on your preferences

6. **Keep knowledge fresh:** Add new files to Drive regularly for current content

7. **Test before automating:** Always run manual test before setting up daily trigger

---

## 📞 Support

For issues or questions:
1. Check Error_Log sheet for details
2. Review Executions log in Apps Script
3. Consult this guide's Troubleshooting section
4. Check API service status pages

---

**System Version:** 1.0.0
**Last Updated:** 2025-01-22
**Compatibility:** Google Apps Script, WordPress 5.6+, Claude Sonnet 4, DALL-E 3
