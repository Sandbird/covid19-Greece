# covid19-Greece
Daily regional statistics for Covid19 cases in Greece (used by https://github.com/Sandbird/covid19-gr)

### Updates
This repository will be updated daily on an irregular basis according to the announcement by the Ministry of Health.


# Changelog

All notable changes to the files will be documented here.

## 14-05-2021

### Added

- vaccinations.csv. Since the 5th of May, the daily values provided by (https://emvolio.gov.gr/vaccinationtracker) now also include the J&J vaccine, which is now included in both 'vaccinations with at least 1 dose' as well as in the 'total vaccinations that were given' categories. In order to properly display the new data, vaccinations had to be separated from the cases.csv. (The 'total_vaccinations' value will still be updated there as well). This change probably happened because the J&J vaccine is only a '1 dose' vaccine thus complicating things with the way the table was previously presented.

## 29-03-2021

### Changed

- cases.csv. Renamed icu_admissions to hospitalized, and icu_discharged to discharged.

### Added

- cases.csv. Added column icu_out to keep the total number of patients that came out of the ICU.
