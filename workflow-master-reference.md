# Cast Member Master Reference Workflow

**Purpose:** Repeatable process for generating consistent, photorealistic 3-view character reference sheets for all Peanut Gallery cast members.

**Based on:** Alex "The Scroller" Chen reference sheet generation (successful iteration)

---

## 🎯 Goal

Generate a **3-view character reference sheet** that serves as the "truth" image for all future generations of a cast member.

**Layout:**
- **Left panel:** Front-facing full-body T-pose
- **Right panel:** Back-facing full-body T-pose
- **Center panel:** Waist-up front view (head and torso)

**Style:** Photorealistic (35mm film, documentary) — NOT CGI/video game art

---

## 📋 Prerequisites

Before generating, you need:

1. **SOUL.md** — Complete persona definition (behavioral profile, voice, traits)
2. **Visual Profile** — Translated visual descriptions from SOUL.md
3. **Character Truth Template** — Specific physical attributes with hex colors, measurements, brand names

---

## 🔧 The Workflow

### Step 1: Define Cast Member Attributes

Fill in this template for your new cast member:

```markdown
## [Cast Member Name] — Core Attributes

### Identity
- **Name:** 
- **Age:** 
- **Pronouns:** 
- **Location:** 
- **Demographic:** 

### Physical Appearance
- **Height:** 
- **Build:** 
- **Hair:** (style, color, distinctive features)
- **Eyes:** (color, shape)
- **Skin tone:** 
- **Distinctive features:** (scars, tattoos, accessories that never change)

### Signature Outfit
- **Top:** (type, color, brand/logo if applicable)
- **Bottom:** (type, color, fit)
- **Shoes:** (type, color, condition)
- **Accessories:** (jewelry, headphones, phone, etc. — be specific with brands/models)

### Color Palette (Hex Codes)
- **Hair base:** `#`
- **Hair accent:** `#` (if applicable)
- **Top:** `#`
- **Bottom:** `#`
- **Shoes:** `#`
- **Accessories:** `#`

### Environment (Optional for reference sheet)
- **Default location:** (bedroom, office, cafe, etc.)
- **Lighting:** (LED colors, natural, artificial)
- **Key props:** (items that tell their story)
```

---

### Step 2: Build the Generation Prompt

Use this **exact structure**, swapping in your cast member's attributes:

```
Create a character reference sheet with three views of the same character in one image. Layout: left panel shows front-facing full-body T-pose, right panel shows back-facing full-body T-pose, center panel shows waist-up front view (head and torso).

Character: [AGE]-year-old [DEMOGRAPHIC], [PRONOUNS] appearance, [FACE SHAPE] face shape with [JAWLINE DESCRIPTION], [EYE COLOR] eyes, [EYE SHAPE] eyes with [SPACING DESCRIPTION], [NOSE DESCRIPTION], [LIP DESCRIPTION] with neutral expression, natural [HAIR COLOR] hair in [HAIR STYLE] with [SPECIFIC DETAILS], distinctive [DISTINCTIVE FEATURE] on [LOCATION], [BUILD] build approximately [HEIGHT]", wearing signature outfit: [TOP WITH BRAND/LOGO DETAILS], [BOTTOM WITH DETAILS], [SHOES WITH CONDITION DETAILS], [ACCESSORIES WITH BRAND/MODEL DETAILS].

All three views show the exact same character with identical features, clothing, and hair. Neutral gray seamless background for all panels, clean character sheet layout, professional reference sheet style.

Photorealistic, captured on 35mm film, documentary style, candid moment, natural lighting, authentic aesthetic, not staged or posed, realistic skin texture with natural imperfections, NO CGI, NO video game art, NO 3D render, NO digital painting, NO illustration, NO anime, NO cartoon, real photograph of actual person, film grain, color graded for appropriate mood, sharp focus on face and hands, consistent lighting across all three views.
```

**Critical elements that made Alex's prompt work:**
- ✅ Specific brand names (Arctic Monkeys, Sony, iPhone 15 Pro, Converse)
- ✅ Condition details (worn and cracked, yellowed case, scuffed shoes)
- ✅ Distinctive features (platinum blonde streak on RIGHT side — always specify side)
- ✅ Hex colors for key items
- ✅ Strong photorealistic language + explicit anti-CGI statements

---

### Step 3: Generate with nano-banana-pro

**Command:**
```bash
uv run generate_image.py \
  --prompt "[YOUR FULL PROMPT FROM STEP 2]" \
  --filename "character-truth-sheet-3view-[cast-member-name].png" \
  --resolution 2K
```

**Settings:**
- Resolution: `2K` (good balance of quality and speed)
- No negative prompt parameter (nano-banana doesn't support it — embed in main prompt)

---

### Step 4: Review Against Checklist

**Character Consistency:**
- [ ] All three views show the same person?
- [ ] Distinctive features visible in all views (hair streak, scars, etc.)?
- [ ] Outfit identical across all views?
- [ ] Accessories consistent (headphones, phone, jewelry)?

**Photorealism:**
- [ ] Looks like a real photograph, not CGI/video game art?
- [ ] Natural skin texture with imperfections?
- [ ] Film grain visible?
- [ ] Documentary/candid feel?

**Technical Quality:**
- [ ] All three views clearly visible and well-lit?
- [ ] Clean layout (not cluttered or confusing)?
- [ ] Neutral background (doesn't distract from character)?
- [ ] Sharp focus on face and hands?

**If any box is unchecked:** Regenerate with adjusted prompt. Common fixes:
- **Too CGI:** Add more "NO CGI, NO video game art" language, emphasize "35mm film"
- **Inconsistent features:** Be more specific about distinctive features and their exact location
- **Generic outfit:** Add brand names, condition details, wear patterns

---

### Step 5: Save and Document

**File naming convention:**
```
character-truth-sheet-3view-[cast-member-name].png
```

**Location:**
```
/projects/peanut-gallery/cast/[cast-member-slug]/assets/portraits/
```

**Commit message:**
```
Add [Cast Member Name] photorealistic 3-view character sheet ([key detail])
```

**Update cast member's config.yaml:**
```yaml
assets:
  reference_sheet: ./assets/portraits/character-truth-sheet-3view-[name].png
```

---

## 🎨 Prompt Engineering Lessons (from Alex's iterations)

### What Worked ✅

| Element | Example | Why It Mattered |
|---------|---------|-----------------|
| **Specific band/logo** | "Arctic Monkeys band logo (front center, screen-printed, worn and cracked)" | Prevents generic/placeholder graphics |
| **Brand names** | "Sony headphones", "iPhone 15 Pro", "Converse high-tops" | Anchors to real-world objects |
| **Condition details** | "yellowed case", "scuff marks", "worn and cracked" | Adds authenticity, prevents pristine CGI look |
| **Distinctive features** | "platinum blonde streak on right side of bangs" | Creates memorable, consistent identifier |
| **Hex colors** | `#3B2F2F`, `#2C1810`, `#E8DCC4` | Precise color matching across generations |
| **Anti-CGI language** | "NO CGI, NO video game art, NO 3D render, real photograph of actual person" | Explicitly prevents unwanted style drift |
| **Film language** | "captured on 35mm film", "documentary style", "film grain" | Reinforces photorealistic aesthetic |

### What Didn't Work ❌

| Attempt | Problem | Fix |
|---------|---------|-----|
| Generic "band logo" | Logo varied or looked placeholder-y | Specify actual band + print style + condition |
| Just "photorealistic" | Still drifted toward CGI | Add "NO CGI" + "35mm film" + "real photograph" |
| "Single view only" instructions | Gemini ignored and made multi-view anyway | Embrace multi-view, prompt for it intentionally |
| Hex codes without context | Colors didn't always match | Pair hex with descriptive color names |

---

## 🧪 Testing & Iteration

**If the first generation isn't perfect:**

1. **Identify the issue** (style drift, inconsistent features, wrong layout)
2. **Adjust ONE element** in the prompt (don't change everything at once)
3. **Regenerate and compare** to previous attempt
4. **Keep the best version**, rename others as `*-ACCIDENTAL.png` for reference
5. **Document what worked** in this workflow file

**Typical iteration count:** 2-4 generations to lock in the perfect reference sheet

---

## 📊 Example: Alex Chen's Iteration History

| Attempt | Filename | Issue | Fix Applied |
|---------|----------|-------|-------------|
| 1 | `*-multi-view-ACCIDENTAL.png` | Accidental 3-view, didn't know if it would work | Tested if Gemini could do multi-view |
| 2 | `*-2view-ACCIDENTAL.png` | Accidental 2-view, still testing | Added "single view only" (didn't work) |
| 3 | `*-3view-intentional.png` | Intentional 3-view, but video game style | Added photorealistic language |
| 4 | `*-3view-photorealistic.png` | ✅ SUCCESS | Added Arctic Monkeys logo + anti-CGI language |

**Key learning:** Gemini naturally creates multi-view sheets — work with it, not against it.

---

## 🔄 Future Cast Members

**Template ready for:**
- [ ] The Workout Gamer (30-40yo, pro-level rhythm game player)
- [ ] The Casual Socialite (20yo, TikTok browser, casual games)
- [ ] [Your next cast member here]

**Process:**
1. Copy this workflow
2. Fill in Step 1 attributes
3. Generate prompt using Step 2 template
4. Follow Steps 3-5

---

## 🛠️ Tool Notes

### nano-banana-pro (Gemini 3 Pro Image)

**Strengths:**
- Naturally creates multi-view character sheets (good for our use case)
- High photorealism quality when prompted correctly
- 2K resolution sufficient for reference sheets

**Limitations:**
- No negative prompt parameter (must embed in main prompt)
- Can't use reference images (img2img) for consistency
- May need 2-4 iterations to lock in character

### Future: ComfyUI Workflow

If we need more control (img2img with reference images, exact pose control), migrate to ComfyUI with:
- IP-Adapter for character consistency
- ControlNet for pose control
- Same prompt structure as above

---

## ✅ Checklist Summary

**Before generating:**
- [ ] SOUL.md complete
- [ ] Visual profile created
- [ ] Character truth template with hex codes and brand names
- [ ] Distinctive features identified (with specific locations)

**After generating:**
- [ ] All three views present and clear
- [ ] Character consistent across views
- [ ] Photorealistic (not CGI)
- [ ] Distinctive features visible
- [ ] Outfit/accessories consistent
- [ ] Saved with correct filename
- [ ] Committed to cast repo
- [ ] config.yaml updated with reference sheet path

---

**Workflow Version:** 1.0  
**Created:** 2026-03-06  
**Based on:** Alex "The Scroller" Chen reference sheet generation  
**Next Review:** After generating 2nd cast member reference sheet
