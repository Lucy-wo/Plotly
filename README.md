# Belly Button Biodiversity — Interactive Dashboard (D3 + Plotly)

## Summary
An interactive dashboard that explores the **Belly Button Biodiversity** dataset. Users pick a **test subject ID** from a dropdown and see:
- A **bar chart** of the top 10 OTUs,
- A **bubble chart** of all OTUs,
- A **gauge** for washing frequency (wfreq),
- A **demographic panel**.  
The page is built with **Bootstrap**, **D3 v5**, and **Plotly**, and loads data from a local `samples.json`.

---

## Goal
Make microbiome data **explorable** for non-technical users: select a subject, view their microbial composition, and compare hygiene behavior (wfreq) with observed OTUs. The dataset includes **sample arrays**, **metadata** (age, gender, location, wfreq), and **subject IDs**. 

---

## Procedure
1. **UI scaffold**  
   Bootstrap layout with a **dropdown** (`#selDataset`), a **metadata** panel, and containers for **bar**, **gauge**, and **bubble** charts. 
2. **Libraries & app script**  
   Load **D3 v5** and **Plotly** from CDNs; wire up interactions in `app.js`.
3. **Data source**  
   Read `samples.json`, which provides `names` (subject IDs), `metadata` (including `wfreq`), and `samples` (OTU ids/values/labels) used to render charts. 
4. **Interactions**  
   On dropdown change, update charts and the demographic panel (`#sample-metadata`) for the selected subject. 
5. **Hosting**  
   Optional GitHub Pages via Jekyll (theme configured).

---

## Result
- **Bar**: Top 10 OTUs per subject (`#bar`)  
- **Gauge**: Washing frequency (`#gauge`)  
- **Bubble**: All OTUs with size/color mapping (`#bubble`)  
- **Demographics**: Age, gender, location, and `wfreq` in a side panel  
All components update instantly when a new **Test Subject ID** is selected. 

---

## Business Impact
- **Education & engagement**: Makes microbial diversity tangible for students and participants in citizen-science projects.
- **Exploratory analysis**: Lets researchers or stakeholders spot patterns (e.g., common OTUs across subjects) before deeper modeling.
- **Reusable template**: This D3/Plotly pattern (dropdown → multi-panel charts) can be repurposed for other datasets.

---

## Next Steps to Make It Better
1. **Data validation & docs**: Add a schema note for `samples.json` (fields, ranges) and basic quality checks.
2. **Performance**: Lazy-load only the selected subject’s slice, or cache computed traces.
3. **Analytics**: Add summary stats (diversity indices, richness) and sorting/filter controls for OTU thresholds.
4. **UX**: Tooltips on demographics, chart legends, and mobile-first layout tweaks.
5. **Accessibility**: ARIA labels for the dropdown and keyboard navigation for chart focus.
6. **Ops**: Split `app.js` into modules (data, charts, controls), add a simple test harness, and CI to deploy to Pages.

---

## Run Locally
```bash
# from project root (serve to avoid CORS on local JSON)
python -m http.server 8000
# then open
http://localhost:8000/index.html
````

## Files

```
.
├── index.html       # Bootstrap layout, divs for dropdown/panels/charts
├── samples.json     # names, metadata (incl. wfreq), and samples arrays
├── app.js           # D3/Plotly logic (load, transform, render, update)
└── _config.yml      # GitHub Pages theme
```
