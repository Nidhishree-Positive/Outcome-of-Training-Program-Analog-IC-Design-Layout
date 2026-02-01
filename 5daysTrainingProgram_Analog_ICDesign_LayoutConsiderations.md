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


### Why is BGR So Important in IC Design?

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



<img width="605" height="467" alt="image" src="https://github.com/user-attachments/assets/62e2c40e-8ca6-433f-bec4-c0ec82560e97" />

### Transient anlysis:
<img width="519" height="638" alt="image" src="https://github.com/user-attachments/assets/d4881884-03e5-4b22-95ab-bd814dc625a8" />



### Ac anlysis :
<img width="507" height="654" alt="image" src="https://github.com/user-attachments/assets/90b2816d-b883-4ada-9df6-558d99c0b787" />







-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Day-2

### Topics covered

- Analysis using Cadence for MOSFET-based circuits (single-stage circuits and differential amplifier)

- Symbol creation for a differential amplifier

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------
Building on the previous day’s simple amplifier, the resistive load was replaced with a PMOS load to analyze MOSFET-based active loading and we have used didoe connected model to ensure pmos alwasy is in Saturation region.

<img width="862" height="677" alt="image" src="https://github.com/user-attachments/assets/8e364e12-daf2-41b6-bb75-13cc651299bb" />


#### Transient responce
<img width="489" height="322" alt="image" src="https://github.com/user-attachments/assets/b1e5c15d-f974-4bc0-a993-acd4baa9e780" />


#### DC responce 
<img width="499" height="327" alt="image" src="https://github.com/user-attachments/assets/c148519e-af24-4e11-8c19-db2cd00c9ddc" />


#### AC responce
<img width="481" height="317" alt="image" src="https://github.com/user-attachments/assets/57dec03e-16be-4490-a2ab-8eaf14fb7d9d" />


Before we got vout =0.435v so now our goal is to get vout=0.5v hence by avrying width of pmos we can vary its resistance hence a parametric anlysis is done to obtain the corrsponding for whcih vout is 0.5v
<img width="1000" height="649" alt="image" src="https://github.com/user-attachments/assets/ebc382fb-2c1b-4605-8400-dc83936675f2" />


from above plot we observed for a **w of 1um**we will get nearly 0.5v.






--------------------------------------------------------------------------------------------------------------------------------------------------------------------- 
<img width="729" height="648" alt="image" src="https://github.com/user-attachments/assets/c61cd9a0-43a3-4e0c-ad2a-f58e55d15085" />

In the previous circuit, the diode-connected PMOS was replaced by an externally biased PMOS. Since the PMOS threshold voltage **V_th_p is −561.778 mV** and the source voltage of pmos**V_s_p is 1v = Vdd** thus using this we need to calculte the value of vbias so that ass the circuit will be saturation region 

Thus, to turn on the pmos V_sg_p>|vth_p| 
by substituting the above values we get vg_p=v_bias<0.439

so let's consider vb=0.4v
and run and obtain the region in which each transistors is opearting and wegot to know that both are in rgion-2 whihch is saturation region

<img width="986" height="673" alt="image" src="https://github.com/user-attachments/assets/3efdaab2-6e17-4b1b-b01e-3348b73d0987" />


----------------------------------------------------------------------------------------------------------------------------------------------------------------------
we implemented a simple differentila amplifier
here **v_th_n = 587.807mv and v_th_p=-573.335 mv**
thus lets consider transitor 5(M_5) 
here to turn on M5 V_gs_n5>v_th_n
vg_5 - vs_5 > 587.807mv
here vs_5 =0v
thus vg_5  > 587.807mv

so let us consider **vg_5 = 0.6v = 600 mv**

for vm1 keeping 1.2v we run the schemtaic and except M5 all other are in sub-threshold region and M_5 is in saturaton region  so here we goit v_A which is drain of M_5  as 0.6587v 

for M_3 ,
V_gs_n3 > v_th_n
vg_3 - vs_3 > 587.807mv
here vs_3=v_A = 0.6587v
thus vg_3  > 1.2466 v ,so consider  vg_3 = 1.3v.
<img width="644" height="475" alt="image" src="https://github.com/user-attachments/assets/a0d0f3d5-fd1a-4e00-aef6-5101b1517472" />
##### Transient & AC analysis 
<img width="1600" height="688" alt="image" src="https://github.com/user-attachments/assets/5376eeec-027f-4809-9e75-d0a832bb52bd" />

--------------------------------------------------------------------------------------------------------------------------------------------------------------------
## Creation of Symbol

The designed differential amplifier was converted into a symbol and reused at the top level. The same input signals and biasing conditions as the original differential amplifier were applied, and the simulation results obtained using the symbol matched the original circuit behavior, thereby validating the symbol creation.


First remove power supply and input and output connect pin to them 
<img width="797" height="624" alt="image" src="https://github.com/user-attachments/assets/bac183a4-4f6d-4d36-98e2-80f695a09233" />

then go to create then cell view in that from cell view and create a symbol and provide the shape you want 
<img width="1201" height="657" alt="image" src="https://github.com/user-attachments/assets/2ae4fd6e-9d4d-4168-b5a9-87db7ecdb501" />

Above circuit is tehe differerntial amplififer we implemented before but we haev used symbol 
##### Transient & AC analysis 

<img width="1600" height="679" alt="image" src="https://github.com/user-attachments/assets/642b82a4-aa15-444b-83a4-17a789d07263" />

As we can see the simulation output is same as our previous differential amplifier cicruit .



----------------------------------------------------------------------------------------------------------------------------------------------------------------------
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
 
<img width="992" height="826" alt="image" src="https://github.com/user-attachments/assets/bc532158-8410-4305-9176-12b9af4767cb" />

 Now we get,   **deriv(vref)=-19.66 uV/celcius** 
 
 
### Day-4 & 5  : IC Layout Design in Cadence Virtuoso

On Day-4, we explored IC Layout Design using Cadence Virtuoso. The session began with an overview of the complete IC design lifecycle, explaining how a circuit evolves from specification to fabrication. The importance of layout in determining performance, reliability, and manufacturability was emphasized.

We learned the key steps in the IC layout flow:

**Floorplanning** – Deciding the placement of major blocks and devices to optimize area, symmetry, and signal flow.

**Placement** – Arranging transistors and components while considering matching, parasitics, and design rules.

**Routing** – Creating interconnections between devices using metal layers, while minimizing resistance, capacitance, and interference.

**DRC (Design Rule Check)** – Ensuring the layout follows foundry design rules.

**LVS (Layout vs Schematic)** – Verifying that the layout matches the schematic electrically.

This session highlighted how layout decisions directly impact analog circuit performance, particularly in terms of matching, noise, and parasitic effects, providing a strong foundation for practical layout implementation.




#### OP-AMP Layout

We implemented the layout for the op-amp designed earlier, consisting of:

**Current Source**: PMOS

**Differential Pair**: NMOS

**Tail Current Source**: PMOS

###### Floorplanning

The layout was divided into three functional regions corresponding to the blocks above.

Power and signal flow were planned vertically to maintain symmetry and simplify routing.

Spacing and guard regions were included to reduce noise coupling.

###### Placement

Differential input transistors are placed symmetrically in the lower section, using common-centroid-like placement to improve matching.

Biasing and current mirror circuits are placed centrally to ensure equal current distribution.

Load and output stage transistors are positioned in the upper section for clean signal routing.

Identical devices are arranged in parallel and mirrored structures to reduce process-induced mismatch.

<img width="538" height="568" alt="Op-amp Placement" src="https://github.com/user-attachments/assets/68752275-65da-49dd-9dd4-6bd792aa3fe7" />

###### DRC Errors

After running DRC, the following errors were detected:

<img width="1022" height="498" alt="DRC Errors" src="https://github.com/user-attachments/assets/7b439276-53be-4b3b-8359-9e8a7eac5b7d" />

###### Routing

Power lines (VDD) use wider metal tracks to reduce IR drop.

Sensitive input signals (Vin+ / Vin−) are routed symmetrically and kept short to minimize parasitic capacitance.

Higher metal layers are used for longer interconnections, while lower layers are used for local connections.

###### Layout Considerations

Matching-critical devices share the same orientation, well, and surroundings.

Dummy devices and well ties are used to improve uniformity.

The layout is prepared to pass DRC and LVS, ensuring physical and electrical correctness.

This layout demonstrates that proper floorplanning, symmetric placement, and careful routing are essential for achieving high-performance analog designs, especially in op-amp circuits.















