# 🎮 FFICONS API – Free Fire Item Icons CDN

> **Free Fire Icon API with no watermarks | Fast CDN delivery | Free, no rate limits**

**FFICONS** is a lightweight, high-performance API that delivers clean Free Fire item icons directly via CDN. Perfect for game panels, Discord bots, trading websites, and community tools.

**Created & maintained by [Shahil Ali](https://github.com/Shahilali5) | Updated by [ShahGCreator](https://github.com/ShahGCreator)**

---

## Table of Contents
- [Quick Start](#quick-start)
- [API Documentation](#api-documentation)
- [Usage Examples](#usage-examples)
- [Features](#features)
- [Getting Item IDs](#getting-item-ids)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

---

## 🚀 Quick Start

### Base URL
```
https://cdn.jsdelivr.net/gh/Shahilali5/FFICONS@main/PNG/{item_ID}.png
```

Simply replace `{item_ID}` with any Free Fire item ID to get the icon.

### Live Example
```
https://cdn.jsdelivr.net/gh/Shahilali5/FFICONS@main/PNG/907092607.png
```

**Response:** PNG image (no JSON, no wrappers – just the image)

---

## 📖 API Documentation

### Endpoint
```
GET https://cdn.jsdelivr.net/gh/Shahilali5/FFICONS@main/PNG/{item_ID}.png
```

### Parameters
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `item_ID` | Integer | ✅ Yes | Free Fire in-game item ID (numeric) |

### Response Codes
| Code | Meaning |
|------|---------|
| `200` | Icon found and returned (PNG image) |
| `404` | Item ID not found or not yet added to database |
| `200` | CDN cache hit (instant delivery) |

### Response Format
- **Content-Type:** `image/png`
- **File Size:** ~2–50 KB per icon (optimized)
- **Dimensions:** 256x256 pixels (PNG)
- **Watermark:** None

---

## 💡 Usage Examples

### HTML/Web Display
```html
<!-- Simple img tag -->
<img src="https://cdn.jsdelivr.net/gh/Shahilali5/FFICONS@main/PNG/907092607.png" 
     alt="Free Fire Item Icon" 
     width="100" 
     height="100">

<!-- CSS Background -->
<div style="background-image: url('https://cdn.jsdelivr.net/gh/Shahilali5/FFICONS@main/PNG/907092607.png');
            background-size: cover;
            width: 100px;
            height: 100px;">
</div>
```

### JavaScript/React
```javascript
// Fetch and display icon
const itemID = '907092607';
const iconURL = `https://cdn.jsdelivr.net/gh/Shahilali5/FFICONS@main/PNG/${itemID}.png`;

// React Component
function ItemIcon({ id }) {
  return <img src={`https://cdn.jsdelivr.net/gh/Shahilali5/FFICONS@main/PNG/${id}.png`} alt="Item" />;
}
```

### Python
```python
import requests
from PIL import Image
from io import BytesIO

item_id = '907092607'
url = f'https://cdn.jsdelivr.net/gh/Shahilali5/FFICONS@main/PNG/{item_id}.png'

response = requests.get(url)
if response.status_code == 200:
    image = Image.open(BytesIO(response.content))
    image.show()
else:
    print(f"Icon not found for ID: {item_id}")
```

### cURL / Command Line
```bash
# Download icon
curl -O https://cdn.jsdelivr.net/gh/Shahilali5/FFICONS@main/PNG/907092607.png

# Using wget
wget https://cdn.jsdelivr.net/gh/Shahilali5/FFICONS@main/PNG/907092607.png
```

### Discord Bot (Python)
```python
import discord
from discord.ext import commands

bot = commands.Bot(command_prefix='!')

@bot.command(name='icon')
async def get_icon(ctx, item_id):
    url = f'https://cdn.jsdelivr.net/gh/Shahilali5/FFICONS@main/PNG/{item_id}.png'
    embed = discord.Embed(title=f"Item #{item_id}", color=discord.Color.red())
    embed.set_image(url=url)
    await ctx.send(embed=embed)
```

### Node.js
```javascript
const fetch = require('node-fetch');
const fs = require('fs');

async function downloadIcon(itemID) {
  const url = `https://cdn.jsdelivr.net/gh/Shahilali5/FFICONS@main/PNG/${itemID}.png`;
  const response = await fetch(url);
  const buffer = await response.buffer();
  fs.writeFileSync(`icon_${itemID}.png`, buffer);
}

downloadIcon('907092607');
```

---

## ⭐ Features

✅ **No Watermarks** – Clean, professional icons  
✅ **Simple URL Structure** – Just append item ID  
✅ **Fast CDN Delivery** – Powered by jsDelivr (global CDN)  
✅ **Completely Free** – No API keys, no authentication required  
✅ **No Rate Limits** – Unlimited requests  
✅ **Zero Dependencies** – Just standard HTTPS GET requests  
✅ **Regular Updates** – New Free Fire items added periodically  
✅ **Optimized Images** – Compressed PNG files for fast loading  
✅ **Cross-Origin Support** – Works with CORS headers  
✅ **Stable & Reliable** – 99.9% uptime via jsDelivr

---

## 🔍 Getting Item IDs

### Where to Find Free Fire Item IDs

1. **In-Game Database**
   - Open Free Fire on mobile/PC
   - Visit item shop or inventory
   - Check game files for item metadata

2. **Community Resources**
   - Free Fire Wiki databases
   - Discord communities (r/FreeFire)
   - Gaming forums and databases

3. **Game Data Extractors**
   - FF Item ID databases online
   - APK data mining resources
   - Community GitHub repositories

4. **API Tools**
   - Free Fire fan APIs
   - Game database APIs

### Example Item IDs
| Item Type | Sample ID |
|-----------|-----------|
| Weapon Skin | `907092607` |
| Character | `301234567` |
| Pet | `401234567` |
| Emote | `501234567` |

---

## 🛠️ Use Cases

### Website & Web Applications
- Game item databases
- Trading platforms
- Gaming news websites
- Wiki & reference sites

### Mobile Apps
- Game companion apps
- Item trading apps
- Game guides & tutorials

### Discord / Community Tools
- Discord bots (item lookups, collections)
- Trading bots
- Game info bots

### Game Servers
- Private server websites
- Clan/guild websites
- Game panels & dashboards

### Data Aggregation
- Item price tracking
- Inventory management tools
- Game statistics websites

---

## 📋 Project Structure

```
FFICONS/
├── PNG/                    # All Free Fire item icons (PNG files)
│   ├── 907092607.png      # Individual item icons
│   ├── 301234567.png
│   └── ...
├── README.md               # This file
├── LICENSE                 # Open-source license
└── .gitignore             # Git ignore file
```

---

## ❓ Troubleshooting

### Icon Not Loading (404 Error)

**Problem:** `https://cdn.jsdelivr.net/gh/Shahilali5/FFICONS@main/PNG/123456.png` returns 404

**Solutions:**
1. Verify the item ID is correct
2. Check if the item exists in Free Fire (new items may not be added yet)
3. Try a known working ID first: `907092607`
4. Clear browser cache and try again
5. Check if jsDelivr is accessible in your region

### Slow Loading

**Problem:** Images load slowly

**Solutions:**
1. jsDelivr should auto-select the fastest regional CDN
2. Try downloading directly with curl: `curl -I https://cdn.jsdelivr.net/...`
3. Check your internet connection speed
4. Images are already optimized (~2-50 KB)

### CORS Issues

**Problem:** Cross-origin requests blocked

**Solution:** jsDelivr has CORS enabled by default. If you still have issues:
- Use a proxy service
- Run from same domain
- Check browser console for specific error

### Out of Date Icons

**Problem:** Icon doesn't match in-game appearance

**Solution:**
- New Free Fire updates may have changed items
- Submit an issue: [GitHub Issues](https://github.com/Shahilali5/FFICONS/issues)
- Community updates are periodic – patience may be needed

---

## 🤝 Contributing

### Report Missing Icons
1. Open an [Issue](https://github.com/Shahilali5/FFICONS/issues)
2. Provide the item ID
3. Include the item name and type (weapon, character, etc.)

### Submit Icons
- New item icons welcome!
- Ensure high quality (256x256 PNG, no watermarks)
- Submit via pull request or issue

### Improve Documentation
- Grammar/clarity fixes
- Add examples
- Suggest new sections

---

## 📊 Statistics & Metadata

- **Total Icons:** 5000+ Free Fire items
- **Update Frequency:** Weekly (new Free Fire items)
- **CDN Provider:** jsDelivr (global coverage)
- **Uptime:** 99.9% (CDN backed)
- **Average Response Time:** <100ms globally

---

## 🔐 License & Credits

### License
This project is **open-source** under the [MIT License](LICENSE).

### Original Creator
**[Shahil Ali](https://github.com/Shahilali5)** – API design, icon curation, and maintenance

### Contributors
**[ShahGCreator](https://github.com/ShahGCreator)** – Updates and improvements

### Official Repository
- **GitHub:** [github.com/Shahilali5/FFICONS](https://github.com/Shahilali5/FFICONS)
- **Issues & Support:** [GitHub Issues](https://github.com/Shahilali5/FFICONS/issues)

---

## 📞 Support & Contact

- **Found a Bug?** [Open an Issue](https://github.com/Shahilali5/FFICONS/issues)
- **Feature Request?** [Create a Discussion](https://github.com/Shahilali5/FFICONS/discussions)
- **Want to Contribute?** Fork the repo and submit a PR!

---

## 🌐 Related Resources

- [Free Fire Official Website](https://ff.garena.com)
- [jsDelivr CDN](https://www.jsdelivr.com)
- [Free Fire Community](https://reddit.com/r/FreeFire)

---

## 📈 Keywords (for SEO)

Free Fire icons API, Free Fire item icons, game icon CDN, free icon API, item icon API, game development API, Discord bot icons, Free Fire trading API, weapon skins icons, character icons Free Fire, no watermark icons

---

**Last Updated:** June 2026  
**Maintained By:** Shahil Ali & ShahGCreator
