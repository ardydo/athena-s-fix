# Athena's Armor Set Hiryu Fix

A fix for Hiryu armor set not appearing even when "Allow Japanese-Only DLC" toggled. I went ahead and made it appear on default while there is not an update.

## Installation
1. Click the green "Clone or download" button and then "download ZIP"
2. Find your Athena's folder and just dump all the five files inside the /Data folder.
3. If you want to test if it's working, restart Athena's, try searching for a set with "Evade Extender", "Airborne" and "Stam Recov Up" and sorting it by family. Hiryu set should be the first one to show up.

## Explanation

Armor pieces are stored by Athena's inside various .txt files. One for each slot (Head, Chest, Arms, etc) and inside that file each line is a single pice of equipmente and it contains all of that armor info. The entries are store like that:

> Name, gender (0-2, both, male, female), type (0-2, both, blademaster, gunner), rarity, slots, available rank (1?-99, low rank, high rank, being 99 unavailable) , village available rank (1?-99, being 99 unavailable), "time available Atsumarina" (I have no idea what this is actually), base defense, max defense, fire res, water res, thunder res, ice res, dragon res, skill 1, skill 1 number,....skill 5, skill 5 number (those are necessary, even if there is no skill, if the "," are not present Athena's will crash.), ingredient 1, # of ingredient 1 needed,...ingredient 4, # of ingredient 4 needed

That's a really long line.

Here's is an example of how and entry looks like. It's actually, the default Hiryu Gunner hat.

> 飛竜の面・地,0,0,7,2,99,99,0,30,61,2,2,3,2,2,跳躍,2,気力回復,3,回避距離,2,,,,,迅竜の黒毛,4,火竜の上鱗,4,歴戦の漆黒皮,2,オプション,1

Note the the ",," beteween the skills and the ingredients that are there because the piece doesn't have 5 skills. Each entry takes the same number of arguments every time and if you don't suply it correctly, Athena's will just crash.

Now, take a look at that entry. You will see that there are two "99" on it, indicating that it's not available in the village and neither on the guild quests. So I changed that to 4, since the event quest is high rank but that didn't work and after experimenting a little, I figured out that the ingredients were also somehow making the pieces not appear. the last item "Option", for some reason, was being filtered out so I just went ahead and deleted it.

Now, the string looks like this:

> 飛竜の面・地,0,0,7,2,4,99,0,30,61,2,2,3,2,2,跳躍,2,気力回復,3,回避距離,2,,,,,迅竜の黒毛,4,火竜の上鱗,4,歴戦の漆黒皮,2,,

So, there it is.

## Thanks

Thanks for Athena for making such an awesome tool that without it I would never even bother making mixed sets because I'm really lazy.