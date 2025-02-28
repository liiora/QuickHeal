
# QuickHeal Turtle WOW

QuickHeal for Turtle WoW (updated for patch 1.17.2)

QuickHeal gives healers fast access to all of their direct healing spells for healing party/raid members and themselves. It lets you heal the people who need it, without having to target them manually, or even having to deselect the enemy you're fighting. It gives maximum mana efficiency, and will automatically use a lower rank of healing if the target doesn't need your biggest heal, or if your mana is running low. This also works when not in a party or a raid, and this will save you mana and precious time by automatically selecting the healing spell. There are several different key bindings for constraining the scope of players that will be considered for heals.

This version was created by Zebouski and before that by Sulpitz, I just added some modifications to fit with Turtle WoW 1.17.2

**Integration of HealComm**

QuickHeal uses the incoming heal information broadcast by HealComm, through the addonchannel to reduce overhealing and making this addon used by multiple raidmembers more effective.

## Installation
- Download QuickHeal from this repository into your Interface folder and remove the "-main" in the folder name
- Download HealComm (mandatory or QH won't work) from here https://github.com/Bestoriop/HealComm
- Download Bonusscanner (Makes QuickHeal and HealComm (Luna unit Frames) more accurate by taking gear and +Heal into account: https://github.com/GryllsAddons/BonusScanner

## Usage

**Help**
`/qh help` displays help inside the console

**Configuration**
`/qh cfg` invokes the configuration interface

**Heal**
To invoke quickheal, make a macro with the `/qh` slash command syntax or set Key Bindings:


**Downrank**
To conserve mana and heal more efficiently you can limit the maximum rank that QuickHeal will use. It is done by moving the slider. on the Downrank Window.

`/qh dr` to open the Downrank Window

**High HPS vs Normal HPS**

`/qh toggle`
Toggles between Normal HPS and High HPS. This corresponds to the **Toggle Heathy Threshold 0/100**.  When invoked, it will echo `QuickHeal mode: Normal HPS` and `QuickHeal mode: High HPS` in the console to display its current state.

High HPS is restricted to fast-casting heal spells.
    High healing throughput but low mana efficiency. e.g. Flash Heal

Normal HPS encomapsses ALL healing spells regardless of relative cast time.
    Normal healing throughput with higher mana efficiency.

**Tank list and mt healing**

`/qh tanklist`
Toggles tanklist display.

`+` adds current target into the list.  `C` clears the list.

**Other keybinds for specific healing**

`/qh [mask] [type] [mod]` OR `/quickheal [mask] [type] [mod]`:<Br>

`[mask]`: constrains healing pool to:<Br>
`player` = yourself<Br>
`target` = your target<Br>
`targettarget` = your target's target<Br>
`party` = your party<Br>
`mt` = main tanks (defined in the configuration panel)<Br>
`nonmt` = everyone but the main tanks<Br>
`subgroup` = raid subgroups (defined in the configuration panel)<Br>

`[type]`: constrains healing spell to:<Br>
`heal`: Forces the use of your class' channeled heal spells.<Br>
`hot`: Forces the use of your class' HoT spell over a channeled spell.  Only works for Priests & Druids & Paladins for holy shock .<Br>
`chainheal`: Forces the use of the Chain Heal spell.  Only works for Shamans.<Br>

`[mod]`: optional argument.  Modifies the application of HoTs:<Br>
`max`= will apply a HoT to the next target that is not @100% hp and that does not currently have a HoT applied.<Br>
`fh` = firehose mode.  Will apply maximum rank HoT on the next target that does not have a HoT applied.<Br>
<hr>


## ChangeLog:

**1.14.5**<Br>
Disabled vestigial config UI tab 'Target Filtering'
Fixed lua error messages that were being generated from bad OnEnter syntax in QuickHeal.xml:1620:FilterRaidGroup1-8
Revised readme.md
<hr>
  
**1.16**<Br>
Added functions `SmartRenew()`, `SmartRenewFirehose()` and `SmartRenewThrottle()`.
Revised readme.md
<hr>
  
**1.16.1**<Br>
Removed functions `SmartRenew()`, `SmartRenewFirehose()` and `SmartRenewThrottle()`.  These were causing target focus problems.<Br>
Implemented `/qh hot` to replace SmartRenewThrottle().<Br>
Regular SmartRenew & SmartRenewFirehose comin' soon-ish like.
<hr>

**1.17.0**<Br>
Modified the verbiage for `/qh toggle` to `QuickHeal mode: Normal HPS` and `QuickHeal mode: High HPS`.<Br>
The main tanks list is now saved to disk and will persist across sessions.</Br>
Removed non-partition mode (`hm`) commands.<Br>
Druids can now cast HoTs while moving.<Br>
Big overhaul on usage syntax
<hr>

**1.17.1**<Br>
Implemented TWA button inside Main Tanks UI that queries TWAssignments' roster and automatically fills Main Tank UI with up-to-date tank assignments.  Does not require TWAssignments to be installed on the local client.  Requires membership to a raid in which at least one other raidmember/leader is using TWAssignments.<Br>
<hr>

**1.17.2**<Br>
Fixed shaman class.
<hr>

**1.17.3**<Br>
Removed `/qh healpct`.<Br>
Channeled heals now proactively rely entirely on HealComm to determine if another player is healing your considered target(s) during the selection process.<Br>
Each healing class now has its own syntax command tree.<Br>
Added [chainheal] healing type selection for Shaman class.<Br>
<hr>

**1.17.4**<Br>
Re-partitioned class modules (i.e. QuickHealDruid.lua, QuickHealPriest.lua, QuickHealPaladin.lua, QuickHealShaman.lua) to allow for class-specific spell/item cast sequences.
<hr>

**1.17.5**<Br>
Added 4 new keybindings: 
- "HoT" [/qh hot] 
- "HoT Firehose (Naxx Gargoyles)" [/qh hot fh] 
- "HoT Subgroup" [/qh subgroup hot] 
- "HoT MT" [/qh mt hot]
<hr>

**1.17.6**<Br>
Druid healing improvements & Shaman chainheal fix.
- Druid: Modified downrank sliders that control Healing Touch and Regowth maximum ranks
- Druid: Split QuickHeal_Druid_FindHealSpellToUse into two separate function blocks: one for <L60 healing and one for =L60
- Druid: Removed "Cfg->General->Healthy Threshold Slider/RatioHealthy" slider and explanation text;
- Druid: Eliminated all in-combat HT ranks above HT4 if =L60. 
- Druid: When in Normal HPS mode, HT4 will be cast over HT3 if Nature's Grace procs.
- Shaman: Fixed intermittent ChainHeal SpellID error
<hr>

**1.18**<Br>
- Shaman : Removal of Purification talent bonus (no longer exist in last Turtle Wow Patch)
- Shaman : Healing Way buff now affects Chain Heal too
- Priest : Holy spells updated for 1.17.2 values
- Priest : Spiritual Healing new value (30% instead of 10%)
- Paladin : Integration of Holy Judgement mechanic to prio HL in that situation
- Paladin : Integration of Daybreak buff detection and multiplier
- Paladin : Flash of Light R7 added
- Druid : Tree of Life doesn't cancel on quickheal usage anymore
- Druid: Brought back "Cfg->General->Healthy Threshold Slider/RatioHealthy" slider and explanation text; You can now use regrowth even out of combat for Tree of life lovers
- Druid : Brought back low ranks
<hr>

  **1.19**<Br>
- Paladin : Integration of Holy Shock logic with the "/qh hot" macro
- Paladin : Holy Shock now use a rank system to limit overheal, updated from 1.17.2 values
- Paladin : Divine Favor is taken in account for holy shock effectiveness
- Paladin : Holy Shock is now usable while moving
- Druid : Improved regrowth is taken in account for Regrowth effectiveness
- Druid : /script QuickHeal(nil,'Swiftmend') now works while moving


