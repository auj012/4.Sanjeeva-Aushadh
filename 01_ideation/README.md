# AI Product Discovery & User Journey — Sanjeevani

**Author:** Ushasree Jakilinki
**Date:** 2026-07-23
**Status:** Discovery WIP — precedes and grounds the PRD.

> **Progress:** §1–5 and §7 populated from prior work. §6, §8–16 have the guiding questions ready — we complete them one at a time.

---

## 1. Problem Discovery

**What problem are we solving?**
Patients with food allergies, celiac disease, gluten sensitivity, or dietary restrictions are often forced to manually coordinate medication safety information across multiple disconnected sources before they can begin treatment. Although food products require allergen labeling, **medications do not consistently disclose major allergens or gluten in a clear, patient-friendly format.**

**Why does it matter now?**
The data exists (openFDA, DailyMed), but no participant owns the end-to-end safety workflow — so the burden falls to the patient. A missed allergen can cause a reaction; the current process delays treatment by days or weeks.

**What evidence shows this is a real problem?**  *(to expand)*

- The current user journey (§3) — the manual, looping research burden.
- The ADINA Act, Beyond Celiac advocacy, gluten-in-medication research, FDA labeling discussions, and patient communities.
- Encountered firsthand (founding experience), and consistent with published work on reactions to inactive ingredients in oral medications.

**What is the current baseline?**
Patients research, contact prescribers/pharmacists/manufacturers, identify alternatives, and navigate insurance — often delaying treatment by days or weeks.

---

## 2. User Discovery

### Personas

| **Primary Users**               | **Secondary Users** |
| ------------------------------------- | ------------------------- |
| Patients with Top 9 food allergies    | Pharmacists               |
| Celiac disease patients               | Prescribers               |
| Gluten-sensitive patients             | Allergy specialists       |
| Caregivers of children with allergies | Care coordinators         |
| Caregivers of elderly patients        |                           |

**Admins / operators / reviewers:** *(to define — who maintains the allergen/alias dictionary, reviews flagged items)*
**Edge-case users:** *(to define — e.g., multiple severe allergies, generic vs. brand switches, non-English labels)*

### Jobs To Be Done

> When I am prescribed a medication, help me quickly determine whether that medication is compatible with my food allergies, celiac disease, gluten sensitivity, or dietary restrictions and is supported by my insurance; if it is not, flag it and suggest a safe alternative — so that I can safely begin treatment without spending days or weeks coordinating information across multiple sources.

- **What triggers the need?** A new prescription; a new diagnosis; a switch between generic and brand.
- **What does success look like?** A clear, sourced safety answer — and, if unsafe, a covered alternative — in one pass.
- **What alternatives do they use today?** FDA/DailyMed searches, Google, LLMs, calls to prescriber/pharmacy/manufacturer (see §3).

---

## 3. Current User Journey (Before AI)

### Journey board — phases, actions, and pain

|                        | ① PRESCRIBED                                                                                                | ② SELF-RESEARCH                                                   | ③ CHASING ANSWERS                                               | ④ ALTERNATIVES                                                 | ⑤ OUTCOME                            |
| ---------------------- | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------ | ---------------------------------------------------------------- | --------------------------------------------------------------- | ------------------------------------- |
| **Patient does** | Gets diagnosis · Receives prescription                                                                      | Searches FDA, DailyMed, Google, LLMs · Decodes ingredient aliases | Calls prescriber · Calls pharmacy · Calls manufacturer         | Finds alternatives · Checks insurance · Returns to prescriber | Still no safe option? · Starts over  |
| **Pain**         | Needs treatment now · Prescriber may not know the medication's ingredients or the patient's allergy history | No single source of truth · One allergen, many names              | Answers vary · Days of waiting · Burden returns to the patient | Each option restarts the research · May not be covered         | Days or weeks pass · Still untreated |

> **The loop is the problem.** Every "No" sends the patient back to research — and the entire process restarts for each alternative. Days or weeks pass while the patient remains untreated.

---

## 4. Pain Points & User Needs

| **Labeling & Ingredients**                     | **Information Access**                   | **Clinical Knowledge & Beliefs**                                   | **Burden & Delay**               |
| ---------------------------------------------------- | ---------------------------------------------- | ------------------------------------------------------------------------ | -------------------------------------- |
| Hidden allergens in medications (incl. gluten/wheat) | Information fragmented across multiple sources | **Belief that "medical-grade" allergens cause no harm**            | Alternatives are difficult to identify |
| Lack of standardized allergen labeling               | No single source of truth                      | Prescriber knowledge gaps (meds ingredients and patient allergy history) | Insurance complexity                   |
| Multiple names for the same allergen                 |                                                | Pharmacist knowledge variability                                         | Excessive coordination burden          |
| Generic vs. brand formulation differences            |                                                |                                                                          | Delayed treatment                      |

**On the belief barrier:** clinicians and pharmacists are frequently taught that pharmaceutical-grade excipients are too purified, or present in too small a quantity, to trigger a reaction — so the question is dismissed rather than investigated. This is not a knowledge *gap* the patient can close with better information; it is a belief that stops the inquiry before it starts.

> ### ⇩ And the result of all of it:
>
> ## **Patients become the system integrator.**

**Key insight:** to determine whether a medication is safe, patients must coordinate across prescribers, pharmacists, manufacturers, FDA sources, DailyMed, and insurance providers. **No single participant owns the complete workflow.**

---

## 5. Opportunity Assessment

### Pain → Capability Mapping

Every pain below is taken directly from §4.

| Pain (from §4)                                                                                                      | Capability                                                                                    |
| -------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Information fragmented across sources · No single source of truth · Generic vs. brand formulation differences      | **Medication Intelligence** — one reliable view of what is actually in a medication    |
| Multiple names for the same allergen · Lack of standardized allergen labeling                                       | **Ingredient Alias Intelligence** — recognize every name an allergen hides behind      |
| Hidden allergens in medications (incl. gluten/wheat)                                                                 | **Allergen & Gluten Intelligence** — detect the top 9                                  |
| Alternatives are difficult to identify · Insurance complexity                                                       | **Alternative & Insurance Intelligence** — find a safe option that is actually covered |
| Belief that "medical-grade" allergens cause no harm · Prescriber knowledge gaps · Pharmacist knowledge variability | **Explainable Decision Support** — a sourced answer that is hard to dismiss            |

**Not solved by any single capability:** *excessive coordination burden*, *delayed treatment*, and *patients become the system integrator* — these result from all capabilities working together (the product, not a feature).

*(to complete together: which opportunities are largest / most feasible / most strategic)*

---

## 6. Why AI?

*(to complete together)*

- Why is AI needed instead of rules or plain automation? *(note: the safety core is deliberately rule-based — this section decides where AI genuinely adds value vs. where deterministic rules are safer)*
- What can AI do better here?
- What can AI **not** do well?
- Where is human judgment still required?

---

## 7. Future AI User Journey

### Journey board — who does the work now

|                           | ① PRESCRIBED                                  | ② UNDERSTAND                                                       | ③ DETECT                              | ④ RESOLVE                                       | ⑤ DECIDE                                                                                  |
| ------------------------- | ---------------------------------------------- | ------------------------------------------------------------------- | -------------------------------------- | ------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Patient does**    | Receives prescription · Enters the medication | *nothing to do*                                                   | *nothing to do*                      | *nothing to do*                                | Reviews a clear answer · Informed conversation with prescriber →**safe treatment** |
| **Sanjeevani does** | Medication search                              | Active + inactive ingredient analysis · Ingredient alias detection | Allergen detection · Gluten detection | Alternative discovery · Insurance compatibility | Explainable safety assessment                                                              |

> ✓ **No loop.** The patient acts twice; the system does everything in between — in one pass, not one call at a time.

### Worked example — a dairy-allergic patient prescribed levothyroxine

|                       | Medication                                | What Sanjeevani finds                                             | Outcome                                                     |
| --------------------- | ----------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------- |
| **Prescribed**  | **Synthroid** (levothyroxine)       | Contains**lactose monohydrate** — a milk-derived excipient | ⚠️**Flagged** — unsafe for this patient            |
| **Candidate 1** | **Tirosint** (levothyroxine)        | Minimal excipients, no dairy                                      | ✔ Safe — ✗**not covered** under the patient's plan |
| **Candidate 2** | **Levoxyl** (levothyroxine, Pfizer) | Lactose-free formulation                                          | ✅**Safe *and* covered → recommended**             |

**Why this example matters:** all three share the same active ingredient, so the clinical decision doesn't change — only the excipients and coverage do. Candidate 1 shows why safety alone isn't enough: a medication the patient can't afford is not a solution.

> ⚠️ **Verify before publishing.** Excipient formulations and formulary coverage change, and coverage is plan-specific. Re-check these claims against current DailyMed labeling and the patient's actual plan — which is exactly why the system re-validates rather than caching an answer.

---

## 8. AI Experience Design

*(to complete together)*

- Input methods · Output format · Explainability · Confidence display · Error handling · Fallback behavior · User control and override

---

## 9. Data Discovery

*(to complete together — PRD names openFDA, DailyMed/SPL, RxNorm, EHR allergy lists as sources)*

- Required data sources · Data quality · Completeness · Label availability · Data ownership · Privacy & access constraints · Integration points

---

## 10. AI Requirements

*(to complete together)*

- Functional requirements · Non-functional requirements · Latency targets · Accuracy targets · Explainability requirements · Security requirements · Compliance requirements

### Capability set (Sanjeevani Intelligence Layers)

| Layer                                         | What it does                                  |
| --------------------------------------------- | --------------------------------------------- |
| **Medication Intelligence**             | Understand the medication                     |
| **Ingredient Alias Intelligence**       | Map ingredient names to known allergens       |
| **Allergen Intelligence**               | Identify Top 9 allergens                      |
| **Gluten Intelligence**                 | Identify gluten risks                         |
| **Alternative Intelligence**            | Discover potential alternatives               |
| **Insurance Intelligence** *(future)* | Assess coverage constraints                   |
| **Decision Support Intelligence**       | Help patients make safer medication decisions |

*(note: reconcile this 7-layer list with the 5 consolidated capabilities in §5)*

---

## 11. Human-in-the-Loop

*(to complete together — core principle: the system informs; a licensed clinician decides and can override)*

- Where humans review outputs · What thresholds trigger review · What humans can override · Escalation paths · Audit and accountability

---

## 12. Evaluation Plan

*(to complete together)*

- Offline evaluation · Human review evaluation · User acceptance criteria · Business KPI impact · Error analysis · Monitoring plan

---

## 13. MVP Scope

*(to complete together)*

- In-scope features · Out-of-scope features · MVP assumptions · MVP success criteria · Release criteria

---

## 14. Cost & Feasibility

*(to complete together)*

- Build cost · Data cost · Inference cost · Operational cost · Technical complexity · Team & timeline feasibility

---

## 15. Risks & Roadmap

*(to complete together)*

- Technical risks · Product risks · Data risks · Compliance risks · Adoption risks · Mitigation plan · Phased roadmap

---

## 16. Responsible AI Check

**Product principles (seed — map to the checklist below):**

1. Patient safety comes first.
2. Recommendations must be explainable.
3. Sources must be transparent.
4. Unknown information must be clearly identified.
5. The system supports decision-making, **not medical diagnosis**.
6. Patients should not need to manually coordinate multiple systems.
7. Reduce time-to-safe-treatment.
8. Translate complex ingredient names into patient-friendly language.
9. Surface risks early.
10. Make medication safety information accessible to non-clinical users.

*(to complete together)*

- Intended use · Out-of-scope use · Prohibited use · Stakeholders & impact · Fairness & bias · Reliability & safety · Privacy & data governance · Security & resilience · Transparency & explainability · Human oversight · Accountability & governance · Vendor & third-party risk · Monitoring after launch · Social & ethical impact

---

## User Stories *(supporting §2)*

**Primary**

> As a patient with food allergies or celiac disease, I want to know whether a medication contains ingredients that are unsafe for me, so that I can avoid adverse reactions and begin treatment safely.

**Secondary**

> As a caregiver, I want to quickly identify allergen and gluten risks within medications, so that I can make safer treatment decisions for my family member.

---

*Discovery grounds the product. Every capability traces back to a pain point in Section 4.*
