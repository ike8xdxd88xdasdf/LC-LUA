LolCore script beta build - Xerath


Test script for Xerath includes: 
- orbwalker script with lasthit (not perfect)
- evade script
- spellcasting script with dedicated prediction module
- automatic target selector script with: left click to focus 

Known issues:
No spell usage for waveclear and missing creep lasthits on push key
No hourglass prediction
No summoners other than flash currently implemented

To have evade use flash -> Enable: lua evade walking + use flash against level 5 threat -> scroll down in lolcore until you find enemy and their abilities, create priority list (5 = will flash when evade is not possible)

Recommended Xerath config: 
1. Enable manual cast Q in League (click once to charge, click again to release)
2. High to very high hitchance
3. W require center at impact
4. E usage - High confidence combo 

How to use: 
Holding spacebar will shoot W and E 
Press Q once and script will auto aim and release Q
Press R to enter R mode, then hold T when you want to shoot
Disable in LolCore - Main: Orbwalker Clicking, Prediction, Evade 
                   - Hero: Everything

Be aware: 
Right clicking to do manual movement can counteract evade movement
When Q can't resolve a good hit, it won't shoot. Don't instantly decrease hitchance
