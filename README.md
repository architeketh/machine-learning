# 🧠 Machine Learning Architecture Hub

A beautiful, secure web application for curating and organizing AI & Machine Learning articles. Browse articles publicly, sign in with Google to add, edit, and manage your collection.

## ✨ Features

- 🔍 **Web Search** - Search for ML & AI articles
- ➕ **Add Articles** - Manually add articles with URLs, descriptions, and images
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
    
    // Settings collection
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
   - Click **"Add Article"** to manually add
   - Delete articles with 🗑️ button
   - Add notes with 📝 button
   - Create custom categories
   - Export your collection

## 🎨 Customization

### Add More Categories

When signed in:
1. Click **"➕ New Category"**
2. Enter category name
3. Click **"+ Add"**

### Change Theme Colors

Edit the Tailwind classes in `index.html`:
- Main gradient: `from-gray-900 via-blue-900 to-purple-900`
- Accent colors: `from-blue-500 to-purple-600`

## 🐛 Troubleshooting

### "Missing or insufficient permissions" error
→ Check Firestore Rules (Step 2 above)

### Sign-in popup blocked
→ Allow popups in your browser for the site

### Articles not saving
→ Check browser console (F12) for detailed errors
→ Verify you're signed in (look for "Sign Out" button)

### Can't access on mobile
→ Make sure `architeketh.github.io` is in Firebase authorized domains

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
