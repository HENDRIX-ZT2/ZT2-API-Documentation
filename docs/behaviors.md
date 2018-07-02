# Overview
This page lists all known modules and functions that can be used to create ZT2 AI.

---

## "animTableEntry"
(actually, the tag is always the name of the anim set, eg. `Stand`)
#### Attributes: 
- __anim__ (_string_) - The exact animation that should be played in this set, eg. `Stand_Idle`.
* __behSet__ (_string_) - May apparently be used instead of an anim.
* __weight__ (_int_) - The probability of using this subset; should add up to 100.
* __minAnimSpeed__ (_float_) - Minimum anim speed to use in playback.
* __maxAnimSpeed__ (_float_) - Maximum anim speed to use in playback.
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
* __weight__ (_int_) - The probability of using this anim; should add up to 100.
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

## AnimalEnters
#### Attributes:
- __BaseScore__ (_int_) - (0, 10, 20),
- __FavoriteAnimalBonus__ (_int_) - (-20, 20, 70),
- __FuzzyFactor__ (_int_) - (20, 50),
- __ShowQualityMult__ (_int_) - (-2, 1, 20, 4, 6),
#### Children:
- [Reaction](#reaction)

---

## AnimalLeaves
#### Attributes:
- __BaseScore__ (_int_) - (0, 10, 20),
- __FavoriteAnimalBonus__ (_int_) - (-20, 20, 70),
- __FuzzyFactor__ (_int_) - (20, 50),
- __ShowQualityMult__ (_int_) - (-2, 1, 20, 4, 6),
#### Children:
- [Reaction](#reaction)

---

## BFAIAttributeFloatMap
#### Attributes:
- __"attribute"__ (_float_ or _bool_) - Assigns the given value to the named attribute.
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
- __invalidateTarget__ (_bool_) - Default is `false`.
- __needPointsBad__ (_float_) - (.1, 1, 30, 5, 50),
#### Children:
- [BFAIAttributeFloatMap](#bfaiattributefloatmap)
- [BFAISubjectData](#bfaisubjectdata)
- [BFAITargetData](#bfaitargetdata)
- [BFAITokenList](#bfaitokenlist)
- [BFBehExecTask](#bfbehexectask)
- [BFBehSendToken](#bfbehsendtoken)
- [userData](#userdata)

---

## BFAICreateData
#### Attributes:
- None
#### Children:
- [Objects](#objects)
- [Objects_AND](#objects_and)
- [Subjects](#subjects)
- [Subjects_AND](#subjects_and)
- [Targets](#targets)
- [Targets_AND](#targets_and)

---

## BFAIEvalData
#### Attributes:
- __fixedScore__ (_int_) - (.00005, 10000, 12000, 12003, 12005),
- __distanceInfluenced__ (_bool_) - (false, true),
- __leaveZoo__ (_bool_) - (true),
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
- __"attribute"__ (_int_ or _bool_) - Assigns the given integer to the named attribute.
#### Children:
- [TrickLearning](#tricklearning)

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
- __"attribute"__ (_int_ or _bool_) - Assigns the given integer to the named attribute.
#### Children:
- [Options](#options)

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
- __Name__ (_string_) - (DefaultTask_Aardvark, DefaultTask_Actor, FastWander, Interact_Player, WanderWater),
- __Priority__ (_int_) - (1, 10, 100, 5, 900),
- __TaskDelayMax__ (_int_) - (100000, 180, 300, 420, 60),
- __TaskDelayMin__ (_int_) - (10000, 180, 30, 300, 60),
- __UniqueID__ (_string_) - (Aardvark:DefaultTask_Aardvark, Aardvark:FastWander, Aardvark:WanderWater, actor:DefaultTask_Actor, playerinteractions:Interact_Player),
- __UseForKeeperPanel__ (_bool_) - (false),
- __UseFromTokenQualifiers__ (_bool_) - (true),
- __attachTag__ (_string_) - (back, cleanerfish, hand, lefthandyoung, mouth),
- __distanceInfluenced__ (_bool_) - (false, true),
- __objectContainer__ (_string_) - (back, hand, lefthandyoung, mouth, righthand),
- __objectName__ (_string_) - (entityname:CheeseCake_lower, entityname:CottonCandy_lower, entityname:FruitCup_lower, entityname:IceCream_lower, entityname:Popcorn_lower),
- __priority__ (_int_) - (-1, 0, 1, 10, 2),
- __reserveTag__ (_string_) - (Browse, General, Graze, Rest, TAP),
- __sensorTag__ (_string_) - (explore, habitat, path, tour, viewanimals),
- __useFromTokenQualifiers__ (_bool_) - (true),
#### Children:
- [BFAIAttributeFloatMap](#bfaiattributefloatmap)
- [BFAIBiomeMap](#bfaibiomemap)
- [BFAICompletionData](#bfaicompletiondata)
- [BFAICreateData](#bfaicreatedata)
- [BFAIEvalData](#bfaievaldata)
- [BFAIFailureData](#bfaifailuredata)
- [BFAIValidationData](#bfaivalidationdata)
- [BFBehExecTask](#bfbehexectask)

---

## BFAITaskTemplateList
The top-level container for all [BFAITaskTemplates](#bfaitasktemplate).
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
* __loopFlag__ (_bool_) - Default is `false`.
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
* __playTime__ (_int_) - How long this behSet should be played.
* __animSpeed__ (_float_) - Exact anim speed to use in playback.
* __minAnimSpeed__ (_float_) - Minimum anim speed to use in playback.
* __maxAnimSpeed__ (_float_) - Maximum anim speed to use in playback.
* __loopFlag__ (_bool_) - Should this loop forever? Default is `false`.
* __interruptFlag__ (_bool_) - Allow interruptions? Default is `false`.
* __interruptible__ (_bool_) - Can this anim be stopped during playback? Default is `false`.
* __blendDuration__ (_int_) - Probably orphaned and not used.
* __groundFit__ (_bool_) - Fit to ground according to leg nodes? Default is `true`.
* __physObj__ (_string_) - For multi-piece objects, which physObj should be animated (eg. `Vendor` for shops)
#### Children:
- ["textkeys"](#textkeys)

---

## BFBehAnimateRandom
Randomly plays an anim from the [randomAnims](#randomanims) table.
#### Attributes:
- __minPlays__ (_int_) - How long many times should this behSet be run?
- __maxPlays__ (_int_) - How long many times should this behSet be run?
* __playTime__ (_int_) - How long this behSet should be played.
* __loopFlag__ (_bool_) - Should this loop forever? Default is `false`.
* __interruptFlag__ (_bool_) - Allow interruptions? Default is `false`.
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
- __exitTAP__ (_bool_) - Either `true` or `false`.
- __!exitTap!__ (_bool_) - Typo for __exitTAP__.
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
- __targetBehSet__ (_string_) - (DockFight, HitMediumEqual, BiteMed, Rendezvous, DefendEqual, ...)
- __detachAction__ (_string_) - (killitem, dropitem, inventory)
- __detachBehSet__ (_string_) - (Chew, DropYoung, DetachBaby, LetBabyOff, DetachRat)
- __!detachBeh!__ (_string_) - Typo for __detachBehSet__.
- __container__ (_string_) - (foodprop, righthand, lefthandobject, mouth, head_inventory, ...)
- __locoMod__ (_string_) - (carry, carryback, drag, carryyoung, carrybaby)
- __physObjToHide__ (_string_) - (mainObj, prop, ballprop)
- __interruptFlag__ (_bool_) - (true)
- __groundFit__ (_bool_) - (false),
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
- __container__ (_string_) - (foodprop, head_inventory, lefthandobject, mouth, righthand),
- __detachAction__ (_string_) - (dropitem, inventory, killitem, maketrash),
- __detachEntity__ (_string_) - (BrownFish_Prop, ElephantAfrican_Gift, ShakerToy, ShakerToy_Open, object),
- __subjectNode__ (_string_) - (Floor, Node_Mouth, Poop, p_GroomNode, p_PreyOffset),
- __targetAnim__ (_string_) - The name of the anim that should be played.
#### Children:
- [textkeys](#textkeys)

---

## BFBehDock
Docks an entity exactly according to subject's and target's dock nodes.
#### Attributes:
- __subjectNode__ (_string_) - Name of the subject's dock node, eg. `Node_Mouth`, `Floor`...
- __targetNode__ (_string_) - Name of the target's dock node, eg. `p_InvestigateNode`, `Dock_Attach`...
- __targetAnim__ (_string_) - The name of the anim that should be played during docking.
* __locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
* __avoidWater__ (_bool_) - Should the entity try to stay on land? Default is `false`.
- __redock__ (_bool_) - Default is `false`.
- __reserveSlotName__ (_string_) - Either `general` or `Trainer`.
* __interpolationDistance__ (_float_) - ?
#### Children:
- None

---

## BFBehDockNow
This (probably) is the docking operation that greatly speeds up an entity's movement to reach the dock almost instantly.
#### Attributes:
- __subjectNode__ (_string_) - Name of the subject's dock node, eg. `Node_Mouth`, `Floor`...
- __targetNode__ (_string_) - Name of the target's dock node, eg. `p_InvestigateNode`, `Dock_Attach`...
- __targetAnim__ (_string_) - The name of the anim that should be played during docking.
- __reserveSlotName__ (_string_) - Either `general` or `Trainer`.
- __redock__ (_bool_) - Default is `false`.
* __unparent__ (_bool_) - Default is `false`.
* __parentToTarget__ (_bool_) - Default is `false`.
#### Children:
- None

---

## BFBehDockQueue
This docks guests to a queue in front of a building.
#### Attributes:
* __container__ (_string_) - Name of the queue container.
- __hitRadius__ (_int_) - Distance to enter the queue.
- __locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
- __queueRadius__ (_int_) - Size of the queue.
#### Children:
- None


#### Example:
```xml
 <BFBehDockQueue hitRadius="2.5" queueRadius="12" locoSpeed="slow"/>
```

---

## BFBehDockRadial
Docks an entity exactly according to subject's dock nodes, ignoring the rotation specified by the target's dock node.
#### Attributes:
- __subjectNode__ (_string_) - Name of the subject's dock node, eg. `Node_Mouth`, `Floor`...
* __targetNode__ (_string_) - Name of the target's dock node, eg. `p_InvestigateNode`, `Dock_Attach`...
- __targetAnim__ (_string_) - Anim the subject should play when docking with the target, eg. `Fly_Ahead`.
- __targetRadius__ (_int_) - Radius around the target.
* __rotError__ (_int_) - Always 180.
* __locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
* __dockRadius__ (_float_) - 
* __interpolationDistance__ (_float_) - ?
#### Children:
- None

---

## BFBehDockSpline
Docks usin spline interpolation, in 3D?
#### Attributes:
- __subjectNode__ (_string_) - Name of the subject's dock node, eg. `Node_Mouth`, `Floor`...
- __targetNode__ (_string_) - Name of the target's dock node, eg. `p_InvestigateNode`, `Dock_Attach`...
- __targetAnim__ (_string_) - The name of the anim that should be played.
* __locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
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
Used to initiate interaction with a building; generally followed by a `useContainer` behSet.
#### Attributes:
- None
#### Children:
- None

#### Example:
```xml
 <BFBehEnter/>
 <BFBehPlaySet behSet="useContainer"/>
```xml
---

## BFBehEscapeObstacle
#### Attributes:
* __locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
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
* __avoidObstacleRadius__ (_int_) - How much distance should be kept between the subject and obstacles?
* __avoidWater__ (_bool_) - Should the entity try to stay on land? Default is `false`.
* __avoidLand__ (_bool_) - Should the entity try to stay in water? Default is `false`.
#### Children:
*[avoidEntityTypes](#avoidentitytypes)

---

## BFBehExecTask
The TSK equivalent to the BEH's [behaviors](#behaviors) container. Can use more or less the same functions.
#### Attributes:
- None
#### Children:
- [BFAISubjectData](#bfaisubjectdata)
- [BFBehAnimSwitchSet](#bfbehanimswitchset)
- [BFBehAnimate](#bfbehanimate)
- [BFBehAnimateRandom](#bfbehanimaterandom)
- [BFBehAttachObject](#bfbehattachobject)
- [BFBehDetachObject](#bfbehdetachobject)
- [BFBehDock](#bfbehdock)
- [BFBehDockQueue](#bfbehdockqueue)
- [BFBehDockRadial](#bfbehdockradial)
- [BFBehDockSpline](#bfbehdockspline)
- [BFBehEnter](#bfbehenter)
- [BFBehEscapeObstacle](#bfbehescapeobstacle)
- [BFBehEvasion](#bfbehevasion)
- [BFBehExit](#bfbehexit)
- [BFBehFaceTarget](#bfbehfacetarget)
- [BFBehFall](#bfbehfall)
- [BFBehHeadLook](#bfbehheadlook)
- [BFBehHide](#bfbehhide)
- [BFBehKill](#bfbehkill)
- [BFBehLocoSwitchSet](#bfbehlocoswitchset)
- [BFBehMove](#bfbehmove)
- [BFBehPlaySet](#bfbehplayset)
- [BFBehPursuit](#bfbehpursuit)
- [BFBehRandomSet](#bfbehrandomset)
- [BFBehScript](#bfbehscript)
- [BFBehSendToken](#bfbehsendtoken)
- [BFBehSendTrigger](#bfbehsendtrigger)
- [BFBehSetAttribute](#bfbehsetattribute)
- [BFBehSpawn](#bfbehspawn)
- [BFBehSyncSet](#bfbehsyncset)
- [BFBehWaitQueue](#bfbehwaitqueue)
- [BFBehWander](#bfbehwander)
- [ZTBehAddSubjectAsDiseaseTarget](#ztbehaddsubjectasdiseasetarget)
- [ZTBehChangeWaterDirtiness](#ztbehchangewaterdirtiness)
- [ZTBehDockFence](#ztbehdockfence)
- [ZTBehDockTankWall](#ztbehdocktankwall)
- [ZTBehDockWater](#ztbehdockwater)
- [ZTBehEconomy](#ztbeheconomy)
- [ZTBehExitTankGate](#ztbehexittankgate)
- [ZTBehFeedback](#ztbehfeedback)
- [ZTBehFindArtifact](#ztbehfindartifact)
- [ZTBehKickOffRider](#ztbehkickoffrider)
- [ZTBehMorph](#ztbehmorph)
- [ZTBehPlaceTarget](#ztbehplacetarget)
- [ZTBehStaffTrainAnimal](#ztbehstafftrainanimal)
- [ZTBehTargetFence](#ztbehtargetfence)
- [ZTBehTeleportToLoc](#ztbehteleporttoloc)
- [ZTBehTestTargetPos](#ztbehtesttargetpos)
- [ZTBehTour](#ztbehtour)
- [ZTBehUsePortal](#ztbehuseportal)
- [ZTBehViewAnimals](#ztbehviewanimals)
- [ZTBehViewEvent](#ztbehviewevent)

---

## BFBehExit
Used to terminate interaction with a building; apparently not necessarily used after [BFBehEnter](#bfbehenter).
#### Attributes:
- __exitBehSet__ (_string_) - (ExitBench, ExitGrandstand, ExitTrashContainer),
#### Children:
- None

---

## BFBehFaceTarget
Makes the subject face its target, preferably by playing the appropriate turning animations.
#### Attributes:
* __rotError__ (_int_) - (180, 22.5),
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
* __locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
* __minPlayTime__ (_int_) - How long this behSet should be played.
* __maxPlayTime__ (_int_) - How long this behSet should be played.
#### Children:
- None

---

## BFBehHeadLook
Toggles the secondary headlook component in the XML.
#### Attributes:
- __disengage__ (_bool_) Turns it off again. Default is `false`.
- __targetNode__ (_string_) - Apparently which node in the target to look at.
#### Children:
- None

---

## BFBehHide
#### Attributes:
- __maxTime__ (_int_) - (1, 20, 8),
- __minTime__ (_int_) - (1, 15, 4),
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
* __fadeOutPeriod__ (_int_) - Duration of the fadeout in seconds, default is probably `0`.
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
* __switch__ (_bool_) - Default is `true`.
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
* __depthBelowSurface__ (_int_ or comparison) - eg. (4, 0, 12, G 1, LE 1, ...)
* __pathRadius__ (_int_) - (0, 3, 10, 7, 20, ...)
* __moveRadius__ (_int_) - (1000, 5, 1, 3, 4, ...)
* __closestApproach__ (_bool_) - Default is `false`.
* __targetNode__ (_string_) - name of the dock node, eg. `p_InvestigateNode`, `Dock_Attach`...
* __locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
* __heightAboveFloor__ (_float_) - Seafloor offset?
* __hitRadius__ (_int_) - (5, 3, 10, 8, 6, ...)
* __depthAboveBottom__ (_int_ or comparison) - (LE 1, LE 3, 1)
#### Children:
- None

---

## BFBehPlaySet
Very generic function that simply plays back another behSet.
#### Attributes:
- __behSet__ (_string_) - The name of the behSet to be played.
* __playTime__ (_int_) - How long this behSet should be played.
* __interruptEvent__ (_string_) - Apparently, this event stops the playing behSet prematurely, eg. `collideWithTarget`.
* __loopFlag__ (_bool_) - Should this loop forever? Default is `false`.
* __interruptFlag__ (_bool_) - Allow interruptions? Default is `false`.
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
* __loopFlag__ (_bool_) - Should this loop forever? Default is `false`.
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

## BFBehSendTrigger
#### Attributes:
- __subjectTrigger__ (_string_) - (Adjust_SurveyData, Adjust_ZooFame, Use_Bathroom, Use_Skytower_Down, Use_Skytower_Up),
#### Children:
- None

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
* __syncEntity__ (_string_) - If this parameter is given, it is always `object`.
#### Children:
- None

#### Example:
```xml
 <BFBehSyncSet syncEntity="object" subjectBehSet="MommaLetYoungOff" targetBehSet="DebarkMom"/>
```

---

## BFBehWaitQueue
Controls guests as they wait in a queue.
#### Attributes:
* __container__ (_string_) - Name of the queue container.
- __maxWaitTime__ (_int_) - (360, 60, 90),
- __minWaitTime__ (_int_) - (30, 60),
- __waitBehSet__ (_string_) - (WaitInLine, WaitInLineStation),
#### Children:
- None

#### Example:
```xml
 <BFBehWaitQueue minWaitTime="30" maxWaitTime="60" waitBehSet="WaitInLine"/>
```

---

## BFBehWander
Random, undirected locomotion, optionally avoiding third-party entities given in [avoidEntityTypes](#avoidentitytypes).
#### Attributes:
* __playTime__ (_int_) - How long this behSet should be played.
* __minPlayTime__ (_int_) - How long this behSet should be played.
* __maxPlayTime__ (_int_) - How long this behSet should be played.
* __minDepth__ (_int_) - How shallow can this entity go?
* __maxDepth__ (_int_) - How deep can this entity go?
* __locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
* __avoidObstacleRadius__ (_int_) - Distance from (static?) obstacles.
* __avoidEntityRadius__ (_int_) - Distance from other entities.
* __avoidLand__ (_bool_) - Should the entity try to stay in water? Default is `false`.
* __avoidWater__ (_bool_) - Should the entity try to stay on land? Default is `false`.
* __ignoreBuoyNodes__ (_bool_) - Should this entity walk on the sea floor?
* __heightAboveFloor__ (_float_) - Seafloor offset?
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
* __interruptFlag__ (_bool_) - Allow interruptions? Default is `false`.
* __groundFit__ (_bool_) - Fit to ground according to leg nodes? Default is `true`.
- __whapAngle__ (_int_) - In degrees, eg. `225`.
- __randomOffset__ (_int_) - Usually `0`,
#### Children:
- None

#### Example:
```xml
 <BFBehWhap targetAnim="Stand_SlamBallRight"/>
```

---

## BeforeShow
#### Attributes:
- __BaseScore__ (_int_) - (0, 10, 20),
- __FavoriteAnimalBonus__ (_int_) - (-20, 20, 70),
- __FuzzyFactor__ (_int_) - (20, 50),
- __ShowQualityMult__ (_int_) - (-2, 1, 20, 4, 6),
#### Children:
- [Reaction](#reaction)

---

## DefaultEvent
#### Attributes:
- __BaseScore__ (_int_) - (0, 10, 20),
- __FavoriteAnimalBonus__ (_int_) - (-20, 20, 70),
- __FuzzyFactor__ (_int_) - (20, 50),
- __ShowQualityMult__ (_int_) - (-2, 1, 20, 4, 6),
#### Children:
- [Reaction](#reaction)

---

## EventScoring
#### Attributes:
- None
#### Children:
- [AnimalEnters](#animalenters)
- [AnimalLeaves](#animalleaves)
- [BeforeShow](#beforeshow)
- [DefaultEvent](#defaultevent)
- [MCEvent](#mcevent)
- [ShowCancelled](#showcancelled)
- [ShowEnds](#showends)
- [Splashed](#splashed)
- [TrickCritical](#trickcritical)
- [TrickFailure](#trickfailure)
- [TrickSuccess](#tricksuccess)
- [WatchingAnimal](#watchinganimal)

---

## MCEvent
#### Attributes:
- __BaseScore__ (_int_) - (0, 10, 20),
- __FuzzyFactor__ (_int_) - (20, 50),
- __ShowQualityMult__ (_int_) - (-2, 1, 20, 4, 6),
#### Children:
- [Reaction](#reaction)

---

## Objects
Objects required for this [BFAITaskTemplate](#bfaitasktemplate).
#### Attributes:
- None
#### Children:
- None

---

## Objects_AND
Objects required for this [BFAITaskTemplate](#bfaitasktemplate).
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

## Reaction
#### Attributes:
- __BehSet__ (_string_) - (TrickSuccess_Path_Pos_1, TrickSuccess_Path_Pos_2, WatchShow_Path_Midpoint, WatchShow_Path_Neg_1, WatchShow_Path_Pos_1),
- __MinScore__ (_int_) - (0, 10, 20, 30, 40),
#### Children:
- None---

---

## ShowCancelled
#### Attributes:
- __Priority__ (_int_) - (1, 10, 100, 5, 900),
- __ShowQualityMult__ (_int_) - (-2, 1, 20, 4, 6),
#### Children:
- [Reaction](#reaction)

---

## ShowEnds
#### Attributes:
- __Priority__ (_int_) - (1, 10, 100, 5, 900),
- __ShowQualityMult__ (_int_) - (-2, 1, 20, 4, 6),
#### Children:
- [Reaction](#reaction)

---

## Splashed
#### Attributes:
- __BaseScore__ (_int_) - (0, 10, 20),
- __FavoriteAnimalBonus__ (_int_) - (-20, 20, 70),
- __FuzzyFactor__ (_int_) - (20, 50),
- __Priority__ (_int_) - (1, 10, 100, 5, 900),
- __ShowQualityMult__ (_int_) - (-2, 1, 20, 4, 6),
#### Children:
- [Reaction](#reaction)

---

## Subjects
Subjects required for this [BFAITaskTemplate](#bfaitasktemplate).
#### Attributes:
- None
#### Children:
- None

---

## Subjects_AND
Subjects required for this [BFAITaskTemplate](#bfaitasktemplate).
#### Attributes:
- None
#### Children:
- None

---

## Targets
Targets required for this [BFAITaskTemplate](#bfaitasktemplate).
#### Attributes:
- None
#### Children:
- None

---

## Targets_AND
Targets required for this [BFAITaskTemplate](#bfaitasktemplate).
#### Attributes:
- None
#### Children:
- None

---

## TrickCritical
#### Attributes:
- __BaseScore__ (_int_) - (0, 10, 20),
- __FavoriteAnimalBonus__ (_int_) - (-20, 20, 70),
- __FuzzyFactor__ (_int_) - (20, 50),
- __PerPrevious__ (_int_) - (40),
- __ShowQualityMult__ (_int_) - (-2, 1, 20, 4, 6),
- __TrickPopularityMult__ (_float_) - (-0.1, 0.3),
#### Children:
- [Reaction](#reaction)

---

## TrickFailure
#### Attributes:
- __BaseScore__ (_int_) - (0, 10, 20),
- __FavoriteAnimalBonus__ (_int_) - (-20, 20, 70),
- __FuzzyFactor__ (_int_) - (20, 50),
- __IgnorePrevious__ (_int_) - (2),
- __PerPrevious__ (_int_) - (40),
- __ShowQualityMult__ (_int_) - (-2, 1, 20, 4, 6),
- __TrickPopularityMult__ (_float_) - (-0.1, 0.3),
#### Children:
- [Reaction](#reaction)

---

## TrickLearning
#### Attributes:
- None
#### Children:
- None

---

## TrickSuccess
#### Attributes:
- __BaseScore__ (_int_) - (0, 10, 20),
- __FavoriteAnimalBonus__ (_int_) - (-20, 20, 70),
- __FuzzyFactor__ (_int_) - (20, 50),
- __ShowQualityMult__ (_int_) - (-2, 1, 20, 4, 6),
- __TrickPopularityMult__ (_float_) - (-0.1, 0.3),
#### Children:
- [Reaction](#reaction)

---

## WatchingAnimal
#### Attributes:
- __BaseScore__ (_int_) - (0, 10, 20),
- __FavoriteAnimalBonus__ (_int_) - (-20, 20, 70),
- __FuzzyFactor__ (_int_) - (20, 50),
- __ShowQualityMult__ (_int_) - (-2, 1, 20, 4, 6),
- __TrickPopularityMult__ (_float_) - (-0.1, 0.3),
#### Children:
- [Reaction](#reaction)

---

## ZTAIShowEvent
Can be called from [ZTBehSplashGuest](#ztbehsplashguest).
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
* __useTargetName__ (_bool_) - Will appear instead of `%s` or `%1s` in the locID.
* __useTargetContents__ (_bool_) - Will appear instead of `%2s` in the locID.
* __useObjectName__ (_bool_) - Will appear instead of `%s` or `%1s` in the locID.
* __timeout__ (_float_) - (0.0f, 15, 30, 60),
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
- __disease__ (_string_) - (Bloodlust, CatScratchFever, PinkElephantDisease),
- __immediate__ (_bool_) - (false, true),
- __types__ (_string_) - (Elephantidae, Elephantidae Mammutidae, Felidae, animal),
#### Children:
- None

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
- __Clean__ (_bool_) - (true),
- __Delta__ (_int_) - (750),
#### Children:
- None

---

## ZTBehChangeWaterDirtiness
#### Attributes:
- __Delta__ (_int_) - (750),
#### Children:
- None

---

## ZTBehCureDisease
#### Attributes:
- None
#### Children:
- None

---

## ZTBehDigArtifact
#### Attributes:
- None
#### Children:
- None

---

## ZTBehDockFence
#### Attributes:
- __locoSpeed__ (_string_) - (burrow, evade, fast, medium, slow),
- __subjectNode__ (_string_) - (Floor, Node_Mouth, Poop, p_GroomNode, p_PreyOffset),
- __targetAnim__ (_string_) - (LieSide_Idle, Lie_Idle, SleepCurl_Idle, Stand_Idle, TreadWater_Idle),
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
#### Attributes:
- __depthBelowWater__ (_int_) - (1, 2),
- __heightAboveGround__ (_int_) - (1),
- __locoSpeed__ (_string_) - (burrow, evade, fast, medium, slow),
- __subjectNode__ (_string_) - (Floor, Node_Mouth, Poop, p_GroomNode, p_PreyOffset),
#### Children:
- None

---

## ZTBehDockTankWall
Subject interacts with a tank wall. Apparently always called from "inside" [ZTBehTargetFence](#ztbehtargetfence).
#### Attributes:
- __subjectNode__ (_string_) - Name of the subject's dock node, eg. `Node_Mouth`, `Floor`...
* __locoSpeed__ (_string_) - Which locoSpeed to use (referred in main XML). Default is `slow`.
- __heightAboveGround__ (_int_) - Measured from the outside ground, not tank floor.
* __depthBelowWater__ (_int_) - Measured from the water surface.
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

## ZTBehDockWater
#### Attributes:
- __drinkDepth__ (_float_) - (.3, .4),
- __interpolationDistance__ (_float_) - (0.15, 0.5, 1, 2, 9.0),
- __subjectNode__ (_string_) - (Floor, Node_Mouth, Poop, p_GroomNode, p_PreyOffset),
- __targetAnim__ (_string_) - (LieSide_Idle, Lie_Idle, SleepCurl_Idle, Stand_Idle, TreadWater_Idle),
#### Children:
- None

---

## ZTBehEconomy
#### Attributes:
- __general__ (_bool_) - (true),
- __transactionName__ (_string_) - (add_user, destroy, donate, getCash, remove_user),
#### Children:
- None

---

## ZTBehEconomy
#### Attributes:
- __transactionName__ (_string_) - (destroy, donate),
#### Children:
- None

---

## ZTBehExitTankGate
#### Attributes:
- None
#### Children:
- None

---

## ZTBehFeedback
#### Attributes:
- None
#### Children:
- [ZTFeedbackData](#ztfeedbackdata)

---

## ZTBehFeedback
Container of [ZTFeedbackData](#ztfeedbackdata).
#### Attributes:
- None
#### Children:
- [ZTFeedbackData](#ztfeedbackdata)

---

## ZTBehFindArtifact
#### Attributes:
- None
#### Children:
- None

---

## ZTBehKickOffRider
#### Attributes:
- None
#### Children:
- None

---

## ZTBehMorph
#### Attributes:
- __NameIt__ (_bool_) - (true),
- __initScale__ (_float_) - (0.4, 0.45, 0.50, 0.55, 1),
- __morphEntity__ (_string_) - (AlligatorChinese_Egg, AnkylosaurusNest_Egg, BirdElephant_Egg, subject, target),
- __morphFade__ (_bool_) - (true),
- __morphPeriod__ (_int_) - (1, 10, 100, 2, 300),
- __morphScale__ (_bool_) - (true),
- __morphTargetEntityType__ (_string_) - (Aardvark_Adult_F, Aardvark_Juvenile_F, Aardvark_Juvenile_M, Carcass_Meat, TermiteMound_Insects_Broken),
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

## ZTBehPlaceTarget
#### Attributes:
- __container__ (_string_) - (foodprop, head_inventory, lefthandobject, mouth, righthand),
- __targetBeh__ (_string_) - (PlaceFood),
- __targetType__ (_string_) - (Guest, s_KeeperDrinkType, s_KeeperEatType),
#### Children:
- None

---

## ZTBehShowEvent
#### Attributes:
- __ExpireWithTask__ (_bool_) - (false, true),
- __Interrupt__ (_bool_) - (false, true),
- __Name__ (_string_) - (DefaultTask_Aardvark, DefaultTask_Actor, FastWander, Interact_Player, WanderWater),
- __Priority__ (_int_) - (1, 10, 100, 5, 900),
- __Timein__ (_float_) - (1004.21, 30, 341.05, 5, 971.84),
- __Timeout__ (_int_) - (-1, 15, 180, 30, 59),
- __Type__ (_string_) - (AnimalEvent),
#### Children:
- None

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
* __interruptFlag__ (_bool_) - Allow interruptions? Default is `false`.
- __splashVector__ (_matrix3x3_) - Always `1 0 0, -1 0 0, 0 1 0`.
* __groundFit__ (_bool_) - Fit to ground according to leg nodes? Default is `true`.
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
#### Attributes:
- __behSet__ (_string_) - (Bleat, Dig, DustBathe, FailureSet, TreadWater_Idle),
- __fenceType__ (_string_) - (tankwallsegment),
- __searchDistance__ (_int_) - (6),
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

## ZTBehTeleportToLoc
Only used in `MC.tsk`'s `ReplaceProp` task.
#### Attributes:
- __resetProp__ (_bool_) - Default is `false`.
#### Children:
- None

#### Example:
```xml
 <ZTBehTeleportToLoc resetProp="true"/>
```

---

## ZTBehTestTargetPos
#### Attributes:
- __illegalBeh__ (_string_) - (KillTarget),
- __legalBeh__ (_string_) - (MWFailFeedback, ZKFailCleanWaterFeedback, ZKFailFeedback),
#### Children:
- None

---

## ZTBehTour
#### Attributes:
- None
#### Children:
- None

---

## ZTBehUsePortal
#### Attributes:
- __locoSpeed__ (_string_) - (burrow, evade, fast, medium, slow),
- __targetAnim__ (_string_) - (LieSide_Idle, Lie_Idle, SleepCurl_Idle, Stand_Idle, TreadWater_Idle),
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

## ZTBehViewAnimals
#### Attributes:
- __dockVPBeh__ (_string_) - (GotoPathVP),
- __retarget__ (_bool_) - (false),
- __viewMeterStart__ (_int_) - (200),
- __viewMeterStartMax__ (_int_) - (250),
- __viewMeterStartMin__ (_int_) - (150),
#### Children:
- [emoteSets](#emotesets)

---

## ZTBehViewEvent
#### Attributes:
- __edDonate__ (_string_) - (f_EdDonNormal),
- __edValue__ (_string_) - (f_EdNormal),
- __targetType__ (_string_) - (Guest, s_KeeperDrinkType, s_KeeperEatType),
- __viewKey__ (_string_) - (DPos_5, Neg_10, Neg_2, Neg_3, Pos_2),
- __viewRadius__ (_int_) - (20),
#### Children:
- [ZTFeedbackData](#ztfeedbackdata)

---

## ZTBehViewEvent
Container of [ZTFeedbackData](#ztfeedbackdata).
#### Attributes:
- __viewKey__ (_string_) - Apparently a grading scale for the quality of the event, eg. `Pos_2`, `Pos_3`, `Neg_5`...
#### Children:
- [ZTFeedbackData](#ztfeedbackdata)

---

## ZTBehWatchShow
#### Attributes:
- None
#### Children:
- [EventScoring](#eventscoring)

---

## ZTEmoticonInfo
#### Attributes:
- __emoticonEntityNode__ (_string_) - (Bip01 Head),
- __emoticonName__ (_string_) - (EmoteAngry, EmoteAnimalExerciseGood, EmoteAnimalExerciseVeryGood, EmoteAnimalHungerGood, EmoteAnimalThirstGood),
- __emoticonScale__ (_float_) - (0.5, 0.75, 1.5),
#### Children:
- None

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
#### Attributes:
- None
#### Children:
- [ZTActionInfo](#ztactioninfo)
- [ZTEmoticonInfo](#ztemoticoninfo)
- [ZTMessageInfo](#ztmessageinfo)
- [ZTThoughtInfo](#ztthoughtinfo)

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
- __filterAttribute__ (_string_) - (b_Rampage EQ true),
- __global__ (_bool_) - (false, true),
- __interval__ (_int_) - (30, 60),
- __locID__ (_string_) - (guestthoughts:AnimalHappy, guestthoughts:AnimalUnhappy, guestthoughts:AnimalVeryHappy, guestthoughts:AnimalVeryUnhappy, null:null),
- __priority__ (_int_) - (-1, 0, 1, 10, 2),
- __timeout__ (_float_) - (0.0f, 15, 30, 60),
- __tolerance__ (_int_) - (1),
- __useEntityName__ (_bool_) - (true),
- __useTargetName__ (_bool_) - (true),
#### Children:
- None

---

## ZTMessageInfo
#### Attributes:
- __locID__ (_string_) - The info to be raised in the info bar of the entity.
* __priority__ (_int_) - This message's relative priority.
* __timeout__ (_int_) - How soon should this message disappear?
* __interval__ (_int_) - how much time must pass until the message is raised again?
* __tolerance__ (_int_) - Unknown.
* __global__ (_bool_) - Not sure. Either (false, true)
* __useEntityName__ (_bool_) - Default is `false`.
* __useTargetName__ (_bool_) - Default is `false`
* __filterAttribute__ (_string_) - Rare, eg. `b_Rampage EQ true`
#### Children:
- None

---

## ZTThoughtInfo
#### Attributes:
- __global__ (_bool_) - (false, true),
- __locID__ (_string_) - (guestthoughts:AnimalHappy, guestthoughts:AnimalUnhappy, guestthoughts:AnimalVeryHappy, guestthoughts:AnimalVeryUnhappy, null:null),
- __priority__ (_int_) - (-1, 0, 1, 10, 2),
- __timeout__ (_float_) - (0.0f, 15, 30, 60),
- __useTargetName__ (_bool_) - (true),
- __useTargetObject__ (_bool_) - (true),
- __useTargetSpecies__ (_bool_) - (true),
- __useTargetTarget__ (_bool_) - (true),
#### Children:
- None

---

## ZTThoughtInfo
#### Attributes:
- __locID__ (_string_) - The info to be raised in the info bar of the entity.
* __priority__ (_int_) - This message's relative priority.
* __timeout__ (_int_) - How soon should this message disappear?
* __global__ (_bool_) - Not sure. Either (false, true)
* __useTargetName__ (_bool_) - Will appear instead of `%s` in the locID.
* __useTargetTarget__ (_bool_) - Will appear instead of `%s` in the locID.
* __useTargetSpecies__ (_bool_) - Will appear instead of `%s` in the locID.
* __useTargetObject__ (_bool_) - Will appear instead of `%s` in the locID.
#### Children:
- None

---

## animTable
#### Attributes:
- None
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
#### Attributes:
- None
#### Children:
- None

---

## avoidEntityTypes
Holds a list of entities that should be avoided in [BFBehWander](#bfbehwander) and [BFBehEvasion](#bfbehevasion) sets.
#### Attributes:
- None
#### Children:
- ["avoidEntityTypesEntry"](#avoidentitytypesentry) (not documented)

---

## behaviorTable
#### Attributes:
- None
#### Children:
- None

---

## behaviorTable
May be used from inside a [BFBehLocoSwitchSet](#bfbehlocoswitchset) or a [BFBehAnimSwitchSet](#bfbehanimswitchset).
#### Attributes:
- None
#### Children:
- ["behaviorTableEntry"](#behaviortableentry)

---

## behaviors
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
- [BFBehDockQueue](#bfbehdockqueue)
- [BFBehDockRadial](#bfbehdockradial)
- [BFBehDockSpline](#bfbehdockspline)
- [BFBehDockTAP](#bfbehdocktap)
- [BFBehEnter](#bfbehenter)
- [BFBehEscapeObstacle](#bfbehescapeobstacle)
- [BFBehEvasion](#bfbehevasion)
- [BFBehFaceTarget](#bfbehfacetarget)
- [BFBehFollowEntity](#bfbehfollowentity)
- [BFBehHeadLook](#bfbehheadlook)
- [BFBehHide](#bfbehhide)
- [BFBehKill](#bfbehkill)
- [BFBehLocoSwitchSet](#bfbehlocoswitchset)
- [BFBehMove](#bfbehmove)
- [BFBehPlaySet](#bfbehplayset)
- [BFBehPursuit](#bfbehpursuit)
- [BFBehRandomSet](#bfbehrandomset)
- [BFBehScript](#bfbehscript)
- [BFBehSendToken](#bfbehsendtoken)
- [BFBehSendTrigger](#bfbehsendtrigger)
- [BFBehSetAttribute](#bfbehsetattribute)
- [BFBehSpawn](#bfbehspawn)
- [BFBehSyncSet](#bfbehsyncset)
- [BFBehWaitQueue](#bfbehwaitqueue)
- [BFBehWander](#bfbehwander)
- [BFBehWhap](#bfbehwhap)
- [ZTBehCureDisease](#ztbehcuredisease)
- [ZTBehDigArtifact](#ztbehdigartifact)
- [ZTBehDockFence](#ztbehdockfence)
- [ZTBehDockTankWall](#ztbehdocktankwall)
- [ZTBehEconomy](#ztbeheconomy)
- [ZTBehFeedback](#ztbehfeedback)
- [ZTBehMorph](#ztbehmorph)
- [ZTBehShowEvent](#ztbehshowevent)
- [ZTBehSplashGuest](#ztbehsplashguest)
- [ZTBehTargetFence](#ztbehtargetfence)
- [ZTBehViewAnimals](#ztbehviewanimals)
- [ZTBehViewEvent](#ztbehviewevent)
- [ZTBehWatchShow](#ztbehwatchshow)

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

## emoteSets
#### Attributes:
- None
#### Children:
- None

---

## randomAnims
#### Attributes:
- None
#### Children:
- None

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
- None

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
- None

---

## textkeys
#### Attributes:
- None
#### Children:
- ["textkeysEntry"](#textkeysentry)

---

## userData
#### Attributes:
- __invalidateHabitat__ (_bool_) - (true),
#### Children:
- None

