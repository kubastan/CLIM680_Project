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

## **Climatology:**

**Observational data:**

### **Mean Monthly Precipitation (MSWEP)**
![Mean Monthly Precipitation (MSWEP)](https://raw.githubusercontent.com/kubastan/CLIM680_Project/figures/MSWEP_MEAN_MON.jpg)

The above figure shows the mean monthly precipitation derived from the MSWEP dataset, highlighting the climatology in the MJO active region.

The code can be found here
[Monthly Climatology Notebook](Monthly_Climatology.ipynb)

**Model:**
In the model I calculated the climatology and anomaly simutaneously based on the forecast day 0-840 due to the fact that there are 2 initializations for each month that each span 35 days. Below is the function I used to calculate the model climatology and anomaly. This calculates an anomaly for every timestep in the model output accounting for duplicate days.

[UFS_Climatology](Calculate_Anomalies_UFS.ipynb)

## **Composite**

In order to do a comparison between the observational data and the UFS model output, I created a composite based on the different phases of the MJO. That way, I could do a visual comparison and eventually test the statistical significance of the model output against the observations. Below is the composite for Precipitation anomalies for the different phases looking at the UFS and the MSWEP.

<div style="text-align: center;">
  <img src="https://raw.githubusercontent.com/kubastan/CLIM680_Project/figures/COMP_MSWEP.jpg" width="30%" style="display: inline-block;" />
  <img src="https://raw.githubusercontent.com/kubastan/CLIM680_Project/figures/COMP_UFS.jpg" width="30%" style="display: inline-block;" />
</div>

--- 
## **Differenced Composites**

I then subtracted the MSWEP composite from the UFS composite to create a difference map to see any potential biases the model had.

![Differenced Composite (UFS-MSWEP) ](https://raw.githubusercontent.com/kubastan/CLIM680_Project/figures/DIFF_COMP.jpg)

Looking above at the figure we see in the convective active phases over the Indian Ocean the UFS underdoes the amount of precipitation compared to the MSWEP. We see it also underdoes the supression behind this convection as well.

Here is a link to the notebook used for the composites:

**Composite and Differenced Composite:**
[Composite and Differenced Composite](Composite_differences.ipynb)


---

## **Statistical Significance Composite**
Below shows a plot of the differences in the composite anomalies of the UFS vs MSWEP. The shaded regions indicate areas of statistical significance(p<0.05). 










---

### **Lag Regression Analysis**
In order to further diagnose the propogation of the MJO I conducted a lagged regression analaysis. This analysis takes the lag regression of the average 10S-10N Precipitation anomalies for all the longitudes against a filtered precipitation index. 

## **Filtered Precipitation index**
This filtered precipitation index uses a space time filter onto zonal wavenumber 1-3, with a frequency of 18-80 days. This will help find the MJO signal. This precipitation index is also calculated on the average within a domain of 160-170E and 5S to 5N. This filtering was done using a kf_filter. Below is the code I used to filter my data. The code has an example using u-winds instead of precipitation.

[Filtered Precipitation Index ](kf_filter.ipynb)


Once I have the filtered precipitation index then I used a function to calculate the lag regression slope. I then plotted it in the form of a longitude and lag plot. I then calculated the slope of the maximum rainfall anomaly for each lag to estimate the phase speed. Below is the plot for the lagged precipitation for the MSWEP data. 

Here is the code I used to calculate the lag-regression.
[MSWEP Lag Regression ](MSWEP_LAG_REGRESSION.ipynb)

![MSWEP Lagged Regression Rainfall Anomalies ](https://raw.githubusercontent.com/kubastan/CLIM680_Project/figures/MSWEP_LAG.jpg)



