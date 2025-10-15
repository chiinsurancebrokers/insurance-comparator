# 🏥 Insurance Policy Comparator
## Bilingual (English/Greek) Insurance Comparison Tool

A React-based web application that helps families compare insurance policies based on premiums, excess, benefits, and exclusions. Provides intelligent scoring and personalized recommendations.

---

## ✨ Features

- 🌍 **Bilingual Interface** - Full support for English and Greek
- 📊 **Smart Analysis** - AI-powered scoring algorithm
- 📁 **Multiple File Formats** - CSV, JSON, and PDF support
- 👨‍👩‍👧‍👦 **Family Plans** - Compare policies for entire families
- 🎯 **Personalized Recommendations** - Age-based and need-based suggestions
- 📱 **Responsive Design** - Works on desktop and mobile

---

## 🚀 Quick Start

### Option 1: GitHub Pages (Standalone - CSV/JSON only)

1. **Clone the repository:**
```bash
git clone https://github.com/yourusername/insurance-comparator.git
cd insurance-comparator
```

2. **No installation needed!** Just open `index.html` in your browser.

3. **Or deploy to GitHub Pages:**
   - Go to Settings → Pages
   - Select branch: `main`
   - Folder: `/` (root)
   - Save and visit: `https://yourusername.github.io/insurance-comparator`

### Option 2: Full Version with PDF Support

Requires Node.js backend for Claude API integration.

```bash
npm install
npm run dev
```

See **Backend Setup** section below.

---

## 📂 File Format Examples

### CSV Format:
```csv
policyName,provider,premium,excess,benefits,exclusions
Oscar Family,HDI,790,150,"Hospital care,Emergency services,Maternity","Pre-existing conditions,Cosmetic surgery"
DCare Core,AKD Insurance,1834.6,650,"Inpatient care,Emergency evacuation,Cancer treatment","Pre-existing conditions,Experimental treatments"
```

### JSON Format:
```json
[
  {
    "policyName": "Oscar Family",
    "provider": "HDI / AKD Insurance",
    "premium": 790,
    "excess": 150,
    "benefits": ["Hospital care", "Emergency services", "Maternity €700"],
    "exclusions": ["Pre-existing conditions", "Cosmetic surgery"]
  }
]
```

---

## 🏗️ Project Structure

```
insurance-comparator/
├── index.html              # Main HTML file (standalone version)
├── README.md              # This file
├── LICENSE                # MIT License
├── src/
│   ├── App.jsx           # Main React component
│   ├── components/       # React components
│   └── utils/            # Utility functions
├── public/               # Static assets
├── docs/                 # Documentation
│   ├── setup.md         # Detailed setup guide
│   └── api-setup.md     # Claude API configuration
└── examples/            # Sample CSV/JSON files
    ├── sample-policies.csv
    ├── sample-policies.json
    └── sample-policies-greek.csv
```

---

## 🔧 Backend Setup (for PDF Processing)

### Prerequisites:
- Node.js 18+
- Anthropic API Key

### Steps:

1. **Create a backend server:**
```bash
mkdir backend
cd backend
npm init -y
npm install express cors @anthropic-ai/sdk dotenv
```

2. **Create `.env` file:**
```
ANTHROPIC_API_KEY=your_api_key_here
PORT=3001
```

3. **Create `server.js`:**
```javascript
const express = require('express');
const cors = require('cors');
const Anthropic = require('@anthropic-ai/sdk');
require('dotenv').config();

const app = express();
app.use(cors());
app.use(express.json({ limit: '50mb' }));

const anthropic = new Anthropic({
  apiKey: process.env.ANTHROPIC_API_KEY,
});

app.post('/api/process-pdf', async (req, res) => {
  try {
    const { pdfBase64 } = req.body;
    
    const message = await anthropic.messages.create({
      model: 'claude-sonnet-4-20250514',
      max_tokens: 4000,
      messages: [{
        role: 'user',
        content: [
          {
            type: 'document',
            source: {
              type: 'base64',
              media_type: 'application/pdf',
              data: pdfBase64,
            },
          },
          {
            type: 'text',
            text: 'Extract insurance policy information...'
          }
        ]
      }]
    });
    
    res.json({ success: true, data: message.content[0].text });
  } catch (error) {
    res.status(500).json({ success: false, error: error.message });
  }
});

app.listen(process.env.PORT, () => {
  console.log(`Backend running on port ${process.env.PORT}`);
});
```

4. **Update frontend to use backend:**
```javascript
// In App.jsx, replace Claude API call with:
const response = await fetch('http://localhost:3001/api/process-pdf', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ pdfBase64: base64Data })
});
```

---

## 📖 Usage Guide

### Step 1: Enter Personal Information
- First Name / Όνομα
- Last Name / Επώνυμο
- Date of Birth / Ημερομηνία Γέννησης
- Nationality / Εθνικότητα
- Citizenship / Υπηκοότητα

### Step 2: Upload Policy Files
- Upload one or more insurance policies (CSV, JSON, or PDF)
- You can upload multiple files to compare

### Step 3: View Analysis
- See detailed comparison with scoring
- Get personalized recommendation
- View reasoning for each policy's score

---

## 🎯 Scoring Algorithm

The app uses a weighted scoring system:

- **Premium (35%)** - Lower premiums score higher
- **Excess (20%)** - Lower excess scores higher
- **Benefits (30%)** - More benefits score higher
- **Exclusions (15%)** - Fewer exclusions score higher
- **Age Adjustments** - Bonus points for age-appropriate coverage

---

## 🌐 Deployment

### GitHub Pages (Standalone):
```bash
git add .
git commit -m "Deploy insurance comparator"
git push origin main
```

Enable GitHub Pages in repository settings.

### Vercel (with Backend):
```bash
npm install -g vercel
vercel
```

### Docker:
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```

---

## 🤝 Contributing

Contributions welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

---

## 📄 License

MIT License - See [LICENSE](LICENSE) file

---

## 👥 Authors

Created by [Your Name]

---

## 🐛 Known Issues

- PDF processing requires backend server
- Large PDFs (>5MB) may take longer to process
- Greek character encoding requires UTF-8

---

## 📞 Support

For issues or questions:
- Open an issue on GitHub
- Email: your.email@example.com

---

## 🙏 Acknowledgments

- Claude AI for document processing
- Tailwind CSS for styling
- React for UI framework
- Lucide React for icons

---

## 📈 Future Enhancements

- [ ] Add more insurance providers
- [ ] Export comparison as PDF
- [ ] Historical premium tracking
- [ ] Email notifications
- [ ] Mobile app version

---

**⭐ If this project helped you, please give it a star!**