---
layout: "post"
title: "Setting up CP"
permalink: "/cross-polarisation/"
use-math: "true"
---

In order to set up CP, the things that you have to check in the beginning are:
1. Offset of the rare nuclei e.g. Carbon
2. Offset of the abundant nuclei e.g. Proton.
3. Spinning Frequency.

Spinning frequency is important because the matching condition for CP set up is:

$$ \nu_{1H} - \nu_{13C} = \nu_r $$

In the LAB sequence follwowing parameters are important.

- o1 : Put it at the centre of your $$^{13}C$$ spectrum.
- o2 : Put it at the centre of your $$^{1}H$$ spectrum.

Use presaturation if you are at low temperatures, or if your T1 is very long.

```jython
#ifndef no_sat
  3 d10
    (p3 pl2 ph15):f2	
    d10
    (p1 pl11 ph15):f1
    lo to 3 times l20
#endif
```

Unless you specify -Dno_dat in the LAB sequence, pre saturation will be active by default.
 