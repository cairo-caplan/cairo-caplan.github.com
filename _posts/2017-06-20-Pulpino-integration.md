---
layout: post
category : GSOC2017
tagline: "Supporting tagline"
comments : "true"
tags : [intro, beginner, jekyll, tutorial]
---
{% include JB/setup %}

This is the first part of my tentative to use the Pulpino project inside the LimeSDR code.

0. Install Vivado 2015.1.

You need to install [Vivado 2015.1 software](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vivado-design-tools/archive.html#collapse-2015-1), from Xilinx. There's a free distribution called WebPack. Don't try to use Pulpino with newer versions, at first, or the building script will fail. I am using Questasim x64 for simulations, Pulpino claims to work with Modelsim SE but some users seems not to be lucky with them (https://github.com/pulp-platform/pulpino/issues/68 https://github.com/pulp-platform/pulpino/issues/75).


1. Clone the Pulpino repository from Github with:

{% highlight bash %}
git clone https://github.com/pulp-platform/pulpino.git
cd pulpino
{% endhighlight %}

2. Download the required IP cores subrepositories through the script
{% highlight bash %}
./update-ips.py
{% endhighlight %}

You should, by the end, get the following message:
{% highlight bash %}
SUMMARY
IPs updated successfully!
Generated new scripts for IPs!
{% endhighlight %}

[ 2.5 optional ] You may want to compile the documentation by going into
{% highlight bash %}
cd doc/datasheet/
make all
cd ../..  # Go back to Pulpino root
{% endhighlight %}

3. Create a directory for the software compilation and copy the cmake script for it:

{% highlight bash %}
mkdir build
cp sw/cmake_configure.riscv.gcc.sh build/
{% endhighlight %}


4. At this point you will have to edit the cmake_configure.riscv.gcc.sh to your environment. When you execute this script both Modelsim and the Risc V GCC toolchain needs to be visible. If you don't use the Pulpino modifiedtoolchain you will need to set GC_ETH to 0.

A modification I needed to do, as of June 2017, is to modify the line PULP_GIT_DIRECTORY from:

PULP_GIT_DIRECTORY=../../

To

PULP_GIT_DIRECTORY=../

Othewise it won't find the /sw folder. This is probably related to the localization of the build folder, which I created inside the pulpino folder.

Then execute it:

{% highlight bash %}
./cmake_configure.riscv.gcc.sh 
{% endhighlight bash %}

And it might return in the end:

{% highlight bash %}
NOTE: Detected RISCV compiler, using RISCV setup
-- Configuring done
-- Generating done
-- Build files have been written to: /home/cairo/cernbox/GSOC2017/pulpino/build
{% endhighlight bash %}

5. Compile the files with

{% highlight bash %}
make vcompile
--> work.tb compilation complete!

--> PULPino platform compilation complete!

Built target vcompile
{% endhighlight bash %}

6. If everything goes right it is time to run a simulation with:

{% highlight bash %}
make helloworld.vsim
{% endhighlight bash %}


The script loads the simulation in a new Modelsim. If you add the UART signals
 of the system and set the radix of the characters to ASCII, you can clearly see
 a "Hello World!!!!" message coming:

 ![Hello World on Pulpino simulation]({{ site.url }}/assets/Hello-pulpino-sim.jpg)






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
