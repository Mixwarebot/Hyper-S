# Cura Profile #

This profile is based on [Ultimaker Cura 4.13.1](https://github.com/Ultimaker/Cura/releases/tag/4.13.1).

## Start ##

- Open your Ultimaker Cura.(If you don't has it, please download)
- Add a new custom printer.
- Input Machine Settings:
 
  ![image](https://user-images.githubusercontent.com/104616944/165910871-daca9507-33b2-4564-886c-7c993bc4a59c.png)
  
  The Start G-code:
  ```

  M140 S{material_bed_temperature} ; Heat bed
  M109 S{material_print_temperature} ; Heat nozzle
  M190 S{material_bed_temperature} ; Wait for bed heating
  G28 ; home all axes
  M117 Purge extruder
  G92 E0 ; reset extruder
  G1 Z5.0 F1000 ; move z up little to prevent scratching of surface
  G1 X0.1 Y20 Z0.3 F5000.0 ; move to start-line position
  G1 X0.1 Y100.0 Z0.3 F1500.0 E15 ; draw 1st line
  G1 X0.4 Y100.0 Z0.3 F5000.0 ; move to side a little
  G1 X0.4 Y20 Z0.3 F1500.0 E30 ; draw 2nd line
  G92 E0 ; reset extruder
  G1 Z5.0 F1000 ; move z up little to prevent scratching of surface
  
  ```
  The End G-code:
  ```
  
  G91; relative positioning
  G1 Z1.0 F3000 ; move z up little to prevent scratching of print
  G90; absolute positioning
  G1 X0 Y200 F1000 ; prepare for part removal
  M104 S0; turn off extruder
  M140 S0 ; turn off bed
  G1 X0 Y220 F1000 ; prepare for part removal
  M84 ; disable motors
  M106 S0 ; turn off fan

  ```
- Import the "Hyper-S Draft.curaprofile" to Profiles.
- Import the "Material Profile/*.xml.fdm_material" to Materials.(A bad news, here can only be imported one by one)
- Start your print.
