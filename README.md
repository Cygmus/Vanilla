# Vanilla
`/run RunMacro("aa")
/run if nil then CastSpellByName("Bash")end
/run c,t=CastSpellByName,"target" _,_,a=GetShapeshiftFormInfo(1)if not a then CastShapeshiftForm(1)else if GetUnitName(t)==nil then TargetNearestEnemy()end;if CheckInteractDistance(t,3)and(not PlayerFrame.inCombat)then c"Bash";else c"Feral Charge"end;end`

bvwrsoibvujnsdifb
