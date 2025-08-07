Max Value Point = 
VAR max_val = MAXX(ALLSELECTED('Date Table'), [Measure value]) // change to MINX for minimum value for the measure
RETURN
IF([Measure value] = max_val, max_val, BLANK())
