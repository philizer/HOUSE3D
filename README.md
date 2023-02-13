# HOUSE3D
Tutorial and files for operating HOUSE3D printer


# Safety rules
For SAFETY reasons, always keep an eye on the printer and do not use it alone (min 2 operators).
Do not go inside the printer when it’s powered 
If any problem occurs, press the emergency switch immediately.

## I - Switch on the printer
Check the cables connections and switch on 

## II - Connexion to the router and to the rasp
Connect to the wifi : “router”, pwd: “lesmaisons3Dcestcool”
In the terminal of your laptop: “ifconfig”: to find your ip
“nmap-sP 192.168.0.0/24”: see the different objects connected to the network, and find the ip of the rasp, the rasp’s IP may change.

## III - In the terminal windows/ubuntu - modify the printer's parameters
Write the ip of the Rasp “ssh pi@192.168.0.___”, id: “pi”, pwd: “printer”, you are known in pi@octopi
To get into the configuration file: “nano printer.cfg”
[printer]: the parts of the file that can be modified, as the rotation distance, the microsteps (need to be the same values as the drivers ones), the position max (the axis does not move beyond this value), …
If there have been any changes: crtl O - enter - ctrl X - enter

## IV - Debugs - in the terminal
“sudo service klipper status”, to get the status of klipper
“sudo service klipper stop”, to stop klipper
“sudo service klipper start”, to start klipper
“tail -f /tmp/klippy.log”, to get klipper log
“tail -f /tmp/printer”, to view the output of the printer

## V - Launch a print (CAO, mesh, slicer, gcode, OctoPrint …)

OctoPrint:

To access OctoPrint: enter the IP address of the rasp on your browser to go on the local network: “https://192.168.0.___”, id: “pi”, pwd: “printer0*i”
Before each demand, it is necessary to go back to the origin, using the “house” button, or the command “G28”, in the terminal. To make only a special axis go to the origin use the command “G28X0” (for the x-axis) 
If any modifications have been done in the configuration’s files, write “FIRMWARE_RESTART” in the Octoprint terminal to take them into account.
If there is any error with the firmware, reconnect, and. then write “FIRMWARE_RESTART” in the terminal
To print an object:
Design a part on a CAO software (Solidworks, Fusion, …) and export it as .STL file
Slice the design on PrusaSlicer using the slice profile attached
Export the .gcode and upload it on OctoPrint
Check the cables and connections
Check the belt’s tension
Home Z axis, press switch manually before hitting the ground
Launch Gcode (the printer will only home the X and Y axis when using the provided profile)

## VI - Shutdown the system
When finish using all the system, write “shutdown-now” in the terminal (in pi@octop) before switching the power off, to avoid damaging the Raspberry Pii 
