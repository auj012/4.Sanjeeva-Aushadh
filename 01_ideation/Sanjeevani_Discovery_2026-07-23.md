# Sanjeevani — Discovery

**Author:** Ushasree Jakilinki
**Date:** 2026-07-23
**Status:** Discovery WIP — this document precedes and grounds the PRD.


---

## 1. Problem Statement

Patients with food allergies, celiac disease, gluten sensitivity, or dietary restrictions are often forced to manually coordinate medication safety information across multiple disconnected sources before they can begin treatment.

Although food products require allergen labeling, **medications do not consistently disclose major allergens or gluten in a clear, patient-friendly format.**

As a result, patients must perform their own research, contact multiple stakeholders, identify alternatives, and navigate insurance hurdles — often delaying treatment by days or weeks.

---

## 2. Target Users

| **Primary Users**               | **Secondary Users** |
| ------------------------------------- | ------------------------- |
| Patients with Top 9 food allergies    | Pharmacists               |
| Celiac disease patients               | Prescribers               |
| Gluten-sensitive patients             | Allergy specialists       |
| Caregivers of children with allergies | Care coordinators         |
|                                       |                           |

---

## 3. Current User Journey

### Journey board — phases, actions, and pain

|                        | ① PRESCRIBED                                                                                                  | ② SELF-RESEARCH                                                   | ③ CHASING ANSWERS                                               | ④ ALTERNATIVES                                                 | ⑤ OUTCOME                            |
| ---------------------- | -------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ | ---------------------------------------------------------------- | --------------------------------------------------------------- | ------------------------------------- |
| **Patient does** | Gets diagnosis · Receives prescription                                                                        | Searches FDA, DailyMed, Google, LLMs · Decodes ingredient aliases | Calls prescriber · Calls pharmacy · Calls manufacturer         | Finds alternatives · Checks insurance · Returns to prescriber | Still no safe option? · Starts over  |
| **Pain**         | Needs treatment now ·<br />Prescriber may not know medications  ingredients or  patients allergry history | No single source of truth · One allergen, many names              | Answers vary · Days of waiting · Burden returns to the patient | Each option restarts the research · May not be covered         | Days or weeks pass · Still untreated |

> **The loop is the problem.** Every "No" sends the patient back to research — and the entire process restarts for each alternative. Days or weeks pass while the patient remains untreated.

**Pain:** days or weeks may pass; the patient remains untreated; the condition may worsen during delays; high emotional and administrative burden.

---

## 4. Core Pain Points

| **Labeling & Ingredients**                     | **Information Access**                   | **Clinical Knowledge & Beliefs**                                             | **Burden & Delay**               |
| ---------------------------------------------------- | ---------------------------------------------- | ---------------------------------------------------------------------------------- | -------------------------------------- |
| Hidden allergens in medications (incl. gluten/wheat) | Information fragmented across multiple sources | **Belief that "medical-grade" allergens cause no harm**                      | Alternatives are difficult to identify |
| Lack of standardized allergen labeling               | No single source of truth                      | Prescriber knowledge gaps both about meds ingredients and patients allergy history | Insurance complexity                   |
| Multiple names for the same allergen                 |                                                | Pharmacist knowledge variability                                                   | Excessive coordination burden          |
| Generic vs. brand formulation differences            |                                                |                                                                                    | Delayed treatment                      |

**On the belief barrier:** clinicians and pharmacists are frequently taught that pharmaceutical-grade excipients are too purified, or present in too small a quantity, to trigger a reaction — so the question is dismissed rather than investigated. Encountered firsthand during this project's founding experience, and consistent with published work on reactions to inactive ingredients in oral medications. This is not a knowledge *gap* the patient can close with better information; it is a belief that stops the inquiry before it starts.

> ### ⇩ And the result of all of it:
>
> ## **Patients become the system integrator.**

---

## 5. Key Product Insight

To determine whether a medication is safe, patients must coordinate information across prescribers, pharmacists, manufacturers, FDA sources, DailyMed, and insurance providers.

**No single participant owns the complete workflow.**

---

## 6. Job To Be Done

> When I am prescribed a medication, help me quickly get to a medication that is both safe for my food allergies, celiac disease, gluten sensitivity, or dietary restrictions and covered by my insurance — so that I can begin treatment safely without spending days or weeks coordinating information across multiple sources.

---

## 7. Pain → Capability Mapping -WIP

Every pain below is taken directly from §4.

| Pain (from §4)                                                                                                      | Capability                                                                                    |
| -------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Information fragmented across sources · No single source of truth · Generic vs. brand formulation differences      | **Medication Intelligence** — one reliable view of what is actually in a medication    |
| Multiple names for the same allergen · Lack of standardized allergen labeling                                       | **Ingredient Alias Intelligence** — recognize every name an allergen hides behind      |
| Hidden allergens in medications (incl. gluten/wheat)                                                                 | **Allergen & Gluten Intelligence** — detect the top 9                                  |
| Alternatives are difficult to identify · Insurance complexity                                                       | **Alternative & Insurance Intelligence** — find a safe option that is actually covered |
| Belief that "medical-grade" allergens cause no harm · Prescriber knowledge gaps · Pharmacist knowledge variability | **Explainable Decision Support** — a sourced answer that is hard to dismiss            |

**Not solved by any single capability:** *excessive coordination burden*, *delayed treatment*, and *patients become the system integrator*. These are the result of all five capabilities working together — which is the product, not a feature of it.

---

## 8. Future State — the same journey, with Sanjeevani

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

**Why this example matters:** all three candidates share the same active ingredient, so the clinical decision doesn't change — only the excipients and the coverage do. Candidate 1 shows why safety alone isn't enough: a medication the patient can't afford is not a solution. Sanjeevani's job is to reach Candidate 2 in one pass, instead of the patient discovering each of these facts over three separate weeks.

---

## 9. User Stories WIP

**Primary**

> As a patient with food allergies or celiac disease, I want to know whether a medication contains ingredients that are unsafe for me, so that I can avoid adverse reactions and begin treatment safely.

**Secondary**

> As a caregiver, I want to quickly identify allergen and gluten risks within medications, so that I can make safer treatment decisions for my family member.

---

## 10. Product Principles WIP

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

---

## 11. Sanjeevani Intelligence Layers WIP

| Layer                                         | What it does                                  |
| --------------------------------------------- | --------------------------------------------- |
| **Medication Intelligence**             | Understand the medication                     |
| **Ingredient Alias Intelligence**       | Map ingredient names to known allergens       |
| **Allergen Intelligence**               | Identify Top 9 allergens                      |
| **Gluten Intelligence**                 | Identify gluten risks                         |
| **Alternative Intelligence**            | Discover potential alternatives               |
| **Insurance Intelligence** *(future)* | Assess coverage constraints                   |
| **Decision Support Intelligence**       | Help patients make safer medication decisions |

---

*Discovery grounds the product. Every capability in the PRD traces back to a pain point in Section 3.*
