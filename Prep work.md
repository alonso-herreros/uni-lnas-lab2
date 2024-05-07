---
title: LNAS - Lab 2 Preliminary work
---

<style>
:root {
    --markdown-font-family: "Times New Roman", Times, serif;
    --markdown-font-size: 10.5pt;
    --vscode-textBlockQuote-border: #9599e1;
}
</style>

<p class="supt1 center">Linear Networks Analysis and Synthesis</p>

# Lab 2 Preliminary Theoretical Work

<p class="subt2 center">
Academic year 2023-2024
</p>
<p class="subt2 center">
Alonso Herreros Copete</br>
NIA: 100493990
</p>

---

## Figures

<a name="figure1"></a>
![FSK with low pass filter](figures/fig_1.png)
<p class="caption center">Figure 1: FSK with a low pass filter to discriminate frequencies</p>

<a name="figure2"></a>
![FSK with high pass filter](figures/fig_2.png)
<p class="caption center">Figure 2: FSK with a high pass filter to discriminate frequencies</p>

<hr class="pagebreak">

## Session 1

<p class="subt2 center">Response of the original low pass filter and high pass filter</p>

### 1.1. S1 Preparatory Homework: Characterization of the initial filters

1. Show that the impedance *seen* on the left by the low pass filter in the following figure is 50 Ω. That is,
   verify that the impedance of the following circuit is 50 Ω.

   ![Amplifier circuit with OpAmp](figures/fig1.1.1.1.png)

    What is the insertion *gain* (the inverse of the insertion loss) of the block marked *Amplifier* when we
    connect a $50$ Ω resistor at its output (node `Out`)? Write your answer in dB.

    > The amplifier is set up with *negative feedback*, creating a *virtual short cirtuit* between its
    > positive and negative terminals. We can use one mesh equation and Ohm's Law to find the impedance seen
    > by the low pass filter.
    >
    > $$\\
    > V_g = Iᵢₙ \cdot (R_g + R₁) ⟹ Iᵢₙ = \frac{V_g}{R_g + R₁}\\
    > Vᵢₙ = V_g - Iᵢₙ R_g = Iᵢₙ R₁ ⟹ \frac{Vᵢₙ}{Iᵢₙ} = R₁ \\
    > \boxed{Zᵢₙ = \frac{Vᵢₙ}{Iᵢₙ} = R₁ = 50 Ω}
    > $$
    >
    > Then, we can find the insertion gain by calculating ratio of the power at the output of the amplifier to
    > the power transmitted without the amplifier. First, we'll find the output voltage.
    >
    > $$\\
    > Iᵢₙ = \frac{Vᵢₙ}{R_g + R₁} \\
    > Vₒᵤₜ = Iᵢₙ R₁ -Iᵢₙ (R₂ + R₃) = \frac{R₁ - R₂ - R₃}{R_g + R₁} Vᵢₙ
    > $$
    >
    > Then, the power at the output and the power without the amplifier.
    >
    > $$\\
    > P₂ = \frac{|Vₒᵤₜ|^2}{R_L} = \frac{1}{R_L} \left(\frac{R₁ - R₂ - R₃}{R_g + R₁} Vᵢₙ\right)² \\
    > P₂₀ = \frac{|V₂₀|^2}{R_L} = \frac{1}{R_L} \left(\frac{R_g}{R_g + R_L} Vᵢₙ\right)² \\
    > $$
    >
    > With that, we can find the insertion gain, which is the inverse of the insertion loss.
    >
    > $$\\
    > G = \frac{P₂}{P₂₀} = \frac{(R_g + R_L)(R₁ - R₂ - R₃)}{(R_g + R₁) R_g} = - 100
    > $$
    >
    > Finally, we can convert it to decibels the usual way.
    >
    > $$\\
    > \underline {G_{dB}} = 10 \log |G| = \boxed{20 \text{ dB}}
    > $$

2. Obtain, by means of circuit analysis, the following properties of the low pass filter used in the circuit
    shown in the [Figure 1](#figure1):

    * Filter order.
    * Transfer function.
    * Frequency at which the filter attenuates $3$ dB.
    * Atenuación del filtro a frecuencias $f_1 = 800 \text{ Hz}$ and $f_2 = 1200 \text{ Hz}$.

    NOTE: Be aware that the filter is fed on the left side by a source with an internal impedance of $50$ Ω
    (the output impedance of the amplifier), and is loaded on its right by another impedance of $50$ Ω. That
    is, the analysis is that of the following circuit:

    ![Low-pass filter](figures/fig1.1.2.1.png)

    > From simple observation that there is only one reactive element in the filter, we can assert that the
    > filter order is $\boxed{n = 1}$.
    >
    > The transfer function can be obtained using node analysis.
    >
    > $$\\
    > \frac{Vᵢₙ - V_L}{R_3} = \frac{V_L}{R_L} + sC V_L
    > ⟹ V_L = \frac{Vᵢₙ}{R₃(\frac{1}{R₃} + \frac{1}{R_L} + sC)} ⟹ \\
    > ⟹ \boxed{H(s) = 2 \frac{V_L}{Vᵢₙ} = \frac{2}{R₃(\frac1{R₃} + \frac1{R_L}+sC)} = \frac{6250}{6250+s}}
    > $$
    >
    > To find at which frequency the filter attenuates $3$ dB, we'll use the transfer function in terms of
    > frequency.
    >
    > $$\\
    > α = -10\log |H(jω)|² = 3 \text{ dB} ⟹ |H(jω)|² = 10^{-3/10} ⟹ \\
    > ⟹ \left|\frac{2}{R₃(\frac1{R₃} + \frac1{R_L}+j2πfC)}\right|² = 10^{-3/10} ⟹ \\
    > ⟹ \boxed{f = \frac{\sqrt{4⋅10^{0.3}R₃⁻² - \left(R₃⁻¹ + R_L⁻¹\right)²}}{2πC} = 992.36\text{ [Hz]}}
    > $$
    >
    > <!--
    > $$
    > 2² = 10^{-3/10} R₃² \left(\left(\frac{1}{R₃} + \frac{1}{R_L}\right)² + (2πC)²f²\right) \\
    > \frac{4⋅10^{3/10}}{R₃²} - \left(\frac{1}{R₃} + \frac{1}{R_L}\right)² = (2πC)²f² \\
    > f = \sqrt{\frac{\frac{4⋅10^{3/10}}{R₃²} - \left(\frac{1}{R₃} + \frac{1}{R_L}\right)²}{4π²C²}} = 992.36
    > $$
    > -->
    >
    > The attenuation at the given frequencies can be found by evaluating the expression of the attenuation at
    > those frequencies
    >
    > $$\\
    > α = -10\log |H(j2πf)|² = -10\log \left|\frac{2}{1 + R₃(R_L⁻¹ + j2πfC)}\right|² \\
    > \boxed{\begin{aligned}
    >     α₁ = α|_{f=f₁} = 2.16 \text{ [dB]} \\
    >     α₂ = α|_{f=f₂} = 3.90 \text{ [dB]}
    > \end{aligned}}
    > $$

3. Repeat the previous item for the high pass filter in the circuit of Figure 2.

    > Since there is still only one reactive element, the filter order is still $\boxed{n = 1}$.
    >
    > The high pass filter can be analyzed easily as a voltage divider.
    >
    > $$\\
    > V_L = \frac{R_L}{R₃ + R_L + \frac{1}{sC}} Vᵢₙ = \frac{1}{1 + R_L⁻¹ (R₃ + s⁻¹C⁻¹)} Vᵢₙ ⟹ \\
    > ⟹ \boxed{H(s) = 2⋅ \frac{V_L}{Vᵢₙ} = \frac{2}{1 + R_L⁻¹ (R₃ + s⁻¹C⁻¹)} = \frac{1}{1 + 6250 s⁻¹}}
    > $$
    >
    > We'll find the frequency at which the filter attenuates $3$ dB ($f_c$) the same way.
    >
    > $$\\
    > α_c = -10\log |H(j2πf_c)|² = 3 \text{ dB} ⟹ |H(j2πf_c)|² = 10^{-3/10} ⟹ \\
    > ⟹ \left|\frac{2}{1 + R_L⁻¹ (R₃ + (j2πf_c C)⁻¹)}\right|² = 10^{-3/10} ⟹ \\
    > ⟹ \boxed{f_c = \frac1{2πR_L C\sqrt{4⋅10^{0.3} - (1 + R_L⁻¹R₃)²}} = 997.08 \text{ [Hz]}} \\
    > $$
    >
    > <!-- 
    > $$\\
    > 2²⋅10^{0.3} = (1 + R_L⁻¹R₃)² + (2πf_c R_L C)⁻² \\
    > 4⋅10^{0.3} - (1 + R_L⁻¹R₃)² = (2πf_c R_L C)⁻² \\
    > 2πf_c R_L C = \frac1{\sqrt{4⋅10^{0.3} - (1 + R_L⁻¹R₃)²}} \\
    > f_c = \frac1{2πR_L C\sqrt{2²⋅10^{0.3} - (1 + R_L⁻¹R₃)²}} \\
    > $$
    > -->
    >
    > And finally, we'll evaluate the attenuation at the given frequencies.
    >
    > $$
    > α = -10\log |H(j2πf)|² = -10\log \left|\frac{2}{1 + R_L⁻¹ (R₃ + (j2πf_c C)⁻¹)}\right|² \\
    > \boxed{\begin{aligned}
    >     α₁ &= α|_{f=f₁=800 \text{ Hz}} &= 4.06 \text{ [dB]} \\
    >     α₂ &= α|_{f=f₂=1200 \text{ Hz}} &= 2.27 \text{ [dB]}
    > \end{aligned}}
    > $$

4. It is desired to replace the previous filter with a more selective filter. For the new filters, the
   attenuation at one the frequencies must be less than $0.5$ dB, and the attenuation at the other frequency
   must be more then $10$ dB. Plot the specification mask of the new filters and then overlay on it the
   response of the initial filters (the ones obtained in the previous items). Use a computer tool that you can
   use during the laboratory session to create this graph. (Matlab, Python, Desmos, Geogebra,...)

    During the laboratory session, you will design a low-pass filter and a high-pass filter that meets these
    specifications, characterise it experimentally, and verify that these specifica- tions are indeed met.
