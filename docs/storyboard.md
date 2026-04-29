# MediScope Final Storyboard

This is the exact sequence of 7 Story Points for the final presentation, telling the complete data narrative from macro scale down to specific clinical recommendations.

## Story Point 1
**Caption:** "The Macro Picture: System Burden and Patient Acuity"
**Visual:** 4 KPI Scorecards showing 100 Total Patients, 76,069 Lab Tests, 39.1% Abnormal Rate, and Average Length of Stay. Beside the Abnormal Rate, a sparkline shows the monthly trend.

![Dashboard Overview](../tableau/screenshots/Dashboard%201.png)

**The Insight to Deliver:** We are dealing with a highly acute patient population. Nearly 40% of all laboratory tests processed in the ICU are flagging as abnormal, setting a baseline of high clinical risk.

## Story Point 2
**Caption:** "Where Are Patients Coming From?"
**Visual:** A split view showing a Bar Chart of Admission Types (Emergency, Elective, Urgent) alongside a Treemap breaking down the cohort by Age Band and Gender.
**The Insight to Deliver:** The operational burden is heavily skewed. Emergency admissions drive 91% of our patient volume, meaning our resources are primarily consumed by unplanned, high-acuity arrivals rather than scheduled care.

## Story Point 3
**Caption:** "The Length of Stay Discrepancy"
**Visual:** A Box-and-Whisker Plot comparing the Length of Stay (in days) across the different Admission Types, highlighting patient outliers.

![Demographic Splits](../tableau/screenshots/Dashboard%202.png)

**The Insight to Deliver:** Emergency patients are not just higher volume; they stay significantly longer. The average emergency stay is nearly 29 days—36% longer than elective patients—creating massive bottlenecks in bed availability.

## Story Point 4
**Caption:** "Who Has the Highest Clinical Risk?"
**Visual:** A Heatmap crossing Age Bands with Gender, where the color intensity represents the Abnormal Lab Rate.
**The Insight to Deliver:** Risk is not evenly distributed. Our statistical testing proves that female patients exhibit a consistently higher rate of abnormal lab flags across all admission types, regardless of age band.

## Story Point 5
**Caption:** "The Departmental Drain: Volume vs. Acuity"
**Visual:** A Quadrant Scatter Plot mapping Lab Categories. The X-axis shows total test volume, and the Y-axis shows the abnormal rate. The size of the bubble represents tests per patient.

![Clinical Deep Dive](../tableau/screenshots/Dashboard%203.png)

**The Insight to Deliver:** Hematology stands out in the critical upper-right quadrant. It requires the highest volume of testing while also returning the highest rate of abnormal results, making it our largest operational drain.

## Story Point 6
**Caption:** "Testing Burden Over Time"
**Visual:** A Dual-Axis chart showing the total volume of lab tests (bars) against the abnormal rate (line) over the months of the year.
**The Insight to Deliver:** While the volume of tests spikes during certain months, the actual rate of abnormal results remains relatively flat. This suggests instances of routine over-testing that do not yield new clinical findings.

## Story Point 7
**Caption:** "Actionable Recommendations"
**Visual:** Three clean recommendation text cards (no raw data charts).
**The Insight to Deliver:** 
1. **Triage Adjustment:** Fast-track protocols for non-critical emergency admits to reduce the 29-day average.
2. **Gender-Stratified Baselines:** Review lab reference ranges for female patients to reduce alert fatigue.
3. **Hematology Protocol Review:** Implement stricter guidelines for repeat testing to cut down on low-yield high-volume orders.
