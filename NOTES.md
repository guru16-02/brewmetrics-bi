# DAX Development Notes (GitHub Copilot Interaction Log)

### Measure 1: MoM Sales Growth %
* **Copilot Initial Suggestion:**
  ```dax
  MoM Growth = 
  ([Total Sales] - CALCULATE([Total Sales], PREVIOUSMONTH(Dim_Date[Date]))) 
  / CALCULATE([Total Sales], PREVIOUSMONTH(Dim_Date[Date]))


  Issues & Corrections:
The raw AI suggestion used direct division, which throws #DIV/0! errors when evaluating the first available month (April) since there is no prior data. I rewrote it using DIVIDE() with a BLANK() fallback and structured it with VAR blocks and DATEADD for safer, clearer monthly boundary evaluation.