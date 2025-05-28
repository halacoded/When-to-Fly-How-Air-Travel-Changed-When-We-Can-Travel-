# When to Fly: How Air Travel Changed When We Can Travel Safely (1908–2009)

## Project Topic & Problem Statement
**Topic:**  
How air travel has evolved from being dependent on seasons to enabling year-round travel.  

**Problem:**  
Plane crashes don’t happen evenly throughout the year—some months, times, and holidays are riskier than others. I analyzed 101 years of crash data to determine when flying was safest and when it was most dangerous.

## Strategy for Solving the Problem
*(One cell hidden)*  

## Detailed Analysis

### 4.1 - Dataset Description
The dataset consists of 5,246 entries, tracking critical aspects of each airplane crash.

#### 🧮 Dataset Before Cleaning & Engineering
| Column        | Description |
|--------------|-------------|
| Date        | Crash date |
| Time        | Time of crash (many missing values) |
| Location    | Location of the crash |
| Operator    | Airline or company |
| Flight #    | Flight number (many missing values) |
| Route      | Route taken (many missing values) |
| Type       | Aircraft type |
| Registration | Aircraft registration number |
| cn/In       | Construction number (many missing values) |
| Aboard     | Number of people aboard |
| Fatalities | Number of deaths |
| Ground     | Number of ground fatalities |
| Summary    | Short crash description |

Total entries: **5,268**  
There are many missing values, especially in *Time*, *Flight #*, *Route*, *Registration*, etc.

#### 🧮 Dataset After Cleaning & Engineering
| Column         | Description |
|---------------|-------------|
| Date        | Date of airplane crash |
| Time        | Time of crash (formatted as HH:MM or 'Unknown') |
| Aboard     | Number of people aboard the aircraft |
| Fatalities | Number of fatalities from the crash |
| Summary    | Brief description of the incident |
| Year       | Extracted year from Date |
| Month      | Extracted month from Date |
| Season     | Based on Month: Winter, Spring, Summer, Fall |
| TimeOfDay  | Based on Time: Morning, Afternoon, Evening, Night, Unknown |
| HolidayName | Name of nearby holiday (if any) |
| HolidayCountry | Country associated with the holiday |
| IsHoliday  | Boolean indicating if crash occurred during/near a holiday |
| SurvivalRate | Percent of passengers who survived the crash |

Total entries: **5,246**  
Most missing values are handled, with only some remaining in *Time* as 'Unknown'.

### 4.2 - Data Cleaning
- **Dropped unnecessary columns:**  
  `Flight #`, `Registration`, `cn/In`, `Ground`, `Operator`, `Route`, `Type`, `Location`.
- **Handled missing values:**  
  - *Time:* 2,219 missing → filled with 'Unknown'.
  - *Aboard:* 22 missing → rows dropped.
  - *Fatalities:* 12 missing → rows dropped.
  - *Summary:* 390 missing → filled with empty string `""`.
- **Formatted data:**  
  - Date converted to `MM/DD/YYYY` format.
  - Time standardized to `HH:MM` or 'Unknown'.
  - Aboard & Fatalities cleaned and converted to integers.
  - Summary cleaned to include only English letters and numbers.

### 4.3 - Feature Engineering
| New Column | Description |
|-------------|-------------|
| Year        | Extracted from Date |
| Month       | Extracted from Date |
| Season      | Based on Month: Winter, Spring, Summer, Fall |
| TimeOfDay   | Based on Time: Morning, Afternoon, Evening, Night |
| HolidayName | Name of nearby holiday (if any) |
| HolidayCountry | Country where the holiday is observed |
| IsHoliday   | Boolean indicating holiday-related crashes |
| SurvivalRate | Calculated: `((Aboard - Fatalities) / Aboard) * 100` |

### 4.4 - Data Visualizations
1️⃣ **Crashes by Season**  
![Pie Chart](Charts-Photos/Crashes%20by%20Season.png)  
**Insights:**  
Winter (26.7%) and Fall (26.0%) have the highest crash percentages, while Spring has the lowest (22.8%).  

2️⃣ **Crashes by Time of Day**  
![Chart](Charts-Photos/Crashes%20by%20Time%20of%20Day.png)  
**Insights:**  
Nighttime crashes occur significantly more often due to poor visibility and fatigue.  

3️⃣ **Safest Weekday to Travel**  
![Chart](Charts-Photos/Safest%20Weekday%20to%20Travel.png)  
**Insights:**  
Sunday has the lowest crash numbers, making it the safest day to travel. Survival rates remain consistent across all days.  

4️⃣ **Crashes on Holidays vs. Non-Holidays**  
![Chart](Charts-Photos/Airplane%20Crashes%20on%20Holidays%20vs.%20Non-Holidays.png)  
**Insights:**  
Holiday-related crashes spike due to increased air traffic and rushed operations.  

5️⃣ **Top 5 Holidays with Most Airplane Crashes by Country**  
![Chart](Charts-Photos/Top%205%20Holidays%20with%20Most%20Airplane%20Crashes%20by%20Country.png)  
**Insights:**  
Historically, bad weather made travel dangerous. Today, holiday overcrowding mirrors that risk.  

6️⃣ **Crashes by Weather Conditions**  
![Chart](Charts-Photos/Crashes%20by%20Weather%20Conditions.png)  
**Insights:**  
Rain remains the deadliest weather condition for aviation due to visibility issues and unstable runway conditions.  

7️⃣ **Is Flying Getting Safer Over Time?**  
![Chart](Charts-Photos/Is%20Flying%20Getting%20Safer%20Over%20Time.png)  

## Summary of Project Outcomes
Ultimately, we see that the safest time to travel aligns with the seasonal patterns our ancestors once followed.
