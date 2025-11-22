# RSS Feed Troubleshooting Guide

## Changes Made

### 1. ✅ Removed Quick Search Buttons
- Removed the non-working "Quick search" feature
- Cleaned up the search interface

### 2. ✅ Fixed RSS Feed Functionality
- Improved error handling with detailed messages
- Added 15-second timeout (increased from 10s)
- Extended search to last 60 days of articles
- Better CORS handling
- More descriptive error messages

### 3. ✅ NEW: "Fetch All" Feature
- Added **🌐 Fetch All** button that loads articles from ALL RSS feeds simultaneously
- Shows combined results sorted by date
- Displays which source each article came from
- Great for quickly browsing everything at once

## About the "Failed to fetch" Error

The error you're seeing is likely due to **CORS (Cross-Origin Resource Sharing)** restrictions. This happens because:

1. **Browser Security**: Modern browsers block requests from one domain (your GitHub Pages site) to another domain (RSS feeds) for security
2. **RSS2JSON Proxy**: We use RSS2JSON.com as a "middle man" to convert RSS feeds to JSON, but sometimes this service can be:
   - Temporarily down
   - Rate-limited
   - Blocked by your network/firewall
   - Blocked by browser extensions

## Troubleshooting Steps

### Quick Fixes (Try These First):

1. **Disable Browser Extensions**
   - Ad blockers and privacy extensions often block third-party API requests
   - Try in Incognito/Private mode
   
2. **Try "Fetch All" Button**
   - The green "🌐 Fetch All" button tries all feeds at once
   - Some might work even if others fail
   - You'll see which feeds succeeded/failed

3. **Check Browser Console**
   - Press F12 to open Developer Tools
   - Click "Console" tab
   - Look for specific error messages
   - Share screenshot if you need more help

4. **Try Different Network**
   - Some corporate/school networks block external APIs
   - Try from home WiFi or mobile hotspot
   - Try on a different device

### If RSS Feeds Still Don't Work:

**Option 1: Manual RSS URLs**
You can still use RSS feeds manually:
- Copy RSS URL (e.g., https://www.archpaper.com/feed/)
- Use browser RSS reader extension
- Use standalone RSS reader app (Feedly, Inoreader, etc.)

**Option 2: Direct Site Search**
Each source has a search URL - you can:
- Use the web search feature with mock results
- Visit sites directly to browse articles

**Option 3: Backend Solution (Advanced)**
For 100% reliability, you'd need to:
- Set up your own server/proxy
- Use serverless function (Netlify/Vercel Functions)
- Get paid RSS2JSON API key for higher limits

## Testing Individual Feeds

You can test if RSS2JSON is working by visiting this URL in your browser:

```
https://api.rss2json.com/v1/api.json?rss_url=https://www.archpaper.com/feed/&count=5
```

If you see JSON data with articles, RSS2JSON is working!
If you see an error or nothing loads, RSS2JSON might be blocked.

## Current RSS Feeds in Your App

1. **ArchDaily** - http://feeds.feedburner.com/Archdaily
2. **Dezeen** - https://www.dezeen.com/feed/
3. **Architizer** - https://architizer.com/blog/feed/
4. **Construction Dive** - https://www.constructiondive.com/feeds/news/
5. **Architectural Digest** - https://www.architecturaldigest.com/feed/rss
6. **ArchitectPaper** - https://www.archpaper.com/feed/
7. **DesignBoom** - https://www.designboom.com/feed/
8. **Wired Magazine** - https://www.wired.com/feed/rss

## Alternative: Use Your Own RSS API Key

If you want more reliability, you can get a free account at:
- https://rss2json.com/
- Get your own API key (free tier: 10,000 requests/day)
- Replace `api_key=public` with your key in the code

## Need More Help?

Check:
- Browser console for specific errors
- Network tab in Developer Tools
- Try accessing https://rss2json.com/ directly to see if it loads

The app will still work for:
- Manual article entry
- Web search (mock results)
- Managing your saved articles
- All organizational features
