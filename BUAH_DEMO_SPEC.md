# buah Influencer Monitor — Demo Clickdummy
## Slim internal tool, single HTML file

---

## Context

This is a focused demo for buah.de (gefriergetrocknete Früchte, German health snack brand).
Build a single HTML file that shows exactly what this tool does for their team.
NO login. NO user management. NO settings. Opens directly in the dashboard.

Same design system as CreatorPulse spec (DM Sans, clean white, --accent: #0066FF) but:
- Use buah.de branding: logo in top left: `https://buah.de/cdn/shop/files/Buah_logo.png?v=1695722756`
- Topbar: buah logo (left) + "Influencer Monitor" label (muted, next to logo) + "Powered by CreatorPulse" pill (right, subtle grey)
- Brand accent color alongside blue: use buah's warm natural tones as secondary (soft orange #F97316 for health/nature accents in the UI where fitting)

---

## 3 Screens Only

Navigation: 3 tabs in a clean topbar (not sidebar — simpler):
`Dashboard` | `Creators` | `Alerts`

No sidebar. Just top navigation tabs. Clean and simple.

---

## Mock Data — buah.de Influencer Portfolio

6 German/Austrian/Swiss food & health influencers. All data is realistic for this niche.

```javascript
const CREATORS = [
  {
    id: 1,
    name: "Lena Bachmann",
    handle: "@lena.eats.clean",
    platform: "Instagram",
    avatar: "https://www.loremfaces.net/96/id/7.jpg",
    followers: 94200,
    niche: "Healthy Snacking",
    status: "active",
    health_score: 92,
    view_rate: 8.7,
    engagement_rate: 5.1,
    sentiment_score: 94,
    last_post: "vor 3h",
    last_post_img: "https://images.unsplash.com/photo-1490645935967-10de6ba17061?w=400&h=400&fit=crop",
    posts_this_week: 3,
    compliance: 100,
    discount_code: "LENA15",
    red_flags: [],
    last_caption: "Mein absoluter Lieblingssnack gerade: @buah_de Gefriergetrocknete Erdbeeren 🍓 Süß, knusprig, 0 Zuckerzusatz — ich bin obsessed! #buah #healthysnacks #gefriergetrocknet",
    hashtag_ok: true,
    mention_ok: true,
    comments: [
      { user: "sarah_healthy", text: "Wo kann ich das kaufen?? 😍", sentiment: "positive" },
      { user: "snack.queen.de", text: "Die esse ich jeden Tag! Absolut empfehlenswert", sentiment: "positive" },
      { user: "fitgirl.munich", text: "Code LENA15 funktioniert, gerade bestellt! 🙌", sentiment: "positive" },
      { user: "healthy.mama.2", text: "Sind die auch für Kinder geeignet?", sentiment: "neutral" },
      { user: "erdbeer.lover", text: "Meine Kinder lieben die! Schon 3x bestellt", sentiment: "positive" }
    ],
    ai_summary: "Lena's Audience zeigt starke Kaufabsicht — 'Wo kaufen?' und Code-Verwendung in 18% der Kommentare. Die Produktintegration wirkt authentisch. Sentiment stabil bei 94%. Empfehlung: Weiter buchen, Budget erhöhen."
  },
  {
    id: 2,
    name: "Tobias Kramer",
    handle: "@tobi.fitlife",
    platform: "TikTok",
    avatar: "https://www.loremfaces.net/96/id/15.jpg",
    followers: 187400,
    niche: "Fitness & Nutrition",
    status: "warning",
    health_score: 61,
    view_rate: 5.3,
    engagement_rate: 3.2,
    sentiment_score: 71,
    last_post: "vor 42h",
    last_post_img: "https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8b?w=400&h=400&fit=crop",
    posts_this_week: 1,
    compliance: 55,
    discount_code: "TOBI10",
    red_flags: ["posting_behind", "hashtag_missing"],
    last_caption: "Pre-Workout Snack Ideen für mehr Energie 💪 Was esst ihr vor dem Training?",
    hashtag_ok: false,
    mention_ok: false,
    comments: [
      { user: "gym.bro.berlin", text: "Guter Content aber wo ist der buah Link?", sentiment: "neutral" },
      { user: "fitness.anna", text: "Schöner Post aber du hast buah vergessen zu taggen 😅", sentiment: "neutral" },
      { user: "sporty.kai", text: "Das Training sieht gut aus!", sentiment: "positive" }
    ],
    ai_summary: "⚠️ Tobi hat diese Woche nur 1 von 3 vereinbarten Posts geliefert. #buah und @buah_de fehlen im letzten Post komplett. View Rate 5,3% liegt unter dem Ziel von 7%. Sofortiger Reminder empfohlen."
  },
  {
    id: 3,
    name: "Marie Sommer",
    handle: "@marie.plantbased",
    platform: "Instagram",
    avatar: "https://www.loremfaces.net/96/id/22.jpg",
    followers: 52800,
    niche: "Plant-based & Vegan",
    status: "active",
    health_score: 89,
    view_rate: 9.4,
    engagement_rate: 7.2,
    sentiment_score: 96,
    last_post: "vor 6h",
    last_post_img: "https://images.unsplash.com/photo-1512621776951-a57141f2eefd?w=400&h=400&fit=crop",
    posts_this_week: 2,
    compliance: 100,
    discount_code: "MARIE20",
    red_flags: [],
    last_caption: "Smoothie Bowl Upgrade mit @buah_de Gefrierfrüchten 🫐✨ Farbe, Crunch und 100% Natur — was will man mehr? #buah #plantbased #vegansnacks #gefriergetrocknet",
    hashtag_ok: true,
    mention_ok: true,
    comments: [
      { user: "vegan.vibes.de", text: "Das sieht unglaublich aus 😍 Rezept?", sentiment: "positive" },
      { user: "plant.power.girl", text: "Marie empfiehlt = ich kaufe. Bestellt! ✅", sentiment: "positive" },
      { user: "green.living.lu", text: "Endlich mal Snacks ohne Mist drin 🙌", sentiment: "positive" },
      { user: "smoothie.queen.hh", text: "Welche Früchte hast du genommen?", sentiment: "neutral" }
    ],
    ai_summary: "Marie ist die stärkste Micro-Influencerin im Portfolio. Engagement Rate 7,2% — fast dreimal über Branchendurchschnitt. Ihre vegane Community passt perfekt zu buah's 0% Zuckerzusatz-Positionierung. Sehr empfehlenswert für weiteren Ausbau."
  },
  {
    id: 4,
    name: "Felix Hartmann",
    handle: "@felix.snacktime",
    platform: "TikTok",
    avatar: "https://www.loremfaces.net/96/id/31.jpg",
    followers: 341000,
    niche: "Food & Snacks",
    status: "critical",
    health_score: 28,
    view_rate: 2.9,
    engagement_rate: 1.4,
    sentiment_score: 38,
    last_post: "vor 5 Tagen",
    last_post_img: "https://images.unsplash.com/photo-1504674900247-0877df9cc836?w=400&h=400&fit=crop",
    posts_this_week: 0,
    compliance: 15,
    discount_code: "FELIX10",
    red_flags: ["no_post_48h", "sentiment_negative", "view_rate_low", "competitor_detected"],
    last_caption: "Die neuen Snacks von @naturebox sind mega 🔥 #snacks #food",
    hashtag_ok: false,
    mention_ok: false,
    comments: [
      { user: "snack.critic.de", text: "Du machst Werbung für jeden der zahlt oder? 🙄", sentiment: "negative" },
      { user: "food.real.talk", text: "Erst buah, jetzt naturebox — macht dich das nicht unglaubwürdig?", sentiment: "negative" },
      { user: "disappointed.fan", text: "Du hast schon buah promoted und jetzt den Konkurrenten?", sentiment: "negative" },
      { user: "just.a.viewer", text: "Content wird schlechter seit Monaten", sentiment: "negative" }
    ],
    ai_summary: "🚨 KRITISCH. Felix hat 5 Tage nicht gepostet und hat im letzten Post Konkurrenz-Brand @naturebox erwähnt — klarer Vertragsverstoß. Sentiment auf 38% gefallen durch Community-Kritik. Sofortiges Gespräch notwendig. Kooperation überdenken."
  },
  {
    id: 5,
    name: "Jana Wolf",
    handle: "@jana.gesundleben",
    platform: "Instagram",
    avatar: "https://www.loremfaces.net/96/id/44.jpg",
    followers: 128600,
    niche: "Gesund Leben & Familie",
    status: "active",
    health_score: 87,
    view_rate: 7.8,
    engagement_rate: 4.6,
    sentiment_score: 91,
    last_post: "vor 1h",
    last_post_img: "https://images.unsplash.com/photo-1490474418585-ba9bad8fd0ea?w=400&h=400&fit=crop",
    posts_this_week: 3,
    compliance: 95,
    discount_code: "JANA10",
    red_flags: [],
    last_caption: "Gesunder Schulranzen-Snack für die Kinder 🎒 @buah_de Gefrierfrüchte sind unser Favorit — kein Zuckerzusatz, echte Früchte, meine Kinder lieben sie! #buah #gesundleben #kindernacks",
    hashtag_ok: true,
    mention_ok: true,
    comments: [
      { user: "mama.gesund.de", text: "Gerade bestellt für die Schulbox meiner Tochter! 😍", sentiment: "positive" },
      { user: "familie.zuhause", text: "Endlich gesunde Snacks die Kinder auch mögen 🙌", sentiment: "positive" },
      { user: "eltern.tipps.de", text: "Code JANA10 funktioniert! Danke für den Tipp", sentiment: "positive" },
      { user: "healthy.family.at", text: "Welche Früchte empfiehlst du für Kinder?", sentiment: "neutral" }
    ],
    ai_summary: "Jana erreicht eine besonders kaufstarke Zielgruppe: Eltern die gesunde Kindersnacks suchen. 'Für die Schulbox bestellt' ist ein häufiges Kommentarmuster — direkte Kaufkonversion. Gut für buah's Familienpositionierung."
  },
  {
    id: 6,
    name: "Nico Berg",
    handle: "@nicoberg.running",
    platform: "TikTok",
    avatar: "https://www.loremfaces.net/96/id/52.jpg",
    followers: 73200,
    niche: "Running & Endurance",
    status: "warning",
    health_score: 63,
    view_rate: 6.1,
    engagement_rate: 3.8,
    sentiment_score: 74,
    last_post: "vor 28h",
    last_post_img: "https://images.unsplash.com/photo-1476480862126-209bfaa8edc8?w=400&h=400&fit=crop",
    posts_this_week: 2,
    compliance: 70,
    discount_code: "NICO15",
    red_flags: ["view_rate_low", "hashtag_missing"],
    last_caption: "Marathon-Prep Woche 3 — Ernährung ist alles! Meine Go-To Snacks für langen Läufe 🏃 @buah_de dabei natürlich",
    hashtag_ok: false,
    mention_ok: true,
    comments: [
      { user: "runner.berlin.de", text: "Welche Früchte nimmst du auf langen Läufen?", sentiment: "neutral" },
      { user: "marathon.mama", text: "Super Tipp! Werde ich ausprobieren vor dem nächsten Halbmarathon", sentiment: "positive" },
      { user: "trail.runner.at", text: "Gutes Content aber Hashtag fehlt 😄", sentiment: "neutral" }
    ],
    ai_summary: "Nico's Running-Audience ist klein aber sehr spezifisch und konversionsstark. #buah fehlt im letzten Post. View Rate 6,1% knapp unter Ziel. Reminder senden, dann beobachten."
  }
];
```

---

## Alerts Data

```javascript
const ALERTS = [
  { id: 1, severity: "critical", creator: "Felix Hartmann", handle: "@felix.snacktime", message: "Kein Post seit 5 Tagen — Vereinbarung: 3x pro Woche", time: "vor 2h", read: false },
  { id: 2, severity: "critical", creator: "Felix Hartmann", handle: "@felix.snacktime", message: "Konkurrenz-Brand @naturebox im letzten Post erwähnt — Vertragsverstoß", time: "vor 5h", read: false },
  { id: 3, severity: "critical", creator: "Felix Hartmann", handle: "@felix.snacktime", message: "Sentiment auf 38% gefallen — negative Community-Reaktion", time: "vor 6h", read: false },
  { id: 4, severity: "warning", creator: "Tobias Kramer", handle: "@tobi.fitlife", message: "Nur 1/3 Posts diese Woche — Reminder gesendet", time: "vor 8h", read: false },
  { id: 5, severity: "warning", creator: "Tobias Kramer", handle: "@tobi.fitlife", message: "#buah und @buah_de fehlen im letzten TikTok", time: "vor 10h", read: true },
  { id: 6, severity: "warning", creator: "Nico Berg", handle: "@nicoberg.running", message: "#buah Hashtag fehlt im letzten Post", time: "vor 14h", read: true },
  { id: 7, severity: "info", creator: "Marie Sommer", handle: "@marie.plantbased", message: "Beste Engagement Rate der Woche: 7,2% — Ausreißer nach oben", time: "vor 1 Tag", read: true },
  { id: 8, severity: "info", creator: "Lena Bachmann", handle: "@lena.eats.clean", message: "Discount-Code LENA15 wurde 34x diese Woche verwendet", time: "vor 1 Tag", read: true }
];
```

---

## Screen 1: Dashboard (default, opens immediately)

**Topbar:**
- Left: buah logo (img tag, height 32px) + "Influencer Monitor" (muted label, 13px)
- Right: "Powered by CreatorPulse" grey pill + notification bell with badge "3" (unread criticals)

**Alert Banner (always visible, red strip):**
`🚨 3 kritische Alerts — Felix Hartmann benötigt sofortige Aufmerksamkeit` [Jetzt ansehen →]

**4 KPI Cards:**
```
Aktive Creator  |  Ø Health Score  |  Posts heute  |  Ø View Rate
     6          |      70%         |      3        |    6.7%
  4 aktiv       |  ↓ von 78%       |  2 ausstehend |  Ziel: 7%
```

**Creator Status Overview (main content):**
Clean table/list, all 6 creators:

Each row:
- Avatar (circle img, 40px)
- Name + handle (two lines)
- Platform badge (IG orange-tinted / TT black-tinted, small pill)
- Health Score: colored number + thin progress bar (green >80, amber 50-80, red <50)
- View Rate: number + small arrow up/down
- Sentiment: number + colored dot
- Last Post: time ago
- Posts/Week: "3/3 ✅" or "1/3 ⚠️" or "0/3 ❌"
- Compliance: colored percentage
- Status badge: Aktiv (green) / Warnung (amber) / Kritisch (red)
- "Details →" link (goes to Creator Detail inline)

**Bottom: Last 3 Alerts preview**
Small, compact. "Alle Alerts ansehen →" link.

---

## Screen 2: Creators

Header: "Creator Portfolio" + "6 Creators" + search input

**Creator Cards Grid (2 columns, 3 rows):**

Each card (more visual than table):
- Avatar photo (large, 56px circle) + name + handle + platform badge
- Health Score as a colored arc/ring (SVG)
- 3 stat pills: View Rate | Engagement | Sentiment
- Compliance bar
- Status badge
- Last post thumbnail (small, 48x48px rounded) + caption preview (truncated, 60 chars)
- Red flag tags if any (small red pills): "Kein Post", "Hashtag fehlt", "Konkurrenz detected"
- "Details ansehen" button

Clicking "Details ansehen" → opens an inline detail panel (slide-in from right, overlay style, 480px wide):

**Creator Detail Panel:**

Header: Avatar (large, 72px) + name + handle + status + health score ring

Tabs: Übersicht | Letzter Post | Kommentare & Sentiment | AI Analyse

**Tab: Übersicht**
- Stats grid: Follower, View Rate, Engagement, Sentiment, Posts diese Woche, Compliance
- Vereinbarung box: required hashtags, mentions, posting frequency, view rate target
- Discount code: "LENA15" with copy button (visual)

**Tab: Letzter Post**
- Post image (full width in panel, rounded)
- Caption text (full)
- Compliance checklist:
  - ✅/❌ Hashtag #buah vorhanden
  - ✅/❌ @buah_de erwähnt
  - ✅/❌ Kein Konkurrent erwähnt
- Stats: Likes | Comments | Est. Views
- Timestamp

**Tab: Kommentare & Sentiment**
- Big sentiment score (colored arc SVG) — e.g. "94%" with "Sehr positiv" label
- Sentiment breakdown: Positiv / Neutral / Negativ (3 bars)
- Comment list (from mock data):
  Each: avatar placeholder (loremfaces) + username + comment text + sentiment badge (grün/grau/rot)
- AI Sentiment Summary (blue tinted box):
  The ai_summary text from creator data

**Tab: AI Analyse**
Full ai_summary as the main text.
Then 2-3 "Empfehlungen" bullet points.
"Risiko" indicator (low/medium/high with colored dot).

---

## Screen 3: Alerts

Header: "Alert Center" + unread count badge

Filter tabs: Alle (8) | Kritisch (3) | Warnung (3) | Info (2)

Alert list — each item:
```
● [AVATAR 32px] Creator Name · @handle                    [vor 2h]  [×]
  Alert message text
  [Creator ansehen]  [Als gelesen markieren]
```
- Red dot = kritisch, amber = warnung, blue dot = info
- Unread: left colored border accent
- Read: slightly muted

Below list — small info box:
```
ℹ️ So funktioniert das Monitoring
Täglich um 08:00 Uhr werden alle Creator automatisch gecheckt:
• Apify scannt Instagram & TikTok auf neue Posts & Stories
• Claude AI analysiert Kommentare auf Sentiment
• Hashtag & Mention Compliance wird automatisch geprüft
• Bei Verstößen oder Red Flags erscheinen Alerts hier
```
This makes the tool feel real and explains the tech stack simply.

---

## Design Rules (same as main spec)

Fonts: DM Sans + JetBrains Mono for numbers
Colors: --accent #0066FF, all CSS vars from main spec
Cards: white, 1px border, subtle shadow, 12px radius
buah accent: use #F97316 (warm orange) sparingly for nature/food context — e.g. the "Powered by CreatorPulse" pill border, or small decorative elements. Not overused.
Topbar: white, 56px, border-bottom, sticky
Tab nav (top): clean underline-style active tab, no background tabs

---

## Key Interactions

1. Tab nav: Dashboard | Creators | Alerts — all work
2. Creator "Details" → slide-in panel from right (CSS transform translateX)
3. Panel tabs: Übersicht | Letzter Post | Kommentare | AI Analyse
4. Panel close button (×) closes panel
5. Alert "×" marks as read (visual mute)
6. Alert filter tabs filter the list
7. Search in Creators filters by name/handle in real-time
8. Alert Banner "Jetzt ansehen →" goes to Alerts tab

---

## Technical

- Single HTML file: `buah-influencer-monitor.html`
- Vanilla JS only
- No login screen (opens directly on dashboard)
- All data hardcoded in JS
- Mobile not needed (internal tool, desktop only, min 1280px)
- No external JS libraries (only Google Fonts CDN)

---

## What to tell the client this demo shows

The tool monitors automatically:
- ✅ Hat der Creator gestern gepostet? (via Apify Instagram/TikTok Scraper)
- ✅ Wurde der vereinbarte Hashtag verwendet? (Caption-Analyse)
- ✅ Wurde die Brand erwähnt? (@mention Check)
- ✅ Hat er einen Konkurrenten promoted? (Keyword-Detection)
- ✅ View Rate unter Schwellenwert? (öffentliche Post-Daten via Apify)
- ✅ Wie ist das Sentiment der Kommentare? (Claude AI Analyse)
- ✅ Alerts bei Verstößen (Slack / Email)

Everything shown in this demo is technically buildable with:
- Apify (Instagram + TikTok Scraper)
- Claude API (Sentiment Analysis)
- Python/FastAPI backend on Render (daily cron)
- This HTML as the frontend

---

*Build as: buah-influencer-monitor.html*
