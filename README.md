# Longer 3D LK4 Pro

![Longer 3D LK4 Pro](http://www.longer3d.com/data/watermark/20190910/5d76fc6eb8592.jpg)

## Cura 4.4

### Printer settings
_Custom printer_
````
X(Width): 220 mm
Y(Depth): 220 mm
Z(Width): 250 mm

Heated bed [X] 
````

### Start G-code

Add `G90` code at the beginning
````
G90
G28 ;Home
G1 Z15.0 F6000 ;Move the platform down 15mm
[...]
````

### Extruder settings

````
Nozzle size: 0.4 mm
Material diameter: 1.75 mm
````

### Octoprint connection plugins

Install the _Octoprint connection_ plugins.  
Restart Cura is required.

In _printer settings_, 

## Firmware updates

Motherboard firmware updates can be done with Cura in _Printer settings > Upload firmware_.

* [Marlin 2.0](files/firmware-Marlin2.0-BLTouchless.hex) _WIP_  
    Modified Firmware from https://github.com/DaGr70/Marlin_Longer_LK4_pro to make it work without BLTouch.  
    Screen need to be updated also.
    ````
    diff --git a/Marlin/Configuration.h b/Marlin/Configuration.h
    index b92aa85..76f7b5a 100644
    --- a/Marlin/Configuration.h
    +++ b/Marlin/Configuration.h
    @@ -670,7 +670,7 @@
    #define X_MAX_ENDSTOP_INVERTING false // Set to true to invert the logic of the endstop.
    #define Y_MAX_ENDSTOP_INVERTING false // Set to true to invert the logic of the endstop.
    #define Z_MAX_ENDSTOP_INVERTING false // Set to true to invert the logic of the endstop.
    -#define Z_MIN_PROBE_ENDSTOP_INVERTING false  //  For Alphawise and Longer U30 pro LK4 pro
    +#define Z_MIN_PROBE_ENDSTOP_INVERTING true  //  For Alphawise and Longer U30 pro LK4 pro
    
    /**
    * Stepper Drivers
      @@ -885,7 +885,8 @@
    * Use G29 repeatedly, adjusting the Z height at each point with movement commands
    * or (with LCD_BED_LEVELING) the LCD controller.
      */
      -//#define PROBE_MANUALLY
      +#define PROBE_MANUALLY
      +#define HAS_BED_PROBE 1
      //#define MANUAL_PROBE_START_Z 0.2
    
    /**
    @@ -913,7 +914,7 @@
    /**
    * The BLTouch probe uses a Hall effect sensor and emulates a servo.
      */
      -#define BLTOUCH   //  For Alphawise and Longer U30 pro LK4 pro with BLtouch
      +// #define BLTOUCH   //  For Alphawise and Longer U30 pro LK4 pro with BLtouch
    
    /**
    * Pressure sensor with a BLTouch-like interface
      @@ -1043,18 +1044,18 @@
    *     But: `M851 Z+1` with a CLEARANCE of 2  =>  2mm from bed to nozzle.
    */
    #define Z_CLEARANCE_DEPLOY_PROBE   10 // Z Clearance for Deploy/Stow
    -#define Z_CLEARANCE_BETWEEN_PROBES  5 // Z Clearance between probe points
    -#define Z_CLEARANCE_MULTI_PROBE     5 // Z Clearance between multiple probes
    -//#define Z_AFTER_PROBING           5 // Z position after probing is done
    +// #define Z_CLEARANCE_BETWEEN_PROBES  5 // Z Clearance between probe points
    +// #define Z_CLEARANCE_MULTI_PROBE     5 // Z Clearance between multiple probes
    +// //#define Z_AFTER_PROBING           5 // Z position after probing is done
    
    -#define Z_PROBE_LOW_POINT          -2 // Farthest distance below the trigger-point to go before stopping
    +// #define Z_PROBE_LOW_POINT          -2 // Farthest distance below the trigger-point to go before stopping
    
    -// For M851 give a range for adjusting the Z probe offset
    -#define Z_PROBE_OFFSET_RANGE_MIN -20
    -#define Z_PROBE_OFFSET_RANGE_MAX 20
    +// // For M851 give a range for adjusting the Z probe offset
    +// #define Z_PROBE_OFFSET_RANGE_MIN -20
    +// #define Z_PROBE_OFFSET_RANGE_MAX 20
    
    // Enable the M48 repeatability test to test probe accuracy
    -#define Z_MIN_PROBE_REPEATABILITY_TEST
    +// #define Z_MIN_PROBE_REPEATABILITY_TEST
    
    // Before deploy/stow pause for user confirmation
    //#define PAUSE_BEFORE_DEPLOY_STOW

    ````

* [0.3.2](./files/LK4_Pro0.3.2.hex)  
    _Changelog_
    ````
    ...
    ````


## Issues

- ~~Random abnormal temperature error~~ Fixed with the _0.3.2_ update.  
    <img src="./files/abnormalETemp.jpg" width="600px"/>
- Very noisy fans

## Resources

Longer LK4 Pro files : https://drive.google.com/drive/folders/1dvHLv4zWOcAh2wGPTkmM-cPpN2BUfJWg
