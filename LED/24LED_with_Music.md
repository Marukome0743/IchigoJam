<h1 align="center">24LED with Music</h1>

## Code

```
10 '24LEDwithMUSIC
20 PLAY "$T180 O4 CDER CDER GEDCDED2R T360 O5 ER8ER8E2R ER8ER8E2R E.G.C2 D6E2.R8"
30 FOR I=0 TO 69 STEP 6
40 LET [I],50,0,0
50 LET [I+3],0,50,0
60 NEXT
70 WS.LED 24
80 WAIT 30
90 FOR I=0 TO 69 STEP 6
100 LET [I],0,50,0
110 LET [I+3],50,0,0
120 NEXT
130 WS.LED 24
140 WAIT 30
150 GOTO 30
'''
