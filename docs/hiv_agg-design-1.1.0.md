# HIV Digital Data Package Aggregate System Design { #hiv-agg-design-110 }

Version: 1.1.0

## Introduction

This document describes the conceptual system design in DHIS2 for the HIV configuration package for aggregate reporting. The package is designed to facilitate the capture and analysis of a core set of indicators through routine health management information systems (HMIS) as described in the [WHO Analysis and Use of Health Facility Data Guidance for HIV Programme Managers](https://cdn.who.int/media/docs/default-source/documents/ddi/facilityanalysisguide-hiv.pdf) (2019).

The HIV package includes two main components:

1. Aggregate data reporting component (data set, data elements, category combinations for required disaggregation, etc).
2. Dashboard component: focusing on how the data collection part of the configuration has been designed in DHIS2 (i.e. data sets and data elements).

This document is intended for use by DHIS2 implementers at country and regional level to be able to support implementation and localization of the configuration package while adhering to the design principles set forth.

## DataSets

The HIV configuration package for aggregate reporting contains the following datasets for entering input data as summarized below;

| Name | Periodicity | Purpose |
| --- | --- | --- |
| HIV Monthly | Monthly | Reporting of health facility data related to HIV testing, treatment and viral load suppression |
| HIV annual data | Annual | Captures estimated number of people living with HIV |

## DataSet sections

This section will present the main sections (tables) of the datasets (reporting forms), explaining their configuration.

### HIV Section

This section covers the general HIV testing, treatment and viral suppression and it has been configured with data elements using a disaggregation for age (0-14 yrs, 15+yrs) and Sex (Male, Female) with the totals automatically computer in the process of data entry.

![](resources/images/HIVPKG1.png)

### PMTCT Section

This section covers the PMTCT with ANC testing and treatment and it has been configured with data elements that are not disaggregated as the guidelines.

![](resources/images/HIVPKG2.png)

#### Data Elements

These are the data elements in the used to create the dataSets above and also to configure the indicators. They broadly cover; testing, treatment, retention, viral suppression, PMTCT and estimated PLHIV.

| **name** | **Disaggregation** | **Section** | **DataSet** |
| --- | --- | --- | --- |
| HIV - ANC clients newly tested HIV positive and started on ART | none | PMTCT | HIV Monthly |
| HIV - ANC clients tested for HIV | none | PMTCT | HIV Monthly |
| HIV - ANC clients tested positive for HIV | none | PMTCT | HIV Monthly |
| HIV - ANC clients with know HIV positive status | none | PMTCT | HIV Monthly |
| HIV - HIV tests performed | Age and sex (HIV) | General HIV | HIV Monthly |
| HIV - HIV tests positive | Age and sex (HIV) | General HIV | HIV Monthly |
| HIV - PLHIV currently on ART | Age and sex (HIV) | General HIV | HIV Monthly |
| HIV - PLHIV new on ART | Age and sex (HIV) | General HIV | HIV Monthly |
| HIV - PLHIV retained on ART last 12 months | Age and sex (HIV) | General HIV | HIV Monthly |
| HIV - PLHIV started ART 12 months ago | Age and sex (HIV) | General HIV | HIV Monthly |
| HIV - PLHIV virologically suppressed | Age and sex (HIV) | General HIV | HIV Monthly |
| HIV - PLHIV with viral load tests | Age and sex (HIV) | General HIV | HIV Monthly |
| HIV - Estimated people living with HIV | none | Annual estimate | HIV Annual |

### Validation Rules

The following validation rules have been configured and enforced in the system.

| name | instruction | operator | leftSide | rightSide |
| --- | --- | --- | --- | --- |
| HIV - HIV tests positive<=HIV tests performed | HIV tests positive should be less than or equal to HIV tests performed | less_than_or_equal_to | HIV tests positive | HIV tests performed |
| HIV - PLHIV retained on ART last 12 months<=PLHIV started ART 12 months ago | PLHIV retained on ART last 12 months should be less than or equal to PLHIV started ART 12 months ago | less_than_or_equal_to | PLHIV retained on ART last 12 months | PLHIV started ART 12 months ago |
| HIV - PLHIV new on ART<=PLHIV currently on ART | PLHIV new on ART should be less than or equal to PLHIV currently on ART | less_than_or_equal_to | PLHIV new on ART | PLHIV currently on ART |
| HIV - PLHIV virologically suppressed<=PLHIV with viral load tests | PLHIV virologically suppressed should be less than or equal to PLHIV with viral load tests | less_than_or_equal_to | PLHIV virologically suppressed | PLHIV with viral load tests |
| HIV - ANC clients tested positive for HIV<=ANC clients tested for HIV | ANC clients tested positive for HIV should be less than or equal to ANC clients tested for HIV | less_than_or_equal_to | ANC clients tested positive for HIV | ANC clients tested for HIV |

## Indicators

Indicators are aligned to the core indicator list contained in the [WHO Analysis and Use of Health Facility Data Guidance for HIV Programme Managers](https://www.who.int/healthinfo/FacilityAnalysisGuide_HIV.pdf?ua=1). These indicators facilitate analysis of testing, treatment, viral suppression, and with a component of PMTCT. For TB indicators related to PLHIV, see the [WHO Analysis and Use of Health Facility Data Guidance for TB Programme Managers](https://www.who.int/healthinfo/FacilityAnalysisGuide_TB.pdf?ua=1).

| name | description | denominator | numerator | Indicator Type |
| --- | --- | --- | --- | --- |
| HIV - Estimated people living with HIV | Number of cases of HIV expected in a geographical area | 1 | HIV - Estimated people living with HIV | Numerator only |
| HIV - HIV tests performed | Number of HIV tests performed | 1 | HIV tests performed | Numerator only |
| HIV - HIV tests positive | HIV tests found to be positive | 1 | HIV tests positive | Numerator only |
| HIV - PLHIV currently on ART | Number of PLHIV currently on ART | 1 | PLHIV currently on ART | Numerator only |
| HIV - ART retention rate after 12 months (%) | Proportion of client on ART retained after 12 months | Started ART 12 months ago | Retained on ART last 12 months | Percentage |
| HIV - Estimated HIV prevalence rate (%) | Estimated HIV prevalence rate in percent. | Total population | Estimated people living with HIV | Percentage |
| HIV - HIV test positivity rate (%) | Percentage of all HIV tests performed that are HIV positive | HIV tests performed | HIV tests positive | Percentage |
| HIV - HIV viral load testing coverage annualized (%) | Coverage of HIV viral load testing amongst PLHIV on ART | PLHIV currently on ART | PLHIV tested for viral load | Percentage |
| HIV - PLHIV tested that are virologically suppressed (%) | Proportion of PLHIV tested that are virologically suppressed | PLHIV with viral load tests | PLHIV virologically suppressed | Percentage |
| HIV - Ratio of new on ART to newly diagnosed (%) | Number of new on ART during the period divided by the number of HIV positive tests | HIV tests positive | New on ART | Percentage |

## Dashboard

Dashboard items (charts, maps and pivot table) are aligned to the [WHO Analysis and Use of Health Facility Data Guidance for HIV Programme Managers](https://cdn.who.int/media/docs/default-source/documents/ddi/facilityanalysisguide-hiv.pdf) and designed for national, subnational (district) and facility level analysis.

### HIV Burden

This is national and subnational level dashboard that shows HIV burden estimate analysis with all items using the map to present the data.

![](resources/images/HIVPKG3.png)

### HIV National

 This is national level dashboard that shows HIV cascade, 2nd and 3rd 90 indicators, ART coverage, HIV testing, treatment and viral suppression analysis using the charts, pivot tables and maps to present the data.

![](resources/images/HIVPKG41.png)

![](resources/images/HIVPKG42.png)

### HIV District (SNU2)

This is sub national level dashboard that shows HIV cascade, 2nd and 3rd 90 indicators, ART coverage, HIV testing, treatment and viral suppression analysis using the charts, pivot tables and maps to present the data.

![](resources/images/HIVPKG51.png)

![](resources/images/HIVPKG52.png)

### HIV Facility

This is facility level dashboard that shows clinical HIV cascade, 2nd and 3rd 90 indicators, HIV testing, treatment and viral suppression analysis using the charts and pivot tables to present the data.

![](resources/images/HIVPKG61.png)

![](resources/images/HIVPKG62.png)

## References

1. [WHO Analysis and Use of Health Facility Data Guidance for HIV Programme Managers](https://cdn.who.int/media/docs/default-source/documents/ddi/facilityanalysisguide-hiv.pdf)  (March 2019)
2. WHO toolkit for analysis and use of health facility data, accessed at: [https://www.who.int/healthinfo/tools\_data\_analysis\_routine\_facility/en/](https://www.who.int/healthinfo/tools_data_analysis_routine_facility/en/)
