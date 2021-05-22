# covid19-Greece
Daily regional statistics for Covid19 cases in Greece (used by https://github.com/Sandbird/covid19-gr)

### Updates
This repository will be updated daily on an irregular basis according to the announcement by the Ministry of Health.


# Changelog

All notable changes to the files will be documented here.

## 22-05-2021

### Changed

- prefectures.csv. The color indicating the 'Risk Level' for each Prefecture is not available anymore to the general public. EODY is now showing just a reference to the ECDC’s map for travel measures in the EU. From now on the color values will be daily calculated/updated based on the ranges shown on the ECDC map (https://tinyurl.com/ecdcmap), and by using the 'Cases per 100,000' column, which is based on a 7-Day Average of New Cases per 100.000 inhabitants, for the last 14 days.


## 17-05-2021

### Changed

- prefectures.csv. Population values for various prefectures have been updated, based on the 'POPULATION CENSUS of 2011' provided by https://www.statistics.gr/2011-census-pop-hous


## 14-05-2021

### Added

- vaccinations.csv. Since the 5th of May, the daily values provided by (https://emvolio.gov.gr/vaccinationtracker) now also include the J&J vaccine, which is now included in both 'vaccinations with at least 1 dose' as well as in the 'total vaccinations that were given' categories. In order to properly display the new data, vaccinations had to be separated from the cases.csv. (The 'total_vaccinations' value will still be updated there as well). This change probably happened because the J&J vaccine is only a '1 dose' vaccine thus complicating things with the way the table was previously presented.


## 29-03-2021

### Changed

- cases.csv. Renamed icu_admissions to hospitalized, and icu_discharged to discharged.

### Added

- cases.csv. Added column icu_out to keep the total number of patients that came out of the ICU.
