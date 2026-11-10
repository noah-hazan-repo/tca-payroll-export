# Total Care ABA – ADP Payroll Export

A single static page (`index.html`). After you sign in with Google, it queries
`payroll_mart.adp_payroll_export_vw` in BigQuery for the pay period you pick and
downloads a ZIP with one ADP import file per state (`PR<co code>EPI.csv`), plus
`NOT_EXPORTED_issues.csv` for rows ADP can't import.

The page contains no data or credentials. Every query runs as the signed-in
user, so access is controlled in Google Cloud IAM:

- `roles/bigquery.jobUser` on project `total-care-aba-462720`
- `roles/bigquery.dataViewer` on the datasets behind the view
- `roles/storage.objectViewer` on bucket `gs://total-care-aba`
