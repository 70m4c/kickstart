Kickstart
=========

⚠️ WARNING
----------

**EVERY KICKSTART FILE IN THIS PROJECT INCLUDES ТОМАС'S PERSONAL PUBLIC SSH
KEY. USING A KICKSTART FILE IN THIS PROJECT WITHOUT FIRST REMOVING ТОМАС'S
PERSONAL PUBLIC SSH KEY WILL RESULT IN ТОМАС HAVING FULL ACCESS TO YOUR
SYSTEM.**

About
-----

These resources use [Kickstart](https://en.wikipedia.org/wiki/Kickstart_(Linux))
and [iPXE](https://ipxe.org/) to perform automated Linux operating systems
installations.

Usage
-----

The following sections provide details of how to launch Kickstart using various
approaches.

### Manually

Launching Kickstart manually is documented in [section 7.1 of Performing an
advanced RHEL 9 installation](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/html-single/performing_an_advanced_rhel_9_installation/index#starting-a-kickstart-installation-manually_starting-kickstart-installations).

Generally speaking, you will follow these steps:

1. Make the desired Kickstart file available at some network location. _As 
   an example, you might use Python to launch a simple web server in the 
   root of this project:_ `python -m http.server 8000`.
2. Boot the installation medium on a system that will have network access to 
   the Kickstart file described in step 1. _For example, in VirtualBox, 
   configure the network to use a bridged adapter._
3. Once the installation options boot menu is shown, pick an installation 
   option and then press \[Tab\] to edit the configuration options of the 
   menu item.
4. Add `inst.ks` to the configuration options. _For example, if you are 
   running the web server described in step 1, append the following (using 
   your own IP address) to the boot options:_
   `inst.ks=http://192.168.0.1:8000/9/almalinux/[profile]/anaconda-ks.cfg`. 
6. Press \[Enter\] to begin the installation.

### iPXE

Launching Kickstart using iPXE will require providing the appropriate iPXE 
configuration file to the management system. You should only provide 
the _Raw_ URL to the iPXE file. _For example you might provide the URL to 
this Raw iPXE configuration file:_
`https://raw.githubusercontent.
com/70m4c/kickstart/master/9/almalinux/[profile]/kickstart.ipxe`

Shortened URLs
--------------

These shortened URLs can be used to access plain-text versions of Kickstart files.

| Shortcut | Destination |
|----------|-------------|
| https://tinyurl.com/ks-dev | ./9/almalinux/development/anaconda-ks.cfg |
| https://tinyurl.com/ks-srv4ans | ./9/almalinux/server-for-ansible/anaconda-ks.cfg |

Resources
---------

The following resources may be useful to understanding and configuring 
Kickstart.

* [Performing an advanced RHEL 9 
installation](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/html-single/performing_an_advanced_rhel_9_installation/index)
* [Pykickstart’s documentation](https://pykickstart.readthedocs.io/)
* [Kickstart on Wikipedia](https://en.wikipedia.org/wiki/Kickstart_(Linux))

The following resources may be useful to understanding and configuring 
iPXE.

* [iPXE website](https://ipxe.org/)

Copyright & License
-------------------

Copyright © 2022 Томас.

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the “Software”), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.