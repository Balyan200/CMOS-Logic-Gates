# CMOS-Inverter
Complementary Metal Oxide Semiconductor (CMOS) is a digital design technique that utilizes both p-channel MOSFET (PMOS) and n-channel MOSFET (NMOS) to define a logic function.  The PMOS network is responsible for providing a strong 1, called pull up, when its gate input is low while NMOS network provides a strong 0 when its gate input is high, called pull down. This complementary switching action enables the CMOS inverter to deliver full voltage swing with minimal power consumption. Its rapid performance, low static power usage, and dependable functionality establish it as a fundamental and extensively utilized component in digital logic design.
The project is simulated on TSMC 180nm node.

## Schematic Capture (LTspice)
<p align="center">
<img width="500" height="600" alt="image" src="https://github.com/user-attachments/assets/51b4bd67-e096-4640-9361-6515383fe7ff"/>
</p>

Different parameters can be calculated for the made circuit as shown in table:  
**Power:** The average static power consumed by the circuit from VDD.  
**Tdelay:** The average propagation delay of circuit as time for signal to propagate from input to output.  
**Tphl:** Delay between high to low transition at 50% of output to low to high transition at 50% input signal value.  
**Tplh:** Delay between low to high transition at 50% of output to high to low transition at 50% input signal value.  
**PDP:** Power Delay Product presents a trade-off between delay and power in a single value.  
**EDP:** Energy Delay Product is numerically equal to PDP X Delay.  


|Supply Voltage = 1V |	Pre Layout	|Post layout|
|---|---|---|
|Power (nW)	|139.35	|899.87|
|Tdelay (ps)	|17.81|	49.44|
|Tphl (ps)	|26.21	|45.36|
|Tplh (ps)	|13.68	|53.52|
|PDP (aJ)	|2.48	|44.48|
|EDP (aJ -ps)	|44.24	|2199.09|
|L	|180n	|180n (2λ)|
|Wn	|450n	|450n (5λ)|
|Wp	|1200n	|1170n (13λ)|

(a) Transient characteristic
<p align="center">
<img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/db7598b6-625f-4054-8c48-0948253ec6d4"/>
</p>
(b)	Voltage Transfer Characteristic
<p align="center">
<img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/6ce859ce-667b-41b2-9936-84e1f72bb28d" />
</p>
(c)	Noise margins calculation
<p align="center">
<img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/3b364061-5c4f-4dc4-a9ba-71f3b7b3e9bb" />
</p>
(d)	Leakage current and power
<p align="center">
<img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/ae3424a4-99b6-46da-a6de-50e2ca19a85d" />
</p>

**Noise Margins:**
Noise margins describe the limit to which circuit can prevent influence of noise on gate inputs and provide correct output.  
VIH = Minimum High input voltage (to ensure output as 0)  
VIL = Maximum Low input voltage (to ensure output as 1)  
VIL and VIH are determined by the points where slope of VTC curve = -1.  
VOH = Minimum High output voltage   
VOL = Maximum Low output voltage  

Noise Margin Low (NML) = VIL – VOL   
Noise Margin High (NMH) = VOH - VIH  

| |Pre Layout	|POST LAYOUT|
 |---|---|---|
|VOH	|1	|1|
|VIH	|0.507|	0.521|
|VOL	|0	|0|
|VIL	|0.439|	0.447|
|NMH	|0.493	|0.479|
|NML	|0.439	|0.447|

**Leakage power:** Power consumed by circuit in off state i.e. when all the transistors are off. Measured as 477.64fW.   
**Leakage current:** The subthreshold current flowing across transistors in OFF state. Measured to be 803.5fA.  
**Voltage Variation:**
Observing variation in delay and power of circuit with respect to variation in supply voltage. With increase in voltage, power increases while delay decreases.  

|Supply Voltage	|Delay (ps)	|Power (nW)|
|---|---|---|
|0.7	|72.3931	|108.26|
|0.8	|39.5286	|135.05|
|0.9|	25.8347	|137.94|
|1|	17.8192	|139.35|
|1.1	|14.1952|	163.64|
|1.2	|11.6593|	195.53|

## Post Layout simulation (Magic VLSI and Ngspice)
Area: 2.880µ (32λ) X 5.760µ (64λ)  

Extracted capacitances from layout design:   
.option scale=0.09u  
M1000 out in vdd vdd pfet w=13 l=2 ad=78 pd=38 as=78 ps=38  
M1001 out in gnd Gnd nfet w=5 l=2 ad=30 pd=22 as=30 ps=22  
C0 vdd in 0.09fF  
C1 in out 0.19fF  
C2 gnd out 0.08fF  
C3 in gnd 0.04fF  
C4 vdd out 0.21fF  
C5 gnd Gnd 0.13fF  
C6 out Gnd 0.09fF  
C7 in Gnd 0.24fF  
C8 vdd Gnd 0.76fF  

**Layout Design**
<p align="center">
<img width="335" height="547" alt="image" src="https://github.com/user-attachments/assets/7358526d-733d-4943-9dfb-16c9fdcdbe0d" />
</p>
Post Layout Transient Simulation
<p align="center">
<img width="697" height="353" alt="image" src="https://github.com/user-attachments/assets/97107958-fcf0-4a05-90fe-7a029cda14bb" />
</p>

