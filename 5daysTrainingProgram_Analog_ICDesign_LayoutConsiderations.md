# Day 1



## Topics Covered

- Introduction to the 5 Days Training Program on Analog IC Design & Layout Considerations

- Overview of Analog, Digital, and Mixed-Signal IC Design flow

- Basics of Bandgap Reference (BGR) circuits

- Importance and applications of BGR circuits

- Introduction to the Cadence Virtuoso tool

- -on exposure to the Cadence design environment



In the morning session, we were introduced to Analog design, Digital design, and Mixed-Signal design, with a primary focus on Analog IC Design. The session mainly emphasized the introduction and basics of Bandgap Reference (BGR) circuits, their purpose, and their importance in analog IC applications.



### Introduction to basic BGR circuits

Every electronic system—whether it is a mobile phone, a medical device, an automotive controller, or a satellite—depends on stable voltages and currents to function correctly. However, real-world conditions are never stable. Supply voltage fluctuates, temperature changes continuously, and semiconductor device parameters drift due to process variations and aging.

If a circuit directly relies on the power supply or raw transistor parameters, its performance becomes unpredictable. This is where a reference circuit becomes essential. A reference circuit provides a fixed, known voltage or current that remains almost constant regardless of:

- ****Power supply variations****

- ****Temperature changes****

- ****Manufacturing (process) variations****

Among all reference circuits, the ****Bandgap Reference (BGR)**** is the most widely used and trusted solution in integrated circuits.





### What Is a Bandgap Reference (BGR)?

A Bandgap Voltage Reference (BGR) is a precision analog circuit that generates a fixed and stable reference voltage, which remains nearly constant despite variations in power supply, temperature, and circuit loading conditions

By exploiting the temperature-dependent characteristics of semiconductor devices, the BGR achieves excellent immunity to environmental and electrical variations, making it one of the most indispensable reference circuits in integrated circuit design.





### Why Is It Called a “Bandgap” Reference?

The name Bandgap Reference comes from a fundamental property of semiconductor physics: the bandgap energy of silicon.

****Silicon has a bandgap energy of approximately 1.12 eV at room temperature.****

When expressed ****in voltage form&****, this energy corresponds to about ****1.2 V****.

In a BGR circuit, the reference voltage is intentionally designed to be close to this value. Although the circuit does not directly measure the bandgap energy, its output voltage is numerically related to it. Hence, the term “bandgap reference.”

This connection gives the BGR a strong physical foundation, making it inherently stable and repeatable across different IC fabrication processes.





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

Core idea:
By adding a scaled PTAT voltage to a CTAT voltage, their temperature variations cancel each other.

Result:
The combined voltage exhibits an approximately zero temperature coefficient, forming a temperature-independent voltage reference.


With the negative- and positive-TC voltages obtained, we can now develop a
reference (VREF ) that has a nominally zero temperature coefficient.,
### V_REF = α1 *VBE + α2(VT * ln(n))






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












In the afternoon session a basic overview of the Cadence Virtuoso environment was provided, followed by an initial hands-on session to understand the tool interface and basic circuit implementation.






