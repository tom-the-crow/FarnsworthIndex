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

Ultimately, it comes down to this: 
Good Things: It finds the percentage of times a pitcher makes good things happen. This may be more than 100% if they generate more strikeouts than innings pitched. Fantastic, they've got this.

Bad things: It finds the percentage of times a pitcher makes bad things happen. This may be more than 100% if they generate more bad things than innings pitched. There are also more bad things possible. 

I rule Hits as neutral since your fielding could always save you. I am god. Math is my instrument. MY CREATION. I DO WHAT I WILL. Hits don't count.

So you could have a 127% chance of making something good happen and a 119% chance of making something bad happen just by stepping on the field.

Is that absurd? SO IS BASEBALL, FRIEND! LIFE IS MEAINGLESS ABSURDITY!

So, to generate the Farnsworth Index, we divide the two percentages and see what happens. This generates a metric, a ratio, a relative measure comparing "good things" to "bad things. A higher percentage of "good things to "bad things suggests better performance while a lower percentage indicates a lower ratio of positive outcomes to negative outcomes

So a pitcher coming in with a high Farnsworth index, you're probably happy. A low one? OH GOD IT'S FARNSWORTH. 

I should be kept away from math and baseball. 



FarnsworthIndex.py does the initial trimming of the dataset
FarnsworthIndexCalc.py does some calculations and spits out the final data file to feed to Tableau

5/29/23: Made some tweaks to Index like removing the Asterisk (it was bugging me!) and Calc to generate percentages
