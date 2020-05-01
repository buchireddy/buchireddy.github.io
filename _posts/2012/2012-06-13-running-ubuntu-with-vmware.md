---
layout: post
title:  Running Ubuntu with VMWare on Windows 7
date:   2012-06-13 00:00:00
---
I always wanted to run some Linux OS on my laptop but could not install one. So, I though to running Linux as a virtual machine and explored different options recently.

It wasn’t a tough job to choose a decently good software to run virutal machines since it turns out that there are not too many products available (at least the so called famous ones).

**Different options for running VMs?**

There are different options like using VMWare, Virtualbox, Prallells and Sphere for running virtual machines. I have understood that both the VMWare and Virtualbox are the most widely used for this purpose and I have picked VMWare based on some of the references given below.

I just wanted to give some details on how one can quickly launch a Linux virtual machine from Windows7.

**Steps for running a virtual machine using VMWare:**

1\. Download and install latest version of VMPlayer for Windows.

You can download it from [here](http://www.vmware.com/products/player/faqs.html).  This is pretty straight forward and should be done in few minutes.

2\. Download the required VMWare image for the guest operating system you want to run.

For example, [http://www.trendsigma.net/vmware/](http://www.trendsigma.net/vmware/ "http://www.trendsigma.net/vmware/") provides images of bunch of Linux operating systems and you can download the ones you want.

3\. Configure higher memory for the guest OS in vmx file you find in the downloaded zip (you can edit the vmx file with the text editor). Please note that you can skip this step and configure the memory later also.

Default values will be generally 512M which might cause slowness (due to excessive paging) to your guest OS if you are using it extensively.

4\. Launch the VMPlayer installed in step 1 and select to open an existing virtual machine from the options.

There, you need to pick up the vmx file (that you modifed in the previous step) and paly the virtual machine.

You should now see a complete Linux OS running as part of the VMPlayer window.

_If you need any further assistance for this, you can either google for it (there is lot of community support) or reach out to me at buchi dot 22 dot aug at gmail dot com_

* * *
**References:**

Here are some references for comparison of different VM players.

[http://marsbox.com/blog/reviews/vmware-vs-virtualbox/](http://marsbox.com/blog/reviews/vmware-vs-virtualbox/)

[https://www.virtualbox.org/wiki/VBox\_vs\_Others](https://www.virtualbox.org/wiki/VBox_vs_Others)

[http://tidbits.com/article/12498](http://tidbits.com/article/12498)
