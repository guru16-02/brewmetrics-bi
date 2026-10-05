# DAX Development Notes (GitHub Copilot Interaction Log)

### Measure 1: MoM Sales Growth %
* **Copilot Initial Suggestion:**
  ```dax
  MoM Growth = 
  ([Total Sales] - CALCULATE([Total Sales], PREVIOUSMONTH(Dim_Date[Date]))) 
  / CALCULATE([Total Sales], PREVIOUSMONTH(Dim_Date[Date]))


  Issues & Corrections:
The raw AI suggestion used direct division, which throws #DIV/0! errors when evaluating the first available month (April) since there is no prior data. I rewrote it using DIVIDE() with a BLANK() fallback and structured it with VAR blocks and DATEADD for safer, clearer monthly boundary evaluation.

### Measure 2: Cumulative Sales (Running Total)
* **Copilot Initial Suggestion:**
  ```dax
  Running Total = CALCULATE([Total Sales], FILTER(Dim_Date, Dim_Date[Date] <= MAX(Dim_Date[Date])))\

  Issues & Corrections:
Copilot passed the entire unconstrained Dim_Date table instead of an explicit column reference wrapped in ALLSELECTED(). This caused running totals to reset within slicer selections. Fixed by scoping to ALLSELECTED(Dim_Date[Date]).

### Measure 3: City Sales Rank
* **Copilot Initial Suggestion:**
  ```dax
  City Rank = RANKX(ALL(Fact_Sales[city]), [Total Sales])

  Issues & Corrections:
Copilot attempted to rank directly on Fact_Sales[city] rather than the dimension attribute Dim_City[city], violating star schema separation. It also lacked ISINSCOPE(), which produced an unwanted #1 rank on table subtotal rows. Refactored using ALLSELECTED(Dim_City[city]) and ISINSCOPE().