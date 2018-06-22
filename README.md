# General
<summary>Auto Attack</summary>

````js
/run if GetUnitName("target")==nil then TargetNearestEnemy() end for z=1,112 do if IsAttackAction(z) then if not IsCurrentAction(z) then UseAction(z) end end end
````
<summary>&nbsp;Auto Shot</summary>
 
````js
/run if GetUnitName("target")==nil then TargetNearestEnemy() end if CheckInteractDistance("target",3) and not PlayerFrame.inCombat then RunMacro("aa") elseif not IsAutoRepeatAction(1) then CastSpellByName("Auto Shot") end

````
<summary>Bandage Self</summary>
 
````js
/run UseContainerItem(0,3) SpellTargetUnit("player")

````
<summary>Bandage Unit e.g. Pet</summary>
 
````js
/run TargetUnit("pet") UseContainerItem(0,3) TargetLastTarget()
````

# Druid
<summary>Bear Form, Feral Charge, Bash, Auto Attack</summary>
 
````js
/run c,_,_,a=CastSpellByName,GetShapeshiftFormInfo(1) if nil then CastSpellByName("Bash") end RunMacro("aa") if not a then CastShapeshiftForm(1) end if CheckInteractDistance("target",3) then c"Bash" else c"Feral Charge" end
````
<summary>Cancel Form</summary>
 
````js
/run if buffed("Prowl",'player') then CastSpellByName("Prowl") else for i=1,GetNumShapeshiftForms() do _,_,a=GetShapeshiftFormInfo(i) if a~=nil then CastShapeshiftForm(i) break end end end
````

<summary>Claw, Auto Attack</summary>
 
````js
/run RunMacro("aa") CastSpellByName("Claw")
````
<summary>Cat Form, Dash</summary>
 
````js
/run c,_,_,a=CastSpellByName,GetShapeshiftFormInfo(3) if nil then c("Dash") end if not a then CastShapeshiftForm(3) else c"Dash" end
````
<summary>Faerie Fire all forms</summary>
 
````js
/run i,x,c=1,0,CastSpellByName if nil then c("Faerie Fire (Feral)()") end while UnitBuff("player",i) do if strfind(UnitBuff("player",i),"Form")~=nil then x=1 end i=i+1 end if x==1 then c"Faerie Fire (Feral)()" else c"Faerie Fire" end
````
<summary>Bear Form, Growl</summary>
 
````js
/run c,_,_,a=CastSpellByName,GetShapeshiftFormInfo(1) if nil then c("Growl") end RunMacro("aa") if not a then CastShapeshiftForm(1) else c"Growl" end
````
<summary>Maul, Auto Attack</summary>
 
````js
/run RunMacro("aa") CastSpellByName("Maul")
````
<summary>Cat Form, Prowl, Pounce</summary>
 
````js
/run c,_,_,a=CastSpellByName,GetShapeshiftFormInfo(3) if nil then CastSpellByName("Prowl") end ClearTarget() TargetNearestEnemy() if not a then CastShapeshiftForm(3) end if a and buffed("Prowl",'player') then c"Pounce" else c"Prowl" end
````
<summary>Rejuvenation, no override</summary>
 
````js
/run c,r=CastSpellByName,"Rejuvenation" if nil then c("Rejuvenation") end if UnitExists("target") and UnitIsFriend("target","player") then if not buffed(r,'target') then c(r) end return end if not buffed(r,'player') then cast(r,1) end
````
<summary>Cat Form, Shred, Ravage</summary>
 
````js
/run c,_,_,a=CastSpellByName,GetShapeshiftFormInfo(3) if nil then c("Shred") end if not a then CastShapeshiftForm(3) end if a and buffed("Prowl",'player') then ClearTarget() TargetNearestEnemy() c"Shred" else RunMacro("aa") c"Shred" end
````
<summary>Travel Form</summary>
 
````js
/run if not buffed("Travel Form",'player') then cast("Travel Form(Shapeshift)") end
/run if not buffed("Aquatic Form",'player') then cast("Aquatic Form(Shapeshift)") end
/run UIErrorsFrame:Clear()
````
<summary>Wrath, Auto Attack</summary>
 
````js
/run RunMacro("aa") CastSpellByName("Wrath")
````

# Hunter

<summary>Aspect of the Cheetah</summary>

````js
/run i,x=1,0 while UnitBuff("player",i) do if UnitBuff("player",i)=="Interface\\Icons\\Ability_Mount_JungleTiger" then x=1 end i=i+1 end if x==0 then CastSpellByName("Aspect of the Cheetah") end
````

<summary>Aspect of the Hawk</summary>

````js
/run i,x=1,0 while UnitBuff("player",i) do if UnitBuff("player",i)=="Interface\\Icons\\Spell_Nature_RavenForm" then x=1 end i=i+1 end if x==0 then CastSpellByName("Aspect of the Hawk") end
````

<summary>Aspect of the Monkey, Deterrence</summary>

````js
/run CastSpellByName("Deterrence")
/run i,x=1,0 while UnitBuff("player",i) do if UnitBuff("player",i)=="Interface\\Icons\\Ability_Hunter_AspectOfTheMonkey" then x=1 end i=i+1 end if x==0 then CastSpellByName("Aspect of the Monkey") end
````

<summary>Concussive Shot, Wing Clip</summary>

````js
/run c=CastSpellByName if nil then c("Concussive Shot") end RunMacro("as") if CheckInteractDistance("target",3) then c"Wing Clip" c"Wing Clip(Rank 1)" else c"Concussive Shot" end
````

<summary>Feign Death</summary>

````js
/run if UnitAffectingCombat("player") then CastSpellByName("Feign Death") end
````

<summary>Freezing Trap, Feign Death</summary>

````js
/run PetPassiveMode() PetFollow()
/run if nil then CastSpellByName("Freezing Trap") end if UnitAffectingCombat("player") then CastSpellByName("Feign Death") else CastSpellByName("Freezing Trap") end
````

<summary>Revive Pet, Dismiss Pet</summary>

````js
/run c,u=CastSpellByName if nil then c("Revive Pet") end if UnitExists("pet") then if UnitHealth("pet")==0 then c"Revive Pet" else c"Dismiss Pet" end else c"Revive Pet" end
````

<summary>Feed Pet, Call Pet</summary>

````js
/run c,g=CastSpellByName,GetPetHappiness RunMacro("pcf") if nil then UseContainerItem(0,1) end if not UnitExists("pet") then c"Call Pet" elseif g()~=nil and g()~=3 and x==0 then c"Feed Pet" PickupContainerItem(0,1) end UseContainerItem(0,0)
````

<summary>Feed Pet Check</summary>

````js
/run i,x=1,0 while UnitBuff("pet",i) do if UnitBuff("pet",i)=="Interface\\Icons\\Ability_Hunter_BeastTraining" then x=1 end i=i+1 end
````

<summary>Mend Pet, Call Pet</summary>

````js
/run i,x,c=1,0,CastSpellByName if nil then c("Mend Pet") end while UnitBuff("pet",i) do if UnitBuff("pet",i)=="Interface\\Icons\\Ability_Hunter_MendPet" then x=1 end i=i+1 end if not UnitExists("pet") then c"Call Pet" elseif x==0 then c"Mend Pet" end
````

<summary>Growl</summary>

````js
/run c=CastSpellByName if nil then c("Growl") end if GetUnitName("target")==nil then TargetNearestEnemy() end c"Growl" PetAttack() PetDefensiveMode()
````

<summary>Raptor Strike, Counterattack, Mongoose Bite, Auto Attack</summary>

````js
/run RunMacro("aa")
/cast Raptor Strike
/cast Counterattack
/cast Mongoose Bite
````

<summary>Scorpid Sting, Viper Sting</summary>

````js
/run c,u=CastSpellByName,UnitClass("target") if nil then c("Viper Sting") end if u=="Rogue" or u=="Warrior" then c"Scorpid Sting" else c"Viper Sting" end

````

<summary>Pet Follow</summary>
 
````js
/run PetFollow() PetPassiveMode()
````

<summary>Pet Stay</summary>
 
````js
/run CastPetAction(3) PetPassiveMode()

````
