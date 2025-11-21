# 📰 RSS Feed Feature Guide

## What's New - RSS Feed Integration!

Your Architecture & AI Hub can now fetch the **latest articles** directly from RSS feeds! Get real-time updates from your favorite architecture sources.

---

## 🎯 How It Works

### View Latest Articles

1. Click **"Search Web"** button
2. Look for the **"📰 Latest articles:"** section
3. Click any orange RSS button (e.g., **🏛️ ArchDaily**)
4. Articles load instantly from the RSS feed!
5. Browse recent articles with images and descriptions
6. Click **"Read Article"** to open the source
7. Click **"➕ Add to Library"** to save to your collection

### RSS-Enabled Sources

These sources have RSS feeds configured:

- **🏛️ ArchDaily** - `http://feeds.feedburner.com/Archdaily`
- **📐 Dezeen** - `https://www.dezeen.com/feed/`
- **🏗️ Architizer** - `https://architizer.com/blog/feed/`
- **👷 Construction Dive** - `https://www.constructiondive.com/feeds/news/`
- **🏠 Architectural Digest** - `https://www.architecturaldigest.com/feed/rss`
- **📄 ArchitectPaper** - `https://www.archpaper.com/feed/`
- **💡 DesignBoom** - `https://www.designboom.com/feed/`
- **🤖 Wired Magazine** - `https://www.wired.com/feed/rss`

---

## 🆚 RSS vs Regular Search

### Regular Search (Gray Buttons)
- Opens the website's search page
- Requires you to type a query
- Opens in new tab
- Manual browsing

### RSS Feed (Orange Buttons)
- Loads latest articles automatically
- No query needed
- Shows recent content in-app
- One-click add to library

---

## ✨ Features

### Automatic Updates
- RSS feeds show the **latest articles** from each source
- Typically 10-20 most recent articles
- Updated in real-time when you click

### Rich Preview
- Article title
- Description/summary
- Publication date
- Thumbnail image
- Direct link to read full article

### Quick Save
- Click **"➕ Add to Library"** to save any article
- Automatically captures:
  - Title
  - URL
  - Description
  - Image
  - Source name
  - Publication date

---

## 🔧 Adding Custom RSS Feeds

Want to add more RSS feeds? Here's how:

### Step 1: Sign In
Must be signed in with Google to manage sources

### Step 2: Open Source Manager
1. Click **"Search Web"**
2. Click **"⚙️ Sources"** button (top right)

### Step 3: Add Source
Fill in the form:
- **Icon**: Emoji (e.g., 🏢)
- **Name**: Source name (e.g., "AIA Journal")
- **Search URL**: Regular search URL
- **RSS URL**: The RSS feed URL (e.g., `https://site.com/feed/`)

### Step 4: Save
Click **"➕ Add"** and your source appears!

---

## 🔍 Finding RSS Feeds

### Common RSS Feed Patterns

Most sites use one of these:
```
https://site.com/feed/
https://site.com/rss/
https://site.com/feed/rss/
https://site.com/blog/feed/
https://site.com/feeds/news/
```

### How to Find a Site's RSS Feed

**Method 1: Check the Footer**
- Look for RSS icon (📰 or similar)
- Often labeled "RSS", "Feed", or "Subscribe"

**Method 2: View Page Source**
- Press `Ctrl+U` (or `Cmd+U` on Mac)
- Search for "rss" or "feed"
- Look for `<link rel="alternate" type="application/rss+xml"`

**Method 3: Try Common Patterns**
- Add `/feed/` to the end of the URL
- Add `/rss/` to the end of the URL
- Check `/blog/feed/` if it's a blog

**Method 4: Use RSS Discovery Tools**
- [RSS.app](https://rss.app) - Generate feeds for any site
- [FetchRSS](https://fetchrss.com) - Create RSS from any page
- Browser extensions like "RSS Feed Reader"

---

## 📋 Example RSS Sources to Add

### Architecture & Design
```
🏢 AIA Journal
URL: https://www.architectmagazine.com/feed/

🎨 Designboom Architecture
URL: https://www.designboom.com/architecture/feed/

🏛️ ArchDaily Projects
URL: https://www.archdaily.com/feed/

📐 Dezeen Architecture
URL: https://www.dezeen.com/architecture/feed/
```

### Technology & AI
```
🤖 MIT Technology Review AI
URL: https://www.technologyreview.com/topic/artificial-intelligence/feed/

🧠 OpenAI Blog
URL: https://openai.com/blog/rss/

💻 Google AI Blog
URL: http://ai.googleblog.com/feeds/posts/default

🔬 DeepMind Blog
URL: https://deepmind.com/blog/feed/basic/
```

### News & Media
```
📰 The Guardian Architecture
URL: https://www.theguardian.com/artanddesign/architecture/rss

🗞️ New York Times Architecture
URL: https://rss.nytimes.com/services/xml/rss/nyt/RealEstate.xml

📻 NPR Design
URL: https://www.npr.org/rss/rss.php?id=1008
```

---

## 💡 Pro Tips

### Workflow for Research
1. **RSS First**: Check RSS feeds for latest articles
2. **Quick Add**: Add interesting articles to your library
3. **Add Notes**: Annotate with key insights
4. **Organize**: Categorize by topic
5. **Search Later**: Use regular search for specific topics

### Stay Updated
- Check RSS feeds weekly for new content
- Subscribe to your favorite sources
- Combine RSS with your categorization system

### Best Practices
- ✅ Add articles that interest you
- ✅ Add notes with key takeaways
- ✅ Organize by category
- ✅ Review your collection regularly
- ❌ Don't add everything - be selective!

---

## 🐛 Troubleshooting

### RSS Feed Not Loading
**Problem**: "Failed to load RSS feed" error

**Solutions:**
1. Check if the RSS URL is correct
2. Try visiting the RSS URL in your browser
3. Some feeds may be blocked by CORS
4. Wait a moment and try again (rate limiting)

### No Articles Showing
**Problem**: Feed loads but shows 0 articles

**Solutions:**
1. The feed might be empty (no recent posts)
2. Try a different feed from the same source
3. Check if the source is still active

### Images Not Loading
**Problem**: Article images show placeholder

**Solutions:**
- This is normal - some RSS feeds don't include images
- The article will still save with a default image
- You can edit the image URL after saving

### Can't Add Custom Source
**Problem**: Add button doesn't work

**Solutions:**
1. Make sure you're signed in
2. Fill in Name and Search URL (required)
3. RSS URL is optional but recommended

---

## 🔄 How RSS Works (Technical)

### Behind the Scenes
1. You click an RSS button
2. App fetches the RSS feed URL
3. Uses RSS2JSON API to convert XML to JSON
4. Parses articles and displays them
5. You can add any article to your library

### RSS Feed Format
RSS feeds are XML files that look like:
```xml
<rss version="2.0">
  <channel>
    <title>Site Name</title>
    <item>
      <title>Article Title</title>
      <link>https://...</link>
      <description>Article summary...</description>
      <pubDate>Mon, 01 Jan 2024 12:00:00 GMT</pubDate>
    </item>
  </channel>
</rss>
```

The app automatically extracts:
- Title
- URL
- Description
- Publication date
- Images (if available)

---

## 🎓 Learning More About RSS

### What is RSS?
**RSS** (Really Simple Syndication) is a web standard for publishing frequently updated content. It allows you to:
- Get updates without visiting websites
- Aggregate content from multiple sources
- Read articles in your preferred format

### RSS Readers
If you want to follow RSS feeds outside this app:
- **Feedly** - Popular RSS reader
- **Inoreader** - Advanced features
- **NewsBlur** - Open source option
- **The Old Reader** - Simple interface

### RSS Benefits
- ✅ No algorithms - chronological feed
- ✅ No tracking or ads
- ✅ Instant updates
- ✅ One place for all sources
- ✅ Ownership of your reading list

---

## 🚀 Future Enhancements

Potential features we might add:
- Automatic RSS feed discovery
- Save RSS feeds as collections
- Schedule automatic imports
- Filter RSS by keywords
- Export RSS reading list

---

## ❓ Questions?

**Q: Do I need an account to view RSS feeds?**  
A: No! Anyone can click RSS buttons and browse articles. Sign in only needed to save to your library.

**Q: How often do RSS feeds update?**  
A: Each time you click the button, it fetches the latest articles. RSS feeds are real-time!

**Q: Can I add multiple articles at once?**  
A: Currently one at a time, but we may add batch import later.

**Q: Are RSS feeds free?**  
A: Yes! RSS is an open standard. The feeds are provided by the source websites.

---

**Enjoy discovering the latest architecture and AI articles with RSS!** 📰🏗️

For more features, see [FEATURES-GUIDE.md](FEATURES-GUIDE.md)
