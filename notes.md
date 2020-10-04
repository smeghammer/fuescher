# F*ck you, Escher!

An experimental level showing portal usage and some trickery with floor heights. Loosely inspired by various MC Escher pictures.



FLOORS:







vertical portals (line special = 57) between floors:


		LINEDEF ARGUMENTS (lineID, tag, portal type arg1, arg2)
floor	tag	Top left	Bottom left	Top right	Bottom right
----------------------------------------------------------------------------
384	17	
		56,16,6,1,1	52,16,6,1,0	86,17,6,0,0	84,17,6,0,1
256	16
		192,8,6,1,1	195,8,6,1,0	193,16,6,0,0	194,16,6,0,1
128	8
		40,7,6,1,1	36,7,6,1,0	74,8,6,0,0	72,8,6,0,1
0	7
		167,15,6,1,1	44,15,6,1,0	166,7,6,0,0	164,7,6,0,1		
-128	15

384	33	
		48,32,6,1,1	52,32,6,1,0	60,33,6,0,0	68,33,6,0,1
256	32


128	32
		69,29,6,1,1	965,29,6,1,0	1096,32,6,0,0	1095,32,6,0,1
0	29

320	58
		1661,57,6,1,1	1675,57,6,1,0	1649,58,6,0,0	1673,58,6,0,1
0	57


horizontal portals (line special = 156) between walls. Pair of rows represents
a two-way portal:

floor	lineid	destTag	selfTag	type	anchor
----------------------------------------------
[central hole porting from basement to 2nd floor. means exit is actually on the second floor...]	
256	155	7	8	2	2		
-128	159	12	11	2	2		
							
256	156	9	10	2	2		
-128	160	14	13	2	2		
							
256	157	11	12	2	2		
-128	161	8	7	2	2		
						
256	158	13	14	2	2			
-128	162	10	9	2	2		
						
[256, S, door passage to 128, S door passage]		
256	154	6	5	2	2		
128	107	5	6	2	2		
						
[128, W, door passage to 0, E door passage]		
128	104	2	1	2	2		
0	96	1	2	2	2		
							
[128, S, door passage to 256 dummy 'basement' room]	
128	107	5	6	2	2		
256	154	6	5	2	2		

[128, SW stair end to 0 E stair end. This fucks with heights...]
128	146	4	3	2	2
0	143	3	4	2	2


line portal puzzle:
IDs 40 - 48





BUG!!!!
-------

----------------------------------------

MAP01 - Entryway

Warning: z-offsetting not allowed for interactive portals. Changing line 96 to teleport-portal!
Warning: z-offsetting not allowed for interactive portals. Changing line 104 to teleport-portal!
Warning: z-offsetting not allowed for interactive portals. Changing line 107 to teleport-portal!
Warning: z-offsetting not allowed for interactive portals. Changing line 143 to teleport-portal!
Warning: z-offsetting not allowed for interactive portals. Changing line 146 to teleport-portal!
Warning: z-offsetting not allowed for interactive portals. Changing line 154 to teleport-portal!
Warning: z-offsetting not allowed for interactive portals. Changing line 155 to teleport-portal!
Warning: z-offsetting not allowed for interactive portals. Changing line 156 to teleport-portal!
Warning: z-offsetting not allowed for interactive portals. Changing line 157 to teleport-portal!
Warning: z-offsetting not allowed for interactive portals. Changing line 158 to teleport-portal!
Warning: z-offsetting not allowed for interactive portals. Changing line 159 to teleport-portal!
Warning: z-offsetting not allowed for interactive portals. Changing line 160 to teleport-portal!
Warning: z-offsetting not allowed for interactive portals. Changing line 161 to teleport-portal!
Warning: z-offsetting not allowed for interactive portals. Changing line 162 to teleport-portal!

Execution could not continue.

Could not realloc 16951417536 bytes


11/09/20 
--------
 - make line portal puzzle with curves· Need to plan this one...
 - need drawing (gdoc etc)

Circle of despair logic:
------------------------
 - Numbering is clockwise, start at top (1 o'clock); left then right segments.
 - Each quadrant is z-offset by 64MUs
 - 


self	target 		route		orientation	position	notes
-----------------------------------------------------------------------------
40	41		1		V		[entrance]	
41					V		L, NNE		forward
									
42					H		L, ENE		
43					H		L, ESE		
									
44					V		L, SSE		
45			2		V		L, SSW		
									
46	50		3		H		L, WSW		
47					H		L, WNW		
									
48					V		L, NNW		
49	56		5		V		R, NNE		
									
50	49		4		H		R, ENE		back
51					H		R, ESE		
									
52					V		R, SSE		
53					V		R, SSW		
									
54					H		R, WSW		
55					H		R, WNW		
									
56					V		R, NNW		exit
			

 - Lighted candles flag the correct route
	- may be back the way you came...
 - each central branch allows view into central column (which is a sector portal) except the exit.

route:
PORTALS
EXIT	ENTRY	TARGET	DIRECTION ON EXIT	PORTAL POS	NOTES
---------------------------------------------------------------------
41	41	45	go back through		L:NNE/L:NNE	arrive from corridor
45	46	51	go ahead to next	L:SSW/L:WSW
51	51	54	go back through		R:ESE/R:ESE
54	53	48	go ahead to next	R:WSW/R:SSW
48	47	55	go ahead to next	L:NNW/L:WNW
55			*** EXIT PUZZLE ***	R:WNW  

THIS WORKS. Add direction flag to OTHER side of portal

TODO:


All Keys needed to access highest three floors (need to add another floor). Each accessed floor 
has a switch that will open part of the exit cage.


18/09/2020:
-----------
 - recursive spiral stair. 			X
 - look OUT through top from window(s)?
 - WTF with the fly thing?
 - continue library
	- make central portal a stair (gate at top so cannot go UP until got key)?


library window logic:
---------------------
type 1, visual only?
1: library window from inside
	looking out, target SHED

2: library window from OUTSIDE
	look up from floor, looking IN, see library interior

3: SHED window from outside
	looking IN, see library interior

line IDs:
library window (ext)	62
library window (int)	61
shed window		60



09:47 19/09/2020
------------------

 - 3-way thrick for keys viewing
 - need yellow key!!!
 - add windows on all upper blocks
 - add corresponding windows
 - LINE PORTAL TABLE!!!
 - try Escher waterfall
 - LINE portal from library to other sector floor? (STAIRS??)

 - Make courtyard portals into a U shape thing... Have one window that actually looks through, just to confuse.

LINE IDs
--------
line #		line ID		pos (x,y)
-----------------------------------------




21/09/2020:
-----------
 - adjust sewer/library linedef textures
bstone2
rrock12

Tag (84) for hidden door in library upper. Need to add switch in library lower to open it.


22/09/2020:
-----------

Line Portals:
-------------

line	target	pos		notes
-------------------------------------

library lower
81	80	790,4190	exit to library upper
----------------------------------------------------------

library upper
-------------
80	81	-320,3000	exit to library lower
84	83	240,2600	drain exit to yellow key
24	25	0,2160		main exit to exterior

observation post
----------------
1	2	-330,760
23	22	200,460
6	5	0,230
3	4	-600,-230
----------------------------------------------------------

north main room
---------------
21	20	0,40
88	0	-260,-90	out only
70	71	-150,-720	WINDOW
----------------------------------------------------------

south main room
---------------
0	0	-160,-816	WINDOW [not set]
2	1	336,-1024	east exit
4	3	608,-960	SSE exit corridor
40	41	-320,-1440	SSW exit corridor to circle puzzle
60	0	0,-1750		S [out only]
31	30	-448,-1896	W exit, lava trap
31	30	-456,-1664	W exit, RETURN ONLY redirects to lava trap
----------------------------------------------------------

cellar
------
5	6	0,-2400		main room exit
22	23	864,-1960
78	77	864,-2104	WINDOW
----------------------------------------------------------

lava cave
---------
30	31	1120,-1544	north exit
89	88	1840,-1888	east exit
----------------------------------------------------------

LH circle
---------
41	45	1016,-50
42	51	1310,-300
43	50	1310,-450
44	56	1030,-750
61	60	960,-670
45	52	890,-730
46	51	600,-450
47	55	608,-320
48	49	896,-32		exit sector

RH circle
---------
49	56	1984,-40
50	55	2272,-320
51	54	2272,-456	exit sector
52	45	1984,-744
53	48	1864,-744	
54	43	1568,-456
55	51	1568,-320
56	48	1856,-32


courtyard windows
-----------------



exterior windows [3rd floor]
----------------------------
62	63	West		WINDOW 
-	-	North		WINDOW [not set]
-	-	East		WINDOW [not set] 
-	-	South		WINDOW  [not set]

exterior windows [2nd floor]
----------------------------

exterior windows [1st floor]
----------------------------

exterior windows [Gnd floor]
----------------------------





haha - make the return from the lava pit a portal to the lava pit!!!
 - done, need to add an exit and HIDE the secret door..

 - need to add lights everywhere.


11:12 24/09/2020
-----------------

door at 72, -1696 needs to be triggered remotely. Tag=102


sort out blue and yellow keys:
 - order not yet correct... I need to get the YELLOW key last.


10:53 25/09/2020
----------------

Escape via 1st level of red key?



Library lower drop-through logic??TODO


Inaccessible bits of tower - make secret?
 - add jaw things, but closed - so you cant jump n by mistake
 - add switch n one to lower jaws of other so you can escape again.
 - add secretty thking
 - make iron/blood themed?

OK - lower RH is target for secret portal (where??). This has jaw-things but UP. Another 


18:58 27/09/2020
----------------
final secret puzzle:
1: arrive at NW tele dest
 - Drop into lower area (E)
 - bottom area switch opens spiral area button (S) ALSO opens beasts in lower area (NE) 
2: teleport back up
 - activate South switch (drops teeth AND West switch)
 - drop down to exit area or:
 - activate East swicth to open sectret secret tele (NNW),


28/09/2020:
-----------
make super-secret level lava with cage all around
 - actually sky and metal.


30/09/2020:
-----------
Tags as of this date (UDB):
5
6
7
8
9
15
16
17
22
23
24
25
26
27
28
29
32
33
57
58
59
84
102
122
151
152
153
154
155
156

exit seq:
---------

Add bars to exit.
Add switch for this in new area, but fenced off from the super super secret bit.




13:29 01/10/2020
----------------

sound from https://www.freesoundeffects.com/free-sounds/fire-10007/

TODO:
-----
library upper 
	- stair wall texture -grey
	- bok column align
 	- Lower door and flag with flicker or similar
	- doortrak!!!

big stair upper
	- adjust light


Need to add final secret source teleporter. From exit room

 - fall all the way back, but give LOADS of ammo etc. Monster closets openin cellar and 1st floor (and possibly others?) to make a big fucking battle on the way out
	- need teleporter rather than portal from  -1760,-1736 to LIBRARY UPPER UPPER secret. Only if you get to the last secret will monster closets tigger (you can get out before, by dropping down foorm secret area 1)


 - crossing tele exit line in secret area opens all lower monster closets.
 - crossing SUPER SECRET tele exit opens more? (archvile?)

 - add monser closet to lava area too


Unfinished tunnel in main area nees to go somewhere...

Also - add beams under roofs.

monsters in library lower. Trigger MORE on switching in small office	DONE
monster in sewer closet (dormant??)					DONE
redo lights on sewer top!!!						DONE
blue key!!! WTF?							DONE
health in library window						DONE
textue in cellar closet							DONE
circle puzzle - monsters around corners					DONE
soul sphere needs to be a secret					DONE
library upper - door to lower needs to be better flagged, 		DONE
	and adjust ceiling texture!!!
sewer texture AGAIN!!!							DONE
another dormant monster in cellar					DONE
move monster away from portal - wierd things if use chainsaw 		DONE
	(its teh yellow ket bit exit)		
mark switch in library lower room					DONE
improve circle exit...
corridor windowsills - too bright					
blue and rfed main door target sector too bright

tele target too narrow for cacos. Change to skulls
tele spot to left of library lower small room exit not placed correctly?
sewer missed a water lfat!!
spectre stuck in super secret area by switch
shells under  corner - need to raise.
better deoms in final ssecret closets, LINK the closets so you don't need to bugger about with the portals 
mid door main silo - adjust floor from metal



 - adjust cirle puzzle to use alt door face rather than candles. Might be clearer...
Also, portals need to be CLOSER to the doors!


REVISIT THIS!!!:
 - Lighted candles flag the correct route
	- may be back the way you came...
 - each central branch allows view into central column (which is a sector portal) except the exit.

route:
PORTALS
EXIT	ENTRY	TARGET	DIRECTION ON EXIT	PORTAL POS	NOTES
---------------------------------------------------------------------
41	41	45	go back through		L:NNE/L:NNE	arrive from corridor
45	46	51	go ahead to next	L:SSW/L:WSW
51	51	54	go back through		R:ESE/R:ESE
54	53	48	go ahead to next	R:WSW/R:SSW
48	47	55	go ahead to next	L:NNW/L:WNW
55			*** EXIT PUZZLE ***	R:WNW  

THIS WORKS. Add direction flag to OTHER side of portal

TODO: I might be able to do it such that the candle you need to follow is ALREADY lit on passing throuh the portal, and STAYS lit (basically, play with the visibility of candle either side of he portal - you will be seeing DIFFERENT candles of course, but as you gp through the portal it will remain lit etc. TODO)


09:24 04/10/2020:
-----------------

 - Make archvile area better combat - ie allow backing out wirhout portal getting in he way.
 - Can I improve the main entry doors in this way?
 - SKY PORTALS!!! :ook nto why loking DOWN fails... Is this just because the space behind the door is too ig? ALSO, are any of them on SAME level so I can use interactive portal
 - DEBUG console mesages!
	Set up logging to text file

11:14 04/10/2020
----------------

BUG
bottom main door:
portal def: 156, 60,61,1,2

Grab red key - opens a closet, force you to run for the baron door... - OK

wierd bug between wheel portals between line IDs 1102 and 1300. "Link offset mismatch between sectors 218 and 277" not sure why...

Console otpu:


Unknown bottom texture '-W' on first side of linedef 4077
Unknown bottom texture '-W' on first side of linedef 4099
Link offset mismatch between sectors 218 and 277


These texture errors are also not ctually there. WTF 


 - Make top exit from silo longer so you don't back out into the circle maze - OK
 - put SSG at silo exit not CGUN -  OK
 - soulspher sector, flag as secret - OK
 - check library lower secret is accessible!! - OK
 - exit from lava GREY1 textures. FIX - OK
 - health in lava trap - OK


 - Check main door floor tex!!
 - SILO EXIT TEXTURE!!!!!!!
 - yellow key seer wate tex!! - OK
 - add exit line action
 - add barons to final trap