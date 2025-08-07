Min Value Point = 
VAR min_val = MINX(ALLSELECTED('Date Table'), [Total Cost]) //total cost is sum of two values, of which one is measure value
RETURN
IF(ABS([Measure value] - min_val) < 0.01, [Total Cost], BLANK())
