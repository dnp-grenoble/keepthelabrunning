---
layout: "post"
title: "Setting up CP"
permalink: "/cross-polarisation/"
use-math: "true"
---

In order to set up CP, the things that you have to check in the beginning are:
1. Spinning Frequency.
1. Offset of the rare nuclei e.g. Carbon
2. Offset of the abundant nuclei e.g. Proton.


Spinning frequency is important because the matching condition for CP set up is:

$$ \nu_{1H} - \nu_{13C} = \nu_r $$

where $\nu ,s$ are RF amplitudes.


In the LAB sequence follwowing parameters are important.

- o1 : Put it at the centre of your $$^{13}C$$ spectrum.
- o2 : Put it at the centre of your $$^{1}H$$ spectrum.

### Pre-Saturation ### 
Use presaturation if you are at low temperatures, e.g DNP at 100 K, or if your T1 is very long.

```jython
#ifndef no_sat
  3 d10
    (p3 pl2 ph15):f2	
    d10
    (p1 pl11 ph15):f1
    lo to 3 times l20
#endif
```

Unless you specify *-Dno_sat* as *zgoptns* in the LAB sequence, pre saturation will be active by default.
Set l20 to about 50 to 100, and d20 to 1 ms.

### CP Matching condition ###
The proton power level is set by *pl22*. Set it to be around 50-60 kHz approximately. Optimise *pl1* so as to get the maximum sensitivity on rare nucleus.
Please note that the RF properties change on the following situations generally:

- Spinning Frequency (Important).
- Temperature.
- Sample.

Adjust *p15* to get the maximum signal. *p15* is the contact time. It is set in microseconds.

The code block in the LAB sequence is:
``` jython
1u pl2:f2 pl1:f1 			;preset pl12 for F2, pl1 for F1
  trigg				;trigger for scope, 10 usec
  (p3 ph1):f2	    ;1H 90 excitation pulse
  0.3u pl22:f2		;set pl22 for CP on F2
  (p15 ph2):f1 (p15:spf0 ph3):f2 	;CP with square or shape on F2
```

Generally we use a ramp pulse of 80-100 on 1H, but this can be varied in exceptional cases.

### Echo ###

This part of the sequence is important when you are doing DNP.

``` jython
#ifndef no_echo
  1u pl11:f1 cpds1:f2 	;set pl11 on F1; start 1H decoupling for echo
  d5									 	;tau
  (p2 ph16):f1					;pi on X
  d6										;tau, 1H decoupler off
  0.5u do:f2					 	;1H decoupler off
#endif
```

The sequence sstates that echo will be active always unless you use *-Dno_echo* in the *zgoptns*.
The delays d5 and d6 depends on the spinning frequency. **So it is very important to set cnst31 = MAS freq.**


### Decoupling ###

There are two decoupling sequences used in the lab sequence
1. cpdprg1.
2. cpdprg2.

In general case, you can set either to SW<sub>f</sub>-TPPM (my recommendation) or SPINAL-64. The power level for these sequences are set by plw12.
**Set plw12 so that it is more than 3 times the spinning frequency.**

And set pcpd2 to be such that it corresponds to 180 degree rotation corresponding to plw12.


## Extras ##

You can calibrate the RF field on X channel, using the option -Dc13cal.

``` jython
#ifdef c13cal
  0.3u pl11:f1
  (p1 ph20):f1					;X 90 flip-back pulse
  d2 pl21:f1						;z-filter delay
  (p21 pl21 ph21):f1		;X 90 excitation pulse for calibration
#endif
```

You have to set an approximate value for p1 and plw11 so that it corresponds to 90 degree pulse and then put plw21 = watts that you want to calibrate. Vary the p21 to get the 90 degree corresponding to plw21. 






 