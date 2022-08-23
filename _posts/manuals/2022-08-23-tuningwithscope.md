---
layout: "post"
title: "High power tuning with Oscilloscope"
permalink: "/tunewithscope/"
use-math: "true"
---

# Tuning the probe using an oscilloscope and VNA

In order to tune a probe, please follow the following steps:

1. Connect the probe to a Variable Network Analyser (VNA), and set the centre frequency to be exactly what your sfo1 is.
2. Say you want to tune proton, set the centre frequency to be 400.158###.
3. Match and tune to the best possible scenario.
4. Take the cable out from the back of the preamplifier, and connect a box filter (bandpass) to it.
5. Now your preamplifier is out of the picture.
6. Attach a bidirectional coupler.
7. Note the value of attenuation on the bidirectional coupler. Generally this attenuation applied to both forward and backward direction.
8. Attach another attenuation of 20 dB between the oscilloscope and the port of the bidirectional coupler. The port is the one where the RF is coming from the direction of the amplifier.

> **If you do not attach this attenuation, you will burn the oscilloscope. Do NOT forget to attach attenuations to the RF coming from the direction of the amplifier.**

9. What 20 dB attenuation does is it divides the power by a factor 100.
10. Connect the probe end to another channel of the oscilloscope.
11. Say CH1 is connected to amplifier end, and CH2 is connected to probe end, if the voltage of both channels are the same, we know that the reflection from the probe (CH2) is 100 times less than that of coming in from the amplifier (CH1, 20 dB, 100 times attenuated).
12. Set up an experiment, say _hpdec_, and put very low power decoupling on 1H. say, plw12 = 0.5 W. Kindly note down the voltage on the oscilloscope. This voltage must not exceed 1 V, or whatever your scope allows.
13. Tune and match whilst pulsing so that the reflection (CH2) is as low as possible.
14. Increase the power on 1H channel and do the same.

> **Do not exceed the maximum Voltage allowed by the Oscilloscope.**

<img src="{{ "docs/assets/images/annotely_scope_howtoimage.jpg" | prepend: site.baseurl | prepend: site.url}}" align = "centre" height = "200" width = "640" alt="Connections to probe and scope" />



