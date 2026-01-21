# Hyperparameters
In Azure Machine Learning (specifically via HyperDrive or Sweep Jobs), the selection of hyperparameters involves three main components: defining the search space, choosing a sampling method, and optionally applying an early termination policy.

## 1. Hyperparameter Search Space

You can define hyperparameters as either discrete or continuous values.

- Discrete Hyperparameters: Specified as a choice among explicit values. These can be numbers, strings, or a range object.
Example: choice(16, 32, 64, 128) or choice(range(1, 10)).

- Continuous Hyperparameters: Specified using a distribution. Azure ML supports:
uniform(low, high): Values are uniformly distributed between low and high.
loguniform(low, high): Drawn according to a log-uniform distribution (useful for learning rates).
normal(mu, sigma): Values from a normal distribution.
lognormal(mu, sigma): Values from a log-normal distribution.

## 2. Sampling Methods
This is the algorithm used to pick combinations from your search space.

- Random Sampling: Randomly selects values from the defined space. Supports both discrete and continuous hyperparameters. Best for getting a good result quickly or for initial exploration.

- Grid Sampling: Systematically tries every possible combination in the search space. Only works with discrete parameters. Best when the search space is small and you have a high budget.

- Bayesian Sampling: Uses a machine learning model to pick the next set of hyperparameters based on previous results to improve the metric. Best for expensive-to-train models; it "learns" which areas of the space are better.

## 3. Early termination policies

- **Bandit Policy**: This policy is based on a **slack factor** (ratio) or **slack amount** (absolute value). It terminates any trial where the primary metric falls outside the allowed slack compared to the best-performing job at a given interval.

- **Median Stopping Policy**: This policy calculates the running averages of the primary metric across all training jobs. It stops a trial if its best primary metric is worse than the **median of the running averages** for all trials at that same interval.

- **Truncation Selection Policy**: This policy cancels a specific **percentage** (an integer between 1 and 99) of the lowest-performing trials at each evaluation interval.

**No Termination Policy (Default)**: If no specific policy is defined, the system allows all trial jobs to execute until they reach their intended completion.

## 4. Configuration and Strategy
The effectiveness of these policies is managed by two key parameters:

- **Evaluation Interval**: Specifies the frequency at which the policy is applied (e.g., every time a metric is logged or every other time).

- **Delay Evaluation**: Postpones the first policy check for a set number of intervals to prevent the **premature termination** of jobs before they have a chance to establish a performance baseline.

The sources offer the following strategic advice for selection:

- **Conservative**: The **Median Stopping Policy** is recommended for saving approximately **25%-35% in costs** without risking the loss of promising jobs.

- **Aggressive**: For higher cost savings, the **Bandit Policy** with a smaller slack or the **Truncation Selection Policy** with a larger percentage should be used.