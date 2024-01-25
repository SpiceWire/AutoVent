
These sketches operate a fresh air vent. The vent resupplies fresh air for exhaust fans and combustion air.
One sketch simply cycles the motor in each direction to allow for electrical debugging. The other two sketches
operate the vent in response to a furnace call for heat. One sketch uses pull up resistors on the limit switches,
the other sketch uses pull down resistors. 

As designed, the vent door opens when the thermostat calls the furnace for heat. The vent is composed
of a sliding door driven by a lead screw connected to a reversible motor.

Arduino's heat call pin should be connected to Normally Open (NO) side of the furnace switch/relay.
When there is a furnace call for heat, the furnace relay closes and heatCallReading will read LOW. 

There are two methods to prevent overtravel of the vent door. A roller switch (maxOpenLimitSw and maxClosedLimitSw
below) engage the lead screw's carriage at the limit of travel on each end. The roller switches signal the
microcontroller to stop the motor (by use of a relay) before the limit of travel. They also inform the Arduino of the
carriage's position when the call for heat is turned on and off.

In addition, vent door overtravel is prevented by two additional roller microswitches wired
in series with the relays. If the software-driven relays fail to stop the door for whatever reason, the
carriage would engage a secondary switch that shuts off power to the motor.

The signal from the furnace is sent from a solenoid relay, which can send "dirty" signals that need debouncing.
Debouncing time is lengthy in order to account for situations where the thermostat is accidentally switched
to "Heat" when manually operated.
