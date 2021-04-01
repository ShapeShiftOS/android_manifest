ShapeShiftOS
===========

<img src="https://i.imgur.com/OkwHNS3.jpg"> 

Credits
-------

* [**LineageOS/Cyanogenmod**](https://github.com/LineageOS)
* [**ABC ROM**](https://github.com/ezio84)
* [**Pixel Experience**](https://github.com/PixelExperience)
* [**DirtyUnicorns**](https://github.com/DirtyUnicorns)
* [**AOSPA**](https://github.com/aospa/)
* [**Nitrogen Project**](https://github.com/nitrogen-project)
* [**Extended-UI**](https://github.com/Extended-UI)
* [**OmniROM**](https://github.com/omnirom/)
* [**BlissRoms**](https://github.com/BlissRoms)
* [**POSP**](https://github.com/PotatoProject)
* [**Evolution-X**](https://github.com/Evolution-X)
* [**Syberia-Project**](https://github.com/syberia-project)
* [**Project Awaken**](https://github.com/Project-Awaken)
* [**Project Fluid**](https://github.com/Project-Fluid)
* [**WaveOS**](https://github.com/wave-project)

### How to build ShapeShiftOS ROM for your device - Tutorial
--------

>> To get started with the building process, you'll need to get familiar with [Git and Repo](http://source.android.com/source/using-repo.html).

### Build Environment

- Tested and Working on any version of Ubuntu - 14.04,14.10,15.04,16.04,18.04 (64-bit)
- Any other distribution based of the Ubuntu Distro such as Lubuntu, Xubuntu and etc.
- Any form of Terminal
- Decent hardware (minimum of at least a quad core CPU and 16 GB of RAM)
- A storage unit of any kind (We recommend utilizing SSDs as Mechanical HDDs slow down the build proccess drastically and the minimum storage size is 70GB. Having more will be useful with CCache[More on that later])
- Required Packages should have been installed

### Required Packages [this is for ubuntu 16.04, for other variants it may differ]
##### Simply copy and paste this in a terminal window:
>> [Hint: This command updates the Ubuntu Packages List (Install Listing) and install the required version of Java]

```bash
     sudo apt-get install openjdk-8-jdk
```

### Let that install and then proceed.

### More copy and paste:
>> [Hint: Running this command installs the other required packages to build android]

```bash
     sudo apt-get update && sudo apt-get install bc git-core gnupg flex bison gperf libsdl1.2-dev libesd0-dev libwxgtk3.0-dev squashfs-tools build-essential zip curl libncurses5-dev zlib1g-dev openjdk-8-jre openjdk-8-jdk pngcrush schedtool libxml2 libxml2-utils xsltproc lzop libc6-dev schedtool g++-multilib lib32z1-dev lib32ncurses5-dev lib32readline6-dev gcc-multilib maven tmux screen w3m ncftp adb fastboot repo python default-jdk
```

### Getting the source
- Making required directories
- Obtaining the repo binary
- Adding repo binary to your path
- Giving the repo binary proper permissions
- Initializing an empty repo
- Syncing the repo

>> Alright, so now we’re getting there. I have outlined the basics of what we’re about to do and broke them down as I know them. This is all pretty much going to be copy/paste so it’ll be fairly difficult to screw this up :)

##### Make directory for the repo binary

```bash
      mkdir ~/bin
```

##### Add directory for the repo binary to its path

```bash
      PATH=~/bin:$PATH
```

##### Downloading repo binary and placing it in the proper directory

```bash
      curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
```

##### Giving the repo binary the proper permissions

```bash
      chmod a+x ~/bin/repo
```

##### Creating directory for where the ShapeShiftOS repo will be stored and synced

```bash
      mkdir ~/ssos
      cd ~/ssos
```

##### Initializing the ShapeShiftOS repo and downloading the manifest

```bash
      repo init -u https://github.com/ShapeShiftOS/android_manifest.git -b android_11
```

##### Syncing the source
>> [Hint: This might take a long time as the source is ~75GB]

```bash
      repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
```

### Building the ShapeShiftOS ROM
- Preparing Required Binaries and Device Drivers
- Setting Up CCache (Optional)
- Building ShapeShiftOS

>> Congratulations on the successful build initialization! Now, we shall go ahead and prepare to build for your device!

##### Setting Up CCache
- CCache is a method of utilizing a specified storage space to speed up building. It can be referred to as the same caching your android device does to speed up application and system boot times. In this case, CCache will help build ShapeShiftOS faster than standard build times (Able to cut-down 50% of time taken to build).
- To set up CCache, follow the following:

```bash
        echo "export USE_CCACHE=1" >> ~/.bashrc
```

##### To build ShapeShiftOS ROM

```bash
      cd ~/ssos
      source build/envsetup.sh
      lunch ssos_<devicecodename>-userdebug
      make bacon -j$(nproc --all) | tee log.txt
```

##### Obtaining the zip created from the build process
>> To get the zip file that has been built, navigate to the following directory and find for the zip file:

```bash
      cd ~/ssos/out/target/product/<devicename>
```

OR

```bash
      cd $OUT
```

>> If you found it, then congratulations! If you didn't, try retrying the build process but before doing so, ensure you do the following to make sure your next build is clean;

```bash
      cd ~/ssos
      make clean
      repo sync --force-sync
```

>> After doing so, redo everything stated from the Building Section.

##### For those who successfully built ShapeShiftOS

>> Well, Congratulations on your victory! Now, you have a .zip file that flashable to your device! Share it to the internet as you wish but be sure to contribute back and also give credits to the ShapeShiftOS Team and its contributors! Do come and build ShapeShiftOS another time as source code is routinely being improved upon. If you wish to contibute, feel free to make a pull request to the ShapeShiftOS Team! See you again builder! 

-----------------------------------------	
Getting Official Maintainership for ShapeShiftOS
==========================================
>> To get Official Maintainership for ShapeShiftOS you should have a stable device source with all the main components working. Read the [**charter**](https://github.com/ShapeShiftOS/Shift_Documentation/blob/slave/Charter.mkdn) to get a clearer idea.

>> First make an unofficial build of ShapeShiftOS and post in [**XDA**](https://xda-developers.com) if you want to. Make sure you use the template here! Click on the raw button and change the links up where ever required.

>> Then, read [**here**](https://github.com/ShapeShiftOS/ShapeShift_Documents/blob/slave/Official.mkdn)

>> Join our [**Telegram Channel**](https://t.me/shapeshiftoschannel) and our  [**Telegram group**](https://t.me/shapeshiftos)

----------------------------
