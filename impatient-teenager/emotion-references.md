# Alex Chen — Emotion Reference Sheets

**Master Reference:** `character-truth-sheet-3view-MASTER.png`

**Purpose:** Generate consistent emotion reference images for Alex Chen across the 15 tracked emotional dimensions.

---

## The 15 Tracked Emotional Dimensions

### Category 1: Friction & Cognitive Load
- Frustration
- Confusion
- Overwhelm
- Clarity
- Patience

### Category 2: Desirability & Engagement
- Excitement
- Boredom
- Flow
- Joy
- Relief

### Category 3: Trust & Security
- Trust
- Skepticism
- Anxiety
- Empowerment
- Confidence

---

## Emotion Reference Workflow

### Step 1: Define Emotion Characteristics

For each emotion, document:
- **Facial expression** (eyebrows, eyes, mouth, jaw)
- **Body language** (posture, hand position, tension)
- **Intensity level** (subtle, moderate, strong)
- **Context trigger** (what causes this emotion while scrolling/watching content)

### Step 2: Generate Using Master Reference

**Img2img workflow:**
1. Use `character-truth-sheet-3view-MASTER.png` as base reference
2. Apply emotion-specific prompt modifications
3. Keep all other features identical (hair, outfit, lighting, layout)

**Prompt structure:**
```
[Base character description from MASTER], [EMOTION-SPECIFIC FACIAL EXPRESSION], [EMOTION-SPECIFIC BODY LANGUAGE], same outfit (Arctic Monkeys tee, black cargo pants, Converse, Sony headphones), same photorealistic 35mm film style, same lighting, same background
```

### Step 3: Review for Consistency

**Checklist:**
- [ ] Same Alex (platinum streak on right side only)?
- [ ] Same outfit (Arctic Monkeys tee, accessories)?
- [ ] Emotion clearly readable in facial expression?
- [ ] Body language matches emotion?
- [ ] Photorealistic style maintained?
- [ ] All three views show same emotion consistently?

---

## Category 1: Friction & Cognitive Load

### 1. Frustration

**Trigger:** Content that wastes Alex's time, false advertising, clickbait that doesn't deliver

**Facial Expression:**
- Eyebrows: Furrowed, drawn together
- Eyes: Narrowed, intense stare at phone
- Mouth: Tight lips or slight grimace
- Jaw: Tense, clenched

**Body Language:**
- Posture: Leaning forward aggressively or recoiling back
- Hands: Gripping phone tightly, thumb hovering aggressively
- Shoulders: Tensed, raised slightly
- Overall: Visible tension

**Intensity:** Moderate to strong (Alex's frustration is immediate and visible)

**Prompt Addition:**
```
frustrated expression, furrowed eyebrows drawn together, narrowed eyes with intense stare at phone, tight lips in slight grimace, tense jaw, leaning forward aggressively, gripping phone tightly with visible tension in hands, shoulders raised and tensed
```

---

### 2. Confusion

**Trigger:** Unclear messaging, contradictory information, unfamiliar concepts without context

**Facial Expression:**
- Eyebrows: One raised higher than the other, or both raised in middle
- Eyes: Slightly squinted, looking intently at screen
- Mouth: Slightly open or pursed to one side
- Head: Tilted slightly

**Body Language:**
- Posture: Leaning in closer to screen
- Hands: Phone held with both hands now (unusual for Alex)
- Shoulders: Slightly hunched forward
- Overall: Attempting to process, working to understand

**Intensity:** Moderate (confusion makes Alex pause scrolling briefly)

**Prompt Addition:**
```
confused expression, one eyebrow raised higher than the other, slightly squinted eyes looking intently at screen, mouth slightly open and pursed to one side, head tilted slightly to the side, leaning in closer to phone screen, holding phone with both hands, shoulders hunched forward in concentration
```

---

### 3. Overwhelm

**Trigger:** Too much information at once, complex interfaces, walls of text, multiple CTAs competing for attention

**Facial Expression:**
- Eyebrows: Raised and drawn together (worried look)
- Eyes: Wide, slightly glazed or darting
- Mouth: Open slightly, corners turned down
- Forehead: Visible tension lines

**Body Language:**
- Posture: Leaning back away from screen or slumping
- Hands: Phone held loosely, thumb inactive
- Shoulders: Slumped forward or raised in tension
- Overall: Withdrawal, wanting to escape

**Intensity:** Strong (overwhelm = immediate scroll away for Alex)

**Prompt Addition:**
```
overwhelmed expression, eyebrows raised and drawn together in worried look, eyes wide and slightly glazed, mouth open slightly with corners turned down, visible tension lines on forehead, leaning back away from phone screen or slumping backward, holding phone loosely with inactive thumb, shoulders slumped forward in defeat
```

---

### 4. Clarity

**Trigger:** Clean messaging, obvious value proposition, "aha moment" when something clicks

**Facial Expression:**
- Eyebrows: Relaxed, natural position
- Eyes: Bright, focused, slight widening (recognition)
- Mouth: Small smile of understanding, relaxed
- Overall: Relief + recognition

**Body Language:**
- Posture: Sitting up straighter, relaxed but engaged
- Hands: Phone held comfortably, thumb active again
- Shoulders: Relaxed, down from tense position
- Overall: Open, receptive

**Intensity:** Moderate (clarity = Alex keeps watching, but not excited yet)

**Prompt Addition:**
```
expression of clarity and understanding, relaxed eyebrows in natural position, bright focused eyes with slight widening of recognition, small smile of understanding on relaxed lips, face relaxed and open, sitting up straighter with relaxed but engaged posture, holding phone comfortably with thumb actively scrolling, shoulders relaxed and down
```

---

### 5. Patience

**Trigger:** Content that's building slowly but showing promise, trustworthy pacing, earning Alex's attention

**Facial Expression:**
- Eyebrows: Neutral, relaxed
- Eyes: Soft focus, steady gaze (not darting)
- Mouth: Neutral, relaxed (not smiling but not frowning)
- Overall: Calm, giving chance

**Body Language:**
- Posture: Neutral, balanced (not leaning in or away)
- Hands: Phone held steadily, thumb moving slowly
- Shoulders: Relaxed
- Overall: Willing to wait, thumb not hovering to scroll

**Intensity:** Subtle to moderate (patience is rare for Alex, so when present it's deliberate)

**Prompt Addition:**
```
patient expression, neutral relaxed eyebrows, soft focused eyes with steady gaze not darting, mouth neutral and relaxed not smiling or frowning, calm composed face, balanced neutral posture not leaning in or away from screen, holding phone steadily with thumb moving slowly, shoulders completely relaxed, willing to wait and give content a chance
```

---

## Generation Commands

For each emotion, use:

```bash
uv run generate_image.py \
  --prompt "[MASTER CHARACTER] + [EMOTION PROMPT ADDITION]" \
  --input-image ./character-truth-sheet-3view-MASTER.png \
  --filename "emotion-[emotion-name]-3view.png" \
  --resolution 2K
```

**Example for Frustration:**
```bash
uv run generate_image.py \
  --prompt "17-year-old Gen Z teenager, androgynous they/them appearance, oval face shape, dark brown hair with distinctive platinum blonde streak on RIGHT side of bangs only (viewer's left in front view), wearing oversized charcoal gray Arctic Monkeys band tee, black cargo pants, Converse high-tops, Sony headphones around neck, frustrated expression, furrowed eyebrows drawn together, narrowed eyes with intense stare, tight lips in grimace, tense jaw, leaning forward aggressively, gripping phone tightly, visible tension, same photorealistic 35mm film documentary style, same lighting, same neutral gray background" \
  --input-image ./character-truth-sheet-3view-MASTER.png \
  --filename "emotion-frustration-3view.png" \
  --resolution 2K
```

---

## File Naming Convention

```
emotion-[emotion-name]-3view.png
```

**Examples:**
- `emotion-frustration-3view.png`
- `emotion-confusion-3view.png`
- `emotion-overwhelm-3view.png`
- `emotion-clarity-3view.png`
- `emotion-patience-3view.png`

---

## Next Steps

After completing Category 1 (Friction & Cognitive Load):
1. Review all 5 emotion sheets for consistency
2. Test if emotions are clearly readable/distinguishable
3. Proceed to Category 2 (Desirability & Engagement)
4. Eventually compile all 15 into emotion reference library

---

**Created:** 2026-03-06  
**Based on:** Alex Chen master reference sheet  
**Status:** Ready to generate Category 1 emotions
