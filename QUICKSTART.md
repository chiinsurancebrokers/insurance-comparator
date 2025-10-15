# 🚀 Quick Start Guide - GitHub Deployment

## Option 1: Instant Deployment (Recommended)

### Step 1: Create Repository
```bash
# On GitHub.com
1. Click "+" in top right → "New repository"
2. Name it: insurance-comparator
3. Make it Public (required for GitHub Pages)
4. Click "Create repository"
```

### Step 2: Upload Files
```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/insurance-comparator.git
cd insurance-comparator

# Copy these files into the folder:
- index.html (the standalone app)
- README.md
- sample-policies.csv
- sample-policies.json
```

### Step 3: Push to GitHub
```bash
git add .
git commit -m "Initial commit - Insurance Policy Comparator"
git push origin main
```

### Step 4: Enable GitHub Pages
```
1. Go to your repository on GitHub
2. Click "Settings"
3. Scroll to "Pages" section
4. Under "Source", select "main" branch
5. Click "Save"
6. Wait 2-3 minutes
7. Visit: https://YOUR_USERNAME.github.io/insurance-comparator
```

---

## 📁 File Structure

Your repository should look like this:

```
insurance-comparator/
├── index.html              ← Main app (standalone)
├── README.md              ← Documentation
├── QUICKSTART.md          ← This file
├── sample-policies.csv    ← Example CSV data
├── sample-policies.json   ← Example JSON data
├── LICENSE                ← MIT License
└── examples/              ← Additional examples folder
    ├── oscar-family.csv
    ├── dcare-core.csv
    └── minetta-vital.csv
```

---

## 🎯 Testing Locally

**No build process needed!** Just:

1. Open `index.html` in any modern browser
2. Or use a local server:

```bash
# Python 3
python -m http.server 8000

# Node.js
npx http-server

# VS Code
# Install "Live Server" extension and click "Go Live"
```

Then visit: `http://localhost:8000`

---

## 📊 How to Use

### Step 1: Prepare Your Data

Create a CSV or JSON file with your insurance policies:

**CSV Example:**
```csv
policyName,provider,premium,excess,benefits,exclusions
My Policy,Insurance Co,1000,500,"Benefit 1,Benefit 2","Exclusion 1,Exclusion 2"
```

**JSON Example:**
```json
[
  {
    "policyName": "My Policy",
    "provider": "Insurance Co",
    "premium": 1000,
    "excess": 500,
    "benefits": ["Benefit 1", "Benefit 2"],
    "exclusions": ["Exclusion 1", "Exclusion 2"]
  }
]
```

### Step 2: Use the App

1. Open the app in your browser
2. Fill in personal information (name, DOB, nationality)
3. Upload your policy files (CSV or JSON)
4. Click "Analyze Policies"
5. View your personalized recommendation!

---

## 🌐 Sharing Your App

Once deployed to GitHub Pages, share your app:

```
✅ Direct link: https://YOUR_USERNAME.github.io/insurance-comparator
✅ Custom domain: Add CNAME file with your domain
✅ QR Code: Generate at qr-code-generator.com
```

---

## 🔧 Customization

### Change Colors
Edit the `index.html` file and modify Tailwind classes:

```html
<!-- Blue theme (default) -->
className="bg-blue-600"

<!-- Green theme -->
className="bg-green-600"

<!-- Purple theme -->
className="bg-purple-600"
```

### Add More Languages
In the `translations` object, add your language:

```javascript
const translations = {
  en: { /* English */ },
  gr: { /* Greek */ },
  es: { /* Spanish */ },
  // Add more...
};
```

### Adjust Scoring Algorithm
Modify weights in the `analyzePolicies()` function:

```javascript
// Current weights:
score += premiumScore * 0.35;  // 35% Premium
score += excessScore * 0.20;   // 20% Excess
score += benefitScore * 0.30;  // 30% Benefits
score += exclusionScore * 0.15; // 15% Exclusions
```

---

## 🐛 Troubleshooting

### Problem: App doesn't load on GitHub Pages

**Solution:**
- Check that `index.html` is in the root folder
- Verify branch is set to `main` in Pages settings
- Wait 2-3 minutes for deployment
- Clear browser cache (Ctrl+Shift+R or Cmd+Shift+R)

### Problem: File upload doesn't work

**Solution:**
- Ensure file is CSV or JSON format
- Check file encoding is UTF-8 (especially for Greek)
- Try the sample files first
- Open browser console (F12) to see error messages

### Problem: Greek characters display incorrectly

**Solution:**
- Save files with UTF-8 encoding
- In Notepad++: Encoding → Convert to UTF-8
- In Excel: Save As → CSV UTF-8

---

## 📱 Mobile Optimization

The app is fully responsive! Test on mobile:

```
1. Open on your phone
2. Add to home screen:
   - iOS: Share → Add to Home Screen
   - Android: Menu → Add to Home Screen
3. Use like a native app!
```

---

## 🔐 Privacy & Security

**Important:**
- All processing happens in the browser
- No data is sent to any server
- No cookies or tracking
- Completely private and secure

---

## 🎨 Branding

Want to add your company logo?

Edit `index.html` and add above the title:

```html
<div className="text-center mb-4">
  <img src="logo.png" alt="Company Logo" className="h-16 mx-auto" />
</div>
```

---

## 🚀 Next Steps

1. ✅ Deploy to GitHub Pages
2. ✅ Test with sample data
3. ✅ Upload your real policies
4. ✅ Share with clients/family
5. ⭐ Star the repository if helpful!

---

## 📞 Support

Questions? Issues?

- Open an issue on GitHub
- Check README.md for detailed docs
- Email: your.email@example.com

---

## 🎉 You're Ready!

Your insurance comparator is now live and ready to use!

**Live URL:** `https://YOUR_USERNAME.github.io/insurance-comparator`

---

**Made with ❤️ for better insurance decisions**