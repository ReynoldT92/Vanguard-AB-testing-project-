# Vanguard Digital Experience A/B Test: UI Redesign Analysis

## Project Overview
This project evaluates a digital experiment conducted by Vanguard from **March 15, 2017, to June 20, 2017**. The goal was to determine whether a modern User Interface (UI) with in-context prompts (cues, hints, or instructions) improves the completion rate of an online investment process compared to the traditional interface.

## Business Context
Vanguard’s Customer Experience (CX) team launched this experiment to address evolving client expectations and increase digital adoption. By introducing a more intuitive UI, the team aimed to encourage more clients to navigate the platform successfully and complete their intended investment actions, a key driver of assets under management (AUM).

## Experiment Design
* **Control Group**: Clients interacted with Vanguard’s traditional online process.
* **Test Group**: Clients experienced the new, modernized digital interface with in-context prompts.
* **The Process**: Both groups navigated an identical sequence: `start` → `step_1` → `step_2` → `step_3` → `confirm`.

## Data Sources
* **Client Profiles (`df_final_demo`)**: Demographics such as age, gender, and account details.
* **Digital Footprints (`df_final_web_data`)**: Detailed traces of client interactions within the online process.
* **Experiment Roster (`df_final_experiment_clients`)**: Mapping of clients to the Control or Test groups.

## Key Performance Indicators (KPIs)
The success of the experiment was evaluated using the following metrics:

* **Primary KPI**:  
  * **Completion Rate** – Proportion of users reaching the `confirm` step.

* **Secondary KPIs**:
  * **Average Backtracks** – Average number of times users returned to previous steps, indicating potential confusion or double-checking.
  * **Error Rate** – Percentage of non-linear movements in the funnel, used as a proxy for friction.
  * **Session Duration** – Median and mean time spent in the process from `start` to `confirm`.

## Key Findings (EDA & Results)
* **Completion Rate**: The Test group achieved a **~58.6%** completion rate, compared to **~49.9%** for the Control group—a lift of **8.7 percentage points**.
* **Friction Points**: The Test group experienced more backtracks (0.44 vs 0.30) and a higher error rate (11.6% vs 8.8%), suggesting more re-checking and adaptation to the new layout.
* **Time Analysis**: While Test users were faster at the `start` step, they spent significantly more time on the final `confirm` page (~223s vs ~139s), indicating heavier scrutiny or complexity at the final decision point.

## Hypothesis Testing
* **Null Hypothesis (\(H_0\))**: The new UI has no effect on completion rates.
* **Alternative Hypothesis (\(H_a\))**: The new UI leads to a statistically significant increase in completion rates.
* **Conclusion**: We **rejected the null hypothesis** as the p-value was < 0.05, confirming that the UI change is the likely driver of the increased conversion.

## Cost-Effectiveness Analysis
* **Threshold**: A 5 percentage point increase in completion was required to justify the redesign.
* **Result**: The observed **8.7 percentage point lift** exceeds this threshold, confirming that the project is cost-effective based on conversion alone.

## Challenges & Learnings

### Technical Challenges
* **Funnel Logic**: Translating non-linear web behavior into a clean 5-step funnel representation.
* **Friction Identification**: Designing custom logic to detect and quantify backtracks (users moving backward in the process).
* **Time Calculation**: Cleaning and aggregating timestamps to measure true interaction time while excluding long periods of inactivity.

### Key Learnings
* **The Full Story**: A higher conversion rate does not always imply a simpler experience; the Test UI increased success but also increased user double-checking (backtracks and confirm-time).
* **Statistical Rigor**: Using a Z-test for proportions was essential to show that the 8.7 percentage point lift was unlikely to be due to random variation.

## Recommendations
1. **Full Rollout**: Implement the Test UI platform-wide for this process due to the significant and statistically supported conversion lift.
2. **Optimize Final Step**: Redesign and A/B test the `confirm` page (simpler summaries, clearer disclosures, and a more prominent primary CTA) to reduce time-on-page and backtracking in the Test group.
3. **Continuous Monitoring**: Track long-term account balances (`bal`) and retention to verify that higher completion rates translate into sustained assets under management rather than short-lived or low-value accounts.

## Tools & Technologies
* **Python**: Data cleaning and transformation (Pandas, NumPy), hypothesis testing (SciPy).
* **Tableau**: Interactive dashboards for demographic- and behavior-based insights.[
](https://public.tableau.com/views/AB_Test_UI_Completion_Analysis/Dashboard1?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)
* * **Kanban (Trello)**: Project management, task tracking, and workflow organization.
