---
title: "Installing Boot9strap (Fredtool)"
---

{% include toc title="Table of Contents" %}

Seedminer-based methods have been replaced by easier, safer methods. Please return to [Get Started](get-started) unless you have a legitimate reason to follow this page (such as broken shoulder buttons).
{: .notice--warning}

### Required Reading

This method of using Seedminer for further exploitation uses your `movable.sed` file to decrypt any DSiWare title for the purposes of injecting an exploitable DSiWare title into the DS Internet Settings application. This requires you to have a DSiWare backup, for example from BannerBomb or the DSiWare Dumper tool.

This is a currently working implementation of the "FIRM partitions known-plaintext" exploit detailed [here](https://www.3dbrew.org/wiki/3DS_System_Flaws).

### What You Need

* A DSiWare Backup (such as the one on SD root from [BannerBomb3](bannerbomb3))
* Your `movable.sed` file from completing [Seedminer](seedminer)
* The latest release of [Frogminer_save](https://github.com/zoogie/Frogminer/releases/latest)
* The latest release of [b9sTool](https://github.com/zoogie/b9sTool/releases/latest)
* The latest release of [Luma3DS](https://github.com/LumaTeam/Luma3DS/releases/latest)

#### Section I - Prep Work

1. Power off your device
1. Insert your SD card into your computer
1. Copy `boot.firm` and `boot.3dsx` from the Luma3DS `.zip` to the root of your SD card
1. Copy `boot.nds` (B9STool) to the root of your SD card
1. Copy the `private` folder from the Frogminer_save `.zip` to the root of your SD card

#### Section II - Fredtool

1. Open [Fredtool](https://3ds.nhnarwhal.com/3dstools/fredtool.php) on your computer
1. Select your `movable.sed` file for the "Your movable.sed" field
1. Select your DSiWare Backup (`<8-character-id>.bin`) file for the "Your dsiware.bin" field
1. Complete the "I'm not a robot" captcha
1. Select "Start"
1. Wait for the process to complete
1. When the process has completed, download your modified DSiWare archive from the site
  + This file contains 2 DSiWare backup files, one clean (unmodified) and one hax (exploited)
1. Navigate to `Nintendo 3DS` -> `<ID0>` -> `<ID1>` -> `Nintendo DSiWare` on your SD card
  + The `<ID0>` will be the same one that you used in [Seedminer](seedminer)
  + The `<ID1>` is a 32 character long folder inside of the `<ID0>`
  + If the `Nintendo DSiWare` folder does not exist, create it inside of the `<ID1>`
1. Copy the `42383841.bin` file from the `output/hax/` folder of the downloaded DSiWare archive (`fredtool_output.zip`) to the `Nintendo DSiWare` folder
1. Reinsert your SD card into your device
1. Power on your device
1. Launch System Settings on your device
1. Navigate to `Data Management` -> `DSiWare`
1. Under the "SD Card" section, select the "Haxxxxxxxxx!" title
1. Select "Copy", then select "OK"
1. Return to main menu of the System Settings
1. Navigate to `Internet Settings` -> `Nintendo DS Connections`, then select "OK"
1. If the exploit was successful, your device will have loaded the JPN version of Flipnote Studio

#### Section III - Flipnote Exploit

If you would prefer a visual guide to this section, one is available [here](https://zoogie.github.io/web/flipnote_directions/).
{: .notice--info}

1. Complete the initial setup process for the launched game until you reach the main menu
  + Select the left option whenever prompted during the setup process
1. Using the touch-screen, select the large left box, then select the box with an SD card icon
1. Once the menu loads, select the face icon, then the bottom right icon to continue
1. Press (X) or (UP) on the D-Pad depending on which is shown on the top screen
1. Select the second button along the top with a film-reel icon
1. Scroll right until reel "3/3" is selected
1. Tap the third box with the letter "A" in it
1. Scroll left until reel "1/3" is selected
1. Tap the fourth box with the letter "A" in it
1. If the exploit was successful, your device will have loaded b9sTool
1. Using the D-Pad, move to "Install boot9strap"
  + If you miss this step, the system will exit to home menu instead of installing boot9strap and you will need to open Nintendo DS Connections and start over from the beginning of Section III
1. Press (A), then press START and SELECT at the same time to begin the process
1. Once completed and the bottom screen says "done.", exit b9sTool, then power off your device
  + You may have to force power off by holding the power button
  + If you see the Luma Configuration screen, continue with the guide without powering off

#### Section IV - Configuring Luma3DS

1. Boot your device while holding (Select) to launch the Luma configuration menu
  + If you encounter issues launching the Luma configuration menu, [follow this troubleshooting guide](https://github.com/zoogie/b9sTool/blob/master/TROUBLESHOOTING.md)
1. Use the (A) button and the D-Pad to turn on the following:
  + **"Show NAND or user string in System Settings"**
1. Press (Start) to save and reboot
  + Your device should load the Home Menu after a short delay. If you get a black screen lasting longer than 5 minutes, [follow this troubleshooting guide](troubleshooting#black-screen-on-sysnand-boot-after-installing-boot9strap)

#### Section V - Restoring DS Connection Settings

1. Power off your device
1. Insert your SD card into your computer
1. Copy the `42383841.bin` file from the `output/clean/` folder of the downloaded DSiWare archive (`fredtool_output.zip`) to the `Nintendo 3DS/<ID0>/<ID1>/Nintendo DSiWare/` folder on your SD card
  + Replace the existing `42383841.bin` file
1. Reinsert your SD card into your device
1. Power on your device
1. Launch System Settings on your device
1. Navigate to `Data Management` -> `DSiWare`
1. Under the "SD Card" section, select the "Nintendo DSi???" title
1. Select "Copy", then select "OK"

___

### Continue to [Finalizing Setup](finalizing-setup)
{: .notice--primary}
