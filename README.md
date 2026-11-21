# Le Nghiem Gia Phu · Lê Nghiêm Gia Phú

Mathematics student at the **High School for the Gifted (PTNK), VNU-HCM** (Ho Chi Minh City, Vietnam). I like projects where a transparent model meets imperfect real data: heat–moisture modelling of public spaces, or machine translation for a low-resource language. I plan to study Applied Mathematics, Computer Science and Artificial Intelligence.

---

## Research and modelling

[Public-Space Cooling Model](https://github.com/lenghiemgiaphu/public-space-cooling-model): a heat–moisture balance framework for choosing cooling systems in open-air and semi-open public spaces (HiMCM 2026, Problem B, Team #19386; results pending). An hourly, quasi-steady, single-zone model is run over seven summers of Open-Meteo data (June–August 2020–2026, 09:00–21:00, 7,728 hours per venue) for four venues (Hanoi Bus Shelter, Hanoi Railway Station, Honolulu Airport, Sun Devil Stadium) and three cooling systems (fans, medium and large evaporative coolers). Configurations are screened on a four-objective Pareto front and ranked with AHP (CR = 0.0038), then stress-tested with 56 one-at-a-time sensitivity cases, a +3 °C heatwave scenario and 10,000 Monte Carlo runs over 16 configurations. The main finding is that efficiency per kWh is not the same as risk reduction, and that the right technology depends on climate: evaporative cooling is limited by the small wet-bulb depression in humid Hanoi but works in dry Phoenix. At Sun Devil Stadium the share of person-hours in the danger zone (team-modified apparent temperature ≥ 38 °C) falls from 66.31% to 50.25% with 40 large evaporative units (`C-40`), and at Hanoi Railway Station from 56.84% to 49.50% with 40 medium units (`B-40`); about half of person-hours stay above the threshold, so hardware must be paired with shade, water and heat monitoring. Limits (uncalibrated model, internal comfort index, placeholder prices) are stated in the repository. I was team leader, formulated the Cooling-Efficiency and Semi-Open Rail Station models, and contributed to the Monte Carlo analysis and the blog post. Team: Le Minh, Do Le Chi Hung, Tran Hung Phat.

```text
Open-Meteo hourly weather (2020–2026, 09:00–21:00) + occupancy + venue geometry
                               │
                               ▼
     single-zone heat–moisture balance  ×  cooling system (A / B / C), unit count n
                               │
                               ▼
   danger share and EDH38 per venue  →  4-objective Pareto front  →  AHP ranking
                               │
                               ▼
   56 OAT cases · +3 °C heatwave · Monte Carlo (10,000 draws × 16 configurations)
                               │
                               ▼
                    recommendation for each venue
```

**[Ede–Vietnamese Machine Translation](https://github.com/lenghiemgiaphu/low-resource-ede-vietnamese-nmt)**: a proof-of-concept Ede–Vietnamese translation model for a low-resource language (about 400,000 speakers), built for the PIISE Research Program with Tran Hung Phat.
`facebook/nllb-200-distilled-600M` is fine-tuned with Indonesian (`ind_Latn`) as a proxy source code, because Ede has no NLLB token. The pipeline scrapes public VOV4 articles, normalises Unicode, pairs sentences with Gemini assistance and augments both directions: 408 pairs become 816 samples. Validation loss falls from 4.709 to 2.888 and SacreBLEU reaches 12.46 / 100 (a 30-sentence pilot reached 9.39 and overfitted). Limits are stated in the repository: outputs are fluent but often semantically wrong and repetitive, the Vietnamese side is a silver-standard label set with no native-speaker validation, and speech synthesis is planned, not built.

---

## Software

| Project | What it is | Stack |
| :--- | :--- | :--- |
| [AI-Powered EdTech Web](https://github.com/lenghiemgiaphu/stem-exam-practice-web) · [link](https://labluyen.vercel.app/#/) | Solo exam-practice platform for high-school Physics, Chemistry and Biology: four question types, timed mock exams scored out of 10, AI quiz generation from documents, an AI tutor and live classroom quiz battles. Demo-scale bank of 353 questions. | Next.js, TypeScript, Tailwind CSS, Firebase Auth, Upstash Redis, Gemini |
| [Screen Translator](https://github.com/lenghiemgiaphu/desktop-screen-translator) | Windows tray tool: hotkey region capture, Tesseract OCR, and translation through a fuzzy-matched local glossary with Google Translate as fallback. | Python, PyQt5, Tesseract, deep-translator |
