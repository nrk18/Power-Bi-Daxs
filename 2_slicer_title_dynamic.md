Page title = 
VAR Sel_Reg = VALUES('Sublot Lookup code'[Region])  //slicer 1
VAR Sel_Sl = VALUES('Sublot Lookup code'[Sublot Name])  //slicer 2
RETURN
//CONCATENATE(VALUES('Sublot Lookup code'[Sublot Name])," ,")
SWITCH(
                    TRUE(),
                    AND(COUNTROWS(Sel_Sl) =1, COUNTROWS(Sel_Reg)=1), "Text: " & Sel_Reg & " - " & Sel_Sl , 
                    AND(COUNTROWS(Sel_Sl) <> 1,COUNTROWS(Sel_Reg) = 1), "Text " & Sel_Reg & " - " & CONCATENATEx( VALUES('Sublot Lookup code'[Sublot Name]) , 'Sublot Lookup code'[Sublot Name], " ,"),
                    ISFILTERED('Sublot Lookup code'[Region]), "Project Accounts: R12+Accrual " & CONCATENATEx( VALUES('Sublot Lookup code'[Region]) , 'Sublot Lookup code'[Region], " ,") & " - " & CONCATENATEx( VALUES('Sublot Lookup code'[Sublot Name]) , 'Sublot Lookup code'[Sublot Name], " ,"),
                    "Text (Consolidated)"
)
// 
