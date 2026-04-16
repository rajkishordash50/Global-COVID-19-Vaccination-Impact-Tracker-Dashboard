**Project Title : Global COVID-19 Vaccination & Impact Tracker**

**Headline **

End-to-end analytics dashboard monitoring 8B+ cases, 110M deaths, and 8B vaccinations worldwide  
Consolidated WHO country-level data to track recovery, mortality, and vaccination equity trends  
Tech: Power BI, DAX, Power Query, World Map Visual, Time Intelligence

**2. Short Description / Purpose**

A single-page Power BI dashboard that aggregates global COVID-19 statistics from 2020-2021 to provide real-time visibility into confirmed cases, deaths, recoveries, and vaccination rollout. Replaces fragmented WHO reports and enables drill-down analysis by country, date, and WHO region to support public health monitoring and policy decisions.

**3. Tech Stack**

**BI & Visualization**	Power BI Desktop, DAX, Power Query M, Map Visual, Scatter Chart, Gauge, Donut
**Data Modeling**	               Star Schema, Calendar Table, Measures, Calculated Columns
**Data Source**	               WHO COVID-19 Dataset / Our World in Data CSV
**Design**	                              KPI Cards, Time-series Line Chart, Stacked Bar, Pie Chart, Geographic Map


**4. Data Source**

Primary: `WHO_COVID19_Global_Data` - Country-level daily aggregates 2020-2021  
Fields used: `Date_YMD`, `COUNTRY`, `WHO_REGION`, `Total_Confirmed`, `Total_Deceased`, `Total_Recovered`, `TOTAL_VACCINATIONS`, `PERSONS_FULLY_VACCINATED_PER100`, `NUMBER_VACCINES_TYPES_USED`  
Grain: 1 row per Country per Date. ∼60K+ rows after processing.

**5. Features and Highligh**ts

**5.1 Business Problem**

Public health teams and media lacked a unified view of pandemic progression. Key issues:
1. *Data Fragmentation*: Cases, deaths, and vaccinations reported in separate WHO CSVs
2. *No Recovery Context*: Most trackers showed cases/deaths but not recovery rate vs mortality
3. *Vaccination Blind Spots*: Hard to compare countries by vaccines administered, fully vaccinated %, and vaccine type diversity
4. *Static Reporting*: WHO situational reports were PDF-based with 24-48hr delay and no interactivity

**5.2 Goal of the Dashboard**

1. *Centralize*: Show 5 core KPIs in 1 view: Total Cases, Deaths, Vaccinations, Fully Vaccinated %, Vaccination Rate
2. *Track Trends*: Plot mortality curve Mar 2020-May 2020 and compare recovered vs confirmed by country
3. *Compare Equity*: Visualize geographic spread via map + compare countries by vaccination coverage and vaccine types used
4. *Enable Filtering*: Add Date, Country, WHO_REGION slicers to drill from global to country-level analysis

**5.3 Walk Through the Key Visuals**

Visual	Type  Purpose & DAX Logic

**KPI Cards Row**	Cards	Global totals: `Total Cases = SUM('COVID'[Total_Confirmed])`, `Total Deaths = SUM('COVID'[Total_Deceased])`, `Vaccinations = SUM('COVID'[TOTAL_VACCINATIONS])`

**Sum of Total Deceased by Year/Quarter**	Scatter/Line Chart	Tracks mortality curve acceleration Mar-May 2020. X-axis=Date, Y-axis=Sum(Deceased), Legend=Total Recovered bins

**Sum of Recovered vs Confirmed by Country**	 Stacked Bar	Compares recovery rate per country. `Recovery % = DIVIDE([Sum of Recovered], [Sum of Confirmed])`
**COUNTRY Map**	Filled Map	Geographic hotspot view. Bubble size = Total Confirmed. Identifies outbreak clusters
**Date/COUNTRY/WHO_REGION**	Slicer	Multi-select filter for time and geography. Enables 2021-04-09 to 2021-10-22 drill-down
**Count of Country by Vaccine Types Used**	Pie Chart	25.88% countries used 4 vaccine types, 16.67% used 3. Measures supply diversity
**Fully Vaccinated per 100**	Gauge	Current global rate = 9.80K per 100K population. Target line at 19.61K for 100%


**5.4 Highlight the Insights**

1. *Mortality Curve*: Deceased count showed exponential growth Mar-May 2020 before vaccinations, flattening post Apr 2021 rollout
2. *Recovery Gap*: Stacked bar shows some countries had Confirmed >> Recovered, indicating reporting lag or healthcare strain
3. *Vaccine Inequity*: Gauge at 9.80K/19.61K shows only ∼50% global full vaccination by Oct 2021. Map shows Africa/South America lighter coverage
4. *Supply Diversity*: 25.88% of countries relied on 4 vaccine types. 8.77% used only 1 type, indicating supply chain risk
5. *Scale*: 8B vaccinations administered vs 8B confirmed cases shows global mobilization scale but 110M deaths highlight severity

**5.5 Show the Business Impact**

Metric	Result
**Analysis Speed**	Reduced time to answer "Which country has lowest recovery rate?" from 30 min of Excel to 5 sec filter
**Data Integration**	Merged 3 WHO datasets into 1 model. Eliminated manual vlookup errors
**Equity Monitoring**	Identified 8.77% single-vaccine countries for WHO supply intervention targeting
**Trend Communication**	Mortality curve visual used to explain pandemic phases to non-technical stakeholders
**Reusability**	Model structure supports daily refresh. Can be updated for new variants/outbreaks

**6 Screenshot / Demo**
see the demo 
https://github.com/rajkishordash50/Global-COVID-19-Vaccination-Impact-Tracker-Dashboard/blob/main/COVID%2019_DASHBOARD%20IMAGE.png


