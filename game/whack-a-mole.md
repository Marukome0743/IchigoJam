<h1 align="center">Whack A Mole</h1>

## Code0

```
10 @ARUN:'whack-a-mole
20 POKE #70B,0,0,8,#FF,1,#20,4,3,2,#FF,0,#1F
30 IF I2CW(98,#70B,1,#70C,1)+I2CW(98,#70D,1,#70E,1)+I2CW(98,#70F,1,#710,1)?"E"
40 IF I2CW(98,#711,1,#714,1)+I2CW(98,#712,1,#714,1)+I2CW(98,#713,1,#714,1)?"E"
50 CLS:? "ﾓｸﾞﾗ ﾀﾀｷ　　　　　　　　"
60 PLAY "G":WAIT 60:Y=0:Z=70:LRUN 0,110
70 OUT 0:D=60:N=25:S=0
80 LRUN 1
100 'LCD
110 POKE #700,64,0,2,#C0,57,17,#70,86,#6C,56,12
120 IF I2CW(62,#701,1,#704,5)?"E"
130 IF I2CW(62,#701,1,#709,2)?"E"
140 FOR J = 0 TO 1:IF I2CW(62,#701,1,#702+J,1)?"E"
150 FOR I = 0 TO 15:POKE #700,64+I:IF I2CW(62,#700,1,#900+I+32*J,1)?"E"
160 NEXT:NEXT:LRUN Y,Z
```

## Code1

```
10 Y=1:Z=30:X=RND(7)+1:LC 0,1:? "SCORE : ";S;"       "
20 LRUN 0,140
30 IF N<=0 LRUN 2
40 IF (X%2)=0 OUT 1,0:GOTO 60
50 BEEP 10,5:OUT 1,1:N=N-1
60 IF ((X/2)%2)=0 OUT 2,0:GOTO 80
70 BEEP 12,5:OUT 2,1:N=N-1
80 IF ((X/4)%2)=0 OUT 3,0:GOTO 100
90 BEEP 15,5:OUT 3,1:N=N-1
100 CLT
110 IF (X%2+IN(1))*(X/2%2+IN(2))*(X/4%2+IN(4))=0 OR X=7 AND IN(1)+IN(2)+IN(4) GOTO 180
120 IF (X%2)=0 OR IN(1) GOTO 140
130 OUT 1,0:X=X&6:BEEP 10,20:GSB 200
140 IF ((X/2)%2)=0 OR IN(2) GOTO 160
150 OUT 2,0:X=X&5:BEEP 12,20:GSB 200
160 IF ((X/4)%2)=0 OR IN(4) GOTO 180
170 OUT 3,0:X=X&3:BEEP 15,20:GSB 200
180 IF TICK()<D GOTO 110
190 OUT 0:WAIT D:GOTO 10
200 S=S+1:D=D-2:RTN
```

## Code2

```
10 Y=2:CLS:? "GAME OVER       "
20 PLAY "O4T180":Z=30:LRUN 0,140
30 LED1:LC 0,1
40 IF S<25 GOTO 70
50 ? "ｵﾐｺﾞﾄ!!         "
60 PLAY ">C<BAG>C<BAG>CED":Y=3:Z=10:LRUN 0,140
70 IF S<20 GOTO 120
80 ? "ﾅｶﾅｶ ﾔﾙﾅ!       "
90 PLAY "CEG>C":Z=100:LRUN 0,140
100 GSB 310:WAIT 60:GSB 320:WAIT 60:GSB 330:WAIT 60
110 IF BTN()=0 GOTO 100 ELSE GOTO 200
120 IF S<10 GOTO 160
130 ? "ﾏｱﾏｱ ｶﾅ?        "
140 PLAY "AF":Z=150:LRUN 0,140
150 GSB 310:WAIT 60:GSB 320:GOTO 190
160 ? "ｳｰﾑ ｻﾞﾝﾈﾝ       "
170 PLAY "A":Z=180:LRUN 0,140
180 GSB 330
190 IF BTN()=0 GOTO 190
200 LED0:LRUN 0
300 'COLOR
310 IF I2CW(98,#711,1,#716,1)+I2CW(98,#712,1,#716,1)+I2CW(98,#713,1,#714,1)?"E" ELSE RTN
320 IF I2CW(98,#711,1,#716,1)+I2CW(98,#712,1,#714,1)+I2CW(98,#713,1,#716,1)?"E" ELSE RTN
330 IF I2CW(98,#711,1,#714,1)+I2CW(98,#712,1,#716,1)+I2CW(98,#713,1,#716,1)?"E" ELSE RTN
```

## Code3

```
10 POKE #716,#4F
20 GSB 110:WAIT 60:GSB 120:WAIT 60:GSB 130:WAIT 60:GSB 140:WAIT 60:GSB 150:WAIT 60:GSB 160:WAIT 60:GSB 170:WAIT 60
30 IF BTN()=0 GOTO 20 ELSE LED0:LRUN 0
100 'RAINBOW 
110 IF I2CW(98,#711,1,#714,1)+I2CW(98,#712,1,#715,1)+I2CW(98,#713,1,#715,1)?"E" ELSE RTN
120 IF I2CW(98,#711,1,#714,1)+I2CW(98,#712,1,#716,1)+I2CW(98,#713,1,#715,1)?"E" ELSE RTN
130 IF I2CW(98,#711,1,#714,1)+I2CW(98,#712,1,#714,1)+I2CW(98,#713,1,#715,1)?"E" ELSE RTN
140 IF I2CW(98,#711,1,#715,1)+I2CW(98,#712,1,#714,1)+I2CW(98,#713,1,#715,1)?"E" ELSE RTN
150 IF I2CW(98,#711,1,#715,1)+I2CW(98,#712,1,#715,1)+I2CW(98,#713,1,#714,1)?"E" ELSE RTN
160 IF I2CW(98,#711,1,#715,1)+I2CW(98,#712,1,#716,1)+I2CW(98,#713,1,#714,1)?"E" ELSE RTN
170 IF I2CW(98,#711,1,#714,1)+I2CW(98,#712,1,#715,1)+I2CW(98,#713,1,#714,1)?"E" ELSE RTN
```
