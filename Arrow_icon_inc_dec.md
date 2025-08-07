Arrow = 
// Variables to store arrow paths
var uparrow = "<path d='M10 90 L50 10 L90 90 Z' fill='green' />"
var downarrow = "<path d='M10 10 L50 90 L90 10 Z' fill='red' />"

// Select arrow to use
var arrow = IF([measure value]>=0,uparrow,downarrow)

// Insert arrow into SVG
var svg ="data:image/svg+xml;utf8," &
         "<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'>"
            & arrow & 
         "</svg>"

RETURN svg
