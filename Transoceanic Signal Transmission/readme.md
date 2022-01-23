<div align="center">

  <h1 align="center">TRANSOCEANIC SIGNAL TRANSMISSION</h1>

</div>

## Explanation of the code

We will consider the case of transmission over a long (e.g. transoceanic) cable in which several repeaters are used to compensate for the attenuation introduced by the transmission.

If each cable segment introduces an attenuation of  1/G1/G , we can recover the original amplitude by boosting the signal with a repeater with gain  GG . However, if the signal has accumulated additive noise, the noise will be amplified as well so that, after  NN  repeaters, the noise will have been amplified  NN  times:

**x̂ N(t)=x(t)+NGσ(t)**
 
If we use a digital signal, on the other hand, we can threshold the signal after each repeater and virtually eliminate the noise at each stage, so that even after several repeaters the trasmission is still noise-free.

