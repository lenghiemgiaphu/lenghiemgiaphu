# Le Nghiem Gia Phu · Lê Nghiêm Gia Phú

Mathematics student at the **High School for the Gifted (PTNK), VNU-HCM** (Ho Chi Minh City, Vietnam). I like projects where a transparent model meets imperfect real data: heat–moisture modelling of public spaces, machine translation for a low-resource language, and software that helps people study or take their medicine. I plan to study applied mathematics, computer science and artificial intelligence.

---

## Research and modelling

**[public-space-cooling-model](https://github.com/lenghiemgiaphu/public-space-cooling-model)**: a heat–moisture balance framework for measuring and optimising cooling in open-air and semi-open public spaces (HiMCM 2026, Problem B, Team #19386).
A single-zone, hourly steady-state model is run over seven summers (June–August, 2020–2026; 09:00–21:00, 7,728 hours per site) of Open-Meteo data, for four sites (Hanoi Bus Stop, Hanoi Railway Station, Honolulu Airport, Sun Devil Stadium) and three cooling systems. A coverage scaling law ρ = c·n·A_cov / A_floor keeps efficiency flat while ρ ≤ 1 and lets it fall as 1/ρ beyond that. Designs are compared on a four-objective Pareto front combined with AHP (CR = 0.0038), then stress-tested with 56 one-at-a-time sensitivity runs, a +3 °C heatwave scenario and 10,000 Monte Carlo runs over 16 configurations. The main finding is that energy efficiency is not the same as risk reduction: at Sun Devil Stadium the share of dangerous hours falls from 66.31% to 50.25% with configuration `C-40`, and at Hanoi Railway Station from 56.84% to 49.50% with `B-40`. I was team leader, built the Cooling-Efficiency and Semi-Open Rail Station models, ran the Monte Carlo analysis and wrote the blog post. Team: Le Minh, Do Le Chi Hung, Tran Hung Phat.

```text
Open-Meteo hourly weather (2020–2026, 09:00–21:00)
        │
        ▼
single-zone heat–moisture balance  ──►  danger share per site
        ▲                                      │
  cooling system (A / B / C)                   ▼
  × coverage ratio ρ = c·n·A_cov/A_floor   Pareto front (4 objectives) + AHP
                                               │
                                               ▼
                       56 OAT tests · +3 °C heatwave · Monte Carlo (10,000 × 16 configs)
                                               │
                                               ▼
                                   recommendation for each site
```

**[PIISE_Ede_Vietnamese_Multimodal_NMT](https://github.com/lenghiemgiaphu/PIISE_Ede_Vietnamese_Multimodal_NMT)**: a proof-of-concept Ede–Vietnamese translation model for a low-resource language (about 400,000 speakers), built for the PIISE Research Program with Tran Hung Phat.
`facebook/nllb-200-distilled-600M` is fine-tuned with Indonesian (`ind_Latn`) as a proxy source code, because Ede has no NLLB token. The pipeline scrapes public VOV4 articles, normalises Unicode, pairs sentences with Gemini assistance and augments both directions: 408 pairs become 816 samples. Validation loss falls from 4.709 to 2.888 and SacreBLEU reaches 12.46 / 100 (a 30-sentence pilot reached 9.39 and overfitted). Limits are stated in the repository: outputs are fluent but often semantically wrong and repetitive, the Vietnamese side is a silver-standard label set with no native-speaker validation, and speech synthesis is planned, not built.

---

## Software

| Project | What it is | Stack |
| :--- | :--- | :--- |
| [PillGuard AI](<PillGuard-repo-url>) · [live](<render-demo-url>) | Web app for visually impaired and elderly users: photo of a handwritten prescription, GPT-4o OCR, a human-verified table, then a dosing schedule pushed to Google Calendar. Working prototype by a team of three (Intel AI Impact Festival 2026); OCR accuracy has not been evaluated. | Flask, Tailwind CSS, JavaScript, OpenAI APIs, Google Calendar API |
| [AI-Powered EdTech Web](https://github.com/lenghiemgiaphu/AI-Powered_EdTech_Web) · [link](https://labluyen.vercel.app/#/) | Solo exam-practice platform for high-school Physics, Chemistry and Biology: four question types, timed mock exams scored out of 10, AI quiz generation from documents, an AI tutor and live classroom quiz battles. Demo-scale bank of 57 questions. | Next.js, TypeScript, Tailwind CSS, Firebase Auth, Upstash Redis, Gemini |
| [UI Screen Translator Tool](https://github.com/lenghiemgiaphu/UI_Screen_Translator_Tool) | Windows tray tool: hotkey region capture, Tesseract OCR, and translation through a fuzzy-matched local glossary with Google Translate as fallback. | Python, PyQt5, Tesseract, deep-translator |
