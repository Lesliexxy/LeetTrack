# LeetTrack

**SM-2 spaced repetition for LeetCode.**

LeetTrack is a free, open-source web app that helps you systematically review LeetCode problems using the SM-2 spaced repetition algorithm — the same algorithm that powers Anki. It runs entirely in the browser with optional cloud sync via Firebase, so your data is never lost.

**Live app → [lesliexxy.github.io/LeetTrack](https://lesliexxy.github.io/LeetTrack)**

---

## Why LeetTrack?

Grinding LeetCode without a system leads to wasted time re-solving problems you've already forgotten. LeetTrack solves this by:

- **Scheduling reviews automatically** — the SM-2 algorithm calculates when you'll start forgetting a problem and schedules it right before that happens
- **Prioritizing weak spots** — problems you rate as difficult get shorter intervals; easy ones space out to weeks or months
- **Keeping daily load manageable** — set a daily limit so you never feel overwhelmed
- **Letting you focus by topic** — filter your queue by topic (Tree, Graph, DP, etc.) or difficulty (Easy/Medium/Hard) for targeted study sessions

---

## How the SM-2 Algorithm Works

After each review, you rate your recall from 1 (blank) to 5 (easy). The algorithm adjusts two values:

**Ease Factor (EF):** starts at 2.5 and moves up or down based on your rating. Higher EF = the problem is getting easier for you.

```
EF(new) = max(1.3, EF + 0.1 − (5 − rating) × (0.08 + (5 − rating) × 0.02))
```

**Interval:** the number of days until your next review. If you rate ≥ 3, the interval grows exponentially. If you rate 1–2, it resets to 1 day.

```
Rating 1–2  →  interval resets to 1 day (review tomorrow)
Rating 3    →  interval grows slowly
Rating 4–5  →  interval = previous interval × EF
```

A typical progression: Day 1 → Day 3 → Day 7 → Day 16 → Day 38 → ...

---

## Features

### Today's Queue
Your daily review list, auto-generated from the SM-2 schedule. Rate each problem after reviewing it and the next date recalculates instantly.

### 14-Day Schedule
See what's coming up across the next two weeks. New introductions are marked in blue, reviews in purple.

### Add Questions
Add any LeetCode problem by number, title, topic, and difficulty. It drops into your queue immediately.

### Progress Dashboard
Track mastered vs. needs-work counts, total review sessions, and topic-by-topic breakdowns.

### Settings
- **Daily review limit** — slider from 1 to 20 questions per day
- **Topic filter** — toggle topics on/off to focus your queue
- **Difficulty filter** — include or exclude Easy, Medium, Hard
- **Active pool preview** — see exactly which questions match your filters

### Cloud Sync (Firebase)
- Sign in with Google or email/password
- All data syncs to Firestore automatically
- Works offline and syncs when reconnected
- Switch devices without losing progress

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Vanilla HTML/CSS/JS — no build step, no framework |
| Fonts | Outfit + JetBrains Mono (Google Fonts) |
| Auth | Firebase Authentication (Google + email/password) |
| Database | Cloud Firestore with offline persistence |
| Hosting | GitHub Pages (free) |
| Algorithm | SM-2 (SuperMemo 2) spaced repetition |

The entire app is a single `index.html` file. No dependencies, no bundler, no npm install.

---

## Getting Started

### Use it now
Visit **[lesliexxy.github.io/LeetTrack](https://lesliexxy.github.io/LeetTrack)**, create an account, and start adding problems.

### Install on your phone
1. Open the link above in Safari (iPhone) or Chrome (Android)
2. **iPhone:** tap Share → "Add to Home Screen"
3. **Android:** tap the 3-dot menu → "Add to Home screen"

It opens full-screen like a native app.

### Run locally
```bash
git clone https://github.com/Lesliexxy/LeetTrack.git
cd LeetTrack
# Open index.html in any browser — that's it
open index.html
```

---

## Responsive Design

The app adapts between desktop and mobile:

- **Desktop (>768px):** sidebar navigation with streak counter
- **Mobile (≤768px):** bottom tab bar with compact cards

---

## Data & Privacy

- Your data is stored in Firebase Firestore, scoped to your user account
- Firestore security rules ensure you can only read/write your own data
- No analytics, no tracking, no ads
- The app works offline using Firestore persistence + localStorage fallback

---

## Roadmap

- [ ] Import/export question pool as JSON or CSV
- [ ] Bulk add from LeetCode problem lists (e.g. Blind 75, Grind 169)
- [ ] Review history charts and learning curve visualization
- [ ] Shared study groups with leaderboard
- [ ] Dark/light theme toggle

---

## Contributing

Pull requests welcome. The app is a single HTML file, so the barrier to entry is low:

1. Fork the repo
2. Edit `index.html`
3. Test locally by opening in a browser
4. Submit a PR

---

## License

MIT — free for personal and commercial use.

---

Built by [Leslie Xu](https://github.com/Lesliexxy) to stop forgetting LeetCode solutions.
