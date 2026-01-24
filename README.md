# Vanguard Digital Experience A/B Test: UI Redesign Analysis

## Project Overview
This project evaluates a digital experiment conducted by Vanguard from **March 15, 2017, to June 20, 2017**. The goal was to determine if a modern User Interface (UI) with in-context prompts (cues, hints, or instructions) improves the completion rate of the online investment process compared to the traditional interface.

## Business Context
Vanguard’s Customer Experience (CX) team launched this experiment to address evolving client needs. By introducing a more intuitive UI, the team aimed to encourage more clients to successfully navigate the platform and complete their intended actions.

## Experiment Design
* **Control Group**: Clients interacted with Vanguard’s traditional online process.
* **Test Group**: Clients experienced the new, "spruced-up" digital interface.
* **The Process**: Both groups navigated an identical sequence: `start` -> `step_1` -> `step_2` -> `step_3` -> `confirm`.

## Data Sources
* **Client Profiles (`df_final_demo`)**: Demographics like age, gender, and account details.
* **Digital Footprints (`df_final_web_data`)**: A trace of client interactions online.
* **Experiment Roster (`df_final_experiment_clients`)**: A list revealing which clients were assigned to the Control or Test groups.

## Key Performance Indicators (KPIs)
Based on initial analysis, the following metrics were used to evaluate success:
* **Primary KPI**: **Completion Rate** (Proportion of users reaching the `confirm` step).
* **Secondary KPIs**:
    * **Average Backtracks**: Frequency of users returning to previous steps.
    * **Error Rate**: Percentage of non-linear movements in the funnel.
    * **Session Duration**: Median and mean time spent in the process.

## Key Findings (EDA & Results)
* **Completion Rate**: The Test group achieved a **~58.6%** completion rate, compared to **~49.9%** for the Control group—a lift of **8.7 percentage points**.
* **Friction Points**: The Test group experienced more backtracks (0.44 vs 0.30) and a higher error rate (11.6% vs 8.8%).
* **Time Analysis**: While Test users were faster at the `start` step, they spent significantly more time on the final `confirm` page (~223s vs ~139s).

## Hypothesis Testing
* **Null Hypothesis ($H_0$)**: The new UI has no effect on completion rates.
* **Alternative Hypothesis ($H_a$)**: The new UI leads to a statistically significant increase in completion rates.
* **Conclusion**: We **rejected the null hypothesis** as the p-value was < 0.05, confirming the UI change was the likely driver of the increased conversion.

## Cost-Effectiveness Analysis
* **Threshold**: A 5% increase in completion was required to justify the redesign.
* **Result**: The observed **8.7% lift** exceeds this threshold, confirming the project is cost-effective.

##  Challenges & Learnings
### Technical Challenges
* **Funnel Logic**: Mapping non-linear web behavior into a 5-step ranked funnel.
* **Friction Identification**: Developing custom logic to detect and count "backtracks" (users moving backward in the process).
* **Time Calculation**: Cleaning timestamps to measure true interaction time while excluding long periods of inactivity.

### Key Learnings
* **The Full Story**: A higher conversion rate doesn't always mean a "simpler" process; the Test UI increased success but also increased user double-checking (backtracks).
* **Statistical Rigor**: Using a Z-test was essential to prove that our 8.7% lift was not just due to random noise.

## Recommendations
1. **Full Rollout**: Implement the Test UI platform-wide due to the significant conversion lift.
2. **Optimize Final Step**: Redesign the `confirm` page to reduce the high time-on-page and backtracking observed in the Test group.
3. **Continuous Monitoring**: Track long-term account balances (`bal`) to see if the new UI impacts total assets under management.

## Tools & Technologies
* **Python**: Data cleaning (Pandas, NumPy) and Statistical Testing (SciPy).
* **Tableau**: Interactive dashboards for demographic-based insights.
* **Kanban (Trello)**: Project management and task division.
