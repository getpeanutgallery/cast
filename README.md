# Peanut Gallery Cast

**The faces behind the feedback.**

---

## What is The Cast?

The Cast is a collection of AI-generated personas who serve as your focus group. Each cast member has:
- A distinct personality and backstory
- Unique content consumption habits
- Specific expertise and perspectives
- Their own environment and visual style

Upload your content, get reactions from the people who matter most to your audience.

---

## How It Works

### For Developers (YAML Config)

Add a config file to your repo:

```yaml
cast_member: impatient-teenager
settings:
  patience_seconds: 3
  include_video: true
```

Run the emotion engine:
```bash
emotion-engine evaluate --persona impatient-teenager --input video.mp4
```

### For Marketers (GUI)

1. Upload or link your content
2. Get cast member recommendations based on your content type
3. Select your preferred cast member (or use the recommendation)
4. Hit "Go" and get your reaction report

---

## Meet the Cast

### Alex "The Scroller" Chen
**The Impatient Teenager**

- **Age:** 17
- **Platform:** TikTok, Reels, Shorts
- **Core Truth:** "I abandon content if the hook takes longer than 3 seconds"
- **Best For:** Testing viral potential, hook effectiveness, Gen Z appeal
- **Vibe:** Impatient, authentic, brutally honest, algorithm-literate

[View Alex's Profile →](./impatient-teenager/SOUL.md)

---

## Coming Soon

- More cast members (marketers, developers, creatives, strategists)
- Video reaction clips
- Custom cast member creation
- Team/enterprise features

---

## Tag System

Cast members are tagged for easy discovery:

**Demographics:** `age:teen`, `gen:z`, `location:urban`  
**Platforms:** `tiktok`, `youtube-shorts`, `instagram-reels`  
**Traits:** `impatient`, `authentic`, `brutally-honest`  
**Content:** `short-form`, `fast-pacing`, `visual-punch`  
**Use Cases:** `viral-potential-test`, `hook-effectiveness`, `gen-z-appeal`

---

## Integration

**Emotion Engine:** The Cast integrates with the OpenTruth Emotion Engine for real-time emotion analysis.

**Documentation:** [Emotion Engine Docs](https://github.com/opentruth/emotion-engine)

---

## Repository Structure

```
cast/
├── README.md (this file)
├── tag-system.md (complete tag taxonomy)
├── visual-guidelines.md (image generation standards)
│
├── impatient-teenager/
│   ├── SOUL.md (persona definition)
│   ├── config.yaml (tags, settings)
│   ├── assets/ (images, videos)
│   └── prompts/ (generation prompts)
│
└── [future-cast-members]/
```

---

**Peanut Gallery** — Where honest feedback meets creative courage

---

*Part of the Peanut Gallery ecosystem. Visit [peanut.gallery](https://peanut.gallery) for more.*
