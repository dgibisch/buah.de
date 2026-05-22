# CreatorPulse — Claude Code Build Spec
## Influencer Intelligence Platform · MVP Clickdummy

---

## What We're Building

A single HTML file (~2000–3000 lines) that simulates a complete SaaS product for influencer marketing intelligence. This is a **fully interactive clickdummy** — all data is mocked/hardcoded, no real API calls. Navigation between screens happens via JS show/hide. The goal is a demo-ready product that looks and feels like a real, shippable SaaS tool.

**Core Value Prop:** Brands define what they agreed with each influencer (posting schedule, hashtags, KPIs). CreatorPulse monitors automatically and uses AI to surface what's working, what's broken, and what needs attention — without the team having to manually check every profile daily.

---

## Design Direction

**Aesthetic:** Modern B2B SaaS. Think Linear, Attio, Raycast Web. Clean. Precise. Data-rich without being overwhelming. Light mode only.

**NOT:** Purple gradient on white. Bootstrap. Material Design. Dark hacker terminal. Rounded-everything pastel. Generic AI slop.

### Typography
- **Display/Headlines:** `Instrument Serif` (Google Fonts) — used sparingly for large hero numbers and empty states only
- **UI/Body:** `DM Sans` (Google Fonts) — clean, modern, slightly geometric
- **Data/Numbers/Code:** `JetBrains Mono` (Google Fonts) — for metrics, percentages, timestamps

Load via:
```html
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@300;400;500;600&family=Instrument+Serif:ital@0;1&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
```

### Color System

```css
:root {
  /* Brand */
  --accent: #0066FF;
  --accent-light: #EBF2FF;
  --accent-dark: #0047CC;

  /* Backgrounds */
  --bg-base: #FAFAFA;
  --bg-surface: #FFFFFF;
  --bg-elevated: #FFFFFF;
  --bg-subtle: #F4F4F5;
  --bg-muted: #F0F0F1;

  /* Text */
  --text-primary: #0A0A0B;
  --text-secondary: #52525B;
  --text-tertiary: #A1A1AA;
  --text-inverse: #FFFFFF;

  /* Borders */
  --border-subtle: #E4E4E7;
  --border-default: #D4D4D8;
  --border-strong: #A1A1AA;

  /* Semantic */
  --green: #16A34A;
  --green-bg: #F0FDF4;
  --green-border: #BBF7D0;
  --red: #DC2626;
  --red-bg: #FEF2F2;
  --red-border: #FECACA;
  --amber: #D97706;
  --amber-bg: #FFFBEB;
  --amber-border: #FDE68A;
  --blue: #2563EB;
  --blue-bg: #EFF6FF;
  --blue-border: #BFDBFE;

  /* Layout */
  --sidebar-width: 240px;
  --header-height: 56px;
  --radius-sm: 6px;
  --radius-md: 8px;
  --radius-lg: 12px;
  --radius-xl: 16px;
  --radius-full: 9999px;

  /* Shadows */
  --shadow-sm: 0 1px 2px 0 rgba(0,0,0,0.05);
  --shadow-md: 0 4px 6px -1px rgba(0,0,0,0.07), 0 2px 4px -1px rgba(0,0,0,0.04);
  --shadow-lg: 0 10px 15px -3px rgba(0,0,0,0.08), 0 4px 6px -2px rgba(0,0,0,0.03);
  --shadow-focus: 0 0 0 3px rgba(0,102,255,0.15);
}
```

### Spacing System
Use 4px base unit. Common values: 4, 8, 12, 16, 20, 24, 32, 40, 48, 64px.

### Component Rules
- Cards: `background: var(--bg-surface); border: 1px solid var(--border-subtle); border-radius: var(--radius-lg); box-shadow: var(--shadow-sm);`
- Inputs: `height: 36px; border: 1px solid var(--border-default); border-radius: var(--radius-md); padding: 0 12px; font-size: 14px;` — on focus: `border-color: var(--accent); box-shadow: var(--shadow-focus);`
- Primary Button: `background: var(--accent); color: white; border-radius: var(--radius-md); height: 36px; padding: 0 16px; font-size: 14px; font-weight: 500;`
- Secondary Button: `background: var(--bg-surface); border: 1px solid var(--border-default); border-radius: var(--radius-md); height: 36px; padding: 0 16px; font-size: 14px;`
- Ghost Button: no border, no background, just text + hover state
- Badges/Pills: `font-size: 12px; font-weight: 500; padding: 2px 8px; border-radius: var(--radius-full);`
- Status dot: 8px circle, inline with label

### Micro-interactions
- All clickable elements: `transition: all 0.15s ease;`
- Hover on cards: subtle shadow lift
- Active state on nav items: accent left border + accent bg tint
- Sidebar item hover: `background: var(--bg-subtle);`
- Smooth screen transitions: fade via opacity 0→1, 200ms

---

## App Architecture

### Layout Shell
```
┌─────────────────────────────────────────────────┐
│  TOPBAR (56px) — Logo | Search | Notifs | User  │
├──────────────┬──────────────────────────────────┤
│              │                                  │
│  SIDEBAR     │   MAIN CONTENT AREA              │
│  (240px)     │   (flex-1, scrollable)           │
│              │                                  │
│  Navigation  │                                  │
│  Workspace   │                                  │
│              │                                  │
└──────────────┴──────────────────────────────────┘
```

The shell is always visible. Content area swaps between screens.

### Navigation Structure (Sidebar)

```
CreatorPulse  [logo mark]

OVERVIEW
  ○ Dashboard
  ○ Alert Center        [3] (badge)

CREATORS
  ○ Portfolio
  ○ Add Creator

INTELLIGENCE
  ○ Sentiment Analysis
  ○ Compliance Monitor
  ○ Competitor Watch

CAMPAIGNS
  ○ Active Campaigns
  ○ Performance

SETTINGS
  ○ Team
  ○ Integrations
  ○ Account
```

Bottom of sidebar: User avatar + name + plan badge

---

## Mock Data

Use this consistent data throughout ALL screens.

### Creators (Portfolio)

Avatar images from loremfaces.net — free, AI-generated, no attribution needed, consistent by ID:
- Sophie Meier: `https://www.loremfaces.net/96/id/7.jpg`
- Luca Bianchi: `https://www.loremfaces.net/96/id/15.jpg`
- Emma Schulz: `https://www.loremfaces.net/96/id/22.jpg`
- Finn Larsen: `https://www.loremfaces.net/96/id/31.jpg`
- Mia Hoffmann: `https://www.loremfaces.net/96/id/44.jpg`
- Jan Weber: `https://www.loremfaces.net/96/id/52.jpg`

For larger sizes use `/256/id/N.jpg`. Always use `<img>` tags with these URLs — they load reliably.

Post thumbnail images from Unsplash (free, no attribution in mockups):
- Beauty/skincare posts: `https://images.unsplash.com/photo-1570194065650-d99fb4bedf0a?w=300&h=300&fit=crop`
- Fitness posts: `https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8b?w=300&h=300&fit=crop`
- Fashion posts: `https://images.unsplash.com/photo-1483985988355-763728e1935b?w=300&h=300&fit=crop`
- Food posts: `https://images.unsplash.com/photo-1504674900247-0877df9cc836?w=300&h=300&fit=crop`
- Travel posts: `https://images.unsplash.com/photo-1469854523086-cc02fe5d8800?w=300&h=300&fit=crop`
- Tech posts: `https://images.unsplash.com/photo-1518770660439-4636190af475?w=300&h=300&fit=crop`

Additional beauty variety: `https://images.unsplash.com/photo-1522335789203-aabd1fc54bc9?w=300&h=300&fit=crop`
Additional travel variety: `https://images.unsplash.com/photo-1476514525535-07fb3b4ae5f1?w=300&h=300&fit=crop`
Lifestyle: `https://images.unsplash.com/photo-1529626455594-4ff0802cfb7e?w=300&h=300&fit=crop`

```javascript
const CREATORS = [
  {
    id: 1,
    name: "Sophie Meier",
    handle: "@sophiemeier",
    platform: "Instagram",
    avatar: "https://www.loremfaces.net/96/id/7.jpg",
    avatar_large: "https://www.loremfaces.net/256/id/7.jpg",
    followers: 184200,
    following: 892,
    tier: "Macro",
    niche: "Beauty & Skincare",
    bio: "✨ Beauty-Enthusiastin | Skincare-Nerd | Hamburg 🇩🇪 | Brand Collabs: sophie@mgmt.de",
    status: "active",
    health_score: 91,
    view_rate: 8.4,
    engagement_rate: 4.2,
    sentiment_score: 89,
    last_post: "2h ago",
    last_post_url: "https://images.unsplash.com/photo-1570194065650-d99fb4bedf0a?w=300&h=300&fit=crop",
    posts_this_week: 3,
    stories_this_week: 5,
    compliance: 100,
    campaign: "Summer Glow 2026",
    discount_code: "SOPHIE15",
    monthly_cost: 2800,
    monthly_revenue: 12400,
    country: "DE",
    city: "Hamburg",
    since: "März 2026",
    red_flags: [],
    recent_posts: [
      { img: "https://images.unsplash.com/photo-1570194065650-d99fb4bedf0a?w=300&h=300&fit=crop", likes: 8420, comments: 312, views: 48200, date: "vor 2h", caption: "Meine aktuelle Morgenroutine mit dem neuen Glow Serum von @glowco 🌟 #summerglow #glowco #skincare", hashtag_ok: true, mention_ok: true, sentiment: 91 },
      { img: "https://images.unsplash.com/photo-1522335789203-aabd1fc54bc9?w=300&h=300&fit=crop", likes: 7180, comments: 289, views: 41300, date: "vor 1 Tag", caption: "SPF ist kein Trend, SPF ist Lifestyle ☀️ @glowco Day Cream ist mein absoluter Favorit #summerglow", hashtag_ok: true, mention_ok: true, sentiment: 87 },
      { img: "https://images.unsplash.com/photo-1529626455594-4ff0802cfb7e?w=300&h=300&fit=crop", likes: 9340, comments: 401, views: 52100, date: "vor 2 Tagen", caption: "Vorher/Nachher nach 4 Wochen #summerglow Routine 😍 Absolute Gamechanger!", hashtag_ok: true, mention_ok: false, sentiment: 94 }
    ],
    story_compliance: [
      { day: "Mo", posted: true, mention: true, link: true, hashtag: true },
      { day: "Di", posted: true, mention: true, link: true, hashtag: true },
      { day: "Mi", posted: false, mention: false, link: false, hashtag: false },
      { day: "Do", posted: true, mention: true, link: false, hashtag: true },
      { day: "Fr", posted: true, mention: true, link: true, hashtag: true },
      { day: "Sa", posted: true, mention: false, link: true, hashtag: true },
      { day: "So", posted: false, mention: false, link: false, hashtag: false }
    ]
  },
  {
    id: 2,
    name: "Luca Bianchi",
    handle: "@lucabianchi",
    platform: "TikTok",
    avatar: "https://www.loremfaces.net/96/id/15.jpg",
    avatar_large: "https://www.loremfaces.net/256/id/15.jpg",
    followers: 312000,
    following: 421,
    tier: "Macro",
    niche: "Fitness & Lifestyle",
    bio: "💪 Personal Trainer | Wien 🇦🇹 | Fitness Content Creator | Koopanfragen: luca@creator.at",
    status: "warning",
    health_score: 64,
    view_rate: 5.1,
    engagement_rate: 3.8,
    sentiment_score: 72,
    last_post: "vor 38h",
    last_post_url: "https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8b?w=300&h=300&fit=crop",
    posts_this_week: 1,
    stories_this_week: 2,
    compliance: 60,
    campaign: "Active Life Q2",
    discount_code: "LUCA20",
    monthly_cost: 3200,
    monthly_revenue: 8200,
    country: "AT",
    city: "Wien",
    since: "April 2026",
    red_flags: ["view_rate_low", "posting_behind"],
    recent_posts: [
      { img: "https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8b?w=300&h=300&fit=crop", likes: 12300, comments: 198, views: 89400, date: "vor 38h", caption: "Mein Morgen-Workout Routine 🔥 Was macht ihr vor dem Sport? #activelive #fitness", hashtag_ok: false, mention_ok: false, sentiment: 72 },
      { img: "https://images.unsplash.com/photo-1526506118085-60ce8714f8c5?w=300&h=300&fit=crop", likes: 9800, comments: 145, views: 71200, date: "vor 4 Tagen", caption: "Leg Day ist jeden Tag 😅 #gym #fitness #motivation", hashtag_ok: false, mention_ok: false, sentiment: 68 }
    ],
    story_compliance: [
      { day: "Mo", posted: true, mention: false, link: false, hashtag: false },
      { day: "Di", posted: false, mention: false, link: false, hashtag: false },
      { day: "Mi", posted: true, mention: true, link: false, hashtag: false },
      { day: "Do", posted: false, mention: false, link: false, hashtag: false },
      { day: "Fr", posted: false, mention: false, link: false, hashtag: false },
      { day: "Sa", posted: false, mention: false, link: false, hashtag: false },
      { day: "So", posted: false, mention: false, link: false, hashtag: false }
    ]
  },
  {
    id: 3,
    name: "Emma Schulz",
    handle: "@emmaschulz",
    platform: "Instagram",
    avatar: "https://www.loremfaces.net/96/id/22.jpg",
    avatar_large: "https://www.loremfaces.net/256/id/22.jpg",
    followers: 67400,
    following: 1203,
    tier: "Micro",
    niche: "Sustainable Fashion",
    bio: "🌿 Slow Fashion | Secondhand Queen | Berlin 🇩🇪 | Nachhaltigkeit im Alltag | emma@greencreator.de",
    status: "active",
    health_score: 88,
    view_rate: 9.1,
    engagement_rate: 6.7,
    sentiment_score: 94,
    last_post: "vor 5h",
    last_post_url: "https://images.unsplash.com/photo-1483985988355-763728e1935b?w=300&h=300&fit=crop",
    posts_this_week: 2,
    stories_this_week: 6,
    compliance: 100,
    campaign: "EcoWear Launch",
    discount_code: "EMMA10",
    monthly_cost: 1200,
    monthly_revenue: 3800,
    country: "DE",
    city: "Berlin",
    since: "Mai 2026",
    red_flags: [],
    recent_posts: [
      { img: "https://images.unsplash.com/photo-1483985988355-763728e1935b?w=300&h=300&fit=crop", likes: 4210, comments: 387, views: 38900, date: "vor 5h", caption: "Diese Kollektion von @greenthread ist das Beste was mir diesen Sommer passiert ist 🌿 #ecowear #slowfashion #greenthread", hashtag_ok: true, mention_ok: true, sentiment: 96 },
      { img: "https://images.unsplash.com/photo-1515886657613-9f3515b0c78f?w=300&h=300&fit=crop", likes: 3890, comments: 312, views: 33200, date: "vor 2 Tagen", caption: "Warum ich nie wieder Fast Fashion kaufe — und was stattdessen #ecowear #nachhaltig", hashtag_ok: true, mention_ok: false, sentiment: 92 }
    ],
    story_compliance: [
      { day: "Mo", posted: true, mention: true, link: true, hashtag: true },
      { day: "Di", posted: true, mention: true, link: true, hashtag: true },
      { day: "Mi", posted: true, mention: false, link: true, hashtag: true },
      { day: "Do", posted: true, mention: true, link: true, hashtag: true },
      { day: "Fr", posted: true, mention: true, link: true, hashtag: true },
      { day: "Sa", posted: true, mention: true, link: false, hashtag: true },
      { day: "So", posted: false, mention: false, link: false, hashtag: false }
    ]
  },
  {
    id: 4,
    name: "Finn Larsen",
    handle: "@finnlarsen",
    platform: "TikTok",
    avatar: "https://www.loremfaces.net/96/id/31.jpg",
    avatar_large: "https://www.loremfaces.net/256/id/31.jpg",
    followers: 89300,
    following: 2841,
    tier: "Micro",
    niche: "Food & Cooking",
    bio: "🍳 Foodie | Home Cook | Zürich 🇨🇭 | Rezepte & Restauranttipps",
    status: "critical",
    health_score: 31,
    view_rate: 3.2,
    engagement_rate: 1.9,
    sentiment_score: 41,
    last_post: "vor 4 Tagen",
    last_post_url: "https://images.unsplash.com/photo-1504674900247-0877df9cc836?w=300&h=300&fit=crop",
    posts_this_week: 0,
    stories_this_week: 0,
    compliance: 20,
    campaign: "Taste DE Campaign",
    discount_code: "FINN15",
    monthly_cost: 1800,
    monthly_revenue: 1200,
    country: "CH",
    city: "Zürich",
    since: "Mai 2026",
    red_flags: ["no_post_48h", "sentiment_negative", "view_rate_low", "competitor_detected"],
    recent_posts: [
      { img: "https://images.unsplash.com/photo-1504674900247-0877df9cc836?w=300&h=300&fit=crop", likes: 1840, comments: 94, views: 28600, date: "vor 4 Tagen", caption: "Loving this from @rivalco lately 🔥 mega lecker #food #kochen", hashtag_ok: false, mention_ok: false, sentiment: 41, competitor: true },
      { img: "https://images.unsplash.com/photo-1565299624946-b28f40a0ae38?w=300&h=300&fit=crop", likes: 2100, comments: 67, views: 31200, date: "vor 8 Tagen", caption: "Mein liebstes Sommerrezept 🌞 Was kocht ihr gerade am liebsten?", hashtag_ok: false, mention_ok: false, sentiment: 58 }
    ],
    story_compliance: [
      { day: "Mo", posted: false, mention: false, link: false, hashtag: false },
      { day: "Di", posted: false, mention: false, link: false, hashtag: false },
      { day: "Mi", posted: false, mention: false, link: false, hashtag: false },
      { day: "Do", posted: false, mention: false, link: false, hashtag: false },
      { day: "Fr", posted: false, mention: false, link: false, hashtag: false },
      { day: "Sa", posted: false, mention: false, link: false, hashtag: false },
      { day: "So", posted: false, mention: false, link: false, hashtag: false }
    ]
  },
  {
    id: 5,
    name: "Mia Hoffmann",
    handle: "@miahoffmann",
    platform: "Instagram",
    avatar: "https://www.loremfaces.net/96/id/44.jpg",
    avatar_large: "https://www.loremfaces.net/256/id/44.jpg",
    followers: 428000,
    following: 634,
    tier: "Macro",
    niche: "Travel & Lifestyle",
    bio: "✈️ Travel Creator | 47 Länder | München 🇩🇪 | Lifestyle & Beauty | mia@mgmt-munich.de",
    status: "active",
    health_score: 95,
    view_rate: 11.2,
    engagement_rate: 5.1,
    sentiment_score: 97,
    last_post: "vor 1h",
    last_post_url: "https://images.unsplash.com/photo-1469854523086-cc02fe5d8800?w=300&h=300&fit=crop",
    posts_this_week: 4,
    stories_this_week: 9,
    compliance: 100,
    campaign: "Summer Glow 2026",
    discount_code: "MIASUMMER",
    monthly_cost: 3200,
    monthly_revenue: 18700,
    country: "DE",
    city: "München",
    since: "März 2026",
    red_flags: [],
    recent_posts: [
      { img: "https://images.unsplash.com/photo-1469854523086-cc02fe5d8800?w=300&h=300&fit=crop", likes: 47200, comments: 1840, views: 312000, date: "vor 1h", caption: "Santorini mit dem @glowco Glow Serum — because your skin deserves vacation too ✨ #summerglow #glowco #travel", hashtag_ok: true, mention_ok: true, sentiment: 98 },
      { img: "https://images.unsplash.com/photo-1476514525535-07fb3b4ae5f1?w=300&h=300&fit=crop", likes: 38900, comments: 1420, views: 289000, date: "vor 1 Tag", caption: "Meine Sommer-Skincare Routine für unterwegs 🌊 @glowco macht's so easy #summerglow", hashtag_ok: true, mention_ok: true, sentiment: 96 },
      { img: "https://images.unsplash.com/photo-1500530855697-b586d89ba3ee?w=300&h=300&fit=crop", likes: 42100, comments: 1680, views: 298000, date: "vor 2 Tagen", caption: "Dieser Sonnenuntergang und meine Haut hat noch nie besser geleuchtet 🌅 #summerglow #glowco #skincare", hashtag_ok: true, mention_ok: true, sentiment: 97 },
      { img: "https://images.unsplash.com/photo-1502082553048-f009c37129b9?w=300&h=300&fit=crop", likes: 35600, comments: 1290, views: 267000, date: "vor 3 Tagen", caption: "Von Mykonos mit Liebe ❤️ und natürlich mit @glowco SPF #summerglow", hashtag_ok: true, mention_ok: true, sentiment: 97 }
    ],
    story_compliance: [
      { day: "Mo", posted: true, mention: true, link: true, hashtag: true },
      { day: "Di", posted: true, mention: true, link: true, hashtag: true },
      { day: "Mi", posted: true, mention: true, link: true, hashtag: true },
      { day: "Do", posted: true, mention: true, link: true, hashtag: true },
      { day: "Fr", posted: true, mention: true, link: true, hashtag: true },
      { day: "Sa", posted: true, mention: true, link: true, hashtag: true },
      { day: "So", posted: true, mention: false, link: true, hashtag: true }
    ]
  },
  {
    id: 6,
    name: "Jan Weber",
    handle: "@janweber",
    platform: "TikTok",
    avatar: "https://www.loremfaces.net/96/id/52.jpg",
    avatar_large: "https://www.loremfaces.net/256/id/52.jpg",
    followers: 156000,
    following: 1840,
    tier: "Macro",
    niche: "Tech & Gaming",
    bio: "🎮 Tech Reviewer | Gaming Content | Berlin 🇩🇪 | Business: jan@techcreator.de",
    status: "warning",
    health_score: 58,
    view_rate: 6.3,
    engagement_rate: 2.9,
    sentiment_score: 68,
    last_post: "vor 22h",
    last_post_url: "https://images.unsplash.com/photo-1518770660439-4636190af475?w=300&h=300&fit=crop",
    posts_this_week: 2,
    stories_this_week: 3,
    compliance: 75,
    campaign: "Tech Summer",
    discount_code: "JAN10",
    monthly_cost: 2400,
    monthly_revenue: 5600,
    country: "DE",
    city: "Berlin",
    since: "Mai 2026",
    red_flags: ["hashtag_missing", "view_rate_low"],
    recent_posts: [
      { img: "https://images.unsplash.com/photo-1518770660439-4636190af475?w=300&h=300&fit=crop", likes: 7840, comments: 234, views: 94200, date: "vor 22h", caption: "Das neue Setup ist endlich fertig 🖥️ Was denkt ihr? #tech #gaming #setup", hashtag_ok: false, mention_ok: false, sentiment: 71 },
      { img: "https://images.unsplash.com/photo-1593640408182-31c228c2b769?w=300&h=300&fit=crop", likes: 6200, comments: 189, views: 78400, date: "vor 3 Tagen", caption: "Review: Lohnt sich der neue GadgetHub Controller? Meine ehrliche Meinung #techsummer #gadgethub", hashtag_ok: true, mention_ok: true, sentiment: 65 }
    ],
    story_compliance: [
      { day: "Mo", posted: true, mention: false, link: false, hashtag: false },
      { day: "Di", posted: true, mention: true, link: true, hashtag: false },
      { day: "Mi", posted: false, mention: false, link: false, hashtag: false },
      { day: "Do", posted: true, mention: false, link: false, hashtag: false },
      { day: "Fr", posted: false, mention: false, link: false, hashtag: false },
      { day: "Sa", posted: false, mention: false, link: false, hashtag: false },
      { day: "So", posted: false, mention: false, link: false, hashtag: false }
    ]
  }
];
```

---

## Fake AI Analyses — Full Texts

Use these VERBATIM in the AI Report tabs and AI insight boxes. They must feel real, specific, and data-driven — not generic.

### Mia Hoffmann — AI Weekly Intelligence Report

**Executive Summary:**
Mia Hoffmann ist diese Woche die klare Ausreißerin im Portfolio. Mit einer View Rate von 11,2% übertrifft sie den Portfolio-Schnitt um 51% und erreicht konsistent sechsstellige Videoabrufe. Ihre Audience zeigt starke Kaufabsicht: "Wo kann ich das kaufen?" ist der meistgestellte Kommentartyp. Keine Brand-Safety-Risiken identifiziert. Empfehlung: Kampagnen-Budget für Q3 um mindestens 40% erhöhen.

**Performance vs. Vereinbarung:**
- Posting-Frequenz: 4/3 Beiträge diese Woche ✅ (Überlieferung +33%)
- Hashtag #summerglow: In 4/4 Posts ✅
- Mention @glowco: In 4/4 Posts ✅
- View Rate: 11,2% vs. Ziel 7% ✅ (+60% über Ziel)
- Sentiment: 97% vs. Ziel 70% ✅
- Konkurrenz-Check: Sauber ✅

**Audience Intelligence:**
Die Kommentar-Analyse von 847 Kommentaren der letzten 7 Tage zeigt folgende Top-Intentionen:
- 23% Kaufabsicht ("wo kaufen?", "Link?", "bestellt!")
- 31% Inspiration ("Ziele", "wunderschön", "träume ich")
- 18% Produktfragen ("Duft?", "für sensitive Haut geeignet?")
- 12% Reisekontext ("wo ist das?", "Santorini?")
- 11% Marken-Erwähnungen positiv (@glowco gelobt)
- 5% Sonstige

Auffällig: Kein einziger negativer Kommentar zur Marke. Die Produktintegration wirkt organisch und nicht werblich — Follower nehmen die Kooperation positiv auf.

**Trend-Analyse:**
View Rate entwickelt sich positiv: +2,1 Prozentpunkte vs. Vormonat. Das Reise-Content-Format (Produkt im Urlaubskontext) performt 34% besser als Studio-/Indoor-Content. Stories werden täglich gepostet und erzielen laut Compliance-Daten konsequente Brand-Mentions.

**Empfehlungen:**
1. Exklusiven Launch-Code für Mia's Audience testen — ihre Conversion Rate dürfte überdurchschnittlich hoch sein
2. Das Reise-Content-Format als Briefing-Standard für neue Creator übernehmen
3. Story-Link-Sticker häufiger einsetzen (aktuell 6/7 Tage — anstreben: täglich)

**Risiko-Score:** Sehr niedrig ◼◻◻◻◻

---

### Sophie Meier — AI Weekly Intelligence Report

**Executive Summary:**
Sophie Meier liefert solide Performance mit einer View Rate von 8,4% und einem Sentiment-Score von 89%. Die Kooperation läuft stabil. Einziger Hinweis: In einem von drei Posts fehlte die @glowco Mention — wahrscheinlich versehentlich. Empfehlung: Freundliche Erinnerung, kein Eskalationsbedarf.

**Audience Intelligence:**
Kommentar-Analyse von 312 Kommentaren:
- 19% Produktfragen ("Für welchen Hauttyp?", "Wie lange bis Ergebnis?")
- 28% Positives Feedback ("Haut sieht toll aus!", "Kaufe ich!")
- 24% Community-Interaktion (Sophie antwortet aktiv auf Kommentare — sehr positiv)
- 14% Kaufabsicht direkt
- 15% Sonstige

Sophie hat eine besonders enge Community-Bindung — sie antwortet auf ca. 40% aller Kommentare, was die Engagement Rate positiv beeinflusst.

**Empfehlungen:**
1. Mention @glowco als Must-Have im Briefing deutlicher kommunizieren
2. Produktvorher/Nachher-Format weiter nutzen — 9.340 Likes war der beste Post dieser Woche
3. Story-Link-Sticker: An 2 Tagen nicht gesetzt — hier Reminder einplanen

**Risiko-Score:** Niedrig ◼◼◻◻◻

---

### Emma Schulz — AI Weekly Intelligence Report

**Executive Summary:**
Emma Schulz ist trotz kleinerem Account (67.400 Follower) ein Top-Performer. Ihre Engagement Rate von 6,7% ist die höchste im Portfolio — nahezu dreimal so hoch wie der Branchen-Durchschnitt für Micro-Influencer. Ihre Nische (Sustainable Fashion) trifft die GreenThread-Positionierung perfekt. Der ROI ist mit 3,17x solide.

**Audience Intelligence:**
Emma's Audience ist überdurchschnittlich engagiert und kaufkräftig. Kommentar-Analyse zeigt:
- 38% Werte-Diskussion ("endlich eine Brand die das ernst nimmt", "so wichtig!")
- 22% Kaufabsicht ("Code?", "sofort bestellt", "brauche ich")
- 18% Community ("ihr seid alle so inspiring")
- 12% Produktdetails
- 10% Sonstige

Besonderheit: Emmas Audience diskutiert aktiv über Nachhaltigkeit — das schafft organische Reichweite weit über die direkten Follower hinaus.

**Empfehlungen:**
1. Kampagnen-Budget verdoppeln — der ROI rechtfertigt die Investition
2. Emma als Markenbotschafterin für Quarterly Launches positionieren
3. Co-Creation Möglichkeit prüfen: Emma könnte an Produkt-Feedback-Runden teilnehmen

**Risiko-Score:** Sehr niedrig ◼◻◻◻◻

---

### Finn Larsen — AI Weekly Intelligence Report ⚠️ KRITISCH

**Executive Summary:**
KRITISCHE SITUATION. Finn Larsen hat diese Woche keine einzige Story oder Post veröffentlicht. Der letzte Post liegt 4 Tage zurück und enthielt eine @rivalco Mention — ein direkter Verstoß gegen die Vereinbarung. Der Sentiment Score ist auf 41% gefallen, getrieben durch kritische Kommentare. Der ROI ist mit 0,67x negativ. Sofortiger Handlungsbedarf.

**Kritische Findings:**
1. **Kein Post seit 4 Tagen** — Vereinbarung sieht 3x/Woche vor. 0 Deliverables diese Woche.
2. **Konkurrenz-Erwähnung** — @rivalco im letzten Post-Caption (14 Mai). Klarer Vertragsverstoß.
3. **Negativer Sentiment-Surge** — 41% positiv. Häufigste negative Kommentare: "Sellout", "nicht authentisch", "Werbung nervt"
4. **View Rate 3,2%** — weit unter dem vereinbarten Mindestziel von 7%
5. **Story-Compliance: 0/7 Tage** — keine einzige Story diese Woche

**Kommentar-Analyse (letzte 2 Posts):**
- 41% positiv (generische Likes, keine Produktinteresse)
- 34% negativ ("wirkt gekauft", "nicht authentisch")  
- 25% neutral
- Kaufabsicht: unter 2% — sehr niedrig

**Empfehlungen:**
1. SOFORT: Persönliches Gespräch mit dem Creator führen
2. Klären ob Kooperation fortgesetzt werden soll
3. Falls ja: Neues Briefing, intensiveres Monitoring, monatliche Check-ins
4. Falls nein: Kooperation formal beenden und Budget umverteilen
5. @rivalco Post im Auge behalten — rechtliche Implikationen prüfen

**Risiko-Score:** Kritisch ◼◼◼◼◼

---

### Luca Bianchi — AI Weekly Intelligence Report

**Executive Summary:**
Luca Bianchi zeigt diese Woche eine deutliche Underperformance. Nur 1 Post statt 3 vereinbarte, keine Kampagnen-Hashtags verwendet, View Rate 5,1% (Ziel: 7%). Die Situation ist ernst aber nicht kritisch — es gibt keine Brand-Safety-Probleme. Empfehlung: Sofortige Reminder-Kommunikation und Ursachen-Klärung.

**Audience Intelligence:**
Luca's Fitness-Audience ist grundsätzlich engagiert, aber das Kampagnen-Content-Format verfehlt sie. Analyse zeigt: Organischer Fitness-Content (ohne Produktplatzierung) performt 2,3x besser als Kooperations-Content. Das deutet auf mangelnde Integration hin — die Produkt-Erwähnung wirkt aufgesetzt.

**Empfehlungen:**
1. Briefing überarbeiten: Produkt natürlicher in Workout-Content integrieren
2. Reminder für Posting-Frequency — 1 Post/Woche ist nicht akzeptabel
3. View Rate Entwicklung über nächste 2 Wochen beobachten
4. Falls keine Verbesserung: Kampagnen-Neustart oder Creator-Wechsel

**Risiko-Score:** Mittel ◼◼◼◻◻

---

### Jan Weber — AI Weekly Intelligence Report

**Executive Summary:**
Jan Weber liefert inkonsistente Performance. 2 Posts diese Woche (Ziel: 3), aber der Kampagnen-Hashtag #techsummer fehlt in einem Post, @gadgethub wurde nicht durchgängig erwähnt. View Rate mit 6,3% knapp unter dem 7%-Ziel. Der Tech-Audience-Fit ist gut, aber das Kampagnen-Commitment ist schwach.

**Audience Intelligence:**
Jan's Gaming/Tech-Audience ist kritisch und qualitätsorientiert — positive Reaktionen auf ehrliche Reviews, negative auf wahrgenommene Werbung. Der @gadgethub Post mit transparenter Meinung ("Meine ehrliche Meinung") performte 2x besser als nicht-transparente Produkterwähnung.

**Empfehlungen:**
1. Hashtag-Compliance als Mindestanforderung nochmals kommunizieren
2. "Ehrliche Review"-Format weiter fördern — kommt bei der Audience besser an als klassische Werbung
3. Story-Konsistenz verbessern: Nur 3 von 7 Tagen gepostet

**Risiko-Score:** Mittel ◼◼◼◻◻

---

## Fake Comments Data (for Sentiment Tab)

### Mia Hoffmann — Sample Comments

```javascript
const MIA_COMMENTS = [
  { user: "lisa_travels", avatar: "https://www.loremfaces.net/48/id/8.jpg", text: "Wo kann ich das kaufen?? Link please!! 😍", sentiment: "positive", intent: "purchase" },
  { user: "skincarequeen_de", avatar: "https://www.loremfaces.net/48/id/12.jpg", text: "Meine Haut liebt das Serum wirklich, seit 3 Wochen dabei und wow 🌟", sentiment: "positive", intent: "testimonial" },
  { user: "travel.addict.mu", avatar: "https://www.loremfaces.net/48/id/19.jpg", text: "Santorini sieht atemberaubend aus! Und deine Haut strahlt so 😍", sentiment: "positive", intent: "inspiration" },
  { user: "beautynerdin", avatar: "https://www.loremfaces.net/48/id/25.jpg", text: "Ist das Serum auch für sehr sensitive Haut geeignet?", sentiment: "neutral", intent: "question" },
  { user: "naturelover_nina", avatar: "https://www.loremfaces.net/48/id/33.jpg", text: "Bestellt! Dein Code hat 10% gespart 🙏 danke Mia!", sentiment: "positive", intent: "purchase" },
  { user: "reise_traumwelt", avatar: "https://www.loremfaces.net/48/id/41.jpg", text: "Diese Farben!! Griechenland auf der Bucket List 💙", sentiment: "positive", intent: "inspiration" },
  { user: "glow.up.berlin", avatar: "https://www.loremfaces.net/48/id/47.jpg", text: "Zeig mal die volle Routine! Wie lange brauchst du morgens?", sentiment: "positive", intent: "engagement" },
  { user: "frau.mueller.k", avatar: "https://www.loremfaces.net/48/id/53.jpg", text: "Endlich mal Skincare die nicht nur 20-Jährige zeigt. Danke! 🙏", sentiment: "positive", intent: "gratitude" }
];
```

### Finn Larsen — Sample Comments (negative)

```javascript
const FINN_COMMENTS = [
  { user: "foodie.frank", avatar: "https://www.loremfaces.net/48/id/62.jpg", text: "Bro warum tust du mit @rivalco wenn du doch für @fresheats wirbt... Sellout?", sentiment: "negative", intent: "criticism" },
  { user: "kochblog.maria", avatar: "https://www.loremfaces.net/48/id/71.jpg", text: "Die Qualität deiner Videos hat stark nachgelassen in letzter Zeit 😕", sentiment: "negative", intent: "criticism" },
  { user: "echte.reviews.only", avatar: "https://www.loremfaces.net/48/id/78.jpg", text: "Ich glaub dir nicht mehr wenn du alles anpreist was Geld zahlt", sentiment: "negative", intent: "distrust" },
  { user: "zuerich.foodie", avatar: "https://www.loremfaces.net/48/id/84.jpg", text: "Tolles Rezept aber habt ihr das mit @rivalco gesehen? Komisch...", sentiment: "negative", intent: "observation" },
  { user: "kochen.macht.spass", avatar: "https://www.loremfaces.net/48/id/91.jpg", text: "Früher warst du authentisch. Was ist passiert?", sentiment: "negative", intent: "disappointment" },
  { user: "swiss.recipes", avatar: "https://www.loremfaces.net/48/id/97.jpg", text: "Das Rezept klingt gut aber mehr postest du ja auch nicht mehr 😂", sentiment: "neutral", intent: "observation" }
];
```
  { id: 1, severity: "critical", creator: "Finn Larsen", handle: "@finnlarsen", type: "no_post", message: "No post in 4 days — agreement requires 3x/week", time: "2h ago", read: false },
  { id: 2, severity: "critical", creator: "Finn Larsen", handle: "@finnlarsen", type: "competitor", message: "Competitor brand @rivalco detected in last post caption", time: "3h ago", read: false },
  { id: 3, severity: "critical", creator: "Finn Larsen", handle: "@finnlarsen", type: "sentiment", message: "Sentiment dropped to 41% — negative comment surge detected", time: "5h ago", read: false },
  { id: 4, severity: "warning", creator: "Luca Bianchi", handle: "@lucabianchi", type: "posting_behind", message: "Only 1/3 posts this week — reminder triggered", time: "6h ago", read: false },
  { id: 5, severity: "warning", creator: "Jan Weber", handle: "@janweber", type: "hashtag", message: "#summerglow hashtag missing from last 2 posts", time: "8h ago", read: true },
  { id: 6, severity: "warning", creator: "Luca Bianchi", handle: "@lucabianchi", type: "view_rate", message: "View rate 5.1% — below agreed threshold of 7%", time: "12h ago", read: true },
  { id: 7, severity: "info", creator: "Mia Hoffmann", handle: "@miahoffmann", type: "performance", message: "Outstanding week — 11.2% view rate, highest in portfolio", time: "1d ago", read: true },
  { id: 8, severity: "info", creator: "Emma Schulz", handle: "@emmaschulz", type: "sentiment", message: "Sentiment score reached 94% — audience loves the content", time: "1d ago", read: true }
];
```

### Campaigns

```javascript
const CAMPAIGNS = [
  { id: 1, name: "Summer Glow 2026", brand: "GlowCo Skincare", status: "active", creators: 2, start: "May 1", end: "Jun 30", budget: 48000, spent: 31100, posts_required: 24, posts_done: 18, avg_sentiment: 93, avg_view_rate: 9.8 },
  { id: 2, name: "Active Life Q2", brand: "SportLine DE", status: "active", creators: 1, start: "Apr 15", end: "Jun 15", budget: 18000, spent: 12400, posts_required: 12, posts_done: 7, avg_sentiment: 72, avg_view_rate: 5.1 },
  { id: 3, name: "EcoWear Launch", brand: "GreenThread", status: "active", creators: 1, start: "May 10", end: "Jul 10", budget: 9000, spent: 4200, posts_required: 8, posts_done: 6, avg_sentiment: 94, avg_view_rate: 9.1 },
  { id: 4, name: "Taste DE Campaign", brand: "FreshEats GmbH", status: "critical", creators: 1, start: "May 1", end: "May 31", budget: 6000, spent: 3800, posts_required: 12, posts_done: 3, avg_sentiment: 41, avg_view_rate: 3.2 },
  { id: 5, name: "Tech Summer", brand: "GadgetHub", status: "warning", creators: 1, start: "May 15", end: "Jul 31", budget: 22000, spent: 8900, posts_required: 16, posts_done: 8, avg_sentiment: 68, avg_view_rate: 6.3 }
];
```

---

## Stories Monitoring — What's Possible

Important context for the clickdummy: Stories monitoring via Apify works but with limitations. Make sure the UI reflects this accurately.

**What CreatorPulse CAN show for Stories:**
- Did the creator post a story yesterday? (yes/no)
- Did they mention the brand handle (@mention) in the story?
- Did they include the required hashtag in story text/sticker?
- Did they set a link sticker (Swipe-Up equivalent)?
- Story archived (media URL saved before 24h expiry)

**What CreatorPulse CANNOT show for Stories:**
- View count (only visible to the creator themselves)
- Replies to stories
- Poll/quiz results

In the UI: Show a "Story Check" row in the compliance table with the above checkable items. Never show a "Story Views" metric — instead show "Story Posted ✅" as the compliance signal.

---

## Shopify Revenue Integration — BETA

This is a V2 feature, shown in the clickdummy as a locked/beta module to communicate product vision.

**How it would work (for context when building the UI):**
- Customer connects their Shopify store (API key, one-time setup)
- Each influencer has a unique discount code registered (e.g. SOPHIE15, LUCAFIT, etc.)
- CreatorPulse calls Shopify Orders API daily: `GET /admin/api/orders.json?discount_code=SOPHIE15`
- Aggregates: total revenue, order count, avg. order value, conversion rate
- Displays ROI automatically: (Revenue - Creator Cost) / Creator Cost

**What this unlocks:**
- Revenue per influencer, automatically, no manual entry
- True ROI per creator and per campaign
- Identify which creators actually drive sales vs. just engagement

**UI treatment in clickdummy:**
- Show a "Revenue & ROI" tab/section in Creator Detail with a `BETA` badge
- Show mock data (realistic numbers) but overlay a subtle "Connect Shopify to unlock live data" banner
- In Integrations screen: Shopify card shows "BETA" badge, with a teaser of what data will flow in
- In Dashboard KPIs: show a "Revenue Today" card with a lock icon and "Connect Shopify →" CTA
- The data IS shown (mocked) but with clear beta/preview labeling so the customer understands this is coming

**Beta badge style:**
```css
.badge-beta {
  background: #FFF7ED;
  color: #C2410C;
  border: 1px solid #FED7AA;
  font-size: 11px;
  font-weight: 600;
  padding: 2px 7px;
  border-radius: 9999px;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}
```

---

## Screens (All in one HTML file)

Build ALL screens. Navigation via sidebar clicks. Use `showScreen('screen-id')` pattern with JS.

---

### SCREEN 1: Login

**Route:** `#login` (default landing)

**Layout:** Centered card on light grey background. No sidebar/topbar.

**Left side (60%):**
- Large background with subtle dot grid pattern
- CreatorPulse logo mark (abstract CP monogram, geometric)
- Tagline: *"Know what your creators are doing. Before your team has to ask."*
- 3 feature highlights with icons (small, subtle):
  - "AI-powered sentiment analysis"
  - "Automated compliance monitoring"
  - "Real-time posting alerts"

**Right side (40%):**
- White card, centered
- "Welcome back" headline
- Email input
- Password input + show/hide toggle
- "Sign in" primary button (full width)
- "Forgot password?" link
- Divider "or"
- SSO button (e.g., "Continue with Google")
- Footer: "New to CreatorPulse? Start free trial →"

Clicking "Sign in" → go to Dashboard screen.

---

### SCREEN 2: Dashboard (Home)

**Route:** `#dashboard`

**Header row:**
- "Good morning, Daniel 👋" (left)
- Date (right, muted)
- "Last sync: 2 minutes ago" with spinning refresh icon

**Alert Banner (if unread alerts exist):**
- Amber/red strip at top: "3 critical alerts need your attention" + "View all →" link

**KPI Row (4 metric cards):**
```
Active Creators    |  Avg. Health Score  |  Posts Today  |  Portfolio Revenue  🔒 BETA
      6            |        71%          |      4        |     Connect Shopify
   +1 this month   |   ↓ from 78%        |  2 pending    |  to track revenue →
```
The 4th card (Portfolio Revenue) has a lock icon, muted styling, and "Connect Shopify →" as a CTA link. On hover: tooltip "Connect your Shopify store to automatically track revenue per influencer via discount codes."

**Main Grid (2 columns):**

Left (60%):
- **Creator Health Overview** — table/list of all 6 creators
  - Avatar + name + handle
  - Platform badge (IG/TT)
  - Health score bar (colored: green >80, amber 50-80, red <50)
  - Status badge (Active / Warning / Critical)
  - Last post timestamp
  - Quick "View" link

Right (40%):
- **Alert Center Preview** — latest 4 alerts, each with:
  - Severity icon (red/amber/blue dot)
  - Creator name
  - Short message
  - Time ago
  - "Mark read" action
- "View all alerts →" footer link

**Bottom Row (3 columns):**
- **Top Performer** — Mia Hoffmann card with big view rate stat + sentiment score
- **Needs Attention** — Finn Larsen card with red flags listed
- **Weekly Activity** — Simple bar chart (7 days, posts per day, mock SVG bars)

---

### SCREEN 3: Alert Center

**Route:** `#alerts`

**Header:**
- "Alert Center" title
- Filter tabs: All (8) | Critical (3) | Warning (3) | Info (2) | Unread (5)
- "Mark all as read" button

**Alert List:**
Each alert as a card row:
```
[●] [CREATOR AVATAR] Creator Name · @handle          [2h ago]    [×]
    No post in 4 days — agreement requires 3x/week
    [View Creator] [Send Reminder]
```
- Red dot = critical, amber = warning, blue = info
- Unread alerts have subtle left accent border in their severity color
- Read alerts are slightly muted

**Sidebar mini-panel (right, 280px):**
- "Alert Settings"
- Threshold config (display-only sliders):
  - View rate threshold: 7%
  - Posting gap: 48h
  - Sentiment floor: 60%
  - Competitor keywords: [list]
- "Configure →" link

---

### SCREEN 4: Portfolio (Creator List)

**Route:** `#portfolio`

**Header:**
- "Creator Portfolio" title + "6 creators" count
- Search input (filter by name/handle)
- Filter dropdowns: Platform | Status | Tier | Campaign
- Sort: Health Score ↓
- "Add Creator" primary button (→ goes to Add Creator screen)

**View toggle:** Grid / Table (default: table)

**Table View:**
```
Avatar | Name + Handle | Platform | Tier | Campaign | Health | View Rate | Sentiment | Posts/Week | Status | Actions
```

Each row is clickable → goes to Creator Detail screen.

Status badges:
- Active: green pill
- Warning: amber pill  
- Critical: red pill

Actions column: "View" | "Edit Goals" | "···" menu

**Grid View (when toggled):**
6 cards in 3-column grid. Each card:
- Avatar (large, 48px) + name + handle + platform badge
- Health score ring/arc
- 3 quick stats: View Rate | Engagement | Sentiment
- Status badge
- Campaign tag
- "View Details →" button

---

### SCREEN 5: Add Creator

**Route:** `#add-creator`

**Layout:** Centered form, max-width 680px, stepped process

**Step indicator:** 3 steps — Search → Configure Goals → Confirm

**Step 1: Search & Verify**
- Large search input: "Enter Instagram or TikTok username..."
- Platform toggle: Instagram | TikTok
- "Search" button

After "searching" (simulate with timeout → show result):
- Creator preview card appears:
  - Profile photo placeholder (avatar initials)
  - Name, handle, platform
  - Auto-fetched stats (mocked):
    - Followers: 94,200
    - Avg. View Rate: 7.8%
    - Engagement Rate: 4.1%
    - Est. Fake Followers: 3.2%
    - Recent brand deals: 2 (last 30 days)
  - AI Vetting Score: 78/100 "Good fit"
  - Green checkmarks / red warnings per metric
- "Looks good — Continue" button or "Not a match — Search again"

**Step 2: Configure Goals & Agreement**
Split layout:
- Left: Goal inputs
  - Min. posting frequency: [dropdown] 1x/week | 2x/week | 3x/week | daily
  - Required hashtags: [tag input — add/remove tags]
  - Required mentions: [tag input]
  - Forbidden competitors: [tag input]
  - Min. view rate target: [number input] %
  - Min. engagement target: [number input] %
  - Min. sentiment score: [slider] 60%
  - Campaign: [dropdown]
  - Cooperation period: [date range picker — display only]
  - Monthly budget: [number input] €

- Right: Live Preview card
  - Shows configured agreement in human-readable format:
  > *"Sophie will post at least 3x per week using #summerglow and @brandname. We expect a min. 7% view rate and 60% positive sentiment. Any post featuring @competitor is a red flag."*
  - Updates as user types

**Step 3: Confirm**
- Full summary of creator + agreement
- "Add to Portfolio" button → success state → auto-navigate to creator detail

---

### SCREEN 6: Creator Detail

**Route:** `#creator/:id`

Show Mia Hoffmann by default, but clicking from portfolio shows correct creator.

**Header:**
- Back link "← Portfolio"
- Large avatar (64px) + name + handle + platform badge + tier badge
- Status badge (Active)
- Health Score prominent: large number "95" with colored ring
- "Edit Goals" button | "Send Reminder" button | "··· More" dropdown

**Tab Navigation:**
Overview | Posts | Stories | Sentiment | Compliance | AI Report | Revenue `BETA`

**Tab: Overview (default)**

3-column grid top:

Left column — Creator Stats:
- Followers: 428,000
- Avg. View Rate: 11.2% ↑
- Engagement Rate: 5.1%
- Sentiment Score: 97%
- Posts this week: 4/3 ✓ (over-delivered)
- Country: 🇩🇪 Germany
- Niche: Travel & Lifestyle
- In portfolio since: March 2026

Middle column — Agreement Summary card:
- Campaign: Summer Glow 2026
- Required: 3x posts/week
- Hashtags: #summerglow, #glowco
- Mentions: @glowco
- Forbidden: @rivalbeauty, @competitorX
- View Rate Target: 7% (current: 11.2% ✅)
- Sentiment Target: 70% (current: 97% ✅)
- Budget: €3,200/month

Right column — Revenue & ROI card:
- This month revenue: €18,700
- Cost: €3,200
- ROI: 484%
- Clicks generated: 12,840
- Estimated sales: 94

Bottom: Recent Posts timeline (5 most recent):
Each post row:
- Post thumbnail placeholder (colored rectangle)
- Caption preview (truncated)
- Posted: "1h ago"
- Views: 47,200 | Likes: 2,340 | Comments: 186
- Hashtag compliance: ✅ all required
- Sentiment badge: 97% positive
- "View comments →"

**Tab: Stories**

Story compliance for this creator:

Top row — 3 status cards:
- Stories posted this week: 4/3 ✅ (over-delivered)
- Brand mention in stories: 3/4 ✅
- Link sticker set: 4/4 ✅

Info banner (subtle blue tint):
> *"ℹ️ Story view counts are only visible to the creator. CreatorPulse verifies posting compliance, brand mentions, and link sticker usage — but cannot access view metrics for external accounts."*

Stories Timeline (last 7 days):
Each story entry:
- Day label (Mon, Tue, etc.)
- Status: Posted ✅ / Not posted ❌
- If posted: Brand mention ✅/❌ | Link sticker ✅/❌ | Hashtag ✅/❌
- "Story archived" note (shows Linkster handles this if connected)
- Timestamp

**Tab: Revenue `BETA`**

Full-width soft banner at top:
```
┌─────────────────────────────────────────────────────────────┐
│  🔗  Connect your Shopify store to unlock live revenue data  │
│  CreatorPulse will automatically pull orders per discount    │
│  code and calculate real ROI for each creator.              │
│                                              [Connect Shopify →]  │
└─────────────────────────────────────────────────────────────┘
```
Banner style: light amber background (#FFFBEB), amber border, not alarming — informational.

Below banner — show MOCKED revenue data with a subtle "Preview data" watermark or "Sample data" label in the top right corner of each card:

Revenue KPI row (4 cards, all showing mock data):
```
Est. Revenue      |   Orders    |  Avg. Order  |    ROI
  €18,700         |     94      |   €198.90    |   484%
  via MIASUMMER   | this month  |              | vs €3,200 cost
```

Revenue over time — line chart (SVG, 30 days)
Showing: revenue bars per week attributed to this creator

Top Products sold via this creator:
Small table:
```
Product                    | Units | Revenue
Glow Serum 30ml            |  47   | €4,230
Vitamin C Cream            |  31   | €2,480
SPF Day Moisturizer        |  16   | €1,120
```

Attribution note (muted, small):
> *"Revenue tracked via discount code MIASUMMER. Actual revenue may be higher — customers who purchase without using the code are not captured. Estimated undercount: ~30%."*
- Larger preview
- Full stats
- Comment count + quick sentiment bar
- Compliance checklist (hashtags ✓, mentions ✓, no competitors ✓)

**Tab: Sentiment**

Full sentiment analysis view:
- Big sentiment score: 97% with gauge/arc visualization
- Trend chart (last 30 days, line chart — SVG mock)
- Sentiment breakdown: Positive 97% | Neutral 2% | Negative 1%
- Topic cloud (top comment themes — simulated as badges):
  "love this ❤️" | "where to buy?" | "looks amazing" | "skin goals" | "worth it"
- Recent comments sample (5 comments):
  Each: avatar initials + comment text + sentiment label (green/amber/red)
- AI Summary box (blue tinted card):
  > *"Mia's audience is highly engaged and purchase-intent is strong. The most common comment theme is 'where to buy' (18% of comments), indicating the product is resonating. No negative brand mentions detected. Recommend featuring this creator in next campaign brief."*

**Tab: Compliance**

Compliance score: 100% (green)

Checklist table:
```
Requirement          | Status  | Details
─────────────────────|─────────|──────────────────────
Post 3x/week         | ✅ Met  | 4 posts this week
#summerglow in posts | ✅ Met  | In 4/4 posts
@glowco mentioned    | ✅ Met  | In 3/4 posts
No competitor posts  | ✅ Met  | 0 detected
View Rate ≥ 7%       | ✅ Met  | 11.2% avg
Sentiment ≥ 70%      | ✅ Met  | 97% avg
```

Timeline of recent compliance checks (last 7 days, visual checklist)

**Tab: AI Report**

Full AI-generated intelligence report. Layout like a document:

Header: "Weekly Intelligence Report — Mia Hoffmann"
Generated: "Today, 08:00 · Next update: tomorrow 08:00"

Sections:
1. **Executive Summary** — 3-4 sentence paragraph
2. **Performance vs. Agreement** — mini table, all green
3. **Audience Intelligence** — comment analysis, top intents
4. **Trend Analysis** — is performance improving/declining?
5. **Recommendations** — 3 bullet AI suggestions
6. **Risk Score** — Low (visual indicator)

Export button: "Export PDF" (non-functional but present)

---

### SCREEN 7: Sentiment Analysis (Global)

**Route:** `#sentiment`

**Portfolio-level sentiment overview**

Top stats:
- Portfolio avg. sentiment: 82%
- Creators above target: 4/6
- Creators below target: 2/6
- Most negative creator: Finn Larsen (41%)

**Creator Sentiment Ranking** — horizontal bar chart (SVG):
```
Mia Hoffmann    ████████████████████ 97%  ●
Emma Schulz     ███████████████████  94%  ●
Sophie Meier    █████████████████    89%  ●
Jan Weber       █████████████        68%  ▲
Luca Bianchi    ██████████████       72%  ▲  
Finn Larsen     ████████             41%  ▼
```

**Comment Intelligence Panel:**
- Tabs per creator (or select from dropdown)
- Shows: top positive themes | top negative themes | neutral
- Real comment examples (mocked)

**AI Global Insight box:**
> *"Portfolio sentiment dropped 6 points this week, driven primarily by Finn Larsen's campaign. Two creators (Finn Larsen, Jan Weber) are showing concerning negative comment patterns. Emma Schulz is a standout performer with 94% sentiment — consider increasing her campaign allocation."*

---

### SCREEN 8: Compliance Monitor

**Route:** `#compliance`

**Overview cards (top):**
- Overall compliance rate: 76%
- Fully compliant: 3/6 creators
- Hashtags missing: 2 creators
- Behind on posting: 2 creators
- Competitor detected: 1 creator

**Compliance Matrix Table:**
Rows = creators, Columns = compliance criteria. Include a "Story" column with a small info tooltip: "ℹ️ Story check: posted yes/no + brand mention only. View counts not available externally."

```
Creator        | Posts  | Stories | Hashtags | Mentions | No-Compete | View Rate | Sentiment | TOTAL
───────────────|────────|─────────|──────────|──────────|────────────|───────────|───────────|──────
Mia Hoffmann   |   ✅  |   ✅    |    ✅    |    ✅    |     ✅     |    ✅    |    ✅     |  100%
Emma Schulz    |   ✅  |   ✅    |    ✅    |    ✅    |     ✅     |    ✅    |    ✅     |  100%
Sophie Meier   |   ✅  |   ✅    |    ✅    |    ✅    |     ✅     |    ✅    |    ✅     |  100%
Jan Weber      |   ✅  |   ⚠️    |    ⚠️    |    ✅    |     ✅     |    ⚠️    |    ⚠️     |   67%
Luca Bianchi   |   ⚠️  |   ✅    |    ✅    |    ✅    |     ✅     |    ⚠️    |    ✅     |   60%
Finn Larsen    |   ❌  |   ❌    |    ✅    |    ❌    |     ❌     |    ❌    |    ❌     |   14%
```

Story column tooltip on hover: "We check: story posted within 24h ✓, brand @mention in story ✓, link sticker set ✓. View counts are only visible to the creator."

Click on any cell → shows detail tooltip/modal.

**Action Center (right sidebar):**
Quick actions per non-compliant creator:
- "Send automated reminder" button
- "Flag for review" button
- "Pause cooperation" button (destructive, styled red)

---

### SCREEN 9: Competitor Watch

**Route:** `#competitor-watch`

**Header:** "Competitor Intelligence"
Subtitle: "Monitoring 4 competitor brands across your creator portfolio"

**Watched Competitors:**
Tag pills showing: @rivalco | @competitorbeauty | @rivalsport | @techtreats
"+ Add competitor" button

**Detection Events:**
Timeline of detected competitor appearances:
```
[🔴 CRITICAL]  Finn Larsen posted content featuring @rivalco — May 21, 14:32
               Caption: "Loving this from @rivalco lately 🔥 #food"
               [View Post] [Contact Creator] [Escalate]

[⚠️ WARNING]   Jan Weber liked 3 posts from @rivalsport — May 20, 09:15
               Unusual activity pattern detected
               [Monitor] [Dismiss]

[ℹ️ INFO]      Emma Schulz mentioned @competitorbeauty in a comment reply — May 18
               Context: responding to follower question, not promotional
               [Review] [Mark Safe]
```

**Competitor Activity Overview:**
Which competitors are gaining traction with your creators' audiences?
Simple table with competitor name + mentions detected + creators affected + risk level.

---

### SCREEN 10: Active Campaigns

**Route:** `#campaigns`

**Campaign Cards (grid, 2 columns):**

Each card:
- Campaign name (large)
- Brand name (muted)
- Status badge (Active / Warning / Critical)
- Date range
- Progress bar: Posts done/required (e.g., 18/24)
- 3 stats: Creators | Budget Used | Avg. Sentiment
- Health indicator (green/amber/red)
- "View Details →" link

Clicking a campaign → Campaign Detail (inline expand or new screen)

**Campaign Detail view:**
- Full campaign metrics
- Creator list within campaign
- Posts timeline
- Budget breakdown
- AI campaign summary

---

### SCREEN 11: Performance

**Route:** `#performance`

**Date range selector:** Last 7 days | Last 30 days | Last 90 days | Custom

**Portfolio Performance Charts (SVG mock charts):**

1. **View Rate Trend** — line chart, 30 days, one line per creator (color-coded)
2. **Posts Published** — bar chart, daily count
3. **Sentiment Trend** — area chart, portfolio average
4. **Revenue Attribution** — horizontal bars, per creator

**Performance Table:**
All creators with: View Rate | Engagement | Sentiment | Posts | Revenue | vs. Target

**AI Performance Summary box:**
> *"This month's strongest performer is Mia Hoffmann with 11.2% view rate — 60% above portfolio average. Recommend rebalancing budget toward top performers. Finn Larsen's campaign is underperforming significantly and requires immediate intervention."*

---

### SCREEN 12: Settings — Integrations

**Route:** `#integrations`

**Integration Cards (grid):**

```
[Linkster]          Connected ✅     Last sync: 2 min ago        [Configure]
[Slack]             Connected ✅     #influencer-alerts          [Configure]
[Shopify]           BETA 🔶          Unlock revenue tracking     [Connect →]
[Google Sheets]     Not connected    Export data to Sheets       [Connect]
[Zapier]            Not connected    Automate workflows          [Connect]
[WhatsApp]          Not connected    Alert via WhatsApp          [Connect]
[Power BI]          Not connected    Advanced reporting          [Connect]
[Looker Studio]     Not connected    Dashboard export            [Connect]
```

Shopify card gets special treatment — slightly larger, with a feature teaser:
- BETA badge (amber pill, top right of card)
- Headline: "Shopify Revenue Tracking"
- Subtext: "Automatically pull orders per discount code. See real ROI per creator — no manual entry."
- Feature list (small, bulleted):
  - ✓ Revenue per influencer via discount code
  - ✓ Automatic daily sync
  - ✓ True ROI calculation
  - ✓ Top products per creator
- "Connect Shopify →" primary button
- Muted footer: "Requires unique discount code per creator"

Each integration card:
- Logo placeholder (colored square with icon)
- Name + description
- Status badge
- Action button

**Alert Preferences section (below):**
- Notification channel: [Slack selected]
- Alert for Critical: [toggle ON]
- Alert for Warning: [toggle ON]
- Alert for Info: [toggle OFF]
- Daily digest time: [08:00]
- "Save preferences" button

---

### SCREEN 13: Team Settings

**Route:** `#team`

**Team Members table:**
```
Avatar | Name          | Email                    | Role    | Last Active | Actions
SM     | Sandra Müller | sandra@glowco.de         | Admin   | Today       | ···
TK     | Thomas Klein  | thomas@glowco.de         | Editor  | Yesterday   | ···
LH     | Lisa Hartmann | lisa@agency-partner.com  | Viewer  | 3 days ago  | ···
```

Roles explained: Admin (full access) | Editor (manage creators) | Viewer (read only)

"Invite team member" button → inline form appears:
- Email input
- Role dropdown
- "Send invite" button

---

## Interaction Details

### Screen Navigation
```javascript
function showScreen(screenId) {
  document.querySelectorAll('.screen').forEach(s => s.style.display = 'none');
  document.getElementById(screenId).style.display = 'block';
  document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));
  document.querySelector(`[data-screen="${screenId}"]`).classList.add('active');
  window.scrollTo(0, 0);
}
```

### Key Interactions to Implement:
1. Login button → Dashboard
2. All sidebar nav items → correct screens
3. "Add Creator" → Add Creator screen with working multi-step form
4. Search in Add Creator → simulate loading (300ms) → show mock result
5. Creator table rows → Creator Detail (show Mia Hoffmann for all clicks, or match by id)
6. Alert "Mark read" → visual update (mute row)
7. Portfolio search input → filter creator list in real-time
8. Tab switching in Creator Detail → show/hide tab content
9. Compliance Monitor cell hover → tooltip with details
10. Campaign cards → expand to show campaign detail inline

### Simulated AI Analysis
When on AI Report or Sentiment tabs, show a "Generating AI report..." loading state (1.5s) then reveal content. Use `setTimeout` to simulate.

---

## SVG Charts

Build all charts as inline SVG. No external chart libraries needed.

### Bar Chart Pattern:
```svg
<svg viewBox="0 0 400 200" xmlns="http://www.w3.org/2000/svg">
  <!-- Grid lines -->
  <line x1="0" y1="160" x2="400" y2="160" stroke="#E4E4E7" stroke-width="1"/>
  <!-- Bars -->
  <rect x="20" y="60" width="40" height="100" fill="#0066FF" rx="4"/>
  <!-- Labels -->
  <text x="40" y="180" text-anchor="middle" font-size="11" fill="#A1A1AA">Mon</text>
</svg>
```

### Line Chart Pattern:
Use `<polyline>` or `<path>` with calculated points based on mock data.

### Progress Arc Pattern (Health Score):
Use `<circle>` with `stroke-dasharray` and `stroke-dashoffset` for circular progress indicators.

---

## Empty States

Every list/table should have a beautiful empty state if filtered to zero results:
- Centered icon (large, muted)
- Headline: "No creators found"
- Subtext: "Try adjusting your filters or add a new creator"
- CTA button

---

## Technical Requirements

- **Single HTML file** — all CSS in `<style>`, all JS in `<script>`, inline SVG charts
- **No external JS libraries** — vanilla JS only (exception: Google Fonts via CDN)
- **No dark mode** — light only, hardcoded
- **Responsive down to 1280px** — no mobile optimization needed (SaaS tool)
- **Performance** — no heavy animations, smooth 60fps transitions
- **Clickdummy fidelity** — every nav item works, key interactions work, data is consistent throughout

---

## File Naming

Save as: `creatorpulse-mvp.html`

---

## Quality Checklist

Before finishing, verify:
- [ ] Login screen works, clicking sign in goes to dashboard
- [ ] All 13 screens accessible from sidebar
- [ ] Mock data is consistent (same creators/numbers throughout)
- [ ] No broken/empty screens
- [ ] Search in portfolio filters creators in real-time
- [ ] Creator detail shows correct data
- [ ] Charts render properly (SVG)
- [ ] Alert badges show correct counts
- [ ] Add Creator multi-step works
- [ ] Tabs in creator detail all have content
- [ ] Integrations screen shows all tools
- [ ] Design is consistent (fonts, colors, spacing) throughout
- [ ] No console errors

---

*End of spec. Build this as one complete, polished HTML file.*
