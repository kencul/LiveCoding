# Live Coding Week 2 Ken Kobayashi

## Knotts Changing Response

# Things I learned
1. #Occupy is a radical democratic movment that employs the internet to drive and disperse radical movments while avoiding govenment intervention
2. Multiplayer instruments allow anyone to control any other person's instrument, allowing for more creativity and interaction between players not possible without network music groups.

# Things I knew
1. A symphony orchestra has very little player autonomy, while string quartets require a lot more player autonomy.
2. Music ensembles can easily be compared to political structures, and the power balance between the state and the people can vary.

# Estuary

1. Trying a subtly weird time signiture and the random silence
```
stack[
s "bd ~7 sd ~6",
s "hhZ`*15?"
]
```

2. Making the kick and snare more intersting with a snare roll and ht to fill space
``` 
stack[
s "bd ~6 [ ~ sd*2] sd ht ~5",
s "<hc ho>*15?" 
] 
```

3. The randomness with the pipe sounds way better
```
stack[
s "bd ~6 [ ~ sd*2] sd ht ~5",
s "[hc | ho]*15?" 
] 
```

4. Using paranthesis to make stuttery claps in the time signiture polyrythmically
```
stack[
s "bd ~6 [ ~ sd*2] sd ht ~5",
s "[hc | ho]*15?",
s "[cp*2 ~](3, 15)"
]
```

5. Put the claps into the curly brackets with the first line, and used the paranthesis instead for a "pitch control" and created a unique clap sound by playing the clap sound twice really fast
```
stack[
s "{bd ~6 [~ sd*2 sd ht ~5, [cp*2] (1, 633) ~ ~}",
s "[hc | ho]*15?"
]
```

6. Added a low tom into the basic groove and made the snare roll, high tom and low tom play once every few cycles to create change. Some silence was removed accidentally so now its in 11/8
```
stack[
s "{bd ~6 [~ sd*2]/2 sd ht/3 lt/5, [cp*2] (1, 633) ~ ~}",
s "[hc | ho]*15?"
]
```

7. Adjusted hats to the new time signature and double "?" to make the resolution of the beats higher but not as frequent
```
stack[
s "{bd ~6 [~ sd*2]/2 sd ht/3 lt/5, [cp*2] (1, 633) ~ ~}",
s "[hc? | ho?]*22?"
]
````


stack[
slow 2 $ s "stab*24?" # n (irand 25)  # pan (sine*0.5+0.25),
s "808 ~ 808 ~ 808 ~ 808 ~ 808 ~ 808 ~ 808 ~ 808 ~" # n (irand 7)
] # silence