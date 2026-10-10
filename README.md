# Keyboard Workshop (Deep Version)

A typing n-back trainer. Single HTML file, no build step.

Built from the **Brain Workshop 2.0** web port (`goodstuff2/brain-workshop-web`) — same n-back engine, same
difficulty progression, same look — but the A/L response is gone.

## The change

Brain Workshop asks a yes/no question: *does the stimulus match N back?* → press A (position) or L (sound).

**Keyboard Workshop asks you to produce the answer.** A letter is shown on screen and spoken. On every
scored trial you must **type the letter that was shown N trials back**. There is no "match" key to press:
you have to hold the letter in memory and reproduce it.

```
trial:   1    2    3    4    5
letter:  C    Q    R    S    T
                    ▲
        N=2 → at trial 3 you type Q
```

- Input: your keyboard (`C H K L Q R S T`) or the on-screen letter pad.
- One letter per trial. Window closes at the end of the trial — late keys do not count.
- Green = right. Red = wrong, and the correct key is marked gold-dashed. Same on a miss.
- First N trials of a session are warm-up: the letter is shown, input is blocked, nothing is scored.

## Carried over from Brain Workshop 2.0

- Letter pool: 8 sounds — C H K L Q R S T (BW 2.0's default set, GPL audio).
- Lures: ~1/8 of scored trials the current letter equals the N-back letter, ~1/8 it is a near miss
  (one step early or late). These are what make recall fail.
- Trial length: 3.0 s (N≤3), 3.5 s (N 4–6), 4.0 s (N 7–9).
- Session = 20 + N² trials.
- Advance at ≥80%. Three sessions in a row <50% drops one level. Minimum N=1.
- Progress, settings and session history saved in localStorage.

## Run

Open `index.html` in a browser. Serve the folder if you want the letter sounds (`sounds/*.wav`):

```
python3 -m http.server 8000    # then http://localhost:8000/
```

## Credits

Letter sounds from Brain Workshop (GPL-2.0-or-later, Paul Hoskinson, Samantha McVey and contributors,
https://github.com/brain-workshop/brainworkshop). Engine ported from Brain Workshop 2.0.
