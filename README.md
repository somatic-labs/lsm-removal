# lsm-removal
plan foir the removal of the liquidity staking module from the cosmos hub



## Checklist

thus in my opinion the next steps, which should be executed in parallel are:

who knew what, and when:
  * https://x.com/gyunit_/status/1846429565435929077
  * I have a feeling that Grace volunteered here and I'd happily follow her lead on it


Research
* we need to determine if there is a way to disable LSM functionality.  My opinion is that there actually isn't one but I am happy to be wrong about this.
  * @pitasi suggested using x/circiut, but that doesn't seem to be present in the hub's source code:  https://github.com/cosmos/gaia/blob/main/app/app.go -- so I don't think this will be an option.
  * the hub does have an indirect dependency on x/circiut: https://github.com/cosmos/gaia/blob/ea3eda99b677bfd47d2334ac86b5e7fa8e75850a/go.mod#L61
   * we should check if it is somehow usable without direct integration, and also look into how a module not used by the hub gets used as indirect for the hub.  I don't think so though, probably just a dependency quirk.


* we need to determine what the consequences of removing LSM are for chains that connect ot the hub over ICS
  * Neutron
  * Stride
  * Crypto Dungeon

* we need to determine what the consequences of removing LSM are for chains that connect ot the hub over IBC
  * all of them -- too many to list, we will need to make generalizations

* we need to determine what the consequences of removing LSM are for chains that connect ot the hub over ICA (focus on liquid staking chains of course)
  * teams - Each team is listed, with point of contact and their thoughts should be collected here.
   * Stride - @RoboMcGobo 
   * Neutron - @Spaydh 
   * Quicksilver - @joe_bowman 
   * Persistence (I understand the product is EOL'd but should check in to make sure there are no issues we'd cause)

  
* we need to determine where those 6000 atoms are, and what the consequences are for their holders if LSM is disabled or removed
  * @arlai_mk is going to track down tokenized staked atoms that aren't with any particular LS provider, and if they've left the hub.


Software - software steps, to be executed sequentially
  1) learn what the changes to application state made by LSM are, and come up with a plan for a migration back to normal, boring, safe, cosmos-sdk modules looks like.  We musn't make any assumptions here, the documentation must be precise.
   
   * .proto files
   * store keys
   * ...others (assume there are some but don't know what they are yet)


  2) code these changes and test them on the hub testnet, ensuring that there is sufficient state in the hub testnet environment

  3) use software to test these changes against the actual state of the cosmos hub, before the code is deployed to mainnet, to ensure that there will be no issues with migration


**Technical Comms**
The cosmos-sdk repository contains software known to be developed by agents of the worlds largest cryptocurrency theft organization.  This needs to be labeled as such.  All -lsm branches should contain an explicit and clear warning.


 - [ ] marked in its readme.md file to include code history
  
   - [x] v50: https://github.com/cosmos/cosmos-sdk/pull/22272
  
    - [x] v47: https://github.com/cosmos/cosmos-sdk/pull/22273
  
    - [x] v45: https://github.com/cosmos/cosmos-sdk/pull/22274
  
  - [ ] retracted/deprecated


* we need to commmunicate unilaterally -- independent of the ICF or amulet, that these steps are being taken, and show a proper intolerance to known thieves contributing code to cosmos
   * Me: https://x.com/gadikian/status/1846452653595021713
   * AIB: https://x.com/Allinbits_inc/status/1846315815521440201
   * (I will include others statements of intolerance to known theft actors as contributors as they are made.  Just pass links to me and I'll get you in here)
