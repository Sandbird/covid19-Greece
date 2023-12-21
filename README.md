# covid19-Greece
Daily regional statistics for Covid19 cases in Greece (used by https://github.com/Sandbird/covid19-gr, https://covid19-greece.tk/)

### Updates
This repository will be updated daily on an irregular basis according to the announcement by the Ministry of Health.

### Notes
The new daily cases reported in greece.json (transition.carriers) derive from the daily difference of 'confirmed' cases (cases.csv) and they include any subsequent corrections made by EODY on previous reports. If you want to use the daily reported cases then use the 'transition.new_reported_cases' array.

- positive_rate_7day_ma - Positivity rate taking into account only PCR tests and cases.
- positive_rate_combined_7day_ma - Positivity rate taking into account PCR+Rapid tests and cases.

# Changelog 
All notable changes to the files will be documented here.

## 21-12-2023
### Changed
cases.csv, cases_weekly_ecdc.csv: Every Tuesday afternoon, I will update both files with the latest EODY updates. This means that the 'new_cases', 'confirmed' values will encompass both new cases and reinfections. When the ECDC report is released, the values will be adjusted accordingly. This adjustment will also apply to the 'reinfections' values. In general, if you encounter a 0 value in the reinfections column, it indicates that the ECDC report has not been released yet.


## 09-12-2023
### Changed
cases_weekly_ecdc.csv. As of December 1, 2023, ECDC will no longer update its dataset (https://www.ecdc.europa.eu/en/covid-19/data). Consequently, no further corrections will be applied to the data, as there will be no official provider of TESSy data available. Moving forward, I will rely on the positivity rate provided by EODY (the National Public Health Organization) every Thursday for the 'new_deaths', 'total_deaths', 'new_cases', 'confirmed', and 'positive_rate' fields. It's important to note that we have currently lost all values for 'reinfections'.



## 25-04-2023
### Changed
vaccinations_ecdc.csv. Added columns: DoseAdditional4, DoseAdditional5. Number of third,forth additional vaccine doses administered after a complete standard primary course to individuals during the reporting week.
greece.json - Added names 'vaccinations_byage.DoseAdditional4', 'vaccinations_byage.DoseAdditional5'



## 24-03-2023
### Added
- cases_weekly_ecdc.csv - Weekly dataset provided by ECDC. Added a few additions (total_vaccinations, new_critical, total_critical) using EODY data. In addition, using the positivity rate from the EODY reports + PCR/Rapid tests, we can calculate the reinfections (EODY Cases - ECDC Cases), since EODY does not send the reinfections to TESSy. The sum of new_cases + new_reinfections gives us the (proper) weekly sum.



## 20-01-2023
### Changed
- predictions.csv - The following values cannot be updated anymore due to lack of data: daily_tests_7day_ma, daily_rapid_tests_7day_ma, positive_rate_7day_ma, positive_rate_combined_7day_ma, daily_prevalence_ratio_7day_ma, true_inf_est_7day_ma, implied_ifr_7day_ma.


## 20-12-2022
### EODY, the organization that has the primary responsibility for informing the public on the pandemic, decided (yet again) in the midst of the winter wave, to no longer issue the weekly epidemiological report. From now on a less detailed report will be issued every Thursday, which will include all respiratory infections. An example of new format can be seen here: https://eody.gov.gr/wp-content/uploads/2022/12/anapneustikon-ion-report-2022-50.pdf. It is unknown, at this moment, of whether I can continue to update this repo or not. The only available data that we have now are Vaccinations. (cases.csv, prefectures.csv, vaccinations/vaccinations_ecdc.csv). At this moment, I am waiting to see what will EODY report to TESSy and subsequently to ECDC.


## 16-09-2022
### Changed
- workbench.csv, workbench_totals.csv - It seems that server that was broadcasting these values has gone offline...Will update if it ever gets online again.



## 05-08-2022
### Changed
- predictions.csv - Due to the w27, w28 weekly reports there was problem calculating prevalence_ratio_7day_ma, implied_ifr_7day_ma values. I had to compensate for the negative values that were being created (for 2 consecutive days) by just ignoring them and copying the previous positive value.



## 28-07-2022
### Changed
- prefectures.csv - Changed population values based on the Greek 2021 Census (https://pastebin.com/raw/AUx4yaag). (From 2022-07-26 and onwards the new values will apply.)



## 09-07-2022
### EODY, the organization that has the primary responsibility for informing the public on the pandemic, decided in the midst of a new outbreak, that the epidemiological report will from now on be published on a weekly basis. In particular, until Sunday 10/07, when ISO week 27 of the year ends, the daily report will be published as usual. On Tuesday (12/7) the first weekly report will be published. It is noted that, on Monday there will be no daily report due to the start of the following week (ISO 28).
I'll do my best to maintain this repository, but expect the unexpected for the following 1-2 weeks. It all depends on the quality/availability of the new information.


## 06-07-2022

### Changed
- Recalculated all of the '«True» number of infections (estimate)' values, based on the updated https://covid19-projections.com/estimating-true-infections-revisited/#prevalence-ratio website. The FAQ section of the website was also changed accordingly. The new formula: 'dailyCases(day_i) * (4.5 * (positivity_rate(day_i))^(0.5) + 2)' replaced the previous one 'dailyCases(n+14) * (16 * \sqrt[2]{posRate(n+14)} + 2.5)' and all values were recalculated. Instead of a two weeks lag in infections, a 10-day one was used in order to approach a more realistic scenario for Greece. 
Affected tables:
- predictions.csv - columns (prevalence_ratio_7day_ma, true_inf_est_7day_ma, implied_ifr_7day_ma)
- greece.json - (predicted_true_inf, infection_fatality_rate)



## 20-06-2022

### Changed
- prefectures.csv - color column. New ranges based on the ECDC map (14-day notification rate per 100.000 population). I will not be renaming the text values, just what they represent (0-40: less25, 40-100: less150, 100-300: less500, >300: over500)


## 13-06-2022
- No report today due to public holiday. EODY will not be publishing a pdf report.


## 03-06-2022

### Changed
- vaccinations_ecdc.csv. Added column: DoseAdditional2. Number of second additional vaccine doses administered after a complete standard primary course to individuals during the reporting week.
- greece.json - Added name 'vaccinations_byage.DoseAdditional2'


## 01-06-2022

### Changed
- greece.json - Changed name 'transition.new_reinfections' to 'transition.new_reported_reinfections'
- cases.csv. Added column: total_reinfections at the end of the table (values are updated daily). The number of total possible re-infections noted on EODY’s pdf report. Any corrections or delayed additions to the total amount of re-infections will be included in this value.


## 17-04-2022

### Changed
- greece.json - Added 'transition.bed_percentages_all' array. Holds all ICU bed coverage percentage values since 18/1/21.
- greece.json - Added 'transition.icu_percentages_all' arrays. Holds all Non-icu bed coverage percentage values since 18/1/21.
The main 'transition.icu_percentages' array will remain for dependency reasons.


## 11-04-2022

### Changed
- greece.json - Added 'transition.new_reinfections' array to hold the new daily reinfection values.
- greece.json - Added 'transition.carriers_plus_reinf' arrays to hold the daily confirmed cases, plus the new reinfections. 

The main 'transition.carriers' array will stay as it is for dependency reasons. If anyone wants to combine the cases and reinfections together they can do so using the carriers + new_reinfections arrays, or simple parse the 'carriers_plus_reinf' array.


## 07-04-2022

### Added
- cases.csv. Added column: reinfections at the end of the table (values are updated daily). The number of possible new re-infections recorded daily by EODY.


## 06-04-2022

### Changed
EODY changed their daily report today, and from now on reinfections will be added into the demographic totals. This affects all demographic tables (cases). Overall 130,334 new cases were added to the totals today.


## 30-03-2022

### Changed
Updated the way 'Active Cases (estimate)', 'Effective Reproduction Number Rj (estimate)' are calculated. Based on the new CDC guidelines for the Omicron variant, incubation period has been changed to 3 days (from 5 based on Delta) and instead of using the last 17 days (Delta), the new median duration of active cases has been changed to 11 days; 


## 05-02-2022

### Changed

- workbench.json - Unfortunately there was no data for date: 2022-02-03.


## 06-01-2022

### Changed

- greece.json - Added 'transition.infected_distribution_total_percent', 'transition.infected_distribution_death_percent', 'infected_distribution_icu_percent' arrays to hold the daily percentage values of Cases distribution (total), Deaths by age (total) and Critically Ill by age (total) charts respectively. They appear when the PERCENT button is pressed.


## 05-01-2022

### Added

- mobility.csv - A new table (checked every day at 23:30 for new updates). Holds the latest Google Mobility Reports for Greece.
- greece.json - Added 'google_mobility' array to hold the data for the Google Mobility chart. First array element holds the caterories (dates), and the rest are the 'splines' for the various mobility indexes as well as a 'column' for the New Cases. I used the weekly average data (7-day mov.avg) with the aim of reduction of fluctuation.


## 03-12-2021

### Added

- workbench_totals.csv - A new table (checked every hour for new updates) using the same source as workbench.csv (01-11-2021). Holds the latest cumulative totals of recoveries, hosp. discharges, active cases, deaths, hospitalizations and cases. The 'date' record is just for reference. In the official records there is no date...only raw data.


## 11-11-2021

### Changed
- prefectures.csv - Added columns 'casesweek100k', 'casesfortnight100k' at the end of the table. They represent the Cases per 100K people with a 7day/14day mov.avg.


## 10-11-2021

### Changed
- vaccinations_ecdc.csv - ECDC has changed the format of the data to include the booster shots (DoseAdditional1). The whole table was recreated to reflect the changes.
- greece.json - 'DoseAdditional1' array was added to the 'vaccinations_byage' array


## 08-11-2021

### Changed

- demography_total_details.csv - Added 4 more columns (DISCHARGED, HOSPITALIZED, HOSPITALIZED_IN_ICU, PASSED_AWAY, RECOVERED, TREATED_AT_HOME). 
The table now holds 2 sets of data. The first (cases, deaths, intensive) are updated daily using the values given by EODY's PDF. The second is updated hourly (first when the daily PDF report comes out, and then every XX:20 up untill 23:20), and the source is a gov.gr page (see details bellow 01-11-2021).


## 07-11-2021 / 11-11-2021

### Changed

- prefectures.csv - Daily updates for columns: deaths(PASSED_AWAY), recovered(RECOVERED), active(TREATED_AT_HOME) with their corresponding values from workbench.csv
- regions.csv - Added column: region_to_prefid that corresponds to the region_id value in prefectures.csv.
- greece.json - Added totalactive, totalrecovered values in 'prefectures-details' array, for every Prefecture. The 'active_cases_estimate' value will remain in the array for now for areas where the value of 'totalactive'(TREATED_AT_HOME from the table workbench.csv) isn't known.
- ~~greece.json - The 'deaths' array in 'prefectures-data' for each individual Prefecture is now updated daily.~~


## 01-11-2021 / 11-11-2021

### Added

**Please note, that the source of this data (url) hasn't been officially released to the public. Until it is, I have my reservations about the disclosure of the domain name. Nonetheless, I can only say that this was taken by a .gov.gr page, open to the public, it has been posted online on a social media platform and I have no reason to assume the data are not valid since the daily reported changes match up exactly to the official daily reports made by EODY. If you don't wish to use the following data then please ignore any addtions into the columns 'deaths, recovered, active' after 30/10/2021 in the tables prefectures.csv and regions.csv**
- workbench.csv - A new table (checked every hour for new updates) from a new source of data extracted from a gov.gr page, that holds Prefecture details including hospitalizations, deaths and cases per Prefecture. The 'date' record is just for reference. In the official records there is no date...only raw data.


## 28-10-2021

### Added

- greece.json. Added active_cases_estimate in 'prefectures-details' array, to hold the estimated active cases for the region. It is based on the last 14 days of confirmed cases.


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
