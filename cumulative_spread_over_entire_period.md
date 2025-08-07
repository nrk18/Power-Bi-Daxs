Cum_all = 
VAR MAXDATE = MAX('Date Table'[Date])
RETURN
CALCULATE(
   SUMX(
    FILTER(
        ALL('Date Table'),
        'Date Table'[Date] >= DATE(2025, 04, 01) &&  //start date
        'Date Table'[Date] <= MAXDATE
    ),
    [month value]
    
))
