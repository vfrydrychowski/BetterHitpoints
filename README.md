# BetterHitpoints
Finding a way to improve hitpoints detections on a drum multi track
Sometimes DAWS mess up when you need to recognise the exact impact in an audio track. Here is an example from Cubase 


❌
![image](https://github.com/vfrydrychowski/BetterHitpoints/assets/44438290/93727b71-ed67-4d1e-9504-3b7c1e593760)
✔️
![image](https://github.com/vfrydrychowski/BetterHitpoints/assets/44438290/ea6a3024-7448-44bf-b99a-a3eff2f1a5cc)

This is a simple example, the offset might be much more important or the detection can even fail to detect a hit.

Another problem is finding the correct wave form. The various elements of the drum set can leave traces in the recording of other elements, the microphone isolation is never perfect. Sometime in the mic we will hear a lot of snare, but we want to detect on this mic only the tom hitpoints. Luckily each hit of the same element have roughly the same unique shape. We can also analyse the wavelength.

Here is an example of a tom mic with snare bleed.
![image](https://github.com/vfrydrychowski/BetterHitpoints/assets/44438290/ff7777a5-2900-404a-97f1-fca924e885eb)

# Data

To build a dataset, I can provide drum track with hitpoint already detected (and manually corrected). We might also need to generate data with a drum kit that play randomly and generate separate tracks with various drum configurations to vary mic bleeds. Hit pattern prediction might also help. 

Note on data retrieving: on cubase, we can export tracks to be imported in another project, and it turns out it do so in a form of a xml and wav file instead of the usual proprietary crap. In this xml, we can retrieve the hitpoints data. It means we can temper with this file to produce the output of or program, but this will be only compatible with cubase/Nuendo (a pretty good start)

[Here](Data/xml_exploration/click_120bpm_48000kHz) is an example of an export of a rendered click 120 bpm at 48000kHz. If we search for hitpoints object, the time value seems to bit the sample number from the beginning of the wav file.
