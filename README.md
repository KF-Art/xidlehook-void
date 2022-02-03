# xidlehook-void
xidlehook binary and source port for Void Linux.

All credits are for <a href="https://github.com/xXR01I1Xx">xXR01I1Xx</a>, who did the port at <a href="https://github.com/void-linux/void-packages/pull/27774">Void's PR</a>. I just extracted the template, updated to 0.10.0, and built binary packages. If Xidlehook gets merged into the repositories, this one will be archived.

<H1>How to install</H1>

Please note that this port was only tested on <code>x86_64-glibc</code> and <code>x86_64-musl</code> (i686 testing is in progress). Feel free to tell me if this works well on i686 and ARM platforms.

 <H2>Building from template</H2>

First of all, we'll need xtools installed in order to use properly xbps-src:

     # xbps-install xtools

If you haven't cloned the <code>void-packages</code> repository already, do it now:

     git clone --depth=1 https://github.com/void-linux/void-packages

Prepare the build environment (do this once if not done already):

     cd void-packages
     ./xbps-src binary-bootstrap

Clone the template to <code>srcpkgs</code> directory, compile it and install (do this inside your <code>void-packages</code> directory):

     cd void-packages
     git clone https://github.com/KF-Art/xidlehook-void srcpkgs/xidlehook
     ./xbps-src pkg -j $(nprocs) xidlehook # build the package
     xi xidlehook # install the package

<H3>Updating template manually</H3>

I'll do my best to give the faster as possible for me the new releases of this package, but in case that I can't update the template, or you just want to update it yourself, here is how to update it. 

In this example, updating from 0.10.0 to a hypothetical 1.0.0. This actually can be used as a example to update any template manually, like MEGASync, Brave, etc.

     cd void-packages # you need to be in the void-packages directory to do these steps

     templatedir="srcpkgs/xidlehook/template"
     sed -i 's/0.10.0/1.0.0/g' $templatedir # update template's version
     xgensum -i $templatedir # regenerate checksum

After that, you'll need to rebuild the package with the previous steps.

 <H2>Installing prebuilt binaries</H2>
There is also an binary package to install directly to your system. I recommend this if you don't want to go through the building process, but this may be outdated sometimes. I'll try to mantain this updated as is possible for me.

First, download the corresponding package for your architecture and libc from the releases page. Once downloaded, open a terminal inside the download folder and proceed:

     xbps-rindex -a *.xbps
     xi -R . xidlehook

I'll consider try to create my own repository to provide updates faster.
     
<H3>Updating cloned repository contents</H3>

     cd srcpkgs/xidlehook
     git pull

