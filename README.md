# THU_RML
This repository gives access to the datasets and source code for reproducing the results from our paper. <br /> Our paper uses a quasi-experimental framework to investigate the impact of recreational marijuana legalization (RML) across North American states. 

# Title
**The American Green Waves: Effects of Recreational Marijuana Legalization on Firm Performance, Productivity, and Innovation**

# Abstract
Incorporating the theoretical nexus between individual health and economic growth, we employ a quasi-experimental framework to investigate the impact of recreational marijuana legalization (RML) and marijuana's increased use on firm behaviors. Leveraging the staggered implementation of RML across 14 U.S. states and Canadian provinces from 2007 to 2021, we utilize a robust difference-in-differences (DiD) event-study methodology. Despite an initial positive market response to RML in the short term, indicating a cultural acceptance of marijuana use, our analysis reveals a subsequent reduction in overall firm performance over the long term, manifested through declines in sales, profitability, and valuation. More importantly, we find that RML detrimentally impacts firms' innovation capacity, evidenced by declines in patent quality, originality, and research impact. These results are associated with a decrease in employee productivity and collaborative effectiveness among diverse individuals, suggesting a negative influence of RML on the production and innovation processes within firms, from ideation to realization. These results are further associated with a significant increase of 2.87\% in marijuana prevalence among adults, which coincides with an immediate decline in individual cognitive function, as proxied by an increase in work-related and automobile accidents.


# Authors
Geoffrey Ducournau, *Tsinghua University* <br />
Jinliang Li, *Tsinghua University* <br />
Yan Li, *The University of Hong Kong* <br />
Zigan Wang, *Tsinghua University* <br />
Qie Ellie Yin, *Hong Kong Baptist University* <br />
***All errors are ours.***

# Correspondence
Geoffrey Ducournau, *Tsinghua University* [gduc@sem.tsinghua.edu.cn]

# Acknowledgments
This work was supported by the School of Economics and Management (SEM) of Tsinghua University and received funding from the China Ministry of Science and Technology (**2023YFC3305402**).

# Data and Replication Code:
## Table3 and TableA3:
> From the folder ./Public_Firm_Level_Samples download the sample ```S1.dta``` and run the following commands:
```bash
eventstudyinteract Abnormal_Stock_Return  g_m5 g_m4 g_m3 g_m2 g_0 g_1 g_2 g_3 g_4, cohort(cohort) control_cohort(never_treat) covariates(GDP GDP_Growth Population Density Amihud_Illiq Returns_Volatility Holding_Returns Size PTBI PTBI_VOL Leverage Firm_Age) absorb(Firm Industry_Year) vce(cluster Industry_Year)

matrix b = e(b_iw)
matrix V = e(V_iw)
ereturn post b V
lincom (g_m5 + g_m4 + g_m3 + g_m2)/4
lincom (g_0 + g_1 + g_2 + g_3)/4
```
> From the folder ./Public_Firm_Level_Samples download the sample ```S2.dta``` and run the following commands:
```bash
eventstudyinteract Analyst_Forecast  g_m5 g_m4 g_m3 g_m2 g_0 g_1 g_2 g_3 g_4, cohort(cohort) control_cohort(never_treat) covariates(GDP GDP_Growth Population Density Size PTBI PTBI_VOL Leverage Firm_Age) absorb(Firm Industry_Year) vce(cluster Industry_Year)

matrix b = e(b_iw)
matrix V = e(V_iw)
ereturn post b V
lincom (g_m5 + g_m4 + g_m3 + g_m2)/4
lincom (g_0 + g_1 + g_2 + g_3)/4
```

## Tables4-6,8 and TablesA4-A6,A8:
> From the folder ./Public_Firm_Level_Samples and ./Private_Firm_Level_Samples download ```S3.dta```, ```S4.dta```, ```S5.dta```, ```S6.dta``` and run the following commands:
```bash 
eventstudyinteract $DEP_VAR$  g_m5 g_m4 g_m3 g_m2 g_0 g_1 g_2 g_3 g_4, cohort(cohort) control_cohort(never_treat) covariates(GDP GDP_Growth Population Density Size PTBI PTBI_VOL Leverage Firm_Age) absorb(Firm Industry_Year) vce(cluster Industry_Year)

matrix b = e(b_iw)
matrix V = e(V_iw)
ereturn post b V
lincom (g_m5 + g_m4 + g_m3 + g_m2)/4
lincom (g_0 + g_1 + g_2 + g_3)/4
```
where ```$DEP_VAR$``` corresponds to: ```Sales_Growth```, ```ROA```, ```Cash_Holding```, ```RD_Intensity```, ```Capital_Intensity```, ```Tangibility```, ```TobinQ```, ```Stock_Return```, ```Sale_Ratio_Employee``` ```ROA_Ratio_Employee```, ```Employee_Reinforcement```, ```Apply```, ```Grant```, ```Citation```, ```Examiner_Citation_Callback```, ```Originality```, ```Hit```, ```Weak```, ```Social```, ```Health```, ```Training```, ```Diversity```

## Tables7, A7 columns 1-4:
> From the folder ./State_Level_sample download ```S8.dta``` and run the following commands:
```bash 
reghdfe $DEP_VAR$  g_m5 g_m4 g_m3 g_m2 g_0 g_1 g_2 g_3 g_4  GDP GDP_Growth Population Density Police_Officers Religion_Index $DEP_VAR_L1$, absorb(State Year) vce(cluster State)

matrix b = e(b_iw)
matrix V = e(V_iw)
ereturn post b V
lincom (g_m5 + g_m4 + g_m3 + g_m2)/4
lincom (g_0 + g_1 + g_2 + g_3)/4
```
where  ```$DEP_VAR$``` corresponds to:  ```Car_Accident```, ```Marijuana_Arrest```, ```Hard_Drug_Arrest```, ```Marijuana_Prevalence_12_17```, ```Marijuana_Prevalence_18_25```, ```Tax_Revenue```, ```TFP```, ```Unemployment_Rate```, ```Working_Accident```

## Tables7, A7 column 5:
> From the folder ./School_Level_sample download ```S7.dta``` and run the following commands:
```bash
eventstudyinteract School_Performance  g_m5 g_m4 g_m3 g_m2 g_0 g_1 g_2 g_3 g_4, cohort(cohort) control_cohort(never_treat) covariates(GDP GDP_Growth Population Density Police_Officers Religion_Index Tuition_Fee Student Student_Ratio_Teacher School_Performance_L1) absorb(School Year) vce(cluster School)

matrix b = e(b_iw)
matrix V = e(V_iw)
ereturn post b V
lincom (g_m5 + g_m4 + g_m3 + g_m2)/4
lincom (g_0 + g_1 + g_2 + g_3)/4
```



 
