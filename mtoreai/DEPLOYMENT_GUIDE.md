# MTOREAI BUSINESS HUB - DEPLOYMENT GUIDE

## 🚀 COMPLETE DEPLOYMENT INSTRUCTIONS

This guide will get your Business Hub live with working chatbots in about 30 minutes.

---

## 📦 WHAT YOU HAVE

**Files:**
1. `hub.mtoreai.solutions.html` - Main hub page with chat interface
2. `netlify.toml` - Netlify configuration
3. `package.json` - Dependencies for functions
4. `.env.template` - Environment variables template
5. `netlify/functions/chat-master-qualifier.js` - Sample function (master template)
6. `CHATBOT_CONFIG.js` - Configuration reference for all bots

**Your Credentials:**
- OpenAI API Key: Already in `.env.template`
- All 10 Assistant IDs: Already documented

---

## 🔧 STEP-BY-STEP DEPLOYMENT

### **STEP 1: Create Netlify Account (if you don't have one)**

1. Go to https://netlify.com
2. Sign up with GitHub (recommended) or email
3. Free tier is perfect for this

### **STEP 2: Prepare Your Files**

Create a folder structure like this:
```
mtoreai-hub/
├── hub.mtoreai.solutions.html  (rename to index.html)
├── logo.png
├── netlify.toml
├── package.json
├── .env.template
├── CHATBOT_CONFIG.js
└── netlify/
    └── functions/
        └── chat-master-qualifier.js
```

**IMPORTANT:** Rename `hub.mtoreai.solutions.html` to `index.html`

### **STEP 3: Create Remaining Function Files**

You need to create 9 more function files (one for each chatbot).

**Copy `chat-master-qualifier.js` and create:**

1. `chat-business-credit.js`
   - Change ASSISTANT_ID to: `asst_mVR4rzHYGcwG3h88QHbDbzgb`

2. `chat-business-loan.js`
   - Change ASSISTANT_ID to: `asst_BDWRY2eXqmphfUzDKg1hUTKa`

3. `chat-business-profile.js`
   - Change ASSISTANT_ID to: `asst_TJaMjTZcbSY5Oam9RYCt5DeU`

4. `chat-automation-advisor.js`
   - Change ASSISTANT_ID to: `asst_KPeuTshkWNPVe2L9zHYCXTQx`

5. `chat-automation-stack.js`
   - Change ASSISTANT_ID to: `asst_DtTrQlH6CMvpNmEEeZtsmiIU`

6. `chat-marketing-advisor.js`
   - Change ASSISTANT_ID to: `asst_7tzsPrrLPshWo95aDlb6EL3j`

7. `chat-content-creator.js`
   - Change ASSISTANT_ID to: `asst_MM4sHJNrqIrmbD5cNLpIFvjM`

8. `chat-mental-clarity.js`
   - Change ASSISTANT_ID to: `asst_M3ClDpgUwkiEFgNtQ7WTcetM`

9. `chat-personal-credit.js`
   - Change ASSISTANT_ID to: `asst_9wE53wWhQzj9Bt7GFdUNJMX9`

**Each file should be identical except for the ASSISTANT_ID line.**

### **STEP 4: Create GitHub Repository**

1. Go to https://github.com/new
2. Create new repository named `mtoreai-business-hub`
3. Make it private (recommended)
4. Don't initialize with README

5. Upload all your files:
   - Go to your repo
   - Click "uploading an existing file"
   - Drag and drop your entire `mtoreai-hub` folder
   - Commit changes

### **STEP 5: Connect to Netlify**

1. Log into Netlify
2. Click "Add new site" → "Import an existing project"
3. Choose "GitHub"
4. Authorize Netlify to access your repos
5. Select `mtoreai-business-hub`
6. Click "Deploy site"

**Build settings should auto-detect:**
- Build command: (leave empty)
- Publish directory: `.`
- Functions directory: `netlify/functions`

### **STEP 6: Add Environment Variables**

1. In Netlify, go to "Site settings"
2. Click "Environment variables"
3. Click "Add a variable"
4. Add:
   - **Key:** `OPENAI_API_KEY`
   - **Value:** Your full API key from `.env.template`
5. Click "Create variable"

### **STEP 7: Set Up Custom Domain**

**Option A: Use Netlify subdomain (Quick)**
1. Your site will be at: `your-site-name.netlify.app`
2. You can rename it in "Site settings" → "Change site name"
3. Rename to: `mtoreai-hub.netlify.app`

**Option B: Use your custom domain (Better)**
1. Go to "Domain settings"
2. Click "Add custom domain"
3. Enter: `hub.mtoreai.solutions`
4. Netlify will give you DNS records to add:
   - Go to your domain registrar
   - Add the CNAME or A record Netlify provides
   - Wait 5-60 minutes for DNS to propagate
5. Netlify will auto-issue SSL certificate

### **STEP 8: Test Everything**

1. Visit your site URL
2. Click on a chatbot card
3. Chat modal should open
4. Type a message and send
5. Should get real AI response (not demo)

If you see "Demo Mode" notice, functions aren't deploying:
- Check "Site settings" → "Functions"
- Make sure OPENAI_API_KEY is set
- Check deploy logs for errors

---

## 🔍 TROUBLESHOOTING

### **Chatbots show demo responses instead of real AI:**

**Check:**
1. Environment variable is set: `OPENAI_API_KEY`
2. Functions deployed successfully (check deploy log)
3. Function files are in correct location: `netlify/functions/`
4. Each function has correct ASSISTANT_ID

**Fix:**
- Go to "Deploys" → Click latest deploy → "Functions" tab
- Should see all 10 functions listed
- If not, check file structure and redeploy

### **"Failed to process request" error:**

**Check:**
1. API key is valid
2. API key has billing enabled
3. Assistant IDs are correct
4. OpenAI API is responsive

**Fix:**
- Test API key at https://platform.openai.com/api-keys
- Check billing at https://platform.openai.com/account/billing

### **Chat modal doesn't open:**

**Check:**
- Browser console for JavaScript errors
- Make sure `index.html` has all the JavaScript at bottom

**Fix:**
- Hard refresh page (Ctrl+F5 or Cmd+Shift+R)
- Clear browser cache

---

## 🎨 CUSTOMIZATION

### **Change Colors:**
Edit CSS variables at top of `index.html`:
```css
:root{
  --bg:#080d18;        /* Background */
  --week:#00d1ff;      /* Primary accent (blue) */
  --work:#28f0a2;      /* Secondary accent (green) */
  --accent:#8a5cff;    /* Tertiary accent (purple) */
}
```

### **Update Content:**
All content is in `index.html`:
- Hero text (line ~505-525)
- Chatbot descriptions (line ~590-750)
- How It Works steps (line ~550-575)

### **Add More Chatbots:**
1. Create new function file in `netlify/functions/`
2. Add new bot card in `index.html`
3. Update `onclick` to match function name
4. Redeploy

---

## 📊 MONITORING

### **Check Usage:**
1. Netlify Dashboard → Functions → See invocations
2. OpenAI Dashboard → Usage → See API calls

### **Check Costs:**
- Netlify Functions: Free tier = 125K requests/month
- OpenAI API: Pay per token (check platform.openai.com/usage)

**Estimated Costs:**
- 100 conversations/day = ~$5-10/month OpenAI
- Netlify = $0 (well within free tier)

---

## 🔒 SECURITY

**Your API key is safe because:**
1. It's stored as Netlify environment variable (encrypted)
2. Never exposed in HTML or JavaScript
3. Only Netlify functions can access it
4. Not in your GitHub repo (if you followed steps)

**Best practices:**
- Never commit `.env` files to Git
- Use `.gitignore` to exclude `.env`
- Rotate API keys every 90 days
- Monitor usage for unusual activity

---

## 🚀 NEXT STEPS

### **Phase 3 (Optional Enhancements):**

1. **Add n8n Webhook for Email Capture**
   - Create n8n workflow
   - Update JavaScript in `index.html`
   - Auto-add to CRM/email list

2. **Add Analytics**
   - Google Analytics
   - Netlify Analytics
   - Track which chatbots are most popular

3. **Add Authentication**
   - Netlify Identity
   - Password-protect hub
   - Track user conversations

4. **White-Label for Brokers**
   - Create duplicate sites
   - Customize branding per broker
   - Share backend API

---

## 📞 NEED HELP?

**Common issues:**
- Functions not deploying → Check file structure
- API errors → Check API key billing
- Chat not working → Check browser console

**Still stuck?**
- Email: support@mtoreai.solutions
- Check Netlify docs: docs.netlify.com
- Check OpenAI docs: platform.openai.com/docs

---

## ✅ DEPLOYMENT CHECKLIST

- [ ] Created folder structure
- [ ] Renamed hub file to `index.html`
- [ ] Created all 10 function files
- [ ] Created GitHub repo
- [ ] Uploaded all files to GitHub
- [ ] Connected repo to Netlify
- [ ] Added OPENAI_API_KEY environment variable
- [ ] Site deployed successfully
- [ ] Custom domain configured (optional)
- [ ] Tested chatbot functionality
- [ ] Confirmed AI responses working
- [ ] Checked function logs for errors

---

**DEPLOYMENT COMPLETE! 🎉**

Your Business Hub is now LIVE with working AI advisors.

Share your hub URL to start building your waitlist and demoing to brokers.

Next: Focus on getting those first 10 users to validate the product, then scale.

You've got this. 💚
