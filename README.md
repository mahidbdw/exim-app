# HS Code Finder

A simple web application to search for Harmonized System (HS) codes by commodity name.

## 🚀 Quick Start

### Local Development

1. Place your Excel file in the same directory as `index.html`
2. Rename your Excel file to `hs-codes.xlsx` OR edit line 237 in `index.html`:
   ```javascript
   const EXCEL_FILE_NAME = 'your-file-name.xlsx';
   ```
3. Open `index.html` in a web browser

**Note:** Due to browser security restrictions, you'll need to use a local web server to run this locally. You can use:

**Python:**
```bash
python -m http.server 8000
```
Then visit: http://localhost:8000

**Node.js (npx):**
```bash
npx serve
```

**VS Code:**
Install the "Live Server" extension and right-click on `index.html` → "Open with Live Server"

## 📊 Excel File Format

Your Excel file should have this structure:

| Column A (HS Code) | Column B (Commodities) |
|-------------------|------------------------|
| 1234567890 | commodity1, commodity2, commodity3 |
| 9876543210 | product1, product2, product3 |

- **Column 1:** HS Code (text or number)
- **Column 2:** Comma-separated list of commodities

## 🌐 Deploy to GitHub Pages

1. Create a new repository on GitHub
2. Upload your files:
   ```bash
   git init
   git add index.html hs-codes.xlsx
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
   git push -u origin main
   ```
3. Go to your repository Settings → Pages
4. Under "Source", select "main" branch and "/" (root) folder
5. Click Save
6. Your site will be available at: `https://YOUR_USERNAME.github.io/YOUR_REPO/`

## ☁️ Deploy to Cloudflare Pages

### Method 1: Connect GitHub Repository

1. Log in to [Cloudflare Dashboard](https://dash.cloudflare.com/)
2. Go to Workers & Pages → Pages
3. Click "Create a project" → "Connect to Git"
4. Select your GitHub repository
5. Configure build settings:
   - **Build command:** Leave empty
   - **Build output directory:** `/`
6. Click "Save and Deploy"
7. Your site will be live at: `https://your-project.cloudflare.pages.dev`

### Method 2: Direct Upload (Drag & Drop)

1. Log in to [Cloudflare Dashboard](https://dash.cloudflare.com/)
2. Go to Workers & Pages → Pages
3. Click "Create a project" → "Upload assets"
4. Drag and drop both files:
   - `index.html`
   - `hs-codes.xlsx`
5. Click "Deploy site"
6. Your site will be live immediately!

## 🔧 Configuration

### Changing the Excel File Name

Edit line 237 in `index.html`:

```javascript
const EXCEL_FILE_NAME = 'hs-codes.xlsx'; // Change this to your file name
```

### Customizing Colors

The color scheme is defined in CSS variables at the top of the file:

```css
:root {
    --bg-primary: #0a0e1a;
    --bg-secondary: #151b2e;
    --accent: #00d9ff;
    --success: #00ff88;
    /* ... */
}
```

## 📝 Features

- ✨ **Auto-load:** Automatically loads Excel file on page load
- 🔍 **Live search:** Real-time search as you type
- 💡 **Smart matching:** Finds commodities anywhere in the text
- 🎨 **Modern UI:** Clean, responsive design
- ⚡ **Fast:** Client-side search, no server required
- 📱 **Mobile-friendly:** Works on all devices

## 🛠️ Troubleshooting

### File Not Found Error

**Problem:** "Error loading file: File not found"

**Solutions:**
1. Make sure your Excel file is in the same directory as `index.html`
2. Check the file name matches exactly (including extension)
3. Use a local web server (see Quick Start)
4. Check browser console (F12) for detailed error messages

### CORS Error (Cross-Origin)

**Problem:** "Access to fetch blocked by CORS policy"

**Solutions:**
1. Use a local web server instead of opening the file directly
2. Deploy to GitHub Pages or Cloudflare Pages
3. Ensure you're accessing via `http://` or `https://`, not `file://`

### Excel File Not Parsing Correctly

**Problem:** Data not showing up or showing incorrect results

**Solutions:**
1. Verify your Excel file has data in columns A and B
2. Make sure column B contains comma-separated values
3. Remove any header rows or ensure data starts from row 1
4. Check browser console for parsing errors

## 📄 License

MIT License - feel free to use and modify as needed!

## 🤝 Contributing

Feel free to submit issues and enhancement requests!
