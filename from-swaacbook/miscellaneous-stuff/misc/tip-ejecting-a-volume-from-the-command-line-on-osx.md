
# Table of Contents

1.  [Tip: Ejecting a volume from the command line on OSX](#tip-ejecting-a-volume-from-the-command-line-on-osx)


<a id="tip-ejecting-a-volume-from-the-command-line-on-osx"></a>

# Tip: Ejecting a volume from the command line on OSX

-   published date: 2016-05-28 06:39
-   keywords: ["command-line", "diskutil", "eject", "osx", "tips"]
-   source:

This turns out to be pretty simple.

    $ diskutil list # find the disk you want to eject
    $ diskutil eject /dev/disk2 # eject it
    # wait...

`diskutil eject` by itself will give help on the verb.

