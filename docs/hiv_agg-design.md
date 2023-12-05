# HIV HMIS System Design { #hiv-agg-design }

Version 2.0.0

## Introduction

This document describes the conceptual system design in DHIS2 for integrating routine HIV programme and case data into a national HMIS for analysis and use. The system design and metadata support all core and optional indicators from routine data sources in the WHO's [Consolidated guidelines on person-centred HIV strategic information: strengthening routine data for impact (2022)](https://www.who.int/publications/i/item/9789240055315), including HIV case surveillance, testing & treatment indicators (n=57) and HIV prevention indicators (n=43).

Dashboards are designed to support national, district and facility levels to conduct routine analysis on a core set of indicators as described in the [WHO Analysis and Use of Health Facility Data Guidance for HIV Programme Managers](https://cdn.who.int/media/docs/default-source/documents/ddi/facilityanalysisguide-hiv.pdf) (2019).

### Acknowledgements

HISP Centre is grateful to the WHO Global HIV Programme and Division of Data, Analytics, and Delivery for Impact (DDI) for their ongoing partnership through a Collaborating Centre agreement. Subject matter expertise from the HIV programme and other focal points was crucial for the development and optimization of this product. We are also grateful to the Global Fund for their financial support to develop the HIV product suite for DHIS2. 

## System Structure

### Architecture

The HMIS module for HIV is designed to support typical national health information system architecture in countries. The architecture recognizes that DHIS2 may not be the primary source for all HIV-related data, but plays a significant role in bringing data together for routine analysis and triangulation with other sources. 

![Illustrative HIV Information System Architecture](resources/images/hiv_architecture_simple.png)

Following this illustrative architecture, the HMIS -- leveraging the robust aggregate data model that is optimized for analysis -- serves as a central repository for routine and other data sources. Individual level data systems for person-centered monitoring are maintained separately from the HMIS for privacy, confidentiality, and optimized performance. These individual level data systems may use DHIS2 Tracker for person-centered monitoring of at-risk populations enrolled in prevention programs, as well as life-long monitoring of individual HIV cases to produce accurate, timely data on strategic information indicators such as linkage of individuals at substanital risk to prevention services, PLHIV currently on treatment, viral load testing coverage, and initiation of TB preventive treatment among PLHIV. 

For more information on designing and using DHIS2 for person-centered monitoring, please see the guides on HIV Prevention and HIV Case Surveillance. 

### Data Sets

The following datasets describe the frequency and type of data to be integrated into the HMIS for routine programme monitoring & analysis. Note that while datasets can be used for aggregate paper-based reporting among facilities and sites that have not yet digitized individual-level reporting, these datasets **also** serve as a central repository for bringing anonymized, aggregated data from DHIS2 Tracker, EMRs, and other sources. These datasets and their corresponding data elements provide the analytical dimensions needed for generating indicators and performant dashboards at national scale and for sub-national use. 

| Name | Periodicity | Purpose |
| --- | --- | --- |
| HIV Monthly | Monthly | Reporting of health facility data related to HIV testing, treatment and viral load suppression |
| HIV annual data | Annual | Captures estimated number of people living with HIV |

## HIV Programme Dashboards 

Two overarching programmatic monitoring dashboards are available and optimized for users at the national programme and district levels. These dashboards use indicators and data visualizations from across programmatic interventions, including the 95-95-95 cascade to monitor the number of people living with HIV who know their HIV status, are on treatment, and virally suppressed; incidence and mortality, new case diagnoses, availability of HIV testing services and essential HIV commodities at facilities and treatment sites; and comorbidities with TB, STIs, and other related diseases. These dashboards include aggregated data from person-centered monitoring using DHIS2 Tracker for prevention and case surveillance; but also include programmatic data from other key sources for holistic programme management. 

The dashboards and underlying indicators included in the HMIS module are designed in a way that prioritizes **bringing data together in DHIS2 as an integrated platform for analysis** from across paper-based and digital sources -- regardless of whether DHIS2 Tracker, EMRs or other digital tools are used at the lowest levels. It also brings in semi-routine data such as Health Facility Profile data on availability and readiness for service delivery, as well as non-routine data like Spectrum estimates and population denominators to allow for meaningful analyses. 

### HIV HMIS - National Dashboard

The national HIV dashboard provides national programmes and other stakeholders with timely key metrics for monitoring the HIV epidemic in their country as well as progress of key HIV interventions. It is optimized to assist in strategy and policy decisions, intervention planning, resource allocation and monitoring key performance indicators. 

![HIV 95-95-95 Targets](resources/images/02_dash_HIV_cascade.png)

![HIV case diagnoses and geographic distribution](resources/images/02_dash_HIV_cases.png)

![PLHIV linked and currently on ART](resources/images/02_dash_HIV_treatment.png)

![Viral Suppression and Comorbidities](resources/images/02_dash_HIV_viral_suppression.png)

![Key performance indicators by sub-national level](resources/images/02_dash_HIV__KPIs.png)

### HIV HMIS - District Dashboard 

## HIV Prevention Dashboards & Datasets

### Prevention Dashboards

Thematic dashboards for monitoring various aspects of HIV prevention programming have been developed based on the core indicators included in WHO’s 2022 [*Consolidated guidelines on person-centred HIV strategic information*](https://www.who.int/publications/i/item/9789240055315). Standard dashboard visualizations developed with WHO’s guidance can be rendered at national or sub-national levels depending on user configuration. 

Dashboards are served entirely by DHIS2 *indicators* as described in the next section. The following dashboards are available for routine analysis of HIV prevention activities.

**HIV Prevention - 01. HTS: HIV testing services**

**HIV Prevention - 02. PrEP: Pre-exposure prophylaxis** 

**HIV Prevention - 03. PEP: Post-exposure prophylaxis**

**HIV Prevention - 04. NSP**

**HIV Prevention - 05. OAMT**

**HIV Prevention - 06. VMMC: voluntary medical male circumcision**

**HIV Prevention - 07. STI: sexually transmitted infections**

**HIV Prevention - 08. Viral Hepatitis** 

**HIV Prevention - 09. Health Facility**

Visualizations in this dashboard are optimized for service delivery site level staff. 

**HIV Prevention - 10. District**

Visualizations in this dashboard are optimized for district level programme staff. 

### Prevention Indicators

The toolkit contains DHIS2 indicators which represent the core and optional indicators listed in the WHO’s 2022 [[Consolidated guidelines on person-centred HIV strategic information](https://www.who.int/publications/i/item/9789240055315)](https://www.who.int/publications/i/item/9789240055315). 

All HIV prevention dashboards are served by DHIS2 indicators, which often combine numerators and denominators from individual-level data or other sources. The DHIS2 indicators are mapped and aligned to the indicator definitions and descriptions contained in the WHO’s Digital Adaptation Kit (DAK) for HIV, second edition.

Two indicator groups have been configured to group the indicators as follows: 

- HIV prevention - WHO standard list (K6esSqLr8Ta): contains all core and optional WHO SI indicators. 
- HIV Prevention - Dashboard (MOrMTBtGQAB): contains all indicators that are used in the standard recommended dashboards; these represent a subset of the WHO standard list

### Prevention Datasets

As described above, dashboards are populated using the aggregate data model, using DHIS2 indicators. Aggregate datasets, data elements and category combinations have been configured to serve the analytics based on the dimensions of analysis included in the strategic information and data use guidelines. When used in tandem with the DHIS2 Prevention Tracker, values from program indicators are mapped to their corresponding aggregate data element and CatCombo in order to populate the *numerators* and *denominators* for all the indicators included above. These datasets can also be used for aggregated reporting among sites that do not yet have Tracker; or sites that submit routine reports that aggregate data from another individual level data collection tool. 

Detailed description of the configuration of program indicators for aggregating tracker data is described in the section **Program Indicators.** Mapping and exchange of Tracker data to Aggregate data model is described in the **section Metadata Mapping & Data Exchange.** 

There are three (3) distinct datasets for capturing prevention data. These have been designed based on the analytical needs represented in the WHO’s analysis framework, whereby some metrics may be analyzed on a monthly basis while others are only reported and analyzed annually. 

1. HIV Prevention - Population estimates (annual)
2. HIV prevention (yearly)
3. HIV prevention (monthly) 

#### HIV Prevention - Population estimates

This dataset contains four (4) data elements which are *not* derived from routine reporting; and are typically made available by the HIV programme on an annual basis. These data elements are used for populating denominators for core indicators from the strategic information guidelines. The data set should be assigned to the lowest administrative level for which high-quality estimates exist and can be used for analysis. 

These estimates are used for the calculation of the following indicators: 

- HIV - PRV.3 PrEP coverage (Population level) (%)
- HIV - PRV.8 NSP coverage (Population level) (%)
- HIV - PRV.9 Regular NSP access (Population level) (%) 
- HIV - PRV.10 Needles–syringes distributed (Population level) (ratio)
- HIV - PRV.11 OAMT coverage (Population level) (%) as today
- HIV - PRV.12 Total person–years on OAMT (Population level)
- HIV - INC.1 HIV incidence (/10000 uninfected)

/resources/images/hiv_prevention_pop_estimates.png

#### HIV Prevention (yearly)

This dataset contains data elements required for annual analysis based on data aggregated from HIV prevention service delivery & distribution sites. It includes the following:

- Clients attending HIV prevention services
- Number of clients by key population category
- Testing services & HIV positive tests by key population category 
- Clients tested for HIV and testing positive for HIV by age and sex
- PrEP recipients by key population category
- PrEP recipients by age and sex
- Clients prescribed PEP and clients testing HIV positive after receiving prep, disaggregated by key population category
- Clients completing PEP by age band
- Clients prescribed PEP by age and sex
- Needles & syringes distributed and number of recipients by age and sex
- Clients starting, received and maintained on OAMT
- Clients undergoing VMMC by age; clients experiencing adverse events following VMMC
- Clients tested for gonorrhoea and syphilis by age and sex
- Clients tested for viral hepatitis

#### HIV Prevention (monthly)

This dataset contains data elements for routine monthly analysis based on data aggregated from HIV prevention service delivery & distribution sites. It contains the following: 

- Clients attending HIV prevention services
- HIV testing services (HTS): tests performed, positive test results, self testing kits distributed, clients receiving interventions within 7 days of a negative result
- PrEP: distributed by product type
- PEP: clients prescribed with PEP
- Condoms distributed
- Clients tested for STIs and diagnosed with STIs
- Clients tested for viral hepatitis

#### Prevention Data Elements

Aggregate domain data elements that are expected to be populated for dashboard analyses are grouped within the Data Element Group **‘HIV prevention (dashboard)’ [LUxGwKWIpME]**. The data element group allows for easy identification of which data elements should be targeted for exchanging Tracker data to aggregate data elements using the Data Exchange App. 

Some of the data elements contained in the datasets above are cloned (as distinct DEs with distinct DHIS2 IDs) and included in both the monthly and yearly dataset. These cloned metrics are typically counting the number of unique clients within a month or a year; and cannot be aggregated by month to produce the correct number since we are interested in a cohort of clients, not the number of services provided. For example, the same client can access the service multiple times during the year; if we collect this information on a monthly basis and sum across the annual period, we cannot be sure that we did not count the same client multiple times. In these cases, the DEs are clearly labeled with a post-fix as monthly or yearly, as in the example below: 

- HIV - Volume: Clients attending HIV prevention services (monthly)
- HIV - Volume: Clients attending HIV prevention services (yearly)

## Validation Rules

The full list of validation rules is available in the Metadata reference file.

## References

1. [WHO Analysis and Use of Health Facility Data Guidance for HIV Programme Managers](https://cdn.who.int/media/docs/default-source/documents/ddi/facilityanalysisguide-hiv.pdf)  (March 2019)
2. WHO toolkit for analysis and use of health facility data, accessed at: [who.int/data/data-collection-tools/health-service-data/toolkit-for-routine-health-information-system-data/modules](https://www.who.int/data/data-collection-tools/health-service-data/toolkit-for-routine-health-information-system-data/modules)
3. WHO (2022). Consolidated Guidelines on person-centred HIV strategic information: strengthening routine data for impact (2022), accessed at: [who.int/publications/i/item/9789240055315](https://www.who.int/publications/i/item/9789240055315)
