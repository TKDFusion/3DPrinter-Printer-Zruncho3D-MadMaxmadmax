<h1>This is the readme for my Micron configuration.</h1>
This configuration is setup to use the Maxwell coupling as the probe switch. This configuration is setup to use the tool_probe_detection in the toolchanger add on.
<br>

Things that have been changed from the previous version:
-
 - Better comments in the files to help you understand what the parameters are for.
 - Much slower speeds for docking. The defaults are very slow, but ready to be adjusted for your printer.
 - homing_override now has an option to use your 3 axis probe (Nudge, sexball) as an endstop.
 - Slicer start gcode typo fixed.

<p>
<h1><center>!! IMPORTANT !!</center><br>Things that YOU (yes, even you) should be changing within this configuration.</h1>

Printer.cfg:
-
 - Board pins
 - Printer Kinematics. This is setup for a Micron, however you can put any printer kinematics in here
   and have success running your tool changer with them. V2, Trident, etc..

Macros.cfg:
-
 - Slicer start gcode is at the top of this file. Tested in Prusa Slicer and Orca Slicer.
 - In <pre>[gcode_macro print_start]</pre> Line 31 is the command to tell the tool head where to wait while warming up to printing temperature. My recommendation is to tell it to move to your ooze blocker if installed.

Priming.cfg:
-
 - Please set up your priming for your tool heads. I use a chip purging macros I found in the DoomCube discord, but I cannot find it now. If it is yours, please contact me for proper attribution.

Homing_override.cfg:
-
 - Set your safe homing X and Y positions in the macro: <pre>[gcode_macro homing_variables]</pre>
 - If you are using a tool offset probe (nudge) for your Z endstop, the option for this should be set to "True".

Toolchanger.cfg (see comments in the file for appropriate values.):
-
 - t_command_restore_axis
 - params_safe_toolhead_y
 - params_safe_shuttle_y
 - params_close_y
 - params_attach_y
 - params_fast_speed
 - params_path_speed

Toolboard_{0/1}.cfg
-
 - Set the proper pins for your tool head board, these are setup for BTT EBB36.
 - Set the correct values for the docking parameters under <pre>[tool T{0/1}]</pre> check the comments for what values are appropriate.
 - Set the correct input shaper values for each tool head. Select the tool head then use the command:
    <pre>SHAPER_CALIBRATE CHIP=toolboard_{0/1}</pre>

Tc_offset_calibration_macros.cfg
-
 - Set the pin for your nudge / sexbolt / other 3 - axis probe.
 - See https://github.com/joseph-greiner/klipper_tc_automatic_offset_calibration for instructions on running the macros within this file.

Offset_save_file.cfg <br>
Stealthburner_macros_tc.cfg<br>
Toolchange_macros.cfg<br>
Tool_detection.cfg
-
 - You do not need to edit these files.
