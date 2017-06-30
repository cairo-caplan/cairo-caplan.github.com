---
layout: post
category : GSOC2017
tagline: "Supporting tagline"
comments : "true"
tags : [gsoc2017, limesdr, riscv]
---

On this initial post I talk about my application and project on Google Summer
of Code , edition 2017,  which will be porting the [Integration of a RISC V CPU on LimeSDR project](https://fossi-foundation.org/2017/05/04/gsoc#integration-of-a-risc-v-cpu-on-limesdr-project), under the mentorship of Andrew Black, Olof Kindgren and Zack Tamosevicius.

## LimeSDR

[LimeSDR](https://www.crowdsupply.com/lime-micro/limesdr) is an open-source project that implements a Software Defined Radio.
In case you don't know what is a Software Defined Radio (SDR), in turn, is defined as
a technique where the majority if the components of radio communication system
 (e.g. mixers, filters, amplifiers, modulators/demodulators, detectors, etc.)
 are not made of electrical pieces, by implemented by a algorithm in software.

The same way students and engineers used to build simulations to learn and
analyze AM/FM transmitters, analog TV or other communication models, be it on paper, on C, Python, MATLAB or Labview to give some examples, with Software Defined
Radios you can emulate or, to what matters, build a flexible radio while save
money or complexity of analog components.


The first time I read about SDR concept, as a person born in the 90s,
I remembered the old times of dial-up internet connections, where modems and
computer devices in general were expensive. It was natural that hardware
manufacturers tried to find ways to provide cheaper hardwares providing similar
functionalities. For 56K modems there was two modems, the traditional "hardmodems",
which, apart from discrete analog components were evolving into embedded systems
for their employment of microcontrollers or DSPs to be able to encode and decode
signals with complex modulations in real-time.


The other choice were the ["softmodems" or "winmodems"](https://en.wikipedia.org/wiki/Softmodem),
which borrow this digital
signal processing capability from the main processor, able to operate at higher
frequencies, thus its operations where performed in software by its OS driver.
The main advantage of softmodems where the low cost of the modem, as it had less
components. But it also came with two disadvantages, the main one is that it
consumes CPU time, already affected as usually this kind of modem where
 mounted on "everything on-board" PCs where not only modem but audio and video
 had to share the same single core CPU by the time.

 The second disadvantage were the OS drivers, usually the manufacturers of those
 modems made such drivers for Windows OS and where more error prone due to its
 complexity, real-time requirements ... or maybe simply because of Windows, making it a
 headache for people who wanted to use them on Linux or other OS.

 ![Softmodem and hardmodem](https://upload.wikimedia.org/wikipedia/commons/5/58/WinmodemAndRegularModem.jpg)
 *Softmodem on the left, hardmodem on the right.*

 Now, back to 2017, we have [Moore's laws and Dennard Scaling going to retirement](https://www.semiwiki.com/forum/content/5394-arm-moores-law-50-we-planning-retirement.html), [Internet of Things
 going places](https://www.intel.com/content/dam/www/public/us/en/images/iot/guide-to-iot-infographic.png), heterogeneous
 architectures and powerful embedded systems becoming a norm. SDRs now have the possibility to become the main choice for high bandwidth communication systems, for their flexibility regarding modulations, frequency and power. But differently from
 the softmodems of old, today there are other hardware choices to do heavy DSP computations workloads, mainly GPUs and FPGAs.
 This way you can, in theory, design systems that can work implement not one but many modems at the same time without
 affecting the performance for other tasks or taking time from the CPU.



 LimeSDR employs an FPGA chip to perform digital signal processing but, further than that, it is also based on another
 class of chip called Field Programmable RF (FPRF), the [LMS7002M](http://www.limemicro.com/products/field-programmable-rf-ics-lms7002m/) by [LimeMicro](http://www.limemicro.com/). The purpose of an FPRF is to bring the same flexibility that
 FPGAs gives to digital systems design and reconfiguration to analog circuits and transceivers.


 The specifications of the hardware is:


 * RF Transceiver: Lime Microsystems LMS7002M MIMO FPRF (Datasheet)
 * FPGA: Altera Cyclone IV EP4CE40F23 - also compatible with EP4CE30F23
 * Memory: 256 MBytes DDR2 SDRAM
 * USB 3.0 controller: Cypress USB 3.0 CYUSB3014-BZXC
 * Oscillator: Rakon RPT7050A @30.72MHz (Datasheet)
 * Continuous frequency range: 100 kHz – 3.8 GHz
 * Bandwidth: 61.44 MHz
 * RF connection: 10 U.FL connectors (6 RX, 4 TX)
 * Power Output (CW): up to 10 dBm
 * Multiplexing: 2x2 MIMO


 With LimeSDR configured by a software tool, as [GnuRadio or Pothos](https://wiki.myriadrf.org/Lime_Suite), you can
 choose to have a Wifi, LTE, Bluetooth, LoRa or whatever wireless modem as you want, limited only
 by the physics of the hardware itself.


 <center><img src="{{ site.url }}/assets/lms7002-functional.gif"></center>
 <center>Functional schematics diagram of the LMS7002M.</center><br>





 You can find more information on SDRs on [this](https://www.allaboutcircuits.com/technical-articles/introduction-to-software-defined-radio/) article by allaboutcircuits.com and on the site of [RTL-SDR](https://www.rtl-sdr.com/), which brands a low cost SDR device, based
 on DVB/Digital TV tuner circuits and counts with many resources on this subject. Finally, you check [MyriadRF](https://myriadrf.org/)
 website for instructions and resources on LimeSDR and join its community.





<center><img src="{{ site.url }}/assets/LimeSDR-board.jpg"></center>
<center>LimeSDR board, still packed.</center><br>

<center><img src="{{ site.url }}/assets/limesdr-mounted.jpg"></center>
<center>LimeSDR mounted.</center><br>


{% include JB/setup %}


 {% if page.comments %}
 <div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = https://cairo-caplan.github.io/;  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = "cairo-2011-12-29-jekyll-introduction"; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://cairo-caplan-github.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>


 {% endif %}
