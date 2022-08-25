  <br>
  <h1 align="center">A DIY Raspberry Pi Kiosk (HOME ASSISTANT)</h1>
  <br>
 <h2 align="center">
<img src="https://github.com/MarkWattTech/MarkWattTech-Tutorials/blob/main/Images/thumbnails/kiosk.png" width="500">
  </br>
                                                                                                                                          
<p>In this one I show you how to setup and build your own DIY Home Assistant Kiosk. Check the video out <a href="https://youtu.be/M3-m2fDttmg" target="_blank">Here</a></p> 
</h2>	

<h2> Commands for Pi (In order of Use) </h2>
<p> Use the below commands in combination with my tutorial video to help setup a working Raspberry Pi Kiosk. </p>
</br>

`SSH` - Connect to our Pi using Secure Shell
```
ssh pi@touchpi.local
# You will need to ammend this to be your username and hostname values.

ssh username@hostname.local 
#local as we are on the same network

# You can also use the IP address
ssh username@192.xxx.x.xx
```


`Command 1` - Check and Update our Pi
```
sudo apt-get update -y
sudo apt-get upgrade -y
```

</br>

`Command 2` - Install minimum GUI components (GUI kit used for Chomium)
```
sudo apt-get install --no-install-recommends xserver-xorg x11-xserver-utils xinit openbox
```

</br>

`Command 3` - Install Chromium Web browser (We are using Chromium to display webpage - you can use others)
```
sudo apt-get install --no-install-recommends chromium-browser
```

</br>

`Command 4` - Edit Openbox config (Openbox Window manager edits)
```
sudo nano /etc/xdg/openbox/autostart

#In the nano editor you will then need to paste in the following config (tip use right click to paste)

# If you want to use XFCE config tools...
#
#xfce-mcs-manager &
xset -dpms            # turn off display power management system
xset s noblank        # turn off screen blanking
xset s off            # turn off screen saver


# Remove exit errors from the config files that could trigger a warning

sed -i 's/"exited_cleanly":false/"exited_cleanly":true/' ~/.config/chromium/'Local State'

sed -i 's/"exited_cleanly":false/"exited_cleanly":true/; s/"exit_type":"[^"]\+"/"exit_type":"Normal"/' ~/.config/chromium/Default/Preferences

# Run Chromium in kiosk mode
chromium-browser  --noerrdialogs --disable-infobars --enable-features=OverlayScrollbar --kiosk $KIOSK_URL --check-for-update-interval=31536000
```

</br>

`Command 5` - Setup Openbox environment (The URL we want to pass in)
```
sudo nano /etc/xdg/openbox/environment

# use the above command to enter the nano editor for the environment and paste in the following line

export KIOSK_URL=https://YourHomeAssistant_URL:8123
```

</br>

`Command 6` - Start the X server on boot
```
# Check if bash_profile exists (If it does just directly edit it)
ls -la ~/.bash_profile

#If it doesn't exist (Create it)
touch ~/.bash_profile
```

</br>

`Command 7` - Edit Bash Profile
```
sudo nano ~/.bash_profile

# After running the above command enter the following line in the file
[[ -z $DISPLAY && $XDG_VTNR -eq 1 ]] && startx -- -nocursor
```

</br>

`Command 8` - Check ~/.bash_profile
```
source ~/.bash_profile
```

</br>

`Command 9` - Reboot Pi (To a hopefully working Kiosk!)
```
sudo reboot
```


</br>
<p> The code for this guide was based off <a href="https://desertbot.io/blog/raspberry-pi-touchscreen-kiosk-setup" target="_blank">Desertbots</a></p>  Kiosk guide. I modified the commands and config to suit the 7inch screen for the TS7 Pro
and to remove some other things like hiding scroll bars.</p>
