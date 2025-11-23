# 🚀 Quick Start Guide - WordPress Content System

## ⚡ 5-Minute Setup (Fast Track)

### 1. Create Google Sheet & Add Script
1. Create new Google Sheet: `Innovative Automations Content System`
2. `Extensions` → `Apps Script`
3. Copy/paste `Innovative_Automations_WordPress_Content_System.gs`
4. Save project

### 2. Add Script Properties
`Project Settings` (⚙️) → `Script Properties` → Add:

```
ANTHROPIC_API_KEY = sk-ant-api03-...
OPENAI_API_KEY = sk-proj-...
WP_SITE_URL = https://innovativeautomations.dev
WP_USERNAME = your_wordpress_username
WP_APP_PASSWORD = (get from WordPress)
```

**Get WordPress App Password:**
- WP Admin → Users → Your Profile
- Scroll to "Application Passwords"
- Name: `Content System`, click `Add New`
- Copy password (remove spaces)

### 3. Initialize System
Return to Google Sheet (refresh page):
1. `🚀 Content System` → `🏗️ Initialize All Sheets`
2. `🚀 Content System` → `📁 Create Knowledge Base Folders`
3. `🚀 Content System` → `🏷️ Setup WordPress Categories`

### 4. Add Content to Drive
1. Open created Drive folder (link in toast)
2. Add 2-3 Google Docs to each category folder:
   - `Success_Stories/`
   - `News_Updates/`
   - `Case_Studies/`

### 5. Configure Email
In `Config` sheet, add your email to `EMAIL_RECIPIENTS` row

### 6. Test Run
`🚀 Content System` → `▶️ Generate & Publish Now`
- Grant permissions when prompted
- Wait 5-8 minutes
- Check email + WordPress for results

### 7. Automate
`🚀 Content System` → `⏰ Setup Daily 4AM Trigger`

**Done! System will now run daily at 4 AM.**

---

## 📊 What It Does

**Every Day at 4 AM:**
1. ✅ Generates 2 SEO-optimized blog posts (1200-2500 words)
2. ✅ Creates professional thumbnails with DALL-E 3
3. ✅ Publishes to WordPress with full metadata
4. ✅ Sends email notification with results
5. ✅ Learns from performance to improve over time

**Smart Features:**
- 🧠 Self-learning (improves after 5 generations)
- 🔄 Smart category rotation (balanced content)
- ✅ 6-layer quality verification
- 🎨 Brand-consistent thumbnails
- 📈 Performance tracking

---

## 💰 Costs

- **Claude API:** ~$0.15-0.20 per day (2 articles)
- **DALL-E 3:** ~$0.08 per day (2 thumbnails)
- **Total:** ~$7-8.50 per month for daily automation

---

## 📁 File Structure

```
Your Google Drive/
└── Innovative_Automations_Knowledge_Base/
    ├── Success_Stories/          ← Add client wins, testimonials
    ├── News_Updates/             ← Add industry news, announcements
    ├── Case_Studies/             ← Add technical docs, methodologies
    └── _Inspiration_Sources/     ← Add competitor content (optional)

Your Google Sheet:
├── Config                        ← System settings
├── Content_Archive               ← All generated articles
├── Self_Learning_Database        ← Performance tracking
├── Error_Log                     ← Error tracking
└── Inspiration_Sources           ← External sources (optional)
```

---

## 🎯 Menu Reference

**🚀 Content System Menu:**
- `▶️ Generate & Publish Now` - Run immediately
- `⏰ Setup Daily 4AM Trigger` - Enable automation
- `🗑️ Delete All Triggers` - Disable automation
- `🏗️ Initialize All Sheets` - Create required sheets
- `📁 Create Knowledge Base Folders` - Create Drive folders
- `🏷️ Setup WordPress Categories` - Auto-detect category IDs
- `📖 Setup Guide` - Full setup instructions

---

## ⚠️ Troubleshooting Quick Fixes

| Error | Quick Fix |
|-------|-----------|
| Missing configuration | Check all 5 Script Properties are set |
| WordPress 401 error | Regenerate Application Password |
| Claude API error | Check Anthropic API key & credits |
| DALL-E error | Check OpenAI API key & credits |
| No email received | Add email to Config sheet |
| Low confidence scores | Add more content to Drive folders |

---

## 📈 Expected Performance

**Generation 1-5 (Week 1):**
- Confidence: 85-90%
- Building baseline style
- Learning from inspiration sources

**Generation 6+ (Week 2+):**
- Confidence: 92-97%
- Self-learning active
- Optimizing based on performance

**Generation 20+ (Month 2+):**
- Confidence: 95%+
- Fully optimized
- Minimal oversight needed

---

## 💡 Pro Tips

1. **Start with drafts:** Change `DEFAULT_POST_STATUS` to `draft` in Config until confident
2. **More content = better results:** Add 5+ docs per category for best quality
3. **Use inspiration sources:** Add competitor blogs to Inspiration_Sources sheet
4. **Monitor weekly:** Check Content_Archive and Self_Learning_Database
5. **Adjust settings:** Tweak Config parameters based on your needs

---

## 📞 Need Help?

1. Check `Error_Log` sheet for details
2. Review Apps Script `Executions` log
3. See `SETUP_GUIDE_WordPress_Content_System.md` for detailed troubleshooting
4. Verify API keys in Script Properties
5. Check API service status pages

---

## ✅ Deployment Checklist

- [ ] Google Sheet created
- [ ] Apps Script code added and saved
- [ ] All 5 Script Properties configured
- [ ] WordPress Application Password created
- [ ] Sheets initialized (Config, Content_Archive, etc.)
- [ ] Knowledge base folders created
- [ ] 2-3 docs added to each category folder
- [ ] WordPress categories verified/created
- [ ] Email configured in Config sheet
- [ ] Test run completed successfully
- [ ] Daily trigger enabled

**All checked? You're live! 🎉**

---

**Version:** 1.0.0 | **Updated:** 2025-01-22 | **Support:** See SETUP_GUIDE_WordPress_Content_System.md
