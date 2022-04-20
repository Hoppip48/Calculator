## Cerulan quest npcs

Implementation of a quest that has you capture a specific Pokemon caught by yourself after the request for an npc every day to gain rewards  

## Description

**Task Npc**
Talking to the old man in a house in Cerulan city triggers the script in cerulanTaskNpc.py.
He will ask for a random common Pokemon choosen from a limited pool.
The pokemon must be caught after the start of the quest and cannot be from another trainer.
After showing a Pokemon that fits the request the reward npc will become unlocked.

**reward Npc**
Talking to the old woman in the same house triggers the script in cerulanRewardNpc.py.
If the task has not been completed the current day, she will simply redirect to the task npc.
Otherwise she will give you a reward.
There are 4 tiers of rewards and 3 pools of rewards, each tier is choosen according to the total ivs.
Each tier has a 25% chance to get the reward of the next tier.

** Tier 1: 2-5 normal rewards ** 
** Tier 2: 1 good reward **
** Tier 3: 2-5 good rewards **
** Tier 4: 1 really good reward **

* 0-80 ivs 
	* 75%
		* Tier 1
	* 25%
		* Tier 2
* 80-120 ivs 
	* 75%
		* Tier 2
	* 25%
		* Tier 1
		* Tier 2
* 120-160 ivs
	* 75%
		* Tier 1
		* Tier 2
	* 25% 
		* Tier 3
* 160+ ivs
	* 75% 
		* Tier 3
	* 25% 
		* Tier 4

## Variables

*User vars*
* cerulanQuest(Str): name of pokemon to catch, expires at midnight
* cerulanReward(int): total ivs of caught Pokemon
* cerulanCompleted(bool): True if quest is completed, expires at midnight

*Task Npc*
* to_hunt(list): pool of Pokemon to catch
* daily_poke(int): name of pokemon to catch
* p(pokemon): caught Pokemon object

*Reward Npc*
* reward(list): pool of normal rewards
* good_reward(list): pool of good rewards
* best_reward(list): pool of really good rewards
* dialogues(dict): ivs(int) matched with dialogues(str)
* pivs(int): (pokemon ivs) total ivs of caught Pokemon
* random_reward(str): random reward :+1:
* q(int): random quantity of rewards
