# General


# Druid

<details>
<summary>Macros</summary>
 
<details>
 <summary>Bear Form then Feral Charge or Bash</summary>
 
`
/run c,t=CastSpellByName,"target"if nil then CastSpellByName("Bash")end;_,_,a=GetShapeshiftFormInfo(1)RunMacro("aa")if not a then CastShapeshiftForm(1)end;if CheckInteractDistance(t,3)and(not PlayerFrame.inCombat)then c"Bash"else c"Feral Charge"end
`
</details>
&nbsp;
<details>
 <summary>Cancel Form</summary>
 
`
/run if buffed("Prowl",'player')then CastSpellByName("Prowl")else for i=1,GetNumShapeshiftForms() do _,_,a=GetShapeshiftFormInfo(i) if a~=nil then CastShapeshiftForm(i)break end;end;end
`
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

</details>

# Hunter

<details>
<summary>Aspect of the Cheetah</summary>

````js
/run i,x=1,0 while UnitBuff("player",i) do if UnitBuff("player",i)=="Interface\\Icons\\Ability_Mount_JungleTiger" then x=1 end i=i+1 end if x==0 then CastSpellByName("Aspect of the Cheetah") end
````
</details>
&nbsp;

<details>
<summary>Aspect of the Hawk</summary>

````js
/run i,x=1,0 while UnitBuff("player",i) do if UnitBuff("player",i)=="Interface\\Icons\\Spell_Nature_RavenForm" then x=1 end i=i+1 end if x==0 then CastSpellByName("Aspect of the Hawk") end
````
</details>
&nbsp;

<details>
<summary>Aspect of the Monkey, Deterrence</summary>

````js
/run CastSpellByName("Deterrence")
/run i,x=1,0 while UnitBuff("player",i) do if UnitBuff("player",i)=="Interface\\Icons\\Ability_Hunter_AspectOfTheMonkey" then x=1 end i=i+1 end if x==0 then CastSpellByName("Aspect of the Monkey") end
````
</details>
&nbsp;

<details>
<summary>Concussive Shot, Wing Clip</summary>

````js
/run c=CastSpellByName if nil then c("Concussive Shot") end RunMacro("as") if CheckInteractDistance("target",3) then c"Wing Clip" c"Wing Clip(Rank 1)" else c"Concussive Shot" end
````
</details>
&nbsp;

<details>
<summary>Feign Death</summary>

````js
/run if UnitAffectingCombat("player") then CastSpellByName("Feign Death") end
````
</details>
&nbsp;

<details>
<summary>Freezing Trap, Feign Death</summary>

````js
/run PetPassiveMode() PetFollow()
/run if nil then CastSpellByName("Freezing Trap") end if UnitAffectingCombat("player") then CastSpellByName("Feign Death") else CastSpellByName("Freezing Trap") end
````
</details>
&nbsp;

<details>
<summary>Revive Pet, Dismiss Pet</summary>

````js
/run c,u=CastSpellByName if nil then c("Revive Pet") end if UnitExists("pet") then if UnitHealth("pet")==0 then c"Revive Pet" else c"Dismiss Pet" end else c"Revive Pet" end
````
</details>
&nbsp;

<details>
<summary>Feed Pet, Call Pet</summary>

````js
/run c,g=CastSpellByName,GetPetHappiness RunMacro("cf") if nil then UseContainerItem(0,1) end if not UnitExists("pet") then c"Call Pet" elseif g()~=nil and g()~=3 and x==0 then c"Feed Pet" PickupContainerItem(0,1) end UseContainerItem(0,0)
````
</details>
&nbsp;

<details>
<summary>Feed Pet Check</summary>

````js
/run i,x=1,0 while UnitBuff("pet",i) do if UnitBuff("pet",i)=="Interface\\Icons\\Ability_Hunter_BeastTraining" then x=1 end i=i+1 end
````
</details>
&nbsp;
<details>
<summary>Mend Pet, Call Pet</summary>

````js
/run c=CastSpellByName if nil then c("Mend Pet") end RunMacro("cm") if not UnitExists("pet") then c"Call Pet" elseif x==0 then c"Mend Pet" end
````
</details>
&nbsp;

<details>
<summary>Growl</summary>

````js
/run c=CastSpellByName if nil then c("Growl") end if GetUnitName("target")==nil then TargetNearestEnemy() end c("Growl") PetAttack() PetDefensiveMode() c("Growl")
````
</details>
&nbsp;

<details>
<summary>Raptor Strike, Counterattack, Mongoose Bite, Auto Attack</summary>

````js
/run RunMacro("aa")
/cast Raptor Strike
/cast Counterattack
/cast Mongoose Bite
````
</details>
&nbsp;

<details>
<summary>Scorpid Sting, Viper Sting</summary>

````js
/run c,u=CastSpellByName,UnitClass("target") if nil then c("Viper Sting") end if u=="Rogue" or u=="Warrior" then c"Scorpid Sting" else c"Viper Sting" end

````
</details>
&nbsp;
