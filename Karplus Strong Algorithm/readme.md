## Explanation of the Code

The Karplus-Strong algorithm is a simple digital feedback loop with an internal buffer of M samples. The buffer is filled with a set of initial values and the loop, when running, produces an arbitrarily long output signal. The K-S loop can be used to synthesize interesting musical sounds.

I started with a basic implementation of K-S loop, initialized the libraries, added the sampling rate. 

With this sampling rate, since the period of the generated signal is equal to the length of the inital buffer, we will be able to compute the fundamental frequency of the resulting sound. For instance, if we init the K-S algorithm with a vector of 50 values, the buffer will fit  16000/50=320 times in a second's worth of samples or, in other words, the resulting frequency will be 320Hz, which corresponds roughly to a E4 on a piano. The cool thing about K-S is that we can use pretty much anything we want; as a matter of fact, using random values will give us a totally fine sound.

From the signal processing point of view, we can describe the system with the following block diagram:

<p align="left">
  <img width="400" height="300" src="sdw.PNG">
</p>

The output can be expressed as: 

y[n]=α^⌊n/M⌋x[n mod M]

By setting α to a value close to but less that one, I can introuce a decay in the note that produces guitar-like sounds. The decay envelope is dependent on both α and M or, in other words, the higher the pitch of the note, the faster its decay.
Much has been written about the chord (which, in fact, is made up of 2 guitars, one of which a 12-string, a piano and a bass) but to keep things simple, we will accept the most prevalent thesis which states that the notes are D3, F3, G3, F4, A4, C5 and G5. To give it a "wider" feeling I added another D2 below.

In Western music, where equal temperament is used, A4 is the reference pitch at a frequency at 440Hz. All other notes can be computed using the formula  f(n)=A4×2^n/12 where  nn  is the number of half-tones between A4 and the desired note. The exponent  nn  is positive if the note is above A4 and negative otherwise.

Each note is generated using a separate Karplus-Strong algorithm. I tried to mix the different "instruments" by assigning a different gain to each note. Also, we sustain Paul's D note on the bass a bit longer by changing the corresponding decay factor.

## Result

The sounds generated are very close to the sound of actual instrumental chords. This can be used for making Karplus synthesizer.
