This is a small project I hope to parse the Yankees lineup using a score system
I devise. 

Basically the goal is to take a stat CSV, parse it into a useful .csv, then be able to upload it into a Tableau dashboard. 

The data set is Baseball Reference's 2022 Yankees roster.

Here is what interests me:
The player's name, obviously

Are they left-handed or right-handed?
I want the script to parse BRef's data. If it calls them out
As lefty, they are marked lefty, otherwise they are marked rightie.

Data of interest:
G, GS, SHO, IP, GS, H, R, BB, HR, SO, HBP
BK (Balk), WP (Wild Pitch)

Years ago, we had Kyle Farnsworth on the Yankees.

My enduring memory is my buddy's dad yelling "Oh no, It's Farnsworth!"
when Rowdy Kyle came into a game. That's the way it was that season. With him, you just knew 
something bad was going to happen. We had an Anyone but Farnsworth Facebook group. It ruled.

(I am sorry, Kyle Farnsworth, please do not tackle me, you seem really interesting
and apparently make really good peanut butter cookies but that season
was terrible)

The Farnsworth Index is both a tribute to that season and a tribute to my buddy's dad, which
is borth hilarious but he'd also appreciate it.

The initial dataset pulls from Baseball Reference and the 2022 Yankees pitchers. So:

We care about:
Innings Pitched: IP

A pitcher who throws lots of innings is, broadly speaking, more useful than one that does not. Shut up, I'm right. 

So, what good things can a pitcher do in an inning?
Strike a hitter out (SO)

What bad things can a pitcher do in an inning?
Give up a Run. (R)
Give up a Home Run (HR)
Give up a walk (BB)
Hit a batter (HBP)
Balk (BK)
Wild Pitch (WP)

This metric does not attempt to quantify your pain. Perhaps a later version! This just attempts to determine if you will groan, not the degree.

After thinking about it, I have come to a conclusion: We can consider Hits, perhaps, value neutral. Perhaps there is a strategy to it. Perhaps the fielders will save him. There is still a chance for an Out. 

You may or may not groan at a hit. It's my index and I do what I want. 

FarnsworthIndex.py does the initial trimming of the dataset
