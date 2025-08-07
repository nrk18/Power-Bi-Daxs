cum_period = 
VAR MAXDATE = MAX('Date Table'[Date])
RETURN
CALCULATE(
    [monthly value], 
    'Date Table'[Date] < Date(2025,06,01),  // end date
    'Date Table'[Date] >= DATE(2025, 04, 01) // start date
)
