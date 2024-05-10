---
title: LNAS - Lab 2 Session 2 Report
---

<style>
:root {
    --markdown-font-family: "Times New Roman", Times, serif;
    --markdown-font-size: 10.5pt;
    --vscode-textBlockQuote-border: #9599e1;
}
</style>

<p class="supt1 center">Linear Networks Analysis and Synthesis</p>

# Lab 2. May 2024

<p class="subt2 center">
<strong>FULL NAME</strong>: Alonso Herreros Copete</br>
<strong>NIA</strong>: 100493990
</p>
<p class="subt2 center">
<strong>DATE AND TIME</strong>: 08/05/2024, 13:05 PM</br>
<strong>ROOM</strong>: 4.1.E05
</p>

---

## Session 2

<p class="subt2 center">Design and characterization of a bandpass filter</p>

### 1. AMPLITUDE response of the designed bandpass filter

Obtain the **modulus** of the frequency response of the designed bandpass filter. To do this you must make
measurements with the circuit simulator. The frequencies chosen to characterize the filter should allow to
verify that the filter response in amplitude meets the specifications. Compare the obtained measurements with
the expected theoretical result.

<!--
* [ ] Insert screenshot(s) here 
* [ ] Results, explanations and comments
* [ ] Table/graph of measurements and theoretical values
* [ ] Optional: Insert link to the designed circuit in Falstad (this can be done in all answers)
-->

### 2. PHASE response of the designed bandpass filter

Now make the necessary measurements to obtain the **phase** response, but only of the passband (the center of
the passband and two more frequency points are enough).

<!--
* [ ] Insert screenshot(s) here
* [ ] Results, explanations and comments
* [ ] Table/graph of measurements and theoretical values
-->

### 3. Group delay

Estimate the group delay at the center frequency of the bandpass filter.

<!--
* [ ] Explain the estimation/measurement method
* [ ] Result:
-->

### 4. Effect of noise WITHOUT the bandpass filter

Study the effect of adding noise to the FSK signal in the system with the low pass and high pass filters that
you designed in the first session, but **without** the band-pass filter you just designed (complete the
circuit for this [link](https://tinyurl.com/29qgxltj)):

* Determine, by progressively increasing the amplitude of the noise, what is the maximum noise level at which
  the signal is no longer correctly detected at the node `RX signal`.

    <!--
    * [ ] Insert screenshot(s) here
    * [ ] Result and explanation/comment
    -->

    * Suppose now that you use the envelope of the output of the high pass filter to determine the symbol that
  arrives at it (node `P1`). What would be the maximum noise level at which it would be possible to recover,
  with few errors, the transmitted data?

    <!--
    * [ ] Insert screenshot(s) here
    * [ ] Result and explanation/comment
    -->

    * Suppose now that you use the envelope of the output of the low-pass filter to determine the symbol that
  arrives at it (node P2). What would be the maximum noise level at which it would be possible to recover,
  with few errors, the transmitted data?

    <!--
    * [ ] Insert screenshot(s) here
    * [ ] Result and explanation/comment
    -->

    NOTE: Try to explain the different noise levels obtained

### 5. Effect of noise WITH the bandpass filter
Now add the band pass filter to the system (complete the circuit of this
[link](https://tinyurl.com/2yxxu5f5)):

* What is the delay of the received data signal RX signal with respect to the original **binary signal**?
  Relate the result with the phase response of the bandpass filter studied in sections 2 and 3. Insert
  screenshot(s) here Results and explanations/comments

    <!--
    * [ ] Insert screenshot(s) here
    * [ ] Result and explanation/comment
    -->

* Repeat section 4 and compare the results. Draw conclusions about the effectiveness of the bandpass filter in
  limiting the effect of noise. Insert screenshot(s) here Results and explanations/comments

    <!--
    * [ ] Insert screenshot(s) here
    * [ ] Result and explanation/comment
    -->
