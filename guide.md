# 📖 PrivMITLab Project Viewer — Complete Guide

> **Hinglish mein samjhaya gaya hai** | Last Updated: March 2026

---

## 🌐 App Kya Hai?

**PrivMITLab Project Viewer** ek modern, dark-theme wala portfolio/project showcase app hai.  
Isme tumhare saare projects **cards** ke form mein dikhte hain — ekdum premium look ke saath.

**Live Site:** https://privmitlab.github.io/PrivMITLab-project-viewer/

---

## 🗂️ File Structure

```
Project_Viewer-main/
│
├── index.html        ← Main app (poora UI + JavaScript)
├── projects.json     ← Tumhara data file (sirf yahi edit karna hai!)
├── guide.md          ← Yeh guide file
└── README.md         ← GitHub par dikhne wala description
```

> ✅ **Golden Rule:** Sirf `projects.json` edit karo. `index.html` mein haath mat lagao!

---

## ✨ App Mein Kya-Kya Features Hain?

### 1. 🌑 Loading Screen
- Jab page open hota hai, pehle ek **animated loader** aata hai
- "PrivMITLab" text gradient animation ke saath dikhta hai
- Progress bar fill hoti hai — 1.6 seconds baad automatically hata jata hai

### 2. 🎯 Liquid Cursor (Desktop)
- Mouse cursor ke upar ek **glowing ring** follow karta hai
- Kisi bhi button/card pe hover karo — ring badi ho jaati hai
- Mobile pe automatically disabled rahta hai

### 3. 🌌 Animated Background
- 3 **glowing orbs** slowly float karte hain (cyan, purple, pink)
- Subtle **grid pattern** background mein dikhta hai
- Noise texture se premium feel aata hai

### 4. 🧭 Navigation Bar
- Top pe fixed navbar hai — scroll karne pe bhi dikhta hai
- **PrivMITLab** logo (left side)
- Nav links: `Projects` | `Stats` | `Contact`
- **"Get in Touch"** button (right side) — Contact section tak le jaata hai
- Mobile pe nav links hide ho jaate hain (responsive)

### 5. 🔍 Search Bar
- Projects ko **real-time search** kar sako — title, description, tags, category sab search hote hain
- 200ms debounce hai — type karte hi results filter hote hain

### 6. 🏷️ Filter Tabs
- **5 category filters:** `All` | `IaC` | `Kubernetes` | `Automation` | `Security`
- Click karo — sirf us category ke cards dikhenge
- Search aur filter ek saath kaam karte hain

### 7. 🃏 Project Cards (Main Feature!)
Har card mein ye cheezein hoti hain:

| Element | Kya hai |
|---------|---------|
| **Status dot** | Pulsating dot — `ONLINE` / `UNKNOWN` |
| **Category badge** | Top-right pe category tag |
| **Title** | Project ka naam |
| **Description** | Short description |
| **Tech tags** | Technologies used (e.g. Docker, Python) |
| **Console block** | Terminal-style command aur benefits |
| **Repo button** | GitHub repository link kholega |
| **Launch button** | Live demo link kholega |

**3D Tilt Effect:** Card pe mouse le jao — card 3D mein tilt hota hai!  
**Glow Effect:** Card ke andar mouse move karo — glow follow karta hai!

### 8. 🐙 GitHub Stats Integration (New Feature!)
- Har card mein ab **real-time GitHub data** dikhta hai:
  - ⭐ **Stars** | 🍴 **Forks** | 👁️ **Watchers** | 📝 **Open Issues**
- **Kaise kaam karta hai?**
  - Jab page load hota hai, app automatically GitHub API se data fetch karta hai.
  - Har card ke niche ek small bar dikhta hai badges ke saath.
  - Agar project ka `repo` link GitHub ka hai, tabhi stats dikhenge.
  - Data har **1 ghante** mein automatically refresh hota hai load hone par.
- **Loading State:** Jab data fetch ho raha hota hai, ek chhota **spinner** dikhta hai card ke andar.

### 9. 📊 Stats Section
- 4 animated counters:
  - **99.9%** Uptime
  - **25** Projects
  - **12** Certifications
  - **24** Support/7
- Jab ye section scroll mein aata hai — numbers 0 se count up karte hain

### 10. 🦶 Footer
- **4 columns:** About | Navigation | Connect | Expertise
- Social media icons: GitHub, LinkedIn, Twitter, Discord
- Copyright text

---

## 📋 `projects.json` — Poora Samjho

### Basic Template (Naya Project Add Karna)

```json
{
    "title": "Project Ka Naam",
    "desc": "Project ki short description yahan likho.",
    "usage": "terminal-command --flag",
    "benefits": ["Benefit 1", "Benefit 2"],
    "tags": ["Tag1", "Tag2"],
    "category": "Automation",
    "color": "168, 85, 247",
    "status": "online",
    "repo": "https://github.com/tumhara-username/repo-name",
    "demo": "https://tumhari-live-site.com"
}
```

### Har Field ki Detail:

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `title` | String | ✅ | Project ka naam — card pe bada dikhta hai |
| `desc` | String | ✅ | 1-2 line description |
| `usage` | String | ✅ | Terminal command — console block mein `$` ke saath dikhta hai |
| `benefits` | Array[2] | ✅ | Exactly 2 features/benefits — console mein `✓` ke saath |
| `tags` | Array | ✅ | Technologies list — small badges ban jaate hain |
| `category` | String | ✅ | Filter tab se match karna chahiye (niche dekho) |
| `color` | String | ✅ | RGB values — card ka accent color |
| `status` | String | ✅ | `"online"` rakho always |
| `repo` | String | ⚠️ Optional | GitHub repo URL — Repo button ke liye |
| `demo` | String | ⚠️ Optional | Live demo URL — Launch button ke liye |

### ✅ Valid Categories (Filter ke saath match karo):

```
"IaC"          → Infrastructure as Code projects
"Kubernetes"   → K8s, Docker, container projects
"Automation"   → CI/CD, scripting, pipeline projects
"Security"     → Security tools, auth, scanning
```

> ⚠️ **Note:** Category bilkul exactly match karna chahiye (case-sensitive!)  
> `"automation"` ≠ `"Automation"` — lowercase kaam nahi karega!

### 🎨 Color Guide (Acche Colors ke liye):

```
Cyan/Teal:   "0, 240, 254"
Purple:      "168, 85, 247"
Pink:        "236, 72, 153"
Green:       "34, 197, 94"
Orange:      "249, 115, 22"
Red:         "239, 68, 68"
Blue:        "59, 130, 246"
Yellow:      "255, 215, 0"
Lime:        "127, 255, 0"
Aqua:        "0, 255, 255"
```

---

## 🚀 Naya Project Add Karne ka Workflow

### Step 1: `projects.json` kholo

VS Code mein ya GitHub web editor mein:

### Step 2: Last project ke baad naya object add karo

```json
[
    {
        ...existing project...
    },
    {
        ...existing project...
    },
    {
        "title": "Mera Naya Project",    ← Yahan apna project daalo
        "desc": "Description here.",
        "usage": "my-tool --run",
        "benefits": ["Fast", "Secure"],
        "tags": ["Python", "AWS"],
        "category": "Automation",
        "color": "99, 102, 241",
        "status": "online",
        "repo": "https://github.com/privmitlab/my-new-project",
        "demo": "https://privmitlab.github.io/PrivMITLab-project-viewer/"
    }
]
```

> ⚠️ **Common Mistake:** Last object ke baad comma mat lagao! JSON mein trailing comma invalid hai.

### Step 3: Commit & Push karo

```bash
git add projects.json
git commit -m "Add: Mera Naya Project"
git push
```

### Step 4: ~2 minute wait karo → Live site refresh karo ✅

---

## 💻 Local Testing Kaise Karo?

`index.html` seedha double-click se open karna **kaam nahi karega** kyunki browser `file://` protocol pe JSON fetch block karta hai (CORS).

### Solution: VS Code Live Server use karo

1. VS Code mein **Live Server** extension install karo
2. `index.html` pe right-click karo
3. **"Open with Live Server"** click karo
4. Browser mein `http://127.0.0.1:5500` pe khulega ✅

---

## 🔧 Common Problems & Solutions

| Problem | Reason | Solution |
|---------|--------|----------|
| Cards nahi dikh rahe locally | CORS / file:// issue | Live Server use karo |
| Naya project nahi dikh raha GitHub pe | GitHub Pages cache | 2-5 minute wait karo ya Ctrl+Shift+R press karo |
| Filter kaam nahi kar raha | Category typo | Exactly `"IaC"` / `"Kubernetes"` / `"Automation"` / `"Security"` likhoo |
| Repo/Demo button kuch nahi karta | `repo`/`demo` field empty ya missing | JSON mein sahi URL daalo |
| JSON load nahi ho raha | JSON syntax error | jsonlint.com pe validate karo |
| Card ka color kaam nahi | Color format galat | Exactly `"R, G, B"` format use karo — e.g. `"168, 85, 247"` |

---

## 📱 Responsive Design

| Screen Size | Layout |
|-------------|--------|
| Desktop (1500px+) | 4 column grid |
| Laptop (1200px) | 3 column grid |
| Tablet (900px) | Nav links hide, 2 column |
| Mobile (768px) | Single column, compact footer |
| Small Mobile (480px) | Single column, smaller fonts |

---

## 🛠️ Tech Stack (Kya use hua hai)

| Technology | Kahan use hua |
|------------|---------------|
| **HTML5** | Structure |
| **Vanilla CSS** | Styling, animations, responsive |
| **Vanilla JavaScript** | Data fetch, render, 3D tilt, cursor, filters |
| **Google Fonts** | Space Grotesk + Plus Jakarta Sans |
| **Font Awesome 6** | Icons (GitHub, rocket, search, etc.) |
| **GitHub Pages** | Free hosting |
| **projects.json** | Data source — no backend needed! |

---

## 🎯 Quick Cheatsheet

```
✅ Naya card add karna     → projects.json mein naya object add karo
✅ Card ka color badalna   → "color" field mein RGB change karo
✅ Repo link add karna     → "repo" field mein GitHub URL daalo
✅ Demo link add karna     → "demo" field mein live URL daalo
✅ Project delete karna    → JSON mein us object ko remove karo
✅ Search customize karna  → index.html line ~1570 filterProjects() function
✅ Filter tabs add karna   → HTML mein .filter-tab button add karo
❌ index.html regularly touch mat karo
❌ JSON mein trailing comma mat lagao
❌ Category mein lowercase mat likho
```

---

## 🌟 Summary

> `projects.json` = Tumhara **control panel** hai.  
> Isme data daalo, push karo, aur site automatically update ho jaayegi.  
> `index.html` ko touch karne ki zaroorat **kabhi nahi padegi** normal usage mein.

---

*Made with ❤️ by PrivMITLab*
