# Motor DC Voltage drop causes

## Introduction

This document shows the possible causes that makes the voltage of the DC line, that powers the azimuth and elevation motors, drops. The DC line is manage by the Phase Main Power supply (MPS). The capacitor banks cabinet are wired to the DC bus, so, the capacitor banks charge/discharge operation are managed by the MPS. Most of the causes are listed bellow, but there could be other causes that are not listed, they will be less suitable but not impossible.

1. EtherCAT line failure. If the EtherCAT line where the MPS is attached goes down, the power supply will go to safe state, and this is DC bus discharged. Possible causes for EtherCAT failure are (probably not all the causes are listed)
    * TMA-PXI reboot or switch off.
    * Ethernet cable disconnection/cut between the TMA-PXI and the MPS (TMA-AZ-CS-CBT-0001, TMA-PI-CS-CBT-0101, TMA-AZ-DR-CBT-0001).
    * Switch off the TMA-AZ-CS-CBT-0001 cabinet.
    * Switch off the TMA-PI-CS-CBT-0101 cabinet.
    * Put TMA-PXI EtherCAT in configuration mode using the NI distributed system manager or any other tool (see [Manage EtherCAT line status](https://github.com/lsst-ts/ts_tma_tma-documentation_maintenance-documents_ethercat_manage-ethercat-line-status)).
2. Aux-PXI reboot. The Aux-PXI has the control of the MPS, and we it starts it will ask to the MPS to switch off.
3. Push Emergency Push button in any of the capacitor banks cabinets. The capacitor banks controller will discharge the capacitor banks
4. Earthquake interlock from GIS. TMA-IS will send to the capacitor banks controller to discharge, according to the TMA-IS safety matrix.
5. Press OFF button in the EUI/HHD.
6. Send 601 command with parameter 0 (power off MPS) from the CSC.
7. Failure in the MPS.
8. Failure in the power line. Makes that the power supply goes to safe state, discharge capacitor banks.

Also, opening one capacitor bank will make that this capacitor bank is discharged. Open any capacitor bank when the line is charge is not recommended because in can cause damage in the capacitor banks. Connect the any capacitor bank when the line is charged is very dangerous for the capacitor bank and for the telescope.
