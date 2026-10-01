# Merchify

# Listing Readiness Engine

> Turn a random product photo into a marketplace-ready image, and learn exactly why the original wasn't ready.

**Live demo:** <deployed link>
**Demo video:** <video link>
**Hackathon:** Cloudinary AI Hackathon, PS-01 (AI media pipeline)

## Problem
Small online sellers shoot products on their phones with messy backgrounds,
hands in the frame and inconsistent framing. Marketplaces expect clean,
standardised images, and sellers rarely know what is wrong with a photo.

## Solution
Upload a raw photo. The app scores it out of 100 with clear reasons, fixes it
automatically, scores it again, and exports it in a marketplace preset.

## Screenshots
<before/after screenshot>
<score and reasons screenshot>

## How it works
Upload -> Score and reasons -> Remove obstacles -> Remove background ->
Centre on white square -> Optimise delivery -> Re-score -> Export

## How Cloudinary is used
| Feature | Where we use it |
|---|---|
| Upload API | Receives the seller photo; returns size and format used in scoring |
| Generative Remove | Removes hands and unwanted objects |
| AI Background Removal | Isolates the product |
| Trim and pad transformations | Centres the product on a pure white square |
| f_auto / q_auto | Optimised delivery of the final image |

## How the score works
| Rule | Points |
|---|---|
| Resolution meets preset minimum | <points> |
| Background is clean / white | <points> |
| Product fills target share of frame | <points> |
| Square canvas | <points> |

Marketplace rules live in `lib/presets.json`. Adding a new marketplace is
one new entry. Sources: <official links>

## Tech stack
<Next.js, Node, Cloudinary SDK, sharp, deployed on Vercel/Netlify>

## Setup
1. Clone: `git clone <repo link>` and `cd listing-readiness-engine`
2. Install: `npm install`
3. Create `.env.local` in the project root:
```
   CLOUDINARY_CLOUD_NAME=
   CLOUDINARY_API_KEY=
   CLOUDINARY_API_SECRET=
```
4. Run: `npm run dev` and open http://localhost:3000

## Limitations
- Free Cloudinary plan has limited credits, so each photo is processed once and cached.
- Generative Remove can struggle with complex or overlapping objects.
- Marketplace rules are our reading of official guidelines and may change.

## Team
- <Name> - Cloudinary and backend
- <Name> - Frontend
- <Name> - Quality, rules and pitch
