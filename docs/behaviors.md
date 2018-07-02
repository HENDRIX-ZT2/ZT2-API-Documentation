# Overview
This page lists all known modules and functions that can be used to create ZT2 AI.

---

## "animTableEntry"
(actually, the tag is always the name of the anim set, eg. `Stand`)
#### Attributes: 
- __anim__ (_string_) - The exact animation that should be played in this set, eg. `Stand_Idle`.
- __*behSet__ (_string_) - May apparently be used instead of an anim.
- __*weight__ (_int_) - The probability of using this subset; should add up to 100.
- __*minAnimSpeed__ (_float_) - Minimum anim speed to use in playback.
- __*maxAnimSpeed__ (_float_) - Maximum anim speed to use in playback.
#### Children:
- None

---

## "behaviorTableEntry"
(actually, the tag is always the name of the state the entity is in, eg. `default`, `Stand`, `water`, `underwater`)
#### Attributes:
- __behSet__ (_string_) - Specifies the behSet to be played in the current state.
#### Children:
- None

---

## "randomAnimsEntry"
(The tag is really the name of the anim that should be played, eg. `Stand_Idle`)
#### Attributes:
- __*weight__ (_int_) - The probability of using this anim; should add up to 100.
#### Children:
- None

---

## "randomSetsEntry"
(actually, the tag is always the name of the behSet, eg. `DefaultPant`)
#### Attributes: 
- __weight__ (_int_) - The probability of using this subset; should add up to 100.
#### Children:
- None

---

## "textkeysEntry"
(actually, the tag is always the name of the function, eg. `blowhole`, `tranquilize`, `detachobject`, `attachobject`)
#### Attributes:
- __text__ (_string_) - In one-line txtkeys syntax, specifying nodes etc.
#### Children:
- None

---

## BFAIAttributeFloatMap
#### Attributes:
- __amusement__ (_int_) - (-100, -30, -50, -75),
- __b_Rampage__ (_bool_) - (E true, false),
- __bathroom__ (_int_) - (-100, -40, -50, 30, 5),
- __breath__ (_int_) - (.45, 1.0, 2.5, GE 95, LE 95),
- __dessert__ (_int_) - (-100, -50, -75),
- __exercise__ (_int_) - (-10, -100, -20, -30, -50),
- __explore__ (_int_) - (-25, -30),
- __f_CouldntFindDonationBox__ (_int_) - (1),
- __f_DidFindDonationBox__ (_int_) - (1),
- __gift__ (_int_) - (+25, -100, -50, -75),
- __health__ (_int_) - (-10, -5, 5, G 0, GE 50),
- __hunger__ (_int_) - (-1, -10, -40, GE 90, L 90),
- __hygiene__ (_int_) - (-25, 15, 30, GE 90, L 90),
- __lifespan__ (_int_) - (1.1, GE 2, GE 2.09, GE 5, LE 1),
- __privacy__ (_int_) - (-10, -20, -25, -35, -50),
- __reproduction__ (_int_) - (-20, -27, -30, -40, -50),
- __rest__ (_int_) - (10, 20, GE 70, LE 49, LE 69),
- __social__ (_int_) - (-10, -2, -20, -30, -40),
- __space__ (_int_) - (-40, GE 70, GE 90),
- __stimulation__ (_int_) - (-10, -20, -25, -30, -35),
- __thirst__ (_int_) - (-1, -3, -50, GE 90, L 90),
- __viewanimals__ (_int_) - (-100, -50, -75),
- __wetness__ (_int_) - (-50, 10, 50),
- __work__ (_int_) - (-.5, -1, -2, -5, -50),
#### Children:
- None

---

## BFAIBiomeMap
Maps each biome to a preference / weight in range 0-1. Always called from [BFAIEvalData](#bfaievaldata).
#### Attributes:
- __"biome"__ (_float_) - Assigns the given preference to the named biome.
#### Children:
- None

#### Example:
```xml
 <BFAIBiomeMap alpine=".30" borealforest=".75" temperateforest=".75" desert=".10" grassland=".50" savannah=".10" tropicalrainforest=".10" scrub=".10" tundra=".10" wetlands="1.00"/>
```

---

## BFAICompletionData
#### Attributes:
- __invalidateTarget__ (_bool_) - (true),
- __needPointsBad__ (_float_) - (.1, 1, 30, 5, 50),
#### Children:
- [BFAIAttributeFloatMap](#bfaiattributefloatmap)
- [BFAISubjectData](#bfaisubjectdata)
- [BFAITargetData](#bfaitargetdata)
- [BFAITokenList](#bfaitokenlist)
- [BFBehExecTask](#bfbehexectask)
- [BFBehSendToken](#bfbehsendtoken)

---

## BFAICreateData
#### Attributes:
- None
#### Children:
- [Objects](#objects)
- [Subjects](#subjects)
- [Subjects_AND](#subjects_and)
- [Targets](#targets)
- [Targets_AND](#targets_and)

---

## BFAIEvalData
#### Attributes:
- __fixedScore__ (_int_) - (.00005, 10000, 12000, 12003, 12005),
- __needPointsBad__ (_int_) - (.1, 1, 30, 5, 50),
- __needPointsGood__ (_float_) - (.1, 10, 15, 5, 50),
- __?f_needPointsGood?__ (_string_) - (15, G 0, L 50),
- __!needGoodPoints!__ (_int_) - (5),
- __!needPointsgood!__ (_int_) - (5),
#### Children:
- [BFAIAttributeFloatMap](#bfaiattributefloatmap)
- [BFAIBiomeMap](#bfaibiomemap)

---

## BFAIFailureData
#### Attributes:
- None
#### Children:
- [BFAIAttributeFloatMap](#bfaiattributefloatmap)
- [BFBehExecTask](#bfbehexectask)

---

## BFAISubjectData
Must be called from [BFBehSetAttribute](#bfbehsetattribute).
#### Attributes:
- __"attribute"__ (_int_) - Assigns the given integer to the named attribute.
#### Children:
- TrickLearning (not documented)

#### Example:
```xml
 <BFBehSetAttribute>
	<BFAISubjectData health="30"/>
 </BFBehSetAttribute>
```

---

## BFAITargetData
Must be called from [BFBehSetAttribute](#bfbehsetattribute).
#### Attributes:
- __"attribute"__ (_int_) - Assigns the given integer to the named attribute.
#### Children:
- Options (not documented)

#### Example:
```xml
 <BFBehSetAttribute>
	<BFAITargetData exercise="-10"/>
 </BFBehSetAttribute>
```

---

## BFAITaskTemplate
#### Attributes:
- __CursorTask__ (_bool_) - (false),
- __Name__ (_string_) - (Ambient, DefaultTask_Animal, Die, Die_Land, t_Attack),
- __Priority__ (_int_) - (1, 100, 2, 5, 900),
- __TaskDelayMax__ (_int_) - (120, 15, 30, 300, 60),
- __TaskDelayMin__ (_int_) - (10, 20, 30, 300, 60),
- __UniqueID__ (_string_) - (ambient_ground:Ambient, ambient_ground:Die, ambient_water:Ambient, ambient_water:Die, ambient_water:Die_Land),
- __UseForKeeperPanel__ (_bool_) - (false),
- __attachTag__ (_string_) - (Mouth, back, cleanerfish, lefthandyoung, mouth),
- __distanceInfluenced__ (_bool_) - (false),
- __objectContainer__ (_string_) - (back, lefthandyoung, mouth, righthand),
- __priority__ (_int_) - (-1, 0, 1, 10, 2),
- __reserveTag__ (_string_) - (Animal_Training_Area, Animals_Waiting_Area, Animals_Waiting_Area_Treat, General, Rampage),
- __sensorTag__ (_string_) - (explore, habitat),
- __useFromTokenQualifiers__ (_bool_) - (true),
#### Children:
- [BFAICompletionData](#bfaicompletiondata)
- [BFAICreateData](#bfaicreatedata)
- [BFAIEvalData](#bfaievaldata)
- [BFAIFailureData](#bfaifailuredata)
- [BFAIValidationData](#bfaivalidationdata)
- [BFBehExecTask](#bfbehexectask)

---

## BFAITaskTemplateList
#### Attributes:
- None
#### Children:
- [BFAITaskTemplate](#bfaitasktemplate)

---

## BFAIToken
A token (= an object) that can be sent to an entity / other entities. Must be called from [BFAITokenList](#bfaitokenlist)
#### Attributes:
- __Name__ (_string_) - Name of the token to be sent. Usuall prefaced with ´t_´, eg. ´t_GiveTreat´
- __GiveTo__ (_string_) - 
- __Payload__ (_string_) - Either `subject` or `target`.
- __Radius__ (_int_) - How far can this token be sent?
- __Chance__ (_int_) - How likely will this token be sent, in percent.
- __Reconsider__ (_bool_) - Default is `false`.
- __RetainOnFailure__ (_bool_) - Default is `false`.
- __RetainOnSuccess__ (_bool_) - Default is `false`.
- __RetainOnError__ (_bool_) - Default is `false`.
- __OnlyOne__ (_bool_) - Default is `false`.
- __ModifyChance__ (_bool_) - Default is `false`.
- __Timein__ (_float_) - Delay, in seconds?
- __Timeout__ (_int_) - Delay, in seconds?
#### Children:
- None

---

## BFAITokenList
Contains [BFAITokens](#bfaitoken). Can be called from [BFBehSendToken](#bfbehsendtoken), [ZTBehSplashGuest](#ztbehsplashguest) and possibly more
#### Attributes:
- None
#### Children:
- [BFAIToken](#bfaitoken)

#### Example:
```xml
 <BFBehSendToken>
	<BFAITokenList>
	   <BFAIToken Name="t_GiveTreat" Payload="subject" GiveTo="target" Timeout="5" Reconsider="true"/>
	</BFAITokenList>
 </BFBehSendToken>
```

---

## BFAIValidationData
#### Attributes:
- None
#### Children:
- [Subjects](#subjects)
- [Targets](#targets)

---

## BFBehAnimSwitchSet
May switch between different behSets according to the state (= anim set) the subject entity is currently in.
#### Attributes:
- __*loopFlag__ (_bool_) - Default is `false`.
#### Children:
- [behaviorTable](#behaviortable)

#### Example:
```xml
 <BFBehAnimSwitchSet>
	<behaviorTable>
	   <Stand behSet="DefaultStand"/>
	   <Lie behSet="DefaultLie"/>
	   <Sleep behSet="DefaultSleep"/>
	   <Rest behSet="DefaultRest"/>
	   <default behSet="DefaultStand"/>
	</behaviorTable>
 </BFBehAnimSwitchSet>
```
		 
---

## BFBehAnimate
Plays an animation, optionally specifying ["textkeys"](#textkeys) as well.
#### Attributes:
- __targetAnim__ (_string_) - The name of the anim that should be played.
- __*playTime__ (_int_) - How long this behSet should be played.
- __*animSpeed__ (_float_) - Exact anim speed to use in playback.
- __*minAnimSpeed__ (_float_) - Minimum anim speed to use in playback.
- __*maxAnimSpeed__ (_float_) - Maximum anim speed to use in playback.
- __*loopFlag__ (_bool_) - Should this loop forever? Default is `false`.
- __*interruptFlag__ (_bool_) - Allow interruptions? Default is `false`.
- __*interruptible__ (_bool_) - Can this anim be stopped during playback? Default is `false`.
- __*blendDuration__ (_int_) - Probably orphaned and not used.
- __*groundFit__ (_bool_) - Fit to ground according to leg nodes? Default is `true`.
- __*physObj__ (_string_) - For multi-piece objects, which physObj should be animated (eg. `Vendor` for shops)
#### Children:
- ["textkeys"](#textkeys)

---

## BFBehAnimateRandom
Randomly plays an anim from the [randomAnims](#randomanims) table.
#### Attributes:
- __minPlays__ (_int_) - How long many times should this behSet be run?
- __maxPlays__ (_int_) - How long many times should this behSet be run?
#### Children:
- [randomAnims](#randomanims)

---

## BFBehAnimateSwitch
Switches between different animations according to which state (anim set) the AI is in.
#### Attributes:
- None
#### Children:
- [animTable](#animtable)

#### Example:
```xml
 <BFBehAnimateSwitch>
	<animTable>
	   <Swim anim="TreadWater_Idle"/>
	   <TreadWater anim="TreadWater_Idle"/>
	   <default anim="TreadWater_Idle"/>
	</animTable>
 </BFBehAnimateSwitch>
```
---

## BFBehAnimateTAP
Starts a TAP interaction, must be preceded by [BFBehDockTAP](#bfbehdocktap).
#### Attributes:
- __subjectNode__ (_string_) - Name of the subject's dock node, eg. `Node_Mouth`, `Floor`...
- __targetTAP__ (_string_) - The name of the TAP anim / node the entity should follow.
- __exitTap__ (_bool_) - Either `true` or `false`.
- __exitTAP__ (_bool_) - Either `true` or `false`.
#### Children:
- None

---

## BFBehAttachObject
Attaches an object to the subject.
#### Attributes:
- __attachEntity__ (_string_) - May be the name of an entity (eg. `Trash`) or a property referring to an entity (eg. `s_prop`).
- __targetAnim__ (_string_) - The name of the anim that should be played during attaching.
- __subjectNode__ (_string_) - Name of the subject's node that will be parent to the attachment, eg. `Node_Eat`. This is often specified in the targetAnim's txtkey rather than explicitly in the BEH.
- __targetNode__ (_string_) - Name of the target's attachment root node, usually `Dock_Attach`...
- __detachAction__ (_string_) - (killitem, dropitem, inventory)
- __detachBehSet__ (_string_) - (Chew, DropYoung, DetachBaby, LetBabyOff, DetachRat)
- __container__ (_string_) - (foodprop, righthand, lefthandobject, mouth, head_inventory, ...)
- __locoMod__ (_string_) - (carry, carryback, drag, carryyoung, carrybaby)
- __targetBehSet__ (_string_) - (DockFight, HitMediumEqual, BiteMed, Rendezvous, DefendEqual, ...)
- __physObjToHide__ (_string_) - (mainObj, prop, ballprop)
- __interruptFlag__ (_bool_) - (true)
#### Children:
- None

#### Example:
```xml
 <BFBehAttachObject attachEntity="s_prop" targetAnim="Graze_Idle" targetNode="Dock_Attach" detachAction="killitem" container="foodprop"/>
```
 
---

## BFBehDetachObject
Detaches an object from the subject.
#### Attributes:
- __targetAnim__ (_string_) - The name of the anim that should be played.
- __detachEntity__ (_string_) - (object, ShakerToy, ShakerToy_Open, BrownFish_Prop, Remora, ...)
- __detachAction__ (_string_) - (killitem, dropitem, inventory),
#### Children:
- textkeys

---

## BFBehDock
Docks an entity exactly according to subject's and target's dock nodes.
#### Attributes:
- __subjectNode__ (_string_) - Name of the subject's dock node, eg. `Node_Mouth`, `Floor`...
- __targetNode__ (_string_) - Name of the target's dock node, eg. `p_InvestigateNode`, `Dock_Attach`...
- __targetAnim__ (_string_) - The name of the anim that should be played during docking.
- __*locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
- __*avoidWater__ (_bool_) - Should the entity try to stay on land? Default is `false`.
- __redock__ (_bool_) - Default is `false`.
- __reserveSlotName__ (_string_) - Either `general` or `Trainer`.
- __*interpolationDistance__ (_float_) - ?
#### Children:
- 

---

## BFBehDockNow
This (probably) is the docking operation that greatly speeds up an entity's movement to reach the dock almost instantly.
#### Attributes:
- __subjectNode__ (_string_) - Name of the subject's dock node, eg. `Node_Mouth`, `Floor`...
- __targetNode__ (_string_) - Name of the target's dock node, eg. `p_InvestigateNode`, `Dock_Attach`...
- __targetAnim__ (_string_) - The name of the anim that should be played during docking.
- __reserveSlotName__ (_string_) - Either `general` or `Trainer`.
- __redock__ (_bool_) - Default is `false`.
#### Children:
- None

---

## BFBehDockRadial
Docks an entity exactly according to subject's dock nodes, ignoring the rotation specified by the target's dock node.
#### Attributes:
- __subjectNode__ (_string_) - Name of the subject's dock node, eg. `Node_Mouth`, `Floor`...
- __*targetNode__ (_string_) - Name of the target's dock node, eg. `p_InvestigateNode`, `Dock_Attach`...
- __targetAnim__ (_string_) - Anim the subject should play when docking with the target, eg. `Fly_Ahead`.
- __targetRadius__ (_int_) - Radius around the target.
- __*rotError__ (_int_) - Always 180.
- __*locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
- __*dockRadius__ (_float_) - 
- __*interpolationDistance__ (_float_) - ?
#### Children:
- None

---

## BFBehDockSpline
Docks usin spline interpolation, in 3D?
#### Attributes:
- __subjectNode__ (_string_) - Name of the subject's dock node, eg. `Node_Mouth`, `Floor`...
- __targetNode__ (_string_) - Name of the target's dock node, eg. `p_InvestigateNode`, `Dock_Attach`...
- __targetAnim__ (_string_) - The name of the anim that should be played.
- __*locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
- __ignoreCollisionWithTarget__ (_bool_) - Default is `true`.
- __useBuoyNodes__ (_bool_) - Default is `true`.
- __redock__ (_bool_) - Default is `false`.
#### Children:
- None

---

## BFBehDockTAP
Starts a TAP interaction, is followed by [BFBehAnimateTAP](#bfbehanimatetap).
#### Attributes:
- __subjectNode__ (_string_) - Name of the subject's dock node, eg. `Node_Mouth`, `Floor`...
- __targetAnim__ (_string_) - The name of the anim that should be played.
- __targetTAP__ (_string_) - The name of the TAP anim / node the entity should dock at.
#### Children:
- None

---

## BFBehEnter
#### Attributes:
- None
#### Children:
- None

---

## BFBehEscapeObstacle
#### Attributes:
- __*locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
- __escapeTime__ (_int_) - (5, 20)
- __escapeRadius__ (_int_) - (5)
#### Children:
- None

---

## BFBehEvasion
Directed motion fleeing from a target, optionally avoiding third-party entities given in [avoidEntityTypes](#avoidentitytypes).
#### Attributes:
- __locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
- __evasionRadius__ (_int_) - Minimal distance between subject and target to stop evading.
- __evasionTime__ (_int_) - How much time should be spent evading the target?
- __*avoidWater__ (_bool_) - Should the entity try to stay on land? Default is `false`.
- __*avoidLand__ (_bool_) - Should the entity try to stay in water? Default is `false`.
#### Children:
- *[avoidEntityTypes](#avoidentitytypes)

---

## BFBehExecTask
The TSK equivalent to the BEH's [behaviors](#behaviors) container. Can use more or less the same functions.
#### Attributes:
- None
#### Children:
- [BFAISubjectData](#bfaisubjectdata)
- [BFBehAnimate](#bfbehanimate)
- [BFBehAnimateRandom](#bfbehanimaterandom)
- [BFBehDock](#bfbehdock)
- [BFBehDockRadial](#bfbehdockradial)
- [BFBehDockSpline](#bfbehdockspline)
- [BFBehEnter](#bfbehenter)
- [BFBehEscapeObstacle](#bfbehescapeobstacle)
- [BFBehEvasion](#bfbehevasion)
- [BFBehFaceTarget](#bfbehfacetarget)
- [BFBehFall](#bfbehfall)
- [BFBehHeadLook](#bfbehheadlook)
- [BFBehKill](#bfbehkill)
- [BFBehLocoSwitchSet](#bfbehlocoswitchset)
- [BFBehMove](#bfbehmove)
- [BFBehPlaySet](#bfbehplayset)
- [BFBehPursuit](#bfbehpursuit)
- [BFBehRandomSet](#bfbehrandomset)
- [BFBehScript](#bfbehscript)
- [BFBehSendToken](#bfbehsendtoken)
- [BFBehSetAttribute](#bfbehsetattribute)
- [BFBehSpawn](#bfbehspawn)
- [BFBehSyncSet](#bfbehsyncset)
- [BFBehWander](#bfbehwander)
- [ZTBehAddSubjectAsDiseaseTarget](#ztbehaddsubjectasdiseasetarget)
- [ZTBehChangeWaterDirtiness](#ztbehchangewaterdirtiness)
- [ZTBehDockFence](#ztbehdockfence)
- [ZTBehDockTankWall](#ztbehdocktankwall)
- [ZTBehDockWater](#ztbehdockwater)
- [ZTBehEconomy](#ztbeheconomy)
- [ZTBehFeedback](#ztbehfeedback)
- [ZTBehKickOffRider](#ztbehkickoffrider)
- [ZTBehMorph](#ztbehmorph)
- [ZTBehStaffTrainAnimal](#ztbehstafftrainanimal)
- [ZTBehTargetFence](#ztbehtargetfence)
- [ZTBehTeleportToLoc](#ztbehteleporttoloc)
- [ZTBehUsePortal](#ztbehuseportal)
- [ZTBehViewEvent](#ztbehviewevent)

---

## BFBehFaceTarget
Makes the subject face its target, preferably by playing the appropriate turning animations.
#### Attributes:
- None
#### Children:
- None

---

## BFBehFall
#### Attributes:
- None
#### Children:
- None

---

## BFBehFollowEntity
Makes the subject follow the target.
#### Attributes:
- __subjectNode__ (_string_) - Name of the subject's follow node, eg. `Node_Mouth`, `Floor`...
- __targetNode__ (_string_) - Name of the target's (ie. the leader's) follow node, eg. `p_InvestigateNode`, `Dock_Attach`...
- __*locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
- __*minPlayTime__ (_int_) - How long this behSet should be played.
- __*maxPlayTime__ (_int_) - How long this behSet should be played.
#### Children:
- None

---

## BFBehHeadLook
Toggles the secondary headlook component in the XML.
#### Attributes:
- __disengage__ (_bool_) Turns it off again. Default is `false`.
#### Children:
- None

---

## BFBehKill
Deletes entities, optionally fading them out.
#### Attributes:
- __killSubject__ (_bool_) - Default is `false`.
- __killTarget__ (_bool_) - Default is `false`.
- __killUsingDestroyEntity__ (_bool_) - Default is `false`.
- __radiusKillType__ (_string_) - Probably related to the above bool, names an entity like ´fence´, `ShakerToy_Open` to be killed in the radius (below).
- __radius__ (_int_) - The radius in which entities of the given type should be killed in.
- __targetAnim__ (_string_) - The name of the anim that should be played.
- __*fadeOutPeriod__ (_int_) - Duration of the fadeout in seconds, default is probably `0`.
#### Children:
- None

#### Example:
```xml
 <BFBehKill targetAnim="Stand_BashFence" killTarget="true" radius="5" radiusKillType="fence" fadeOutPeriod="1" killUsingDestroyEntity="true"/>
```

---

## BFBehLocoSwitchSet
May switch between different behSets according to the location the subject entity is currently in.
#### Attributes:
- __*switch__ (_bool_) - Default is `true`.
#### Children:
- [behaviorTable](#behaviortable)

#### Example:
```xml
 <BFBehLocoSwitchSet>
	<behaviorTable>
	   <ground behSet="Ground_Failure"/>
	   <water behSet="Water_Failure"/>
	</behaviorTable>
 </BFBehLocoSwitchSet>
```

---

## BFBehMove
#### Attributes:
- __*depthBelowSurface__ (_int_ or comparison) - eg. (4, 0, 12, G 1, LE 1, ...)
- __*pathRadius__ (_int_) - (0, 3, 10, 7, 20, ...)
- __*moveRadius__ (_int_) - (1000, 5, 1, 3, 4, ...)
- __*closestApproach__ (_bool_) - Default is `false`.
- __*targetNode__ (_string_) - name of the dock node, eg. `p_InvestigateNode`, `Dock_Attach`...
- __*locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
- __*heightAboveFloor__ (_float_) - Seafloor offset?
- __*hitRadius__ (_int_) - (5, 3, 10, 8, 6, ...)
- __*depthAboveBottom__ (_int_ or comparison) - (LE 1, LE 3, 1)
#### Children:
- None

---

## BFBehPlaySet
Very generic function that simply plays back another behSet.
#### Attributes:
- __behSet__ (_string_) - The name of the behSet to be played.
- __*playTime__ (_int_) - How long this behSet should be played.
- __*interruptEvent__ (_string_) - Apparently, this event stops the playing behSet prematurely, eg. `collideWithTarget`.
- __*loopFlag__ (_bool_) - Should this loop forever? Default is `false`.
- __*interruptFlag__ (_bool_) - Allow interruptions? Default is `false`.
#### Children:
- None

#### Example:
```xml
 <BFBehPlaySet behSet="Graze"/>
```

---

## BFBehPursuit
Chases the target and stops when the subject has reached it.
#### Attributes:
- __hitRadius__ (_int_) - The maximum distance between subject and target for the pursuit to stop.
- __pursuitRadius__ (_int_) - The maximum distance between subject and target for the pursuit to start.
- __failureRadius__ (_int_) - The minimum start distance between subject and target for the pursuit to fail.
- __locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
- __pollFreq__ (_float_) - How often it is updated? Usually `0.1`.
#### Children:
- None

---

## BFBehRandomSet
Randomly plays behSets given in [randomSets](#randomsets) according to each entries' weight.
#### Attributes:
- __minPlays__ (_int_) - How long many times should this behSet be run at least?
- __maxPlays__ (_int_) - How long many times should this behSet be run at max?
- __*loopFlag__ (_bool_) - Should this loop forever? Default is `false`.
#### Children:
- [randomSets](#randomsets)
- ?[BFBehAnimate](#bfbehanimate)? (probably an error)


#### Example:
```xml
 <BFBehRandomSet minPlays="1" maxPlays="2">
	<randomSets>
	   <SpawnF weight="50"/>
	   <SpawnM weight="50"/>
	</randomSets>
 </BFBehRandomSet>
```

---

## BFBehScript
Executes a function from a BIN or LUA script.
#### Attributes:
- __context__ (_string_) - Always `behavior`.
- __file__ (_string_) - Absolute path to a BIN or LUA script, eg. `scripts/CrateAnimal.lua`, scripts/playparticle.lua, scripts/justgavebirth.lua, scripts/canreproduce.lua, scripts/setmates.lua, ...)
- __function__ (_string_) - Name of a function in the given script, eg. `CrateAnimal`.
- __params__ (_string_) - Additional parameters to be passed to the function, usually for particles (in txtkeys syntax?) eg. `{Floor} runps PlacementCloud`.
#### Children:
- None

#### Example:
```xml
 <BFBehScript context="behavior" file="scripts/playparticle.lua" function="playParticle" params="{Floor} runps PlacementCloud"/>
```

---

## BFBehSendToken
Always contains a [BFAITokenList](#bfaitokenlist).
#### Attributes:
- None
#### Children:
- [BFAITokenList](#bfaitokenlist)

---

## BFBehSetAttribute
Can set attributes on the subject or the target.
#### Attributes:
- None
#### Children:
- [BFAISubjectData](#bfaisubjectdata)
- [BFAITargetData](#bfaitargetdata)
- !BFAISubjecttData! (typo, in the wild, not functional!)

---

## BFBehSpawn
Creates new (child) entities.
#### Attributes:
- __spawnEntity__ (_string_) - Entity type that should be spawned, eg. `Poop_Ungulate`, `AntelopeSableGiant_Young_F`.
- __subjectNode__ (_string_) - Name of the subject's node from which the entities should be spawned.
- __targetAnim__ (_string_) - The name of the anim that should be played during spawning.
- __spawnRelation__ (_string_) - If this parameter is given, it is always `child`.
- __fadeInPeriod__ (_int_) - Default is `0`.
- __randomPosOffset__ (_int_)
- __randomRotOffset__ (_int_)
- __spawnInTA__ (_bool_) - TA = TAP? Default is `false`
#### Children:
- None

#### Example:
```xml
 <BFBehSpawn spawnEntity="Poop_Medium" subjectNode="Poop" targetAnim="Poop_Idle"/>
```

---

## BFBehSyncSet
Simultaneously plays behSets on subject and target.
#### Attributes:
- __subjectBehSet__ (_string_) - The behSet performed by the subject.
- __targetBehSet__ (_string_) - The behSet performed by the target.
- __resetPhase__ (_bool_) - Default is `false`
- __useTargetName__ (_bool_) - Use the name in the info; default is `false`
- __*syncEntity__ (_string_) - If this parameter is given, it is always `object`.
#### Children:
- None

#### Example:
```xml
 <BFBehSyncSet syncEntity="object" subjectBehSet="MommaLetYoungOff" targetBehSet="DebarkMom"/>
```

---

## BFBehWander
Random, undirected locomotion, optionally avoiding third-party entities given in [avoidEntityTypes](#avoidentitytypes).
#### Attributes:
- __*playTime__ (_int_) - How long this behSet should be played.
- __*minPlayTime__ (_int_) - How long this behSet should be played.
- __*maxPlayTime__ (_int_) - How long this behSet should be played.
- __*minDepth__ (_int_) - How shallow can this entity go?
- __*maxDepth__ (_int_) - How deep can this entity go?
- __*locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
- __*avoidObstacleRadius__ (_int_) - Distance from (static?) obstacles.
- __*avoidEntityRadius__ (_int_) - Distance from other entities.
- __*avoidLand__ (_bool_) - Should the entity try to stay in water? Default is `false`.
- __*avoidWater__ (_bool_) - Should the entity try to stay on land? Default is `false`.
- __*ignoreBuoyNodes__ (_bool_) - Should this entity walk on the sea floor?
#### Children:
- [avoidEntityTypes](#avoidentitytypes)

#### Example:
```xml
 <BFBehWander minPlayTime="7" maxPlayTime="15" avoidWater="true" avoidEntityRadius="8">
	<avoidEntityTypes>
	   <b_XLargePredator/>
	   <b_LargePredator/>
	   <b_MediumPredator/>
	   <b_SmallPredator/>
	</avoidEntityTypes>
 </BFBehWander>
```

---

## BFBehWhap
Used for interaction with physics objects, like balls.
#### Attributes:
- __targetAnim__ (_string_) - The name of the anim that should be played.
- __*interruptFlag__ (_bool_) - Allow interruptions? Default is `false`.
- __*groundFit__ (_bool_) - Fit to ground according to leg nodes? Default is `true`.
- __whapAngle__ (_int_) - In degrees, eg. `225`.
- __randomOffset__ (_int_) - Usually `0`,
#### Children:
- None

#### Example:
```xml
 <BFBehWhap targetAnim="Stand_SlamBallRight"/>
```

---

## Objects
#### Attributes:
- None
#### Children:
- None

---

## Options
#### Attributes:
- __Reset__ (_bool_) - (true),
#### Children:
- None

---

## Subjects
#### Attributes:
- None
#### Children:
- None

---

## Subjects_AND
#### Attributes:
- None
#### Children:
- None

---

## Targets
#### Attributes:
- None
#### Children:
- None

---

## Targets_AND
#### Attributes:
- None
#### Children:
- None

---

## TrickLearning
#### Attributes:
- None
#### Children:
- None

---

## ZTAIShowEvent
Can be called from [ZTBehSplashGuest](#ztbehsplashguest) and more.
#### Attributes:
- __Name__ (_string_) - Name of this event.
- __interrupt__ (_bool_) - Either `true` or `false`.
- __ExpireWithTask__ (_bool_) - Either `true` or `false`.
- __Timeout__ (_int_) - When is this event discarded?
#### Children:
- None

#### Example:
```xml
 <ZTBehShowEvent Type="AnimalEvent" Name="TrickFailure" Priority="2" Interrupt="true" ExpireWithTask="true" Timein="1" Timeout="3"/>
 <ZTBehSplashGuest targetAnim="SwimSub_JumpFailure" interruptFlag="true" groundFit="false">
	<ZTAIShowEvent Name="Splashed" Interrupt="true" ExpireWithTask="false" Timeout="1"/>
	<BFAITokenList>
	   <BFAIToken Name="t_Splashed" GiveTo="target" Payload="subject" Timeout="15" Reconsider="true" OnlyOne="true"/>
	</BFAITokenList>
 </ZTBehSplashGuest>
```

---

## ZTActionInfo
This info is shown in the entity's info panel.
#### Attributes:
- __locID__ (_string_) - The info to be raised in the info bar of the entity, may include placeholders.
- __*useTargetName__ (_bool_) - Will appear instead of `%s` or `%1s` in the locID.
- __*useTargetContents__ (_bool_) - Will appear instead of `%2s` in the locID.
- __*useObjectName__ (_bool_) - Will appear instead of `%s` or `%1s` in the locID.
#### Children:
- None

#### Example:
```xml
 <ZTBehFeedback>
	<ZTFeedbackData>
	   <ZTActionInfo locID="animalactions:GoingToLookAt" useTargetName="true"/>
	</ZTFeedbackData>
 </ZTBehFeedback>
```
 
---

## ZTBehAddSubjectAsDiseaseTarget
#### Attributes:
- __attributes__ (_string_) - (b_Carnivore=true),
- __disease__ (_string_) - (Bloodlust, PinkElephantDisease),
- __immediate__ (_bool_) - (false, true),
- __types__ (_string_) - (Elephantidae, animal),
#### Children:
- None

---

## ZTBehChangeWaterDirtiness
#### Attributes:
- __Delta__ (_int_) - (750),
#### Children:
- None

---

## ZTBehDockFence
#### Attributes:
- __locoSpeed__ (_string_) - (charge, evade, fast, medium, slow),
- __subjectNode__ (_string_) - (Floor, Node_Mouth, Poop, p_FightOffset, p_PreyOffset),
- __targetAnim__ (_string_) - (Fly_Ahead, Fly_Call, Stand_Idle, Swim_Ahead, TreadWaterSub_Idle),
#### Children:
- None

---

## ZTBehDockTankWall
Subject interacts with a tank wall. Apparently always called from "inside" [ZTBehTargetFence](#ztbehtargetfence).
#### Attributes:
- __subjectNode__ (_string_) - Name of the subject's dock node, eg. `Node_Mouth`, `Floor`...
- __*locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
- __heightAboveGround__ (_int_) - Measured from the outside ground, not tank floor.
- __*depthBelowWater__ (_int_) - Measured from the water surface.
#### Children:
- None

#### Example:
```xml
 <ZTBehDockTankWall subjectNode="Node_RamWall" locoSpeed="fast" heightAboveGround="1"/>
```

---

## ZTBehDockWater
#### Attributes:
- __drinkDepth__ (_float_) - (.3, .4),
- __interpolationDistance__ (_float_) - (0.15, 0.5, 1, 2, 9.0),
- __subjectNode__ (_string_) - (Floor, Node_Mouth, Poop, p_FightOffset, p_PreyOffset),
- __targetAnim__ (_string_) - (Fly_Ahead, Fly_Call, Stand_Idle, Swim_Ahead, TreadWaterSub_Idle),
#### Children:
- None

---

## ZTBehEconomy
#### Attributes:
- __transactionName__ (_string_) - (destroy, donate),
#### Children:
- None

---

## ZTBehFeedback
Container of [ZTFeedbackData](#ztfeedbackdata).
#### Attributes:
- None
#### Children:
- [ZTFeedbackData](#ztfeedbackdata)

---

## ZTBehKickOffRider
#### Attributes:
- None
#### Children:
- None

---

## ZTBehMorph
Morphs the subject into another entity, either maintaining or discarding its initial identity.
#### Attributes:
- __morphEntity__ (_string_) - Either `subject`, `target` or an entity type, eg. `CamarasaurusNest_Egg`.
- __morphTargetEntityType__ (_string_) - The entity type to morph into, eg. `BearGrizzly_Juvenile_F`.
- __NameIt__ (_bool_) - Names the result? Default is `false`.
- __morphFade__ (_bool_) - Morph by crossfading the alpha values. Default is `false`.
- __morphScale__ (_bool_) - Morph by adjusting the scale. Default is `false`.
- __morphPeriod__ (_int_) - Time to spend morphing.
- __initScale__ (_float_) - Initial scale of the final entity for scale morphing; should match the scale of the subject.
#### Children:
- None

#### Example:
```xml
 <ZTBehMorph morphEntity="AnkylosaurusNest_Egg" morphTargetEntityType="Ankylosaurus_Young_F" morphPeriod="2"/>
```

---

## ZTBehShowEvent
#### Attributes:
- __Type__ (_string_) - Always `AnimalEvent`.
- __Name__ (_string_) - eg. ``...
- __Priority__ (_int_) - (1, 900, 5, 100, 2, ...)
- __interrupt__ (_bool_) - (false, true)
- __ExpireWithTask__ (_bool_) - (true, false)
- __Timein__ (_int_) - (1110, 1008, 1004.21, 416.84, 1, ...)
- __Timeout__ (_int_) - (30, 15, 5, 20, 10, ...),
#### Children:
- None

---

## ZTBehSplashGuest
Subject splashes guests, plays a particle system and triggers a reaction in guests.
#### Attributes:
- __targetAnim__ (_string_) - The name of the anim that should be played.
- __*interruptFlag__ (_bool_) - Allow interruptions? Default is `false`.
- __splashVector__ (_matrix3x3_) - Always `1 0 0, -1 0 0, 0 1 0`.
- __*groundFit__ (_bool_) - Fit to ground according to leg nodes? Default is `true`.
- __splashFromWaterSurface__ (_bool_) - Default is `true`.
- __splashName__ (_string_) - The name of the particle effect that should be played, eg. `directed_large`, `directed_medium`, `directed_small`.
#### Children:
- [BFAITokenList](#bfaitokenlist)
- [ZTAIShowEvent](#ztaishowevent)

---

## ZTBehStaffTrainAnimal
#### Attributes:
- __AnimalDoesTrickLoopingBeh__ (_string_) - (Idle_Bored),
- __AnimalDoesTrickPrimaryBeh__ (_string_) - (Point),
- __AnimalDoesTrickTimeout__ (_int_) - (60),
- __CleanupPrimaryBeh__ (_string_) - (Cleanup),
- __GoToPlatformPrimaryBeh__ (_string_) - (DockPlatform),
- __IncrementAmt__ (_float_) - (11.0),
- __PreTrainingPrimaryBeh__ (_string_) - (),
- __RewardAnimalPrimaryBeh__ (_string_) - (GiveTreat),
- __SummonAnimalLoopingBeh__ (_string_) - (Idle_Bored),
- __SummonAnimalPrimaryBeh__ (_string_) - (),
- __SummonAnimalTimeout__ (_int_) - (60),
- __TrainAnimalPrimaryBeh__ (_string_) - (TrainAnimal),
#### Children:
- None

---

## ZTBehTargetFence
Makes the subject find a fence.
#### Attributes:
- __behSet__ (_string_) - This behSet is used to dock to the tank wall, and will usually contain [ZTBehDockTankWall](#ztbehdocktankwall).
- __fenceType__ (_string_) - Entity subclass of fences, eg. `tankwallsegment`.
- __searchDistance__ (_int_) - How far the subject may travel to find a fence.
#### Children:
- None

---

## ZTBehTeleportToLoc
#### Attributes:
- __resetProp__ (_bool_) - (true),
#### Children:
- None

---

## ZTBehUsePortal
#### Attributes:
- __locoSpeed__ (_string_) - (charge, evade, fast, medium, slow),
- __targetAnim__ (_string_) - (Fly_Ahead, Fly_Call, Stand_Idle, Swim_Ahead, TreadWaterSub_Idle),
#### Children:
- None

---

## ZTBehViewEvent
Container of [ZTFeedbackData](#ztfeedbackdata).
#### Attributes:
- __viewKey__ (_string_) - Apparently a grading scale for the quality of the event, eg. `Pos_2`, `Pos_3`, `Neg_5`...
#### Children:
- [ZTFeedbackData](#ztfeedbackdata)

---

## ZTEmoticonInfo
This raises an emoticon over the subject entity.
#### Attributes:
- __emoticonName__ (_string_) - Name of the emoticon to be raised, eg. `EmoteAnimalHungerBad`.
- __emoticonScale__ (_float_) - Scale of the emoticon.
- __emoticonEntityNode__ (_string_) - Name of the emoticon's parent node, eg. `Bip01 Head`.
#### Children:
- None

---

## ZTFeedbackData
May be used from inside a [ZTBehFeedback](#ztbehfeedback) or a [ZTBehViewEvent](#ztbehviewevent).
#### Attributes:
- None
#### Children:
- [ZTActionInfo](#ztactioninfo)
- [ZTThoughtInfo](#ztthoughtinfo)
- [ZTEmoticonInfo](#ztemoticoninfo)
- [ZTMessageInfo](#ztmessageinfo)

---

## ZTMessageInfo
#### Attributes:
- __locID__ (_string_) - The info to be raised in the info bar of the entity.
- __*priority__ (_int_) - This message's relative priority.
- __*timeout__ (_int_) - How soon should this message disappear?
- __*interval__ (_int_) - how much time must pass until the message is raised again?
- __*tolerance__ (_int_) - Unknown.
- __*global__ (_bool_) - Not sure. Either (false, true)
- __*useEntityName__ (_bool_) - Default is `false`.
- __*useTargetName__ (_bool_) - Default is `false`
- __*filterAttribute__ (_string_) - Rare, eg. `b_Rampage EQ true`
#### Children:
- None

---

## ZTThoughtInfo
#### Attributes:
- __locID__ (_string_) - The info to be raised in the info bar of the entity.
- __*priority__ (_int_) - This message's relative priority.
- __*timeout__ (_int_) - How soon should this message disappear?
- __*global__ (_bool_) - Not sure. Either (false, true)
- __*useTargetName__ (_bool_) - Will appear instead of `%s` in the locID.
- __*useTargetTarget__ (_bool_) - Will appear instead of `%s` in the locID.
- __*useTargetSpecies__ (_bool_) - Will appear instead of `%s` in the locID.
- __*useTargetObject__ (_bool_) - Will appear instead of `%s` in the locID.
#### Children:
- None

---

## animTable
Switches between different animations in a [BFBehAnimateSwitch](#bfbehanimateswitch)
#### Attributes:
- None
#### Children:
- ["animTableEntry"](#animtableentry)

---

## avoidEntityTypes
Holds a list of entities that should be avoided in [BFBehWander](#bfbehwander) and [BFBehEvasion](#bfbehevasion) sets.
#### Attributes:
- None
#### Children:
- ["avoidEntityTypesEntry"](#avoidentitytypesentry) (not documented)

---

## behaviorTable
May be used from inside a [BFBehLocoSwitchSet](#bfbehlocoswitchset) or a [BFBehAnimSwitchSet](#bfbehanimswitchset).
#### Attributes:
- None
#### Children:
- ["behaviorTableEntry"](#behaviortableentry)

---

## behaviors
This is the top-level container for BEH behavior. Note that not all structures can be called directly from top level. Some may be encapsulated in other components.
#### Attributes:
- None
#### Children:
- [BFBehAnimSwitchSet](#bfbehanimswitchset)
- [BFBehAnimate](#bfbehanimate)
- [BFBehAnimateRandom](#bfbehanimaterandom)
- [BFBehAnimateSwitch](#bfbehanimateswitch)
- [BFBehAnimateTAP](#bfbehanimatetap)
- [BFBehAttachObject](#bfbehattachobject)
- [BFBehDetachObject](#bfbehdetachobject)
- [BFBehDock](#bfbehdock)
- [BFBehDockNow](#bfbehdocknow)
- [BFBehDockRadial](#bfbehdockradial)
- [BFBehDockSpline](#bfbehdockspline)
- [BFBehDockTAP](#bfbehdocktap)
- [BFBehEscapeObstacle](#bfbehescapeobstacle)
- [BFBehEvasion](#bfbehevasion)
- [BFBehFaceTarget](#bfbehfacetarget)
- [BFBehFollowEntity](#bfbehfollowentity)
- [BFBehHeadLook](#bfbehheadlook)
- [BFBehKill](#bfbehkill)
- [BFBehLocoSwitchSet](#bfbehlocoswitchset)
- [BFBehMove](#bfbehmove)
- [BFBehPlaySet](#bfbehplayset)
- [BFBehPursuit](#bfbehpursuit)
- [BFBehRandomSet](#bfbehrandomset)
- [BFBehScript](#bfbehscript)
- [BFBehSendToken](#bfbehsendtoken)
- [BFBehSetAttribute](#bfbehsetattribute)
- [BFBehSpawn](#bfbehspawn)
- [BFBehSyncSet](#bfbehsyncset)
- [BFBehWander](#bfbehwander)
- [BFBehWhap](#bfbehwhap)
- [ZTBehDockTankWall](#ztbehdocktankwall)
- [ZTBehFeedback](#ztbehfeedback)
- [ZTBehMorph](#ztbehmorph)
- [ZTBehShowEvent](#ztbehshowevent)
- [ZTBehSplashGuest](#ztbehsplashguest)
- [ZTBehTargetFence](#ztbehtargetfence)
- [ZTBehViewEvent](#ztbehviewevent)
- [ZTBehViewEvent](#ztbehviewevent)

---

## randomAnims
#### Attributes:
- None
#### Children:
- ["randomAnimsEntry"](#randomanimsentry)

---

## randomSets
#### Attributes:
- None
#### Children:
- ["randomSetsEntry"](#randomsetsentry)

---

## textkeys
#### Attributes:
- None
#### Children:
- ["textkeysEntry"](#textkeysentry)

