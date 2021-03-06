Marla & Moretz Kernels for CM11.0
===================

Branches Supported in this Repository
-------------------

**Marla** - CM11.0 based kernel for the Samsung Skyrocket, Hercules, 
Blaze 4G & Exhilarate devices.  This branch is intended to be very close
to stock with specific modifications to improve performance and
battery consumption vs. stock.  This is intended to be a flash
and forget kernel.  There is no need for users to screw with 
anything to get optimal results.

**Moretz** - CM11.0 based kernel for the Samsung Skyrocket, Hercules, 
Blaze 4G & Exhilarate devices.  This branch is the 'hot rod' kernel, it
contains over clocked CPU frequencies, a bunch of different schedulers and
governors, etc.  It is intended for the tweakers.

Terms of Use
-------------------

No warranty implied or written.  You use this source at your own risk.

This is free useable, forkable, kangable, whatever.  However, you **MUST**
keep original code attributions intact when cherry-picking, forking, etc.

You do not have to ask permission to use the Moretz & Marla code branches.
What I do ask is that you at least send me a link to your distribution or
forked repository in github/bitbucket.  Lastly, please give credit to
the following people & groups in your distribution:

	Team Chopsticks
	CyanogenMod
	Car vs Driver
	elbermu
	your mom

Change requests and bug fixes.
--------------------

For any bugs or changes, please submit pull requests.  I will review them
weekly as necessary.

Do not submit new feature requests to the marla branch, they will be
ignored immediately.  New features outside of CM10.2 will only be
considered for the moretz branch.
    
How to pull this into your CM11.0 build.
--------------------

To use this kernel in your Samsung Hercules, Skyrocket or Exhilarate builds for 
CM10.2, you will need to edit your roomservice.xml (or local_manifest.xml) and 
add the following:

	<remote  name="bitbucket"
		fetch="ssh://git@bitbucket.org" />
          
	<project 
		name="carvsdriver/android_kernel_samsung_msm8660-common" 
		path="kernel/samsung/msm8660-common" 
		remote="bitbucket" 
		revision="moretz" />
            
Change your revision to either moretz or marla depending on which one you 
want to use.

Now, follow the instructions located at the link below for the init.d
helper scripts that go along with both kernel variants:

https://bitbucket.org/carvsdriver/vendor_moretz-kernel

Next, you will need to remove the stock kernel from your manifest and 
cm.depdenencies script.

Finally, you will need to remove the stock mpdecision binary from your
target ROM. This can be done through your installation script within
your flashable zip file.  The file you need to remove when using either
moretz or marla is:

	/system/bin/mpdecision

If you don't remove this, it will conflict with the kernel based
MSM_MPDecision logic and may cause deadlocks on the CPU cores.
