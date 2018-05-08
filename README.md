# Druid
<details>
 <summary>Bear Form then Feral Charge or Bash</summary>
 
```js
/run c,t=CastSpellByName,"target"if nil then CastSpellByName("Bash")end;_,_,a=GetShapeshiftFormInfo(1)RunMacro("aa")if not a then CastShapeshiftForm(1)end;if CheckInteractDistance(t,3)and(not PlayerFrame.inCombat)then c"Bash"else c"Feral Charge"end
```
</details>
&nbsp;
<details>
 <summary>Cancel Form</summary>
 
````js
/run if buffed("Prowl",'player')then CastSpellByName("Prowl")else for i=1,GetNumShapeshiftForms() do _,_,a=GetShapeshiftFormInfo(i) if a~=nil then CastShapeshiftForm(i)break end;end;end
````
</details>
&nbsp;
<details>
 <summary>Claw and Auto Attack</summary>
 
````js
/run RunMacro("aa") CastSpellByName("Claw")
````
</details>
&nbsp;
<details>
 <summary>Cat Form then Dash</summary>
 
````js
/run c=CastSpellByName;if nil then c("Dash")end;_,_,a=GetShapeshiftFormInfo(3)if not a then CastShapeshiftForm(3)else c"Dash"end
````
</details>
&nbsp;
<details>
 <summary>Faerie Fire in all forms</summary>
 
````js
/run i,m,c,u=1,0,CastSpellByName,UnitBuff if nil then c("Faerie Fire")end;while(u("player",i)~=nil)do if(strfind(u("player",i),"Form")~=nil)then m=1 end;i=i+1 end if m==1 then c("Faerie Fire (Feral)")else c("Faerie Fire")end
````
</details>
&nbsp;
<details>
 <summary>Bear Form then Growl</summary>
 
````js
/run c=CastSpellByName;if nil then c("Growl")end _,_,a=GetShapeshiftFormInfo(1)RunMacro("aa")if not a then CastShapeshiftForm(1)else c"Growl"end
````
</details>
&nbsp;
<details>
 <summary>Maul</summary>
 
````js

`/run RunMacro("aa") CastSpellByName("Maul")`
````
</details>
&nbsp;
<details>
 <summary>Cat Form then Prowl then Pounce</summary>
 
````js
/run if nil then CastSpellByName("Prowl")end;ClearTarget();TargetNearestEnemy();c,t=CastSpellByName,"target" _,_,a=GetShapeshiftFormInfo(3)if not a then CastShapeshiftForm(3)end;if a and buffed("Prowl",'player')then c"Pounce";else c"Prowl"end
````
</details>
&nbsp;
<details>
 <summary>Rejuvenation without overriding</summary>
 
````js

/run r="Rejuvenation" if nil then CastSpellByName("Rejuvenation") end if UnitExists("target") and UnitIsFriend("target","player") then if not buffed(r,'target') then CastSpellByName(r) end return end if not buffed(r, 'player') then cast(r,1) end
````
</details>
&nbsp;
<details>
 <summary>Cat Form then Shred or Ravage</summary>
 
````js
/run c,t=CastSpellByName,"target" if nil then c("Shred")end; _,_,a=GetShapeshiftFormInfo(3)if not a then CastShapeshiftForm(3)end;if a and buffed("Prowl",'player')then ClearTarget();TargetNearestEnemy();c"Shred";else RunMacro("aa");c"Shred"end
````
</details>
&nbsp;
<details>
 <summary>Travel Form</summary>
 
````js
/script if not buffed("Travel Form", 'player') then cast("Travel Form(Shapeshift)")end;
/script if not buffed("Aquatic Form", 'player') then cast("Aquatic Form(Shapeshift)")end;
/script UIErrorsFrame:Clear()
````
</details>
&nbsp;
<details>
 <summary>Wrath then Auto Attack</summary>
 
````js
/run RunMacro("aa") CastSpellByName("Wrath")
````
</details>

# Hunter
