# **MJO Propagation in the UFS vs Observations**

The **Madden-Julian Oscillation (MJO)** is a region of enhanced convection and precipitation in the tropics that propagates eastward from Eastern Africa to the Central Pacific Ocean. Unlike other atmospheric phenomena, the MJO evolves over longer timescales, with a period ranging between **30–90 days**. This characteristic makes the MJO a critical focus for studying intraseasonal variability.

The MJO significantly impacts the global atmospheric response, offering valuable insights for **weekly-scale weather predictions**. An **active MJO** is characterized by the eastward progression of enhanced convection, with suppressed convection following in its wake.  

This project investigates the ability of the **Unified Forecast System (UFS)**, a coupled ocean-climate model, to simulate this atmospheric cycle.

---

## **Data Overview**

### **1. Observational Data**
- **Dataset**: [MSWEP (Multi-Source Weighted-Ensemble Precipitation)](https://www.gloh2o.org/mswep/)
- **Resolution**:
  - Spatial: **0.1°**
  - Temporal: **Daily (04/01/2011 – 04/18/2018)**
- **Variable**: Daily Precipitation (**mm/day**), derived from MSWEP and sliced.

---

### **2. Model Data**
- **Dataset**: UFS Prototype 8 (**UFS P8**)
- **Resolution**:
  - Spatial: **0.25°**
  - Temporal: **Daily (04/01/2011 – 04/18/2018)** initialized on the 1st and 15th of each month spanning 35 days
- **Variable**: Precipitation (**mm/day**), pre-processed to align with observational data.

---

### **3. Climate Index**
- **Dataset**: MJO Daily Time Series (1979 – Present)
- **Description**:  
  The dataset provides projections of **20–96 day filtered ERA5 OLR**. It includes all eastward and westward wave numbers projected onto daily spatial **EOF patterns** of **30–96 day eastward filtered OLR** from ERA5.  
  - **EOFs** are calculated using data from 1940 to the present.

---

### **Code Description:**

**Climatology:**
Below shows the Monthly Climatology for precipitation in the MJO active region. We see that in the summer months the highest precipitation amounts shift north.




















Results: What does your analysis show that is scientifically interesting? What have you discovered?  
Summary: Provide short summary of what you learned from your analysis of your data (both scientific and technical), what you would do next to advance this analysis, and any challenges or issues you encountered/overcame.
