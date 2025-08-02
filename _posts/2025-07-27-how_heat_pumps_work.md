
Let's start from the fundamentals to understand how a heat pump works. Beginning with the **First law of thermodynamics** which states energy cannot be created or destroyed, it can only be transferred. It can also expressed as: 
ΔU = Qnet - W
Where:
- ΔU is the change in internal energy 
- Qnet is the net heat added to the system 
- W is the work done by the system

A basic diagram of the flow of energy for heat pumps:
![image](/assets/heat_pump_basic_diagram.png)
The equation for the first law of thermodynamics can be modified for heat pumps:
- Work is done on the system by a compressor to transfer heat from a cold environment to a hot environment. Therefore, the work term becomes positive: -(-W).
- At the end of a cycle the heat pump returns to the same state as at the beginning, so the change in internal energy in one cycle is zero: ΔU = 0
- Qnet = Qcold - Qhot where Qcold is energy from cold environment and Qhot is the heat delivered to hot environment

To get the performance of a heat pump we care about Qhot relative to the W we put in. If we substitute the work equation we found earlier 

![image](/assets/COPhp_basic.png)

Now we have the equation for the COP of heat pumps let's turn to the second law of thermodynamics. The second law of thermodynamics states **Heat will not spontaneously flow from a lower temperature to a higher temperature.** This means that heat flows from hot to cold unless some energy is inputted which is what a heat pump does.

The Carnot COP is the maximum COP that a heat pump can achieve in a given environment. We can understand this by looking at the reversed Carnot cycle which is applicable for heat pumps. The reversed carnot cycle consists of four reversible processes:
1. **Isothermal Expansion**
    - Gas absorbs heat from cold environment -> Entropy increases
    - Isothermal process is where the temperature remains constant 
2. **Adiabatic Compression**
    - Gas is compressed, heating up gas. No heat transfer -> Entropy remains constant.
    - Adiabatic is a process with no heat transfer
3. **Isothermal Compression**
    - Gas releases heat Qhot to the hot environment -> Entropy decreases
    - Work is done on the system during compression
4. **Adiabatic Expansion**: 
    - Gas expands, cooling to the cold environment temperature -> entropy remains constant. Temperature drops

![image](/assets/carnot_hp_cycle.png)

For a reversible cycle, the net entropy change of the system and environment is zero. This is because the system returns to its initial state after one full cycle, so its net entropy change is zero. **Entropy gained by the environment** equals **entropy lost by the system**.

![image](/assets/carnot_equations.png)


We can then put this in the equation we derived earlier to get the Carnot COP.  This is the maximum theoretical efficiency a heat pump can achieve.
![image](/assets/carnot_hp_equation.png)

In reality, the Carnot COP is hardly achieved due to: 
- Friction losses in mechanical parts
- Heat loss from case
- Refrigerant losses
- Part load operation - cycling drops efficiency due to stop starts  
- Heat exchanger area - larger exchangers improve efficiency
- Defrost cycles needed
- Pumps and Fans require additional electrical input

This is why standardised lab tests are conducted to find out the real performance of heat pumps in a range of conditions. For example, in Europe the EN 14825 is done. The EN 14825 calculates COP at different outdoor temperatures ( -7°C, +2°C, +7°C, +12°C) and part-load ratios (88%, 54%, 35%, 15% of design heating demand) at temperature profiles for average, warmer, and colder climates.

We can also understand the heat pumps from the actual components:

 1. **Refrigerant**
- Heat pumps operate using a special fluid called the refrigerant. What’s unique about refrigerants is that it boils at very low temperatures. This characteristic allows the capture of energy even from low temperatures. The refrigerant begins as a low pressure, low temperature liquid, which is directed to the evaporator.

 2. **Evaporator**
- The evaporator, a heat exchanger, interacting with outside air for air source heat pumps, causes the refrigerant to boil as ambient air passes over it, transforming the refrigerant into a low temperature cold vapour. As the liquid boils it gains energy from the outside air, causing it to evaporate into a gas. This vapour is then carried to the compressor. They also have a fan to ensure airflow over the heat exchanger.

 3. **Compressor**
- Before the compressor works, a reversing valve or a 4 way valve is used to switch between heating and cooling. It allows the flow to reversed when needed e.g. defrost it reverses to melt ice on the evaporator. 
- The compressor uses electricity to increase the pressure of the refrigerant which causes the temperature to rise. The high pressure high temperature vapour is then taken to the condenser. 

 4. **Condenser**
- The condenser is a heat exchanger, which releases energy to the water in the storage tank. During this process, the refrigerant undergoes condensation, releasing energy and transforming into a liquid.
- The refrigerant then passes out the storage tank and to the expansion vessel.

 5. **Expansion vessel**
- The expansion vessel drops the pressure, leading to a drop in temperature. The now low pressure, low temperature liquid repeats the cycle by returning to the evaporator.

![heat pump](/assets/heat_pump_diagram.png)