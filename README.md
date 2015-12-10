# Control_Simulation
On-board software for controller, state estimator and simulations thereof.


OUTLINE
=======
Satellite Software
- Main program (calls Determine State and Determine Control... AND interfaces with Arduino?)
- Determine State
	- definitely includes an attitude propagator
- Determine Control
	- may include an attitude propagator

libs
- Clock and Time conversion functions
- Orbit propagator
	- we need a better propagator, or at least determine why our results are so different from the STK validation data, cf. Orbit_Propagator repo
- Attitude propagator
- Rotations
- Quaternions
- IGRF
- Kalman filter
	- getAttitudeState() will implicitly call getSensorData() from Arduino API, then will call on Kalman filter to turn the sensor data into a state estimate
	- dependencies: Clock, Orbit Propagator, Attitude propagator, Rotations, IGRF
- Arduino API (for getting sensor data / posting actuator signal)



Physics Simulation
- Clock
- Orbit propagator
- Attitude propagator
- Noise...


===========
Writing Order:
(Fill in interfaces as needed)
- Determine State
- Determine Control
- Main program (esp. where the program will interface with the Arduino?)
	- yes, this is where the interfacing with the arduino should be... the determineState() and determineControl() functions should just interface with the data stored in some file... the Main program can just call upon the Arduino to update this data
	- the determineState() and determineControl() functions should know how to interpret this data

- Fill in libraries

- Simulation libraries
- Simulation

- Perhaps the programs should use the same time() (and maybe some other) functions as they will on-board the satellite... and if already defined on the system where this simulation is running, then overrule them.
