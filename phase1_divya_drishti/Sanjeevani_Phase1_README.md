# Sanjeevani — Phase 1: Divya Drishti

### Quantifying Hidden Allergens in FDA-Approved Oral Medications

> *Divya Drishti — "divine sight": establishing a baseline descriptive metric for the true prevalence of food allergens in U.S. medications.*

**Status:** Problem discovery & descriptive-analysis design (Phase 1 of the Sanjeevani platform).
**Approach:** Problem first, solution second — validate the scale of the problem before building anything.

---

## The problem

**Start with the bigger picture — the food allergy epidemic.**


Food allergies affect **~33M Americans** — about 1 in 10 adults and 1 in 13 children. Reactions are serious and rising: more than half of adults with food allergies have had a severe reaction, and claim lines for anaphylactic food reactions rose **377% (2007–2016)**. The burden is roughly **$25B a year and ~3.4M ER visits**.

![The Food Allergy Epidemic — infographic by FARE](assets/food-allergy-epidemic-fare.png)

*Source: FARE (Food Allergy Research & Education), "The Food Allergy Epidemic." Underlying data: Prevalence & Severity of Food Allergies Among US Adults, JAMA Network Open (2019); The Public Health Impact of Parent-Reported Childhood Food Allergies, Pediatrics (2018); FARE Health White Paper (Nov 2017). Reproduced with attribution.*

**Now the hidden subset — allergens in medications.**

Within that epidemic sits a blind spot: prescribed and over-the-counter **oral medications routinely contain the same top-9 allergens** — milk/lactose, wheat/gluten, soy, egg — as *inactive* binders and fillers. Patients react to these refined excipients, yet they are **invisible at the point of prescribing**. Up to ~60% of adult anaphylaxis is labeled *"idiopathic,"* and ~99% of providers have no allergen visibility for the drugs they prescribe.

**The gap:** OpenFDA exposes raw ingredient data, but **no centralized baseline metric** establishes how widespread the *medication* piece actually is.

> *Context statistics above are drawn from published literature — not from this project's own computation. Add citations before publishing.*

---

## The Phase 1 question

**What exact percentage of FDA-approved oral medications contain one or more of the top-9 major food allergens?**

This is a **descriptive** problem — summarize the current state of the data through mathematical aggregation, with **no inferential modeling**.

---

## Approach & key outputs

**Required input schema**

| Field                | Notes                         |
| -------------------- | ----------------------------- |
| Drug Name            |                               |
| Active Ingredients   |                               |
| Inactive Ingredients | where hidden allergens appear |
| Manufacturer         |                               |
| Route                | filter =**Oral**        |

**Core metrics**

1. **Percentages** — baseline % of all oral drugs containing each of the top-9 allergens.
2. **Mode** — the single most frequent inactive allergen filler across all drugs (e.g., lactose).
3. **Frequency distributions** — allergen frequency broken down by drug manufacturer.

---

## Data source & lifecycle

- **Source:** OpenFDA drug-label data (with DailyMed / FDA SPLs as needed).
- **Automated monthly pipeline:** OpenFDA updates monthly, so the analytical pipeline is automated to keep the prevalence reports accurate over time.
- **Key data risk:** high dependency on the accuracy and consistency of OpenFDA source data.

---

## Who this serves (ecosystem)

| Stakeholder                      | Impact                                                  | Risk to manage                                      |
| -------------------------------- | ------------------------------------------------------- | --------------------------------------------------- |
| **Patients & families**    | Reveals the scale of the risk so they can be more aware | Raw data without alternatives → "so what?" fatigue |
| **Providers & pharmacies** | Visibility into a fragmented system, across specialties | Needs an alternative-drug search tool in Phase 2    |
| **Insurers**               | Highlights the scope of a $25B issue                    | Potential coverage friction                         |
| **Drug manufacturers**     | Awareness that patients react to refined fillers        | Potential manufacturer pushback                     |

---

## Roadmap

```
Baseline Prevalence Metric  →  Provider Awareness  →  Phase 2: Alternative-Drug Solutions
        (Divya Drishti)                                   (Lakshmana Rekha → Sanjeevani)
```

**Phase 1 (this):** establish the baseline prevalence metric.
**Phase 2:** point-of-prescribing alerts (human-in-the-loop, pharmacist override) and allergen-free, insurance-covered alternatives.

---

*Part of the **Sanjeevani Aushad** medication allergen-safety platform. Built in the open.*
