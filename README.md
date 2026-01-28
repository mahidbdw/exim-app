# HS Code Finder - Hierarchical Version

A web application to search for Harmonized System (HS) codes with hierarchical display showing the complete classification tree.

## 🌳 Hierarchical Structure

The HS Code system has 4 levels:
- **Chapter (2 digits)** - e.g., `51` - WOOL, FINE OR COARSE ANIMAL HAIR
- **Heading (4 digits)** - e.g., `5113` - WOVEN FABRICS OF HORSEHAIR  
- **Subheading (6 digits)** - e.g., `511300` - WOVEN FABRICS OF HORSEHAIR
- **Tariff Item (8 digits)** - e.g., `51130010` - UNBLEACHED WOVEN FABRICS

When you search for a commodity like "horse", the app will:
1. Find all matching HS codes
2. Automatically include their parent codes (2, 4, 6 digit levels)
3. Display them in a hierarchical tree structure

### Example Search Result for "horse":

```
51 - WOOL, FINE OR COARSE ANIMAL HAIR, HORSEHAIR YARN
    5113 - WOVEN FABRICS OF COARSE ANIMAL HAIR OR OF HORSEHAIR
        511300 - WOVEN FABRICS OF HORSEHAIR
            51130010 - UNBLEACHED WOVEN FABRICS OF HORSEHAIR
            51130030 - DYED WOVEN FABRICS OF HORSEHAIR
            51130090 - OTHER WOVEN FABRICS OF HORSEHAIR

01 - LIVE ANIMALS
    0101 - LIVE HORSES, ASSES, MULES AND HINNIES
        010121 - PURE-BRED BREEDING HORSES
            01012100 - PURE-BRED BREEDING HORSES
```

## 🚀 Quick Start

### Local Development

1. Place your Excel file in the same directory as `index.html`
2. Rename your Excel file to `hs-codes.xlsx` OR edit line 320 in `index.html`:
   ```javascript
   const EXCEL_FILE_NAME = 'your-file-name.xlsx';
   ```
3. Serve using a local web server:

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
Install "Live Server" extension → Right-click `index.html` → "Open with Live Server"

## 📊 Excel File Format

Your Excel file must include ALL levels of the HS code hierarchy:

| Column A (HS Code) | Column B (Description) |
|-------------------|------------------------|
| 51 | WOOL, FINE OR COARSE ANIMAL HAIR, HORSEHAIR YARN AND WOVEN FABRIC |
| 5113 | WOVEN FABRICS OF COARSE ANIMAL HAIR OR OF HORSEHAIR |
| 511300 | WOVEN FABRICS OF COARSE ANIMAL HAIR OR OF HORSEHAIR |
| 51130010 | UNBLEACHED WOVEN FABRICS OF HORSEHAIR |
| 51130030 | DYED WOVEN FABRICS OF HORSEHAIR |
| 01 | LIVE ANIMALS |
| 0101 | LIVE HORSES, ASSES, MULES AND HINNIES |
| 010121 | PURE-BRED BREEDING HORSES |
| 01012100 | PURE-BRED BREEDING HORSES |

**Important:**
- Include 2-digit chapters (e.g., `01`, `51`)
- Include 4-digit headings (e.g., `0101`, `5113`)
- Include 6-digit subheadings (e.g., `010121`, `511300`)
- Include 8-digit tariff items (e.g., `01012100`, `51130010`)
- The app will automatically build the tree structure

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
3. Go to repository Settings → Pages
4. Select "main" branch and "/" (root) folder
5. Click Save
6. Site will be live at: `https://YOUR_USERNAME.github.io/YOUR_REPO/`

## ☁️ Deploy to Cloudflare Pages

### Method 1: Direct Upload (Easiest)

1. Log in to [Cloudflare Dashboard](https://dash.cloudflare.com/)
2. Go to Workers & Pages → Pages
3. Click "Create a project" → "Upload assets"
4. Drag and drop:
   - `index.html`
   - `hs-codes.xlsx`
5. Click "Deploy site"
6. Live instantly at: `https://your-project.cloudflare.pages.dev`

### Method 2: Connect GitHub Repository

1. Push your code to GitHub (see above)
2. Go to Cloudflare Pages → "Connect to Git"
3. Select your repository
4. Build settings:
   - **Build command:** Leave empty
   - **Build output directory:** `/`
5. Click "Save and Deploy"

## 🎨 Features

- 🌳 **Hierarchical Tree View:** Shows complete HS code classification structure
- 🔍 **Smart Search:** Finds commodities and auto-displays parent codes
- 🎨 **Color-Coded Levels:** 
  - Purple = Chapter (2 digits)
  - Pink = Heading (4 digits)
  - Orange = Subheading (6 digits)
  - Green = Tariff Item (8 digits)
- ⚡ **Live Search:** Real-time results as you type
- 📱 **Responsive:** Works on all devices
- 🚀 **No Backend:** Pure client-side, fast and free to host

## 🔧 Configuration

### Change Excel File Name

Edit line 320 in `index.html`:

```javascript
const EXCEL_FILE_NAME = 'hs-codes.xlsx'; // Your file name here
```

### Customize Colors

Edit CSS variables in the `<style>` section:

```css
:root {
    --level-2: #7c3aed;  /* Chapter - Purple */
    --level-4: #ec4899;  /* Heading - Pink */
    --level-6: #f59e0b;  /* Subheading - Orange */
    --level-8: #10b981;  /* Tariff - Green */
}
```

## 🛠️ Troubleshooting

### File Not Found Error

**Solutions:**
1. Ensure Excel file is in same directory as `index.html`
2. Check file name matches exactly (case-sensitive)
3. Use a local web server (not `file://` protocol)
4. Check browser console (F12) for detailed errors

### Hierarchy Not Showing Correctly

**Problem:** Parent codes not appearing in tree

**Solutions:**
1. Verify your Excel includes ALL code levels (2, 4, 6, 8 digits)
2. Check that parent codes exist in your data
3. Ensure HS codes don't have leading/trailing spaces
4. For code `01012100`, you need entries for: `01`, `0101`, `010121`, `01012100`

### Search Returns No Results

**Problem:** Valid commodity doesn't return results

**Solutions:**
1. Check spelling and try partial words
2. Verify commodity text exists in Excel file
3. Search is case-insensitive but must match exact text
4. Try searching for HS code directly

### CORS Error

**Problem:** "Access blocked by CORS policy"

**Solutions:**
1. Don't open HTML file directly (`file://`)
2. Use a local web server
3. Deploy to GitHub Pages or Cloudflare
4. Ensure URL starts with `http://` or `https://`

## 📖 How It Works

1. **Data Loading:** Reads Excel file with all HS code levels
2. **Search:** When you search for "horse", finds all matching codes
3. **Hierarchy Building:** Automatically identifies parent codes:
   - For `01012100` → adds `010121`, `0101`, `01`
   - For `51130010` → adds `511300`, `5113`, `51`
4. **Tree Display:** Shows codes grouped by chapter in hierarchical structure

## 📝 Sample Data Included

The `hs-codes-hierarchical.xlsx` file includes sample data for:
- Horses and horse-related products
- Live animals
- Meat products
- Electronics
- And more...

Use this as a template for your own data!

## 📄 License

MIT License - free to use and modify!

## 🤝 Contributing

Suggestions and improvements welcome! Open an issue or submit a PR.
