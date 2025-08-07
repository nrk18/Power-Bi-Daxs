//add this to filters pane for the table to apply filtering and set the value as not blank  
Color Condition = 
VAR RRS = SELECTEDVALUE('Risk Score Switch'[Risk Score Switch Fields])  //field parameter
VAR RiskColor = SELECTEDVALUE('Color Filter Table'[Color])   //color selection values on a different table
RETURN

IF( RiskColor <> BLANK(),
    SWITCH(
        
        TRUE(),
        RRS = "'Risk Profiling'[Residual Risk Score]",
                                                        CALCULATE(
                                                                COUNTROWS('Risk Profiling'),
                                                                FILTER(
                                                                    'Risk Profiling',
                                                                    'Risk Profiling'[Color grade residual risk] = RiskColor)
                                                            ),
        RRS = "'Risk Profiling'[Inherent Risk Score]",
                                                        CALCULATE(
                                                                COUNTROWS('Risk Profiling'),
                                                                FILTER(
                                                                    'Risk Profiling',
                                                                    'Risk Profiling'[Color grade inherent risk] = RiskColor)
                                                            ) 
    , 1
        )
    ,1

)
