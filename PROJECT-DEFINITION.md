# AbacCondo v2 — Project Definition & UI Strategy

## 1. What We're Building

**AbacCondo** is a student housing marketplace for ABAC (Assumption University) students to find, compare, and inquire about condos near campus.

**Current state:** Airbnb-clone MVP with basic listing grid, single-image detail pages, category filters, and an inquiry form. Functional but lacks the **depth of information** students need to make confident housing decisions.

**Target state:** A professional, information-rich housing platform that reduces decision anxiety by giving students everything they need — pricing breakdowns, real photos, amenities, neighborhood context, and social proof — without ever leaving the site.

---

## 2. User Personas

### Primary: The Searching Student (80% of traffic)
- **Who:** ABAC undergraduate/graduate, 18-25, Thai or international
- **Goal:** Find affordable, safe housing close to campus — fast
- **Pain points:**
  - Doesn't know the area (especially international students)
  - Scared of hidden costs (deposits, utilities, internet)
  - Can't tell from one photo if a place is good
  - No way to compare options side-by-side
  - Doesn't know which neighborhoods are safe/convenient
  - Language barrier for some international students
- **Behavior:** Browses on mobile (70%+), compares 3-5 options, shares links with parents, makes decision within 1-2 weeks

### Secondary: The Landlord/Agent (posts listings)
- **Who:** Condo owner, property agent, or existing tenant subletting
- **Goal:** Fill vacancy quickly with reliable tenants
- **Pain points:**
  - Doesn't want to answer the same questions repeatedly
  - Wants qualified leads, not tire-kickers

### Tertiary: The Parent
- **Who:** Parent helping child find housing remotely
- **Goal:** Verify safety, cost, and quality
- **Behavior:** Views shared links on desktop, focuses on pricing, location safety, and contact info

---

## 3. User Behavior Analysis

### What Students Actually Do When Searching for Housing

```
AWARENESS          RESEARCH              COMPARISON         DECISION           ACTION
─────────────────────────────────────────────────────────────────────────────────────
"I need a condo"   "What's near ABAC?"   "A vs B vs C"     "This one looks     "Contact
 near campus"       "How much?"           "Which is          good, but I need    landlord"
                    "Is it safe?"          closer?"           to confirm          "Visit"
                    "What's included?"    "Price vs value?"   details"           "Sign lease"
```

### Critical Moments (where current UI fails)

| Moment | What User Needs | Current UI Provides | Gap |
|--------|----------------|--------------------|----|
| First landing | Trust signals, clear value prop | Generic Airbnb-style grid | No ABAC-specific messaging, no social proof |
| Browsing listings | Quick scan of key facts | Image + price + title | Missing: room size, utilities included?, furnished?, floor |
| Viewing a listing | Full decision-making info | 1 photo, auto-generated description, basic specs | No photo gallery, no real description, no amenities list, no cost breakdown |
| Comparing options | Side-by-side view | Nothing — must open tabs | No compare feature, no standardized data |
| Sharing with parents | Professional, trustworthy page | Basic listing page | Looks like a student project, not a platform parents trust |
| Contacting landlord | Confidence they'll respond | Inquiry form | No response time indicator, no verified badge |

---

## 4. Information Architecture — What Each Listing MUST Show

### Tier 1: Essential (above the fold)
- **Photo gallery** (5+ photos: exterior, bedroom, bathroom, kitchen, common areas)
- **Price** with breakdown: rent + utilities + internet + deposit
- **Location** with walking/driving time to ABAC campus
- **Room specs**: size (sqm), floor, bedrooms, bathrooms, furnished?
- **Availability**: move-in date

### Tier 2: Important (scrollable)
- **Amenities checklist**: WiFi, A/C, washing machine, gym, pool, parking, 7-Eleven nearby, shuttle
- **Building info**: security, CCTV, key card access, building age
- **Neighborhood context**: nearest BTS/MRT, convenience stores, restaurants
- **Utilities estimate**: typical monthly water + electric cost
- **Contract terms**: minimum lease, deposit amount, advance payment
- **Landlord info**: response time, verified status

### Tier 3: Nice to have
- **Student reviews** from past tenants
- **Similar listings** for comparison
- **Price history / trend** for the area

---

## 5. User Flows

### Flow 1: First-Time Student Visitor

```
Landing Page (index.html)
│
├── Hero: "Find Your Perfect Condo Near ABAC"
│   └── Search bar: [Location/Keyword] [Price Range] [Move-in Date]
│
├── Trust Bar: "500+ students housed" · "Verified listings" · "Free forever"
│
├── Quick Filters: Walking Distance | Short Ride | Budget | New | Furnished
│
├── Featured Listings Grid
│   └── Card shows: Photo · Price · Title · Distance · Key specs (sqm, bed, bath)
│       └── Click → Listing Detail Page
│
├── Area Guide Section: "Neighborhoods Near ABAC"
│   └── Cards: Bearing | Bangna | Samrong — with avg price, vibe description
│
└── CTA: "Can't decide? Tell us your budget and we'll help" → Quick inquiry form
```

### Flow 2: Listing Detail (the money page)

```
Listing Detail Page (listing.html?id=X)
│
├── Photo Gallery (swipeable, 5+ images)
│   └── Fullscreen lightbox on tap
│
├── Header: Title · Location · Verified badge · Share button
│
├── Key Facts Bar: ฿8,500/mo · 28 sqm · Floor 12 · 1 Bed · Furnished
│
├── [LEFT COLUMN]
│   ├── Description (real text, not auto-generated)
│   ├── Amenities Grid (icons + labels)
│   │   └── WiFi ✓ | A/C ✓ | Washing ✓ | Pool ✓ | Gym ✗ | Parking ✓
│   ├── Cost Breakdown Card
│   │   └── Rent: ฿8,500 | Electric: ~฿800 | Water: ~฿150 | Internet: included
│   │   └── Deposit: 2 months | Advance: 1 month
│   ├── Location & Neighborhood
│   │   └── Map + "5 min walk to ABAC Gate 1" + nearby landmarks
│   ├── Building Info
│   │   └── Year built · Total floors · Security type · Shuttle service
│   └── Student Reviews (if any)
│
├── [RIGHT COLUMN — sticky]
│   ├── Price Card: ฿8,500/mo
│   ├── Availability: "Available from May 1, 2026"
│   ├── Quick Contact: [Name] [Phone/LINE] [Message]  → Send Inquiry
│   ├── "Response time: Usually within 2 hours"
│   └── Get Directions from ABAC
│
└── Similar Listings Carousel at bottom
```

### Flow 3: Browse & Compare

```
Explore Page (explore.html)
│
├── Split View: Map (left) + Listings (right)
│
├── Filters Bar (top of listing panel):
│   ├── Price Range Slider: ฿3,000 – ฿15,000
│   ├── Room Type: Studio | 1-Bed | 2-Bed
│   ├── Distance: Walking | < 5 min ride | < 10 min ride
│   ├── Amenities: Pool, Gym, Furnished (multi-select)
│   └── Sort: Price ↑↓ | Distance | Rating | Newest
│
├── Listing Cards (enriched):
│   └── Photo · Title · ฿Price · 28sqm · 1bed · "Furnished · Pool"
│
├── Compare Mode (NEW):
│   └── Select 2-3 listings → side-by-side table:
│       Price | Size | Distance | Amenities | Utilities
│
└── Map Interaction:
    └── Click pin → popup card → "View Details" or "Add to Compare"
```

### Flow 4: Mobile-First Student Journey

```
Mobile Home → Category Tap → Scroll listings → Tap card
→ Photo swipe → Scroll details → Tap "Send Inquiry"
→ Fill quick form (name, LINE ID, message)
→ Success: "We'll connect you within 2 hours"
```

---

## 6. UI Design Upgrades — Priority List

### P0: Critical (do first)
1. **Listing detail page overhaul** — photo gallery, amenities grid, cost breakdown, real descriptions
2. **Listing cards enrichment** — show sqm, bed/bath count, "Furnished" tag
3. **Trust signals** — "Verified" badges, student count, response time
4. **Better search/filters** — price range, room type, amenities filter

### P1: Important
5. **Area/neighborhood guide section** on homepage
6. **Compare feature** — select & compare 2-3 listings
7. **Cost breakdown card** on listing detail (rent + utilities + deposit)
8. **Similar listings** carousel on detail page
9. **Better mobile listing cards** with swipeable photos

### P2: Nice to Have
10. **Student reviews** system
11. **Saved/favorited listings** (currently no persistence)
12. **LINE integration** for contact (most Thai students use LINE)
13. **Thai language toggle**
14. **Virtual tour / 360 photo** support
15. **Roommate matching** feature

---

## 7. Design Direction

### Current: Airbnb clone (coral/orange, playful)
### Target: **Professional + Friendly + Informative**

**Visual principles:**
- Clean white backgrounds with structured information cards
- Larger typography for key facts (price, size, distance)
- Icon-based amenities grid (scannable at a glance)
- Photo gallery as the hero element (not a single image)
- Trust indicators: verified badges, green "available" tags, response time
- Progressive disclosure: key facts first, details on scroll

**Color refinement:**
- Keep coral (#FF5A5F) as accent/CTA
- Add a professional navy/dark tone for headings and trust elements
- Use green for availability/verified states
- More white space, less visual clutter

**Typography:**
- Keep Nunito but use weight more intentionally
- 800 for prices and titles only
- 600 for labels and key info
- 400 for body text

---

## 8. Database Schema Needs

Current `listings` columns need expansion for information-rich UI:

```
NEW COLUMNS NEEDED:
├── size_sqm          (integer — room size in square meters)
├── floor_number      (integer)
├── total_floors      (integer — building height)
├── bedrooms          (integer)
├── bathrooms         (integer)
├── is_furnished      (boolean)
├── deposit_months    (integer — typically 1-2)
├── min_lease_months  (integer — minimum contract)
├── available_date    (date)
├── electric_estimate (integer — ฿/month estimate)
├── water_estimate    (integer — ฿/month estimate)
├── internet_included (boolean)
├── description       (text — real description, not auto-generated)
├── amenities         (jsonb — {"pool": true, "gym": false, "parking": true, ...})
├── photos            (jsonb — array of image URLs for gallery)
├── line_id           (text — landlord LINE contact)
├── verified          (boolean)
├── building_name     (text — e.g. "Lumpini Ville Bangna")
├── neighborhood      (text — e.g. "Bearing", "Bangna", "Samrong")
└── year_built        (integer)
```

---

## 9. Next Steps

1. **Align on scope** — which P0 items to tackle first?
2. **Update database schema** in Supabase with new columns
3. **Redesign listing detail page** (biggest impact on user satisfaction)
4. **Enrich listing cards** on homepage
5. **Add filters** on explore page
6. **Populate data** — update existing listings with new fields

Ready to start building when you are.
