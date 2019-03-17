# lineageos-build
My advanture in building lineage os for my Samsung J7 (2017) *[j7y17lte]*


**Built on the sholders of gients**
 - [Exynos7870](https://github.com/Exynos7870)
 - [Mohi1117](https://github.com/Mohi1117)
 - [lineageos](https://github.com/lineageos)


**Other repos**
 - https://github.com/mentos1386/android_vendor_samsung
 - https://github.com/mentos1386/android_device_samsung_exynos7870-common
 - https://github.com/mentos1386/android_device_samsung_j7y17lte


# Guide

**Requirements**
 - Docker
 - Phone *(duh)*
 - 100+ GB Disk space, 4 or more cores
 
It's also usefull to read LineageOS wiki on how to build for official devices
 (even though we don't have an official device) [here](https://wiki.lineageos.org/devices/a7y17lte/build).
 
### Setting up environemnt

Use this awesome [docker-lineageos](https://github.com/stucki/docker-lineageos)
docker container. Which has all the tools required to build your new lineageos rom.

> Read the docs on repo for more info...
```
git clone https://github.com/stucki/docker-lineageos.git
cd docker-lineageos
./run.sh
```

And then initialize the repo. This takes a while...

```
repo init -u git://github.com/lineageos/android.git -b lineage-15.1
repo sync -c -j 16
source build/envsetup.sh
```

If your phone woudl be officialy supported you would just write:
```
breakfast <device codename>   # example: breakfast grouper
brunch <device codename>      # example: brunch grouper
```
But we are doing this the hard way.


### local_manifest
This is one of the more important config files. Here we provide all the sources
that are needed for us to build the LineageOS. We need to provide:

 * Kernel
 * Propriatery Vendor stuff
 * AOSP Device Tree
 
You can get my [local_manifest](local_manifest/j7y17lte.xml) and put it in your 
`.repo/local_manifests/j7y7lte.xml`. When you change manifests, you need to update
your resources by running `repo sync` command again.

#### Kernels
Located at `kernel/<vendor>/<device codename>`

#### Propriatery vendor stuff
Located at `vendor/<vendor>/<device codename>`

#### AOSP Device Tree
Located at `device/<vendor>/<device codename>`


### Compile
When we have all the files we can compile everything.

```
croot
brunch <device codename>
```

Now you will probably get some error, which you have to figure it out yourself in
this three easy steps.

 1. Google
 2. Search through other peoples projects on github
 3. ...?

