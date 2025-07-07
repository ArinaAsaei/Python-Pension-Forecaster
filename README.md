# Pension Fund Stochastic Forecasting & Valuation Engine

A comprehensive Python toolkit for performing actuarial valuations and stochastic forecasts for Defined Benefit (DB) pension plans.

> **⚠️ Project Status: In Progress & Core Engine Complete**
>
> This project provides a powerful, class-based engine for pension fund analysis. The core logic for both deterministic valuation (`PensionValuation` class) and stochastic population forecasting (`PensionForecaster` class) is implemented. The engine has been tested with a standard set of plan provisions, but is still under development to support a wider array of designs and to add a user interface.

---
## About The Project

This project provides an object-oriented framework for modeling the complex dynamics of Defined Benefit pension plans. It is designed to help actuaries and plan sponsors understand both the current liabilities and the long-term financial trajectory of a pension fund under uncertainty.

The toolkit is built around two primary classes:
* **`PensionValuation`**: A powerful actuarial engine that calculates key liability figures (e.g., Actuarial Accrued Liability, Normal Cost) for a given census of members using various actuarial cost methods (PUC, EAN).
* **`PensionForecaster`**: A dynamic simulator that takes the valuation engine as a tool. It projects the fund's population and financials over a long-term horizon by simulating annual life events (retirement, termination, death, new hires) and recalculating liabilities each year.

##  Core Features Implemented

* **Detailed Member Modeling:** Simulates individual member life cycles, including hiring, salary growth, termination, retirement (normal and early), and mortality.
* **Stochastic Population Forecasting:** Dynamically generates new entrants based on statistical profiles (for age, salary, and marital status) and simulates annual life events like spouse mortality, divorce, and new marriages.
* **Flexible Plan & Actuarial Assumptions:** Manages all plan rules—from benefit formulas and vesting to complex death benefits—through a detailed and easily configurable dictionary structure. Decrement rates can be defined with dynamic formulas (e.g., `"0.10 - 0.005 * (age - 25)"`).
* **Multiple Actuarial Cost Methods:** The `PensionValuation` engine supports multiple standard cost methods, including Projected Unit Credit (PUC) and Entry Age Normal (EAN).
* **Comprehensive Liability Calculations:** Correctly calculates liabilities for different member statuses, including active employees, retirees, and terminated vested members, and handles various payment options like Joint & Survivor annuities.

---
##  Flexible Assumptions Framework

The engine's flexibility comes from its ability to accept complex parameters via nested dictionaries, allowing for detailed customization of the plan design.

**Example: Plan Provisions Snippet**
```json
{
    "early_retirement_rules": {
        "is_allowed": true,
        "min_age": 55,
        "min_service": 10,
        "reduction_type": "actuarial"
    },
    "death_benefit_rules": {
        "is_provided": true,
        "logic_type": "conditional",
        "conditional_rules": {
            "threshold_variable": "service_years",
            "threshold_value": 10,
            "below_threshold_type": "lump_sum",
            "above_threshold_type": "survivor_annuity"
        },
        "lump_sum_formula": "2 * current_salary"
    }
}
```
---
## 🗺️ Project Roadmap
The following features and improvements are planned for future development:

[ ] Streamlit User Interface: Develop an interactive web application to configure assumptions and visualize valuation and forecast results.

[ ] Expanded Plan Provisions: Add support for more complex benefit formulas and retirement options.

[ ] Advanced Decrement Modeling: Incorporate disability decrements into the simulation.

[ ] Comprehensive Unit Testing: Develop a full suite of tests to validate calculations against a wider range of plan designs and edge cases.

[ ] Detailed Reporting: Implement functions to generate comprehensive PDF reports of the valuation and forecast results.