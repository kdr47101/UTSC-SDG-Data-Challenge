# Decoupling Growth from Emissions — UTSC SDG Data Challenge (1st Place)

> Can countries grow living standards **without** growing emissions?  
This project tests whether **SDG 8.1.1** (annual growth of real GDP per capita) can be achieved while stabilizing or lowering **SDG 13.2.2** (total greenhouse gas emissions), and identifies the macro drivers that separate “grow-green” economies from high-emitting ones.

**Highlights**
- **Scope:** 117 countries, 2000–2017 (18 years)
- **Key construct:** intensity ratio **β = ΔGDPpc% / ΔGHG%** (higher = growth tightly coupled to emissions; β < 0 = decoupled)
- **Methods:** EDA → cross-correlation (lead/lag) → multivariate regression on β  
- **Top drivers of β:** **industry value added**, **natural-resources rents**, **foreign investment** (statistically significant)  
- **Outcome:** Model explains ~50% of β variance; profiles that sustain growth with low emissions typically show **higher industry value added** and **lower dependence on foreign investment**  
- **Result:** **1st place** in the UTSC Sustainable Development data challenge (evidence in repo)

---

## 1) Problem statement

We ask whether economies can raise **real GDP per capita** (SDG 8.1.1) while **maintaining or reducing total GHG emissions** (SDG 13.2.2). We test for decoupling patterns and quantify which macro factors most influence the **growth–emissions coupling**. :contentReference[oaicite:4]{index=4}

---

## 2) Data

- **GDP per capita growth (annual %)** — World Bank WDI, code `NY.GDP.PCAP.KD.ZG` (proxy for SDG 8.1.1). :contentReference[oaicite:5]{index=5}  
- **Total GHG emissions (CO₂-eq)** — UN SDG Indicators metadata (indicator 13.2.2). :contentReference[oaicite:6]{index=6}  
- Additional macro covariates: **industry value added**, **natural resources rents**, **foreign direct investment** (World Bank WDI series).

---

## 3) Methodology (overview)

1. **EDA:** Compute country-level **average percentage changes** in GDP per capita and GHG emissions over 2000–2017 and classify countries by coupling:  
   - **β > 1**: strongly coupled (emissions growth outpaced decoupling)  
   - **0 < β < 1**: weakly coupled  
   - **β < 0**: decoupled (GDP↑ while GHG↓)  
2. **Lead–lag analysis:** Cross-correlation of yearly GDPpc% vs. GHG% per country to see whether growth tends to **lead** or **follow** emissions.  
3. **Regression:** Fit a **multiple linear regression** with response **β** and predictors (country averages over the window) to reduce noise from short-run shocks. Significant predictors: **industry value added**, **natural-resources rents**, **foreign investment**.  
4. **Interpretation:** Compare predictor distributions between “high-emission/low-growth” vs. “low-emission/high-growth” groups to surface practical levers.

*Rationale for averaging:* 10-year (approx.) averages dampen transitory noise (e.g., recessions, commodity spikes) and better reflect structural energy and industrial composition. :contentReference[oaicite:7]{index=7}

---

## 4) Results (brief)

- **Explained variance:** ~**50% R²** on β using the three predictors above.  
- **Group contrasts:**  
  - **Low-emission / high-growth** economies tend to show **higher industry value added**, **lower foreign-investment inflows**, and **similar natural-resource rent shares** relative to **high-emission / low-growth** peers (see table in `reports/`).  
- **Lead–lag:** Patterns vary by country; no universal directionality (growth→emissions vs. emissions→growth) across all 117 countries.

Full details, tables, and figures are in `reports/` and the evidence notebook. :contentReference[oaicite:8]{index=8}

---
