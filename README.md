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

##**Climatology:**

**Observational data:**

### **Mean Monthly Precipitation (MSWEP)**
![Mean Monthly Precipitation (MSWEP)](https://raw.githubusercontent.com/kubastan/CLIM680_Project/figures/MSWEP_MEAN_MON.jpg)

The above figure shows the mean monthly precipitation derived from the MSWEP dataset, highlighting the climatology in the MJO active region.

The code can be found here
[Monthly Climatology Notebook](Monthly_Climatology.ipynb)

**Model:**
In the model I calculated the climatology and anomaly simutaneously based on the forecast day 0-840 due to the fact that there are 2 initializations for each month that each span 35 days. Below is the function I used to calculate the model climatology and anomaly. This calculates an anomaly for every timestep in the model output accounting for duplicate days.

[UFS_Climatology](Calculate_Anomalies_UFS.ipynb.ipynb)

## **Composite**

In order to do a comparison between the observational data and the UFS model output, I created a composite based on the different phases of the MJO. That way, I could do a visual comparison and eventually test the statistical significance of the model output against the observations. Below is the composite for Precipitation anomalies for the different phases looking at the UFS and the MSWEP.

<div style="display: flex; justify-content: space-between;">
  <img src="https://raw.githubusercontent.com/kubastan/CLIM680_Project/figures/COMP_MSWEP.jpg" width="45%" />
  <img src="https://raw.githubusercontent.com/kubastan/CLIM680_Project/figures/COMP_UFS.jpg" width="45%" />
</div>


























Results: What does your analysis show that is scientifically interesting? What have you discovered?  
Summary: Provide short summary of what you learned from your analysis of your data (both scientific and technical), what you would do next to advance this analysis, and any challenges or issues you encountered/overcame.
