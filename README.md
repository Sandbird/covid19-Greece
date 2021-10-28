# covid19-Greece
Daily regional statistics for Covid19 cases in Greece (used by https://github.com/Sandbird/covid19-gr)

### Updates
This repository will be updated daily on an irregular basis according to the announcement by the Ministry of Health.

### Notes
The new daily cases reported in greece.json (transition.carriers) derive from the daily difference of 'confirmed' cases (cases.csv) and they include any subsequent corrections made by EODY on previous reports. If you want to use the daily reported cases then use the 'transition.new_reported_cases' array.

# Changelog
All notable changes to the files will be documented here.

## 28-10-2021

### Added

- greece.json. Added active_cases_estimate in prefectures-details array, to hold the estimated active cases for the region. It is based on the last 14 days of confirmed cases. It is calculated from the beginning of the pandemic untill today, so it is not exactly the data from the last 14 days (ex. the 15th day before today had a value as well, so it takes that into account as well)


## 27-09-2021

### Added

- prefectures.csv. Added column: rj_value (value is updated daily)
- predictions.csv. Added column: rj_value (value is updated daily)

Instead of calculating the value 'on the fly', it will now be stored in the above columns.

(Details on what that value represents: https://covid19-greece.tk/index_en.html#rj-notes)


## 16-09-2021

### Changed

- prefectures.csv. Added column: totaldose3 (value is updated daily)
Booster shot (3rd dose) total values provided by (https://emvolio.gov.gr/vaccinationtracker) for each prefecture.
- vaccinations.csv. Added column: total_booster (value is updated daily). The sum of all 3rd dose booster shots given.
- greece.json. Added an extra value at the end of transition.vaccinations array to hold the daily booster shots given.


## 30-08-2021

### Changed

- cases.csv. Added columns: total_vaccinated_crit, total_unvaccinated_crit (values are updated daily)
The ICU patients will now be divided into 2 categories. Fully vaccinated, and partially or not vaccinated. (total_unvaccinated_crit + total_vaccinated_crit = total_critical)
- greece.json. Added transition.serious.details array.


## 29-08-2021

### Added

- vaccinations_ecdc.csv. Added all the data collected (for Greece) by the ECDC through The European Surveillance System (TESSy). (https://opendata.ecdc.europa.eu/covid19/vaccine_tracker/)
Weekly updated...time unknown...so there will be a check for new updates every 6 hours.
- greece.json. Added vaccinations_byage, vaccinations_bycompany, vaccinations_percent arrays


## 27-07-2021

### Changed

- cases.csv. Added columns: new_selftest, total_selftest (values are updated daily)
(Self-diagnostic results that have been recorded on the Self Testing platform (https://self-testing.gov.gr/))
- greece.json Added transition.selftest array

## 16-07-2021

### Changed

- prefectures.csv. Added columns: vaccrate, vaccrate2, newvacc1rate, newvacc2rate, posrate (All values are updated once, weekly)
- vaccrate: 1st dose, coverage as it results from the location of each vaccination center that may include employees, non-permanent residents of the Regional Unit, etc.
- vaccrate2: Fully Vaccinated, coverage as it results from the location of each vaccination center that may include employees, non-permanent residents of the Regional Unit, etc.
- newvacc1rate: 1st dose, coverage as it results from the available information of residents within the Regional Unit
- newvacc2rate: Fully Vaccinated, coverage as it results from the available information of residents within the Regional Unit
- posrate: The positivity index (%) of the week
- The weekly updates are drawn from the Ministry of Civil Protection page: https://covid19.gov.gr/covid-map-en


## 04-06-2021

### Changed

- prefectures.csv. Population values for various prefectures were reverted back to their previous (prior to the 17/5 change) value. There is a discrepancy between the Census values of 2011 and what EODY is using for some prefectures. For the time being i will be using the same values EODY is using. Hopefully with the 2021 census this problem will disappear.


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
