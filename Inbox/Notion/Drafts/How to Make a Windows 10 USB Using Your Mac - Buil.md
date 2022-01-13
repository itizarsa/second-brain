# How to Make a Windows 10 USB Using Your Mac - Build a Bootable ISO From Your Mac's Terminal

Source: Article
Status: Unprocessed
URL: https://www.freecodecamp.org/news/how-make-a-windows-10-usb-using-your-mac-build-a-bootable-iso-from-your-macs-terminal/

![https://cdn-media-2.freecodecamp.org/w1280/5f9ca043740569d1a4ca4791.jpg](https://cdn-media-2.freecodecamp.org/w1280/5f9ca043740569d1a4ca4791.jpg)

---

Most new PCs don't come with DVD drives anymore. So it can be a pain to install Windows on a new computer.

Luckily, Microsoft makes a tool that you can use to install Windows from a USB storage drive (or "thumbdrive" as they are often called).

But what if you don't have a second PC for setting up that USB storage drive in the first place?

In this tutorial we'll show you how you can set this up from a Mac.

# Step 1: Download the Windows 10 ISO file

You can download the ISO file straight from Windows. That's right - everything we're going to do here is 100% legal and sanctioned by Microsoft.

If you want an English-language version of the latest update of Windows 10, you can [download the ISO here](https://www.microsoft.com/en-gb/software-download/windows10ISO).

If you have a relatively new computer, you probably want the 64-bit version. If you're not sure, go with the 32-bit version to be safe.

If you want a non-English-language version of Windows, or want to get an older update version, [download the ISO here](https://www.microsoft.com/en-gb/software-download/windows10) instead.

# Step 2: Insert your USB storage drive into your Mac

The ISO file is only about 5 gigabytes, but I recommend you use a USB drive with at least 16 gigabytes of space just in case Windows needs more space during the installation process.

I bought a 32 gigabyte USB drive at Walmart for only $3, so this shouldn't be very expensive.

Stick your USB drive into your Mac. Then open your terminal. You can do this using MacOS Spotlight by pressing both the ⌘ and Space bar at the same time, then typing "terminal" and hitting enter.

Don't be intimidated by the command line interface. I'm going to tell you exactly which commands to enter.

# Step 3: Use the diskutil command to identify which drive your USB is mounted on

Open Mac Spotlight using the ⌘ + space keyboard shortcut. Then type the word "terminal" and select Terminal from the dropdown list.

Paste the following command into your terminal and hit enter:

`diskutil list`

You will see output like this (note - your Mac's terminal may be black text on a white background if you haven't customized it).

![How%20to%20Make%20a%20Windows%2010%20USB%20Using%20Your%20Mac%20-%20Buil%2091a8272f4c7446ff8e6e612a6bc84181/default_-_default_freeCodeCamp_-_-zsh_-_130-33.png](How%20to%20Make%20a%20Windows%2010%20USB%20Using%20Your%20Mac%20-%20Buil%2091a8272f4c7446ff8e6e612a6bc84181/default_-_default_freeCodeCamp_-_-zsh_-_130-33.png)

Copy the text I point to here. It will probably be something like

`/dev/disk2`.

# Step 4: Format your USB Drive to work with Windows

Next format your USB drive to Windows FAT32 format. This is a format that Windows 10 will recognize.

Note that you should replace the `disk2` with the name of the your drive from step 3 if it wasn't `disk2`. (It may be `disk3` or `disk4`).

Run this command using the correct disk number for your USB:

`diskutil eraseDisk MS-DOS "WIN10" GPT /dev/disk2`

Then you'll see terminal output like this.

![How%20to%20Make%20a%20Windows%2010%20USB%20Using%20Your%20Mac%20-%20Buil%2091a8272f4c7446ff8e6e612a6bc84181/default_-_default_freeCodeCamp_-_-zsh_-_130-33-1.png](How%20to%20Make%20a%20Windows%2010%20USB%20Using%20Your%20Mac%20-%20Buil%2091a8272f4c7446ff8e6e612a6bc84181/default_-_default_freeCodeCamp_-_-zsh_-_130-33-1.png)

This will probably only take about 20 seconds on a newer computer, but may take longer on an older computer.

Note that for some hardware, you may instead need to run this command, which uses the MBR format for partitioning instead of GPT. Come back and try this command if step 7 fails, then redo steps 5, 6, and 7:

```
diskutil eraseDisk MS-DOS "WIN10" MBR /dev/disk2
```

# Step 5: Use `hdiutil` to mount the Windows 10 folder and prepare it for transfer.

Now we're going to prep our downloaded ISO file so we can copy it over to our USB drive.

You will need to check where your downloaded Windows 10 ISO file is and use that. But your file is probably located in your `~/Downloads` folder with a name of `Win10_1903_V1_English_x64.iso`.

`hdiutil mount ~/Downloads/Win10_1903_V1_English_x64.iso`

# Step 6: Copy the Windows 10 ISO over to your USB Drive

**Update April 2020:** One of the files in the Windows 10 ISO – install.wim – is now too large to copy over to a FAT-32 formatted USB drive. So I'll show you how to copy it over separately.

Thank you to [@alexlubbock](https://twitter.com/alexlubbock) for coming up with this workaround.

First run this command to copy over everything but that file:

`rsync -vha --exclude=sources/install.wim /Volumes/CCCOMA_X64FRE_EN-US_DV9/* /Volumes/WIN10`

Then run this command to install Homebrew (if you don't have it installed on your Mac yet):

`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

Then use Homebrew to install a tool called wimlib with this terminal command:

`brew install wimlib`

Then go ahead and create the directory that you're going to write the files into:

`mkdir /Volumes/WIN10/sources`

Then run this command. Note that this process may take several hours, you may see 0% progress until it finishes. Don't abort it. It will use wimlib to split the install.wim file into 2 files less than 4 GB each (I use 3.8 GB in the following command), then copy them over to your USB:

`wimlib-imagex split /Volumes/CCCOMA_X64FRE_EN-US_DV9/sources/install.wim /Volumes/WIN10/sources/install.swm 3800`

Once that's done, you can eject your USB from your Mac inside Finder. Note that Windows will automatically rejoin these files later when you're installing.

# Step 7: Put your USB into your new PC and start loading Windows

Congratulations - your computer now should boot directly from your USB drive. If it doesn't, you may need to check your new PC's BIOS and change the boot order to boot from your USB drive.

Windows will pop up a screen and start the installation process.

Enjoy your new PC, and your newly-installed copy of Windows.

If you read this far, tweet to the author to show them you care. Tweet a thanks

Learn to code for free. freeCodeCamp's open source curriculum has helped more than 40,000 people get jobs as developers. [Get started](https://www.freecodecamp.org/learn/)