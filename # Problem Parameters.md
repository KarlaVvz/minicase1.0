# Problem Parameters

The `LpProblem` function implements two parameters:

1. Arbitrary Name: The first parameter is the arbitrary name of the problem, provided as a string.

2. Optimization Type: The second parameter can be either `LpMinimize` or `LpMaximize`, specifying whether the problem is a minimization or maximization problem, respectively.

## Variable Naming

Is it mandatory to name the `prob` variable as `prob`?

No, it is not mandatory to name the variable as `prob`. While using variable names like "prob" or "probability" can be a common convention when working with probability-related calculations or probabilistic models, you can choose any valid variable name that is meaningful and descriptive in your code.

## Usage of LpContinuous and LpInteger

The parameters `LpContinuous` and `LpInteger` are used to type the data in the optimization problem.

- `LpContinuous` is used when modeling continuous data.

- `LpInteger` is used when modeling discrete data, where the bounds can be entered directly as numbers, or "None" to represent no bound.

# Objective Function

The objective function is defined as follows:

```python
prob += 0.013 * x1 + 0.008 * x2, "Total Cost of Ingredients per can"

The objective function takes into account the prices of beef and chicken, which are multiplied by the variables x1 and x2:
x1 = LpVariable("ChickenPercent", 0, None, LpInteger)
x2 = LpVariable("BeefPercent", 0)

prob += x1 + x2 == 100, "PercentagesSum"
prob += 0.100 * x1 + 0.200 * x2 >= 8.0, "ProteinRequirement"
prob += 0.080 * x1 + 0.100 * x2 >= 6.0, "FatRequirement"
prob += 0.001 * x1 + 0.005 * x2 <= 2.0, "FibreRequirement"
prob += 0.002 * x1 + 0.005 * x2 <= 0.4, "SaltRequirement"

prob += lpSum([ingredient_vars[i] for i in Ingredients]) == 100, "PercentagesSum"
prob += (
    lpSum([proteinPercent[i] * ingredient_vars[i] for i in Ingredients]) >= 8.0,
    "ProteinRequirement",
)
prob += (
    lpSum([fatPercent[i] * ingredient_vars[i] for i in Ingredients]) >= 6.0,
    "FatRequirement",
)
prob += (
    lpSum([fibrePercent[i] * ingredient_vars[i] for i in Ingredients]) <= 2.0,
    "FibreRequirement",
)
prob += (
    lpSum([saltPercent[i] * ingredient_vars[i] for i in Ingredients]) <= 0.4,
    "SaltRequirement",
)


Aquí tienes el archivo Markdown con la información proporcionada:

markdown
Copy code
# Problem Parameters

The `LpProblem` function implements two parameters:

1. Arbitrary Name: The first parameter is the arbitrary name of the problem, provided as a string.

2. Optimization Type: The second parameter can be either `LpMinimize` or `LpMaximize`, specifying whether the problem is a minimization or maximization problem, respectively.

## Variable Naming

Is it mandatory to name the `prob` variable as `prob`?

No, it is not mandatory to name the variable as `prob`. While using variable names like "prob" or "probability" can be a common convention when working with probability-related calculations or probabilistic models, you can choose any valid variable name that is meaningful and descriptive in your code.

## Usage of LpContinuous and LpInteger

The parameters `LpContinuous` and `LpInteger` are used to type the data in the optimization problem.

- `LpContinuous` is used when modeling continuous data.

- `LpInteger` is used when modeling discrete data, where the bounds can be entered directly as numbers, or "None" to represent no bound.

# Objective Function

The objective function is defined as follows:

```python
prob += 0.013 * x1 + 0.008 * x2, "Total Cost of Ingredients per can"
In this code, the prob variable is obtained using the LpProblem function. The objective function takes into account the prices of beef and chicken, which are multiplied by the variables x1 and x2:

python
Copy code
x1 = LpVariable("ChickenPercent", 0, None, LpInteger)
x2 = LpVariable("BeefPercent", 0)
Constraints

The constraints are defined as follows:

python
Copy code
prob += x1 + x2 == 100, "PercentagesSum"
prob += 0.100 * x1 + 0.200 * x2 >= 8.0, "ProteinRequirement"
prob += 0.080 * x1 + 0.100 * x2 >= 6.0, "FatRequirement"
prob += 0.001 * x1 + 0.005 * x2 <= 2.0, "FibreRequirement"
prob += 0.002 * x1 + 0.005 * x2 <= 0.4, "SaltRequirement"
These constraints ensure that the percentages of chicken and beef add up to 100%, meet the protein and fat requirements, and satisfy the limits for fiber and salt.

Constraints are calculated using the following syntax:

python
Copy code
prob += lpSum([ingredient_vars[i] for i in Ingredients]) == 100, "PercentagesSum"
prob += (
    lpSum([proteinPercent[i] * ingredient_vars[i] for i in Ingredients]) >= 8.0,
    "ProteinRequirement",
)
prob += (
    lpSum([fatPercent[i] * ingredient_vars[i] for i in Ingredients]) >= 6.0,
    "FatRequirement",
)
prob += (
    lpSum([fibrePercent[i] * ingredient_vars[i] for i in Ingredients]) <= 2.0,
    "FibreRequirement",
)
prob += (
    lpSum([saltPercent[i] * ingredient_vars[i] for i in Ingredients]) <= 0.4,
    "SaltRequirement",
)
Optimization Type

This is a maximization problem. By allocating resources efficiently, such as money or materials, the goal is to maximize the utilization or benefit. In this example, Whiskas aims to maximize their profits by allocating their resources in the most efficient way possible.

WhiskasModel1.py Results

After running the WhiskasModel1.py code without any changes, the following variable values are obtained:

Status: Optimal

BeefPercent: 66.0
ChickenPercent: 34.0
Total Cost of Ingredients per can: 0.97