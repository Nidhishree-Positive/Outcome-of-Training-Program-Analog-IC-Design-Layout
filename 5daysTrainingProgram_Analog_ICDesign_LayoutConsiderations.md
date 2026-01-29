# Day 1



## Topics Covered

- Introduction to the 5 Days Training Program on Analog IC Design & Layout Considerations

- Overview of Analog, Digital, and Mixed-Signal IC Design flow

- Basics of Bandgap Reference (BGR) circuits

- Importance and applications of BGR circuits

- Introduction to the Cadence Virtuoso tool

- on exposure to the Cadence design environment

----------------------------------------------------------------------------------------------------------------------------------------------------------------------

In the morning session, we were introduced to Analog design, Digital design, and Mixed-Signal design, with a primary focus on Analog IC Design. The session mainly emphasized the introduction and basics of Bandgap Reference (BGR) circuits, their purpose, and their importance in analog IC applications.



### Introduction to basic BGR circuits

Every electronic system—whether it is a mobile phone, a medical device, an automotive controller, or a satellite—depends on stable voltages and currents to function correctly. However, real-world conditions are never stable. Supply voltage fluctuates, temperature changes continuously, and semiconductor device parameters drift due to process variations and aging.

If a circuit directly relies on the power supply or raw transistor parameters, its performance becomes unpredictable. This is where a reference circuit becomes essential. A reference circuit provides a fixed, known voltage or current that remains almost constant regardless of:

- ****Power supply variations****

- ****Temperature changes****

- ****Manufacturing (process) variations****

Among all reference circuits, the ****Bandgap Reference (BGR)**** is the most widely used and trusted solution in integrated circuits.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------



### What Is a Bandgap Reference (BGR)?

A Bandgap Voltage Reference (BGR) is a precision analog circuit that generates a fixed and stable reference voltage, which remains nearly constant despite variations in power supply, temperature, and circuit loading conditions

By exploiting the temperature-dependent characteristics of semiconductor devices, the BGR achieves excellent immunity to environmental and electrical variations, making it one of the most indispensable reference circuits in integrated circuit design.


----------------------------------------------------------------------------------------------------------------------------------------------------------------------


### Why Is It Called a “Bandgap” Reference?

The name Bandgap Reference comes from a fundamental property of semiconductor physics: the bandgap energy of silicon.

****Silicon has a bandgap energy of approximately 1.12 eV at room temperature.****

When expressed ****in voltage form&****, this energy corresponds to about ****1.2 V****.

In a BGR circuit, the reference voltage is intentionally designed to be close to this value. Although the circuit does not directly measure the bandgap energy, its output voltage is numerically related to it. Hence, the term “bandgap reference.”

This connection gives the BGR a strong physical foundation, making it inherently stable and repeatable across different IC fabrication processes.


----------------------------------------------------------------------------------------------------------------------------------------------------------------------


### Why Is BGR So Important in IC Design?

The Bandgap Reference acts as the heart of an integrated circuit. Once a stable reference is available, designers can build:

- Voltage regulators (LDOs)

- Analog-to-digital converters (ADCs)

- Digital-to-analog converters (DACs)

- Phase-locked loops (PLLs)

- Operational amplifiers and comparators

Without a reliable BGR, achieving accuracy, repeatability, and robustness in modern ICs would be nearly impossible.

In fact, most high-performance chips contain multiple bandgap references, each optimized for different accuracy, power, or area requirements.



## Temperature-Independent Reference

Reference voltages or currents with minimal dependence on temperature are of great importance in analog and mixed-signal circuits, as device parameters vary significantly with temperature. A temperature-independent reference ensures stable and predictable circuit performance over a wide operating temperature range.process parameters vary with temperature, if a reference is temperature-independent, then
it is usually process-independent as well

The fundamental principle behind achieving temperature independence is the combination of two quantities with opposite temperature coefficients. One quantity increases with temperature, exhibiting a positive temperature coefficient (PTAT), while the other decreases with temperature, exhibiting a negative temperature coefficient (CTAT). By properly scaling and summing these two components, their temperature variations cancel each other, resulting in a reference voltage or current with an approximately zero temperature coefficient.

For example, for two voltages V1 and V2 that vary in opposite directions with temperature,
we choose α1 and α2 such that α1*∂V1/∂T + α2*∂V2/∂T = 0, obtaining a reference voltage,
VREF = α1*V1 + α2*V2, with zero TC(Temperature coefficient).

<img width="943" height="227" alt="image" src="https://github.com/user-attachments/assets/e680880e-58ab-4951-bea3-d7b3d2474825" />

**Key observation:**
Semiconductor devices exhibit electrical quantities whose values change with temperature.

Why BJTs are important:
The characteristics of BJTs provide well-defined temperature-dependent quantities with:

- Positive temperature coefficient

- Negative temperature coefficient

PTAT quantity (Positive TC):

The term kT/q (v_T) increases with temperature  - **Hence it is PTAT (Proportional To Absolute Temperature)**

In practice, **PTAT voltage is obtained using ΔV_BE between two BJTs**

CTAT quantity (Negative TC):

**The base–emitter voltage V_BE of a BJT decreases as temperature increases**

Hence **it is CTAT (Complementary To Absolute Temperature)**

**Core idea:**
By adding a scaled PTAT voltage to a CTAT voltage, their temperature variations cancel each other.

**Result:**
The combined voltage exhibits an approximately zero temperature coefficient, forming a temperature-independent voltage reference.

<img width="810" height="598" alt="image" src="https://github.com/user-attachments/assets/50e019fa-edd9-445f-a389-1ff08d382e3a" />



With the negative- and positive-TC voltages obtained, we can now develop a
reference (VREF ) that has a nominally zero temperature coefficient.,
### V_REF = α1 *VBE + α2(VT * ln(n))







----------------------------------------------------------------------------------------------------------------------------------------------------------------------








### Other Devices That Exhibit PTAT / CTAT Behavior

BJTs are not the only devices, but they are the most reliable. Other options include:

1. **MOSFETs in Weak (Subthreshold) Region**

Drain current has an exponential dependence on V_GS, similar to BJTs

Can generate: PTAT voltages&CTAT voltages

Used in MOS-only or ultra-low-power references - Less accurate than BJTs

2. **Resistors**

Some resistors have positive or negative temperature coefficients

Can assist in temperature compensation - Large process variation → not precise alone

3. **Diodes**

PN-junction diodes behave similarly to BJT base–emitter junctions

Exhibit CTAT behavior - Less controllable than BJTs




Bandgap Reference (BGR) circuits are implemented using different architectures based on design requirements such as supply voltage, power consumption, accuracy, temperature coefficient, and process technology. Accordingly, various BGR architectures like conventional BJT-based bandgap references, CMOS bandgap references, sub-bandgap (low-voltage) references, curvature-compensated bandgaps, and resistor-less bandgaps are used. The choice of architecture depends on the target application and performance constraints.






--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------




In the afternoon session a basic overview of the Cadence Virtuoso environment was provided, followed by an initial hands-on session to understand the tool interface and basic circuit implementation.

We started with a simple resistor-MOSFET circuit and created its schematic in Cadence Virtuoso. Basic simulations including DC, Transient, and AC analyses were performed to understand circuit behavior and gain familiarity with the tool interface.



<img width="542" height="468" alt="image" src="https://github.com/user-attachments/assets/d19ca60e-75a2-47a5-be7f-c568bc0c00aa" />









# Day - 3

### Topics covered 

- Measurements in Cadence
- Performing calculations in Cadence
- Analysis of a few BGR architectures
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
####  Circuit  Measurement in cadence


In analog IC design, circuit measurements such as **Signal-to-Noise Ratio (SNR), Spurious-Free Dynamic Range (SFDR), and Total Harmonic Distortion (THD)** are critical to evaluate the performance of a circuit. These metrics quantify how well a circuit preserves the input signal while minimizing noise, distortion, and spurious components. The input signal plays a major role in these measurements—its amplitude, frequency, and waveform directly affect the observed performance. Such analysis ensures circuits are linear, noise-resilient, and suitable for their intended applications, with typical target ranges like **SNR > 60 dB, SFDR > 70–80 dB, and THD < 1%** depending on design requirements, though exact values depend on the application and design specifications. Proper measurement and analysis ensure that the circuit meets its intended performance in real-world operation.



<img width="1600" height="900" alt="measurementSpectrumCRT4SYM" src="https://github.com/user-attachments/assets/87c504e2-bfd6-4842-9aac-d39eb74c40ac" />

this is the spectrum of ota being designed in the previous session and in the outputs we can observe the different measurement at output panel 

----------------------------------------------------------------------------------------------------------------------------------------------------------------------
####  Calculator Performance in Cadence


In Cadence, the calculator (also called the Calculator Window) is used to compute and analyze custom expressions based on simulation results. Designers can calculate ratios, sums, differences, derivatives, integrals, or any mathematical function of node voltages, currents, or simulation outputs. For example:

Expression evaluation: V(out)/V(in) to get gain

Derivative: d(V(out))/dt to get slew rate or transient slope

Other operations: FFT, RMS, min/max, or combining multiple measurements

This feature allows designers to extract precise metrics from simulations, verify design behavior.Basically, the Cadence calculator is a versatile tool to extract any performance metric or derived quantity from your simulation, making it essential for detailed circuit analysis.

## BGR basic architecture design and anlysis

<img width="659" height="602" alt="image" src="https://github.com/user-attachments/assets/ce7dabaa-0499-42b5-9160-2d40a9a4b82e" />

#### Basic BJT-based temperature-independent bandgap reference, often called a first-order or classic BGR

 Here
 #### Vref = V_BE2 + V_T* ln(n)  *(1+R_2/R_3) - (1)

let R_1=R_2=10k ohm

**For zero temperature coefficient (zero TC)  ln(n) * (1+R_2/R_3) = 17.2**

for **n=10**, **R_2=10k ohm**

(1+10*10^3/R_3) = 17.2/ln(10)
**R_3= 1.545 k ohm**


Thus we have designed for the basic BGR circuit 


differentiate the equation (1) with respect to temperature ,we get

deriv(vref) = deriv(V_BE2) + deriv(V_T* ln(n) ) *(1+R_2/R_3)
deriv(vref) = deriv(CTAT) + deriv(PTAT) *(1+R_2/R_3)

using the cademce calculator we have obtain the derivative of  PTAT and derivative of CTAT
deriv(CTAT) = -1.71*10^-3 v/celcius
deriv(PTAT) = 202.2*10^-6 v/celcius

<img width="505" height="631" alt="image" src="https://github.com/user-attachments/assets/c2eac4e5-e724-46e7-993d-8bd90cd2ff59" />


for **R_3= 1.545k ohm**, **R_2=10k ohm**
we get deriv(vref)= -1.9906 *10^-6

so we need to design more accurate one by varying (1+R_2/R_3)

so to make deriv(vref) = 0
 0 = deriv(CTAT) + deriv(PTAT) *(1+R_2/R_3)
 0= -1.71*10^-3 + 202.2*10^-6 *(1+R_2/R_3)
 (1+R_2/R_3) = 8.4569
 let keep R_2=10k ohm itself
 then **R_3= 1.34102 k ohm **

 Now we get,   **deriv(vref)=-19.66 uV/celcius**
 




 

























