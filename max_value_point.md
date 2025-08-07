Max Value Point = 
VAR max_val = MAXX(ALLSELECTED('Date Table'), [Measure value])
RETURN
IF([Measure value] = max_val, max_val, BLANK())
