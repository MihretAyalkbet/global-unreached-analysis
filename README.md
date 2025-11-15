# global-unreached-analysis
Geospatial visualization of Unreached and Frontier People Groups using Tableau. Includes cleaned dataset, world map built from latitude/longitude, population-based sizing, and filters for unreached status and regions. Exported images and Tableau Public link included.
#  Unreached People Groups — Tableau Visualization Project

This repository contains a Tableau visualization project that maps global **Unreached** and **Frontier** people groups using the dataset `UnreachedPeoplesByCountry.new.csv`.  
The visuals highlight where the highest-need communities are located and provide quick insights into population, religion, language, and priority status.


---

##  Dataset (brief)

`UnreachedPeoplesByCountry.new.csv` includes columns such as:

- `PeopNameInCountry` — people group name in country  
- `Ctry` — country  
- `RegionName` — region/continent  
- `Latitude`, `Longitude` — coordinates (decimal degrees)  
- `Population` — numeric population of the people group  
- `PrimaryReligion` — dominant religion  
- `PrimaryLanguageName` — primary language  
- `LeastReached` — Yes/No flag  
- `Frontier` — Yes/No flag (Frontier = most unreached of the unreached)

---

##  Visualization 1 — World Map of Unreached People Groups

**What it shows**
- Each point = a people group.
- Dot size = population (`Population`).
- Dot color = `Frontier` or `LeastReached` (or `Ctry` / `RegionName`, depending on the view).
- Tooltip shows: group name, population, religion, language, frontier status.

**Tableau basics to reproduce**
1. Connect → Text File → `UnreachedPeoplesByCountry.new.csv`  
2. Set `Latitude` & `Longitude` → Right-click → Geographic Role → Latitude/Longitude  
3. Drag `Longitude` → Columns, `Latitude` → Rows  
4. Drag `Population` → Size (use `SUM(Population)` not `AVG`)  
5. Drag `Frontier` → Color (or `LeastReached`)  
6. Drag `PeopNameInCountry` → Detail and Tooltip (so each row is a unique point)  
7. Map → Map Layers → enable Country Borders, Labels, choose Light/Dark style  
8. Worksheet → Export → Image → save as `/images/unreached_map_custom.png`

---

##  Visualization 2 — Top 10 Unreached Countries

**What it shows**
- Horizontal bar chart of the top 10 countries by total unreached population.

**Tableau basics to reproduce**
1. New Worksheet → Drag `Ctry` → Rows, `Population` → Columns  
2. Sort descending by `SUM(Population)`  
3. Filter `Ctry` → Top → By Field → Top 10 by `Population` → Sum  
4. Add `RegionName` or `LeastReached` to Tooltip or Color as needed  
5. Export image → `/images/top10_unreached_countries.png`

---

##  What is a Frontier People Group?

A **Frontier People Group** is:
- A people group with **very few or no followers** of Christianity.
- Has **minimal access** to churches, missionaries, or Christian resources.
- Often **culturally/linguistically/geographically isolated**.
- Typically flagged as `Frontier = Yes` and prioritized for outreach.

---

##  Tools & Skills Demonstrated

- Tableau Desktop / Tableau Public: mapping, map layers, marks/tooltip, color & size encoding, filters, exporting images.  
- Basic data hygiene: ensuring lat/long numeric types, handling aggregation (use `SUM` for population), using unique ID/detail to prevent AVG lat/long.

---

##  Notes & Tips

- If dots appear clustered in one spot, check that Tableau is not aggregating `Latitude`/`Longitude` (convert them to **Dimensions** or add a unique ID to **Detail** so each row plots individually).
- Always use `SUM(Population)` on Size/Color to reflect total population, not `AVG`.
- For portfolio presentation, prefer a **clean background** (Light/Dark) and clear color contrast for `Frontier = Yes`.

---

##  Quick Insights

- Unreached and frontier groups are concentrated in **South Asia, the Middle East, and parts of Africa**.
- A handful of countries account for the majority of the unreached population.
- Frontier groups are usually smaller and more isolated than other least-reached groups.

---

##  Next steps (optional)
- Create a combined **Dashboard** with the world map + Top 10 chart + filters (Region, Frontier).
- Publish interactive dashboard to **Tableau Public** and embed the link in this README.
- Add a small Python script (Pandas) to validate coordinates & population before loading into Tableau.

---

##  License
Include your preferred license here (e.g., MIT).  


