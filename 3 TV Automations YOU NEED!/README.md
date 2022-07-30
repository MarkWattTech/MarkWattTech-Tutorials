  <br>
  <h1 align="center">3 TV Automations YOU NEED!</h1>
  <br>
 <h2 align="center">
<img src="https://github.com/MarkWattTech/MarkWattTech-Tutorials/blob/main/Images/thumbnails/x" width="500">
  </br>
                                                                                                                                          
<p>In this one I show you 3 TV based automations that I utilise in my personal setup. Check the video out <a href="https://youtu.be/M3-m2fDttmg" target="_blank">Here</a></p> 
</h2>	

<h2> ADB Command for Netflix </h2>

`ADB Command Play Video On Netflix` - This script will play a targeted program on Netflix
``` yaml
# Play Peppa Pig on Netflix
alias: Shield TV Play Peppa
sequence:
  - service: androidtv.adb_command
    data:
      command: >-
        input keyevent MENU && am start -n com.netflix.ninja/.MainActivity  -a
        android.intent.action.VIEW -d https://www.netflix.com/watch/{PROGRAM-ID} -f
        0x10808000 -e source 30 && input keyevent 23 && input keyevent 23 &&
        input keyevent 23
    target:
      entity_id: media_player.android_tv_192_168_0_104
mode: single

# E.g. ID - 80025592 = Peppa Pig. Change {PROGRAM-ID} to your chosen ID

```

`Copy Just The Command`
``` yaml
        input keyevent MENU && am start -n com.netflix.ninja/.MainActivity  -a
        android.intent.action.VIEW -d https://www.netflix.com/watch/{PROGRAM-ID} -f
        0x10808000 -e source 30 && input keyevent 23 && input keyevent 23 &&
        input keyevent 23
```
</br>

<h2> ADB Command for Disney Plus </h2>

`ADB Command Play Bluey on Disney Plus` - A small script to play Bluey on Disney Plus
``` yaml
# Play Bluey on Disney Plus
alias: Shield TV Play Bluey
sequence:
  - service: androidtv.adb_command
    data:
      command: >-
        input keyevent MENU &&  am start -a
        "android.search.action.GLOBAL_SEARCH" --es query "play bluey on disney
        plus" -e source 30 && input keyevent 23 && input keyevent 23 && input
        keyevent 23
    target:
      entity_id: media_player.android_tv_192_168_0_104
  - delay:
      hours: 0
      minutes: 0
      seconds: 2
      milliseconds: 0
  - service: androidtv.adb_command
    data:
      command: input keyevent 23
    target:
      entity_id: media_player.android_tv_192_168_0_104
mode: single
# You can replace "Play Bluey on Disney Plus" with anything you want to launch. E.g "Show me Eufy Cameras", "Open MarkWattTech on YouTube"
```

`Copy Just The Command`
``` yaml
        input keyevent MENU &&  am start -a
        "android.search.action.GLOBAL_SEARCH" --es query "play bluey on disney
        plus" -e source 30 && input keyevent 23 && input keyevent 23 && input
        keyevent 23
```
</br>
<h2> Find TV Remote Command </h2>
</br>

`Copy Just The Command`
``` yaml
        am start -a android.intent.action.VIEW -d -n com.nvidia.remotelocator/.ShieldRemoteLocatorActivity
```
