# Hyperparameters

 Azure Machine Learning hyperparameter tuning (managed via **SweepJobs**), early termination policies improve efficiency by automatically ending trial jobs that show poor performance relative to others.

## Early termination policiese

- **Bandit Policy**: This policy is based on a **slack factor** (ratio) or **slack amount** (absolute value). It terminates any trial where the primary metric falls outside the allowed slack compared to the best-performing job at a given interval.

- **Median Stopping Policy**: This policy calculates the running averages of the primary metric across all training jobs. It stops a trial if its best primary metric is worse than the **median of the running averages** for all trials at that same interval.

- **Truncation Selection Policy**: This policy cancels a specific **percentage** (an integer between 1 and 99) of the lowest-performing trials at each evaluation interval.

**No Termination Policy (Default)**: If no specific policy is defined, the system allows all trial jobs to execute until they reach their intended completion.

## Configuration and Strategy
The effectiveness of these policies is managed by two key parameters:
-**Evaluation Interval**: Specifies the frequency at which the policy is applied (e.g., every time a metric is logged or every other time).
-**Delay Evaluation**: Postpones the first policy check for a set number of intervals to prevent the **premature termination** of jobs before they have a chance to establish a performance baseline.

The sources offer the following strategic advice for selection:
-**Conservative**: The **Median Stopping Policy** is recommended for saving approximately **25%-35% in costs** without risking the loss of promising jobs [11].
-**Aggressive**: For higher cost savings, the **Bandit Policy** with a smaller slack or the **Truncation Selection Policy** with a larger percentage should be used.