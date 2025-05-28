---
title: "Designing Experimental Surveys in Qualtrics"
date: 2025-05-24
tags: [qualtrics, survey-design, mturk, experimental-pragmatics, tutorial]
draft: false
---

## 🧠 Overview

This tutorial provides a comprehensive guide to building an experimental survey in **Qualtrics**, specifically designed for testing how **speaker identity** influences listeners’ judgments of **informativeness** in varied **face contexts**. It integrates methodological strategies, Qualtrics configurations, and deployment on **Amazon Mechanical Turk (MTurk)**.

---


## 1. 🎯 Project Setup and Survey Architecture

Before building your survey:

- Clearly define your independent variables:
  - **Speaker Identity** (e.g., Emily vs. Meilin)
  - **Sentence Type** (UI-some, True-some, True-all, False-all)
  - **Face Context** (Neutral vs. Face-threatening)
- Decide how many trials per condition (e.g., 1–2 in pilot).
- Determine a fully **within-subjects design**, block-based, with randomized speaker order.

---

## 2. 📦 Creating and Organizing Blocks

Each speaker (Emily, Meilin) should have the following 4 sub-blocks:

- `IntroBlock` (bio and image)
- `CheckBlock` (3 comprehension questions)
- `ScenarioIntroBlock` (brief task instructions)
- `ScenariosBlock` (16 scenario trials)

Create these in the **Survey Builder** using the "Add Block" button. Use descriptive names (e.g., `EmilyScenarios`).

---

## 3. 🔗 Grouping Questions Within a Trial

Each scenario trial includes:
1. A **Text/Graphic** question with the scenario.
2. A **Felicity Rating** (1–5 Likert scale).
3. An **Attribution Question** (MC, shown conditionally).

📌 To group these:
- Place them consecutively in the block.
- ✅ **Do not insert Page Breaks** between them.
- Use **Display Logic** to show the attribution question only when relevant (e.g., `ConditionType = UI-some`).

---

## 4. 🔁 Randomizing Scenarios Using Loop & Merge

1. Click on your Scenarios block → choose **Loop & Merge**.
2. Define two columns:
   - `ScenarioText`
   - `ConditionType`
3. Enter one row per trial.
4. Enable **"Randomize Loop Order"** at the top.

📌 In the scenario display question, use:
```text
${lm://Field/ScenarioText}
```
Use Display Logic for the Attribution question based on `${lm://Field/ConditionType}`.

---

## 5. 🔀 Randomizing Speaker Blocks with Groups in Survey Flow

1. Go to **Survey Flow**.
2. Add a **Randomizer** (set to randomly present 1 of 2 elements).
3. Under each path, click **“Add a Group”** and insert:
   - 4 blocks for Emily (or Meilin): Intro → Check → ScenarioIntro → Scenarios
   - Set Embedded Data: `BlockOrder = EmilyFirst` or `MeilinFirst`
4. Ensure groups are in the intended fixed order.
5. Click **Apply**.

---

## 6. 🖼️ Adding Speaker Identity Images

Use a **Text/Graphic question** with inline CSS:
```html
<div style="margin-left: 280px;">
  <img src="IMAGE_URL" style="width: 100px; height: 100px; filter: grayscale(100%) opacity(70%);" />
</div>
```
You can upload your image in the Qualtrics editor and reference the URL.

---

## 7. ⏸️ Mid-Survey Breaks

To reduce fatigue:
- After every 8 trials, insert a **Text/Graphic** question that reads:
```text
You're halfway through this section. Feel free to take a short break. Click “Next” when you're ready to continue.
```

To insert it in the middle of randomized items:
- Use **Advanced Question Randomization** and split items into 2 randomization groups, placing the break in between.

---

## 8. 🛡️ Preventing Duplicate Participation

### Recommended:
- Use **Survey Options → Prevent Multiple Submissions** (cookie-based).
- Ask for **MTurk Worker ID** early in the survey.
- Optionally, screen for repeat IDs manually in your exported data.

---

## 9. 🔗 Deploying via MTurk

1. In MTurk, use the **Survey Link template**.
2. Paste your **Qualtrics anonymous link**.
3. Include a **completion code page** in Qualtrics using a final Text/Graphic block:
```text
Thank you for participating! Your completion code is: ABC123XYZ
```
4. Instruct participants to copy this into MTurk to verify.

MTurk Settings:
- Title: “Short Language and Communication Study”
- Reward: ~$1.50 for 10–15 mins
- Requirements: Location = US, HIT approval > 95%

---

## 10. 🧩 Tracking Embedded Data

Use **Embedded Data** in Survey Flow:
- Set `BlockOrder` in each speaker group inside the Randomizer.
- Track participant condition and block order for analysis.

Exported data will include these fields automatically.

---

## 11. 📊 Exporting and Cleaning Data

After data collection:
- Export responses to CSV or SPSS.
- Filter out:
  - Incomplete or fast responses
  - Duplicates by Worker ID
  - Failed comprehension checks

Use the `BlockOrder`, `ConditionType`, and response fields for initial analysis and plotting.

---

## ✅ Final Thoughts

This walkthrough integrates technical setup with practical experimental design for a nuanced pragmatic judgment study. For a real-world example, see our pilot: *"The Cost of Saying Too Little—or Too Much: How Speaker Identity Shapes Judgments of Informativeness."*

