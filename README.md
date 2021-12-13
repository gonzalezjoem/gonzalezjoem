- 👋 Hi, I’m @gonzalezjoem
- 👀 I’m interested in ...bass, drums, guitar, movies, and 3d printing (Blender v2.8, Ultimaker Cura 4.12.1, on upgraded Anet A8 stepper motors and Duet 2 SiFi board)
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...

I am having trouble printing with the new Duet 2 board. All axes work, including extruder. No matter which figures I use, I can't seem to keep the printhead on the heatbed.
The printhead seems to be printing the shape I'm trying to print except it prints off the plate, with the printhead always coming back passed the heatbed left edge and to the
horizontal endstop, then continues to print. I've tried different settings and nothing helps. I think, and I realize I could be wrong, but I think I am not measuring the pringhead
to nozzle, or endstop to heatbed edge, or I don't know what else. No matter what fugures I use for X min, the printhead always goes passed the heatbed and goes to the X endstop. 
I've included below the config.g file from Duet 2 and Cura printhead settings because they are related to this problem. Could someone please help me? Configs below:

--------------------------------------

Duet 2 RepRapFirmware Configuration Tool v3.3.5
part of Config.g file:

; Axis Limits
M208 X10 Y10 Z0.2 S1         ; set axis minimums
M208 X220 Y220 Z240 S0       ; set axis maxima

; Endstops
M574 X1 S1 P"xstop"          ; configure unsupported switch-type endstop for low end on X via pin xstop
M574 Y1 S1 P"ystop"          ; configure unsupported switch-type endstop for low end on Y via pin ystop
M574 Z1 S1 P"zstop"          ; configure unsupported switch-type endstop for low end on Z via pin zstop
                                       
----------------------------------------

Ultimaker Cura 4.12.1
Machine Settings:
  Printer settings: 220 x 220 x 240
    
  Printhead Settings:
  X min   -12
  Y min   -35
  X max    57
  Y max    18
  Gantry Height: 43
  Number of Extruders: 1
  Apply Extruder offsets to G-Code: yes
  
 --------------------------------------
 
 Start G-Code:
 
 ;Sliced at: {day} {date} {time} Monday, 12/13/2021
G21        ;metric values
G90        ;absolute positioning
M82        ;set extruder to absolute mode
M107       ;start with the fan off

G28 X0 Y0  ;move X/Y to min endstops
G28 Z0     ;move Z to min endstops
G29

G0 X0 Y15 F9000 ; Go to front
G0 Z0.15 ; Drop to bed
G92 E0 ; zero the extruded length
G1 X40 E25 F500 ; Extrude 25mm of filament in a 4cm line
G92 E0 ; zero the extruded length
G1 E-1 F500 ; Retract a little
G1 X80 F4000 ; Quickly wipe away from the filament line
G1 Z0.3 ; Raise and begin printing.
  
----------------------------------------

End G-Code: (but it never reaches here because I always have to stop print)

  ;End GCode
M104 S0         ;extruder heater off
M140 S0         ;heated bed heater off

G91             ;relative positioning
G1 E-1 F300     ;retract the filament a
; bit before lifting the nozzle, to
; release some of the pressure

G1 Z+0.5 E-5 X-20 Y-20 F {travel_speed}
 ; move Z up a bit and retract filament
; even more

G28 X0 Y0 ;move X/Y to min endstops,
; so the head is out of the way

M84       ;steppers off
G90       ;absolute positioning

-------------------------------------------

- 📫 How to reach me ...
gonzalezjoem@yahoo.com

<!---
gonzalezjoem/gonzalezjoem is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
