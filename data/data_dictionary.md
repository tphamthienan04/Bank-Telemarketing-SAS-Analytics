# Data Dictionary: Bank Telemarketing Dataset 🏦

This document outlines the metadata configuration and variable descriptions used in the SAS Enterprise Miner predictive pipeline.

| Variable Name | Model Role | Measurement Level | Description |
| :--- | :--- | :--- | :--- |
| **ID** | ID | Nominal | Client contact ID |
| **age** | Input | Interval | Client's age in years |
| **job** | Input | Nominal | Type of employment |
| **marital** | Input | Nominal | Marital status |
| **education** | Input | Nominal | Education level |
| **default** | Input | Nominal | Has credit in default? (yes / no) |
| **balance** | Input | Interval | Average yearly account balance in euros |
| **housing** | Input | Nominal | Has a housing loan? (yes / no) |
| **loan** | Input | Nominal | Has a personal loan? (yes / no) |
| **contact** | Input | Nominal | Contact communication type |
| **day** | Input | Interval | Last contact day of the month |
| **month** | Input | Nominal | Last contact month of year |
| **duration** | Input | Interval | Last contact duration in seconds |
| **campaign** | Input | Interval | Number of contacts made during this campaign for this client |
| **pdays** | Input | Interval | Days since client was last contacted in a prior campaign (missing = not previously contacted) |
| **previous** | Input | Interval | Number of contacts made before this campaign |
| **poutcome** | Input | Nominal | Outcome of previous campaign |
| **TargetBuy** | Target | Binary | Did the client subscribe to a term deposit? (1 = Yes, 0 = No) |
