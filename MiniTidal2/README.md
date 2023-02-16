# Live Coding Week 3 Ken Kobayashi

## Code
~~~
stack[
s "808bd ~ ~ 808bd*6 808bd ~" # n "1 2 3" #gain 0.8,
every 3 (fast 2) $ s "coins*4 [coins*4|coins*4|coins*8] [coins*4|coins*4|coins*3]" # pan 1 #gain 0.8 #speed 1.1,
every 3 (fast 2) $ s "coins*4 [coins*4|coins*4|coins*8] [coins*4|coins*4|coins*3]" # pan 0 #gain 0.8 #speed 0.9,
s "[metal:0 metal:1 metal:2|metal:3 metal:2 metal:1|metal:0 metal:2 metal:4]"  # gain 0.7
]
~~~

This patch has a 808 bass drum part that has a little roll, and uses different samples for hits.
2nd it has hi hats that have a stero effect through detuned, panned duplicates, which use randomization and double time to do cicada hi hat rolls.
Finally a simple melody line with a pool of 3 choices played with a simple plucky synth.


## Issues

### *Choosing a sample number with #n was acting weird when putting in numbers out of order.*

- I shifted around the order and the numbers until it was bearable

### *Switching from #n to specifying each note number next to the sample name shifted all the notes up one step*

- The #n notation is 1 indexed and the : notation is 0 indexed.
