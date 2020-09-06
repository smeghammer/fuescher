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













