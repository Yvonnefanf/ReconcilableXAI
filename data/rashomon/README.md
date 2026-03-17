# Rashomon dashboard data

The dashboard supports multiple datasets. Each dataset has its own subfolder with the same JSON structure.

## COMPAS (Regression)

```bash
cd /path/to/Multiplicity
python main.py
```

Writes to `compas/`:

- `rashomon_dashboard.json` – taskType: regression, radar + recommendation
- `global_results.json` – test MAE/RMSE/R2
- `local_results_long.json` – pred_x, local_MAE, individual_fairness_diff per (seed, test_case)
- `selected_model_metadata.json` – hyperparameters
- `test_cases.json` – top test cases by disagreement (features + prediction_std)

## Loan Approval (Classification)

```bash
python main_loanApproval.py
```

Writes to `loan_approval/`:

- `rashomon_dashboard.json` – taskType: classification, labelNames: ["Rejected", "Approved"]
- `global_results.json` – test_accuracy, test_logloss
- `local_results_long.json` – pred_prob, pred_class, local_accuracy, individual_fairness_diff per (seed, test_case)
- `selected_model_metadata.json` – hyperparameters
- `test_cases.json` – **all** test cases (features + prediction_std)

The admin dashboard loads from `/data/rashomon/{dataset}/` where dataset is selected in the UI (COMPAS or Loan Approval). For classification, the panel shows predicted probability P(Approved) and class label.
