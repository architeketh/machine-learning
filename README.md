# 🏗️ Architecture & AI Hub

A beautiful, secure web application for curating and organizing Architecture and AI articles. Browse articles publicly, sign in with Google to add, edit, and manage your collection. **Now with RSS feed integration for instant access to the latest articles!**

## ✨ Features

- 🔍 **Web Search** - Search for ML & Architecture articles with customizable sources
- 🔗 **Quick Search Sources** - One-click search on Dezeen, Architect Magazine, ArchDaily, and more
- ⚙️ **Custom Sources** - Add your own search sources with custom URLs
- 🧹 **Clear Search** - Clear search results with one click
- ➕ **Add Articles** - Manually add articles with URLs, descriptions, and images
- 📁 **Quick Category Creation** - Create categories instantly with dedicated button and modal
- 📂 **Categories** - Organize with custom categories (ML, AI, Deep Learning, etc.)
- ⭐ **Favorites** - Mark important articles
- 📝 **Notes** - Add personal notes and highlights to articles
- 🔐 **Google Sign-In** - Secure authentication (only signed-in users can edit)
- 📱 **Responsive** - Works perfectly on mobile and desktop
- 💾 **Export** - Export articles to JSON

## 🚀 Live Demo

Visit: `https://architeketh.github.io/machine-learning/`

## 🔧 Setup Instructions

### Step 1: Firebase Configuration (Already Done ✅)

Your Firebase project is configured:
- Project: `ml-architecture-hub`
- Authentication: Google Sign-In enabled
- Firestore: Database created

### Step 2: Update Firestore Security Rules

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Select **ml-architecture-hub** project
3. Click **Firestore Database** → **Rules** tab
4. Replace with these secure rules:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // ML Articles collection
    match /ml-articles/{article} {
      allow read: if true;  // Anyone can read
      allow write: if request.auth != null;  // Only authenticated users can write
    }
    
    // Settings collection (categories and sources)
    match /ml-settings/{setting} {
      allow read: if true;  // Anyone can read
      allow write: if request.auth != null;  // Only authenticated users can write
    }
  }
}
```

5. Click **Publish**

### Step 3: Enable Google Authentication

1. In Firebase Console, click **Authentication** in left sidebar
2. Click **Get Started** (if first time)
3. Click **Sign-in method** tab
4. Click **Google**
5. Toggle **Enable**
6. Add your **Project support email** (your email)
7. Click **Save**

### Step 4: Add Authorized Domain (for GitHub Pages)

1. Still in **Authentication** → **Settings** tab
2. Scroll to **Authorized domains**
3. Click **Add domain**
4. Add: `architeketh.github.io`
5. Click **Add**

### Step 5: Deploy to GitHub Pages

1. Upload `index.html` to your repository
2. Go to repository **Settings** → **Pages**
3. Select **main** branch, **/ (root)** folder
4. Click **Save**
5. Wait 1-2 minutes for deployment

## 🔒 Security

- **Public Reading**: Anyone can browse articles
- **Protected Writing**: Only authenticated users (you) can:
  - Add new articles
  - Edit categories
  - Delete articles
  - Add/delete notes
  - Mark favorites

## 📖 Usage

### For Visitors (No Sign-In)
- Browse all articles
- Search and filter
- Read articles
- View notes

### For Admin (Signed In)
1. Click **"Sign In to Add Articles"**
2. Sign in with your Google account
3. Now you can:
   - Click **"Search Web"** to find articles
   - Use **Quick Search** buttons (ArXiv, GitHub, etc.) to search specific sources
   - Click **⚙️ Sources** to manage custom search sources
   - Click **🧹 Clear** to clear search results
   - Click **"Add Article"** to manually add
   - Click **📁 New Category** to create categories
   - Delete articles with 🗑️ button
   - Add notes with 📝 button
   - Export your collection

## 🎯 New Features Explained

### Quick Search Sources
When you open the search modal, you'll see quick search buttons:
- **📄 ArXiv** - Search academic papers
- **🎓 Google Scholar** - Search scholarly articles
- **💻 GitHub** - Search code repositories
- **📊 Papers with Code** - Search papers with implementations
- **🏆 Kaggle** - Search datasets and notebooks

Type your query and click any source button to search directly on that platform!

### Custom Search Sources
1. Click **"Search Web"** → **⚙️ Sources**
2. Add custom sources with:
   - **Icon** (emoji)
   - **Name** (e.g., "Medium AI")
   - **URL** (e.g., "https://medium.com/search?q=")
3. Your custom sources appear as quick search buttons
4. Remove sources you don't need

### Category Management
- **Header Button**: Click **📁 New Category** in the header for instant access
- **Modal Interface**: Clean, focused interface for creating categories
- **Inline Option**: Also available in the categories section

## 🎨 Customization

### Add Custom Search Sources

When signed in:
1. Click **"Search Web"** → **⚙️ Sources**
2. Fill in:
   - Icon (emoji, e.g., 🔬)
   - Name (e.g., "Nature AI")
   - URL (must end with query parameter, e.g., `https://www.nature.com/search?q=`)
3. Click **➕ Add**
4. Your source appears in quick search buttons

**Example Sources:**
- `🔬 Nature AI` → `https://www.nature.com/search?q=`
- `📰 MIT News` → `https://news.mit.edu/topic/mitmachine-learning?term=`
- `🤖 AI News` → `https://www.artificialintelligence-news.com/?s=`

### Add More Categories

When signed in:
1. Click **"📁 New Category"** in header (or in categories section)
2. Enter category name
3. Click **"✅ Create Category"**
4. Use immediately when adding articles

### Change Theme Colors

Edit the Tailwind classes in `index.html`:
- Main gradient: `from-gray-900 via-blue-900 to-purple-900`
- Accent colors: `from-blue-500 to-purple-600`

## 🐛 Troubleshooting

### GitHub "Secret detected" warning for API key
→ This is **safe and expected**! Firebase API keys are meant to be public.
→ See [SECURITY.md](SECURITY.md) for full explanation
→ You can safely dismiss the GitHub warning
→ Security is enforced by Firestore Rules, not by hiding the key

### "Missing or insufficient permissions" error
→ Check Firestore Rules (Step 2 above) - make sure ml-settings is included

### Sign-in popup blocked
→ Allow popups in your browser for the site

### Articles not saving
→ Check browser console (F12) for detailed errors
→ Verify you're signed in (look for "Sign Out" button)

### Can't access on mobile
→ Make sure `architeketh.github.io` is in Firebase authorized domains

### Quick search buttons not working
→ Make sure your query has text entered
→ Check if popup blocker is preventing new tab

### Custom sources not saving
→ Verify you're signed in
→ Check Firestore rules include ml-settings collection
→ Reload page to see saved sources

### Search results not clearing
→ Click the 🧹 Clear button
→ Refresh the page if needed

### GitHub "Secret Detected" Warning
→ **This is safe!** Firebase API keys are meant to be public in web apps
→ See [SECURITY.md](SECURITY.md) for full explanation
→ Security is enforced by Firestore Rules, not by hiding the key
→ You can safely dismiss the GitHub alert

## 📦 Tech Stack

- **Frontend**: React 18 (via CDN)
- **Styling**: Tailwind CSS
- **Database**: Firebase Firestore
- **Authentication**: Firebase Auth (Google)
- **Hosting**: GitHub Pages

## 🤝 Contributing

This is a personal project, but feel free to fork and customize for your own use!

## 📝 License

Free to use and modify for personal projects.

## 🙏 Credits

Built with ❤️ for organizing ML & AI knowledge

---

**Need Help?** Check the browser console (F12) for detailed error messages.
