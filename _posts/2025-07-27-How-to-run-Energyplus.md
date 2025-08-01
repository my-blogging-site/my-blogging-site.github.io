
Energyplus is a building energy modelling software, that was developed by the US department of Energy.

1. Head to https://energyplus.net and download the suitable energy plus software for your system. I am using a MacOS so will download that.
2. Once you have downloaded Energyplus, you will need an input file and a weather file to run Energy plus. Energyplus input files have the extension .idf (input data file) and weather files are .epw (energy plus weather) files.
3. Run the command: 
```
energyplus -i Energy+.idd  -w /path/to/weather/weather.epw /path/to/input/example.idf -r
```
Where 
- -i specifies the path to the Input Data Dictionary (IDD) file
- the .idd file is the E+ dictionary which defines all the objects, fields, data types, and allowed values.
- the optional -r command will generate a CSV file which post processess the main .eso file.

If it runs successfully, it will show something like this in the terminal:<br>
![energy plus run](/assets/energy_plus_runs.png)


- Let's look at the input file's main sections:
	- **Simulation and Building Setup**
		- Including version, timestep, building, algorithm, simulationcontrol, runperiod, site:location
	- **Material and Construction Properties**
	- **Zone Definition**
	- **Geometry Definition**
	- **Schedules**
	- **HVAC System**
	- **Output Requests**

Once a valid idf has been created and the simulation is run, for each thermal zone, Energyplus solves the heat balance equation at each timestep. After solving the heat balance equation for each zone, EnergyPlus generates several output files, the main output files are:
- **eplusout.eso**: Contains detailed simulation results.
- **eplusout.csv:** Run ReadVarsESO which post processes the eso file into a csv file
- **eplusout.rdd**: Data dictionary file.
- **eplusout.mdd**: Model data dictionary for debugging.
- **eplusout.mtr**: Metered energy consumption data.
- **eplusout.bnd**: Contains node and branch information for the HVAC system.
- **eplusout.eio**: Contains input and output information for components
- **eplusout.htm**: allows you to see the main results in a browser
