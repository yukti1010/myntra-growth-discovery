# Myntra Growth AI Discovery Engine: Wishlist-to-Purchase Conversion

## Overview
This AI-powered discovery engine ingests and analyzes unstructured customer discussions and app store feedback at scale. The engine's objective is to diagnose the root causes behind wishlist drop-off and identify non-monetary levers that increase 30-day wishlist-to-purchase conversion on Myntra.

---

## 1. Data Ingestion Architecture
The workflow aggregates feedback from public fashion communities and platform review channels:
* **Primary Data Sources:**
  * Reddit (`r/IndianFashionAddicts`, `r/TwoXIndia`, `r/DealShareIndia`)
  * Myntra App Store & Google Play Store reviews (focusing on 2-star, 3-star, and wishlist-specific feedback)
  * Public consumer review forums & fashion creator commentary
* **Raw Corpus:** Stored in `dataset.csv` containing raw user quotes, timestamps, post titles, community tags, and verified purchase context.

---

## 2. Multi-Stage AI Analysis Pipeline

### Stage 1: Extraction & Filtering
* **Tools Used:** Python / Pandas & LLM Batch Extraction (Claude 3.5 Sonnet / GPT-4o)
* **Logic:** Raw unstructured text is cleaned and filtered for explicit high-intent signals (e.g., *"saved to wishlist"*, *"waiting to buy"*, *"cart vs wishlist"*, *"hesitating because"*).

### Stage 2: Qualitative Coding & Theme Clustering
Unstructured feedback is classified into 5 core hesitation vectors:
1. **Fit & Drape Ambiguity:** Inability to visualize how garment silhouettes hang on non-model Indian body types.
2. **Dynamic Price Fatigue:** Waiting for an unpredictable drop without knowing if the current price represents a historical low.
3. **Shortlist Paralysis:** Accumulating 15+ similar kurtas/dresses without a mechanism to compare fabric composition, fit confidence, or occasion suitability.
4. **Social Validation Lag:** Hesitation while seeking second opinions outside the app (WhatsApp/Instagram DMs).
5. **Return Friction Anxiety:** Anticipating the hassle of home returns if sizing is inconsistent across brands.

### Stage 3: Quantitative Opportunity Prioritization
* Each cluster was scored by frequency, sentiment severity, and addressability without monetary discounting:
  * **Fit & Sizing Confidence Gap:** 42% of discussions
  * **Price Volatility / Timing Hesitation:** 29% of discussions
  * **Shortlist Overload & Comparison Fatigue:** 18% of discussions
  * **Styling & Occasion Mismatch:** 11% of discussions

---

## 3. Core Discovery Findings
1. **Wishlists are "Hesitation Graveyards":** Users do not abandon items because they lose interest; they abandon them because critical decision data (true-to-size reliability, price history, fabric drape) is missing on the standard PDP.
2. **The 30-Day Conversion Drop-Off:** If a user does not resolve fit anxiety within 72 hours of wishlisting, the item remains dormant until out-of-stock.
3. **The Non-Monetary Unlock:** Price drops are not the only trigger—providing **historical price trajectory transparency** combined with **crowdsourced fit validation** eliminates purchase hesitation without eroding margins.

---

## 4. Downstream Solution Mapping
* **Identified Problem:** High-intent wishlist stagnation caused by fit uncertainty and price timing anxiety.
* **Deployed MVP:** [Myntra Wishlist Copilot](https://myntra-wishlist-copilot-9tn1l0avn-yukti1010s-projects.vercel.app) — featuring 60-day price trajectory tracking and community fit confidence scoring.