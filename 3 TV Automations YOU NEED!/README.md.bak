  <br>
  <h1 align="center">ALEXA in HOME ASSISTANT (Part 2)</h1>
  <br>
 <h2 align="center">
<img src="https://github.com/MarkWattTech/MarkWattTech-Tutorials/blob/main/Images/thumbnails/AlexaPt2.png" width="500">
  </br>
                                                                                                                                          
<p>In this one we are focusing on all the "SOUND" things that I utilise. Check the video out <a href="https://youtu.be/M3-m2fDttmg" target="_blank">Here</a></p> 
</h2>	


`TTS Notification` - A small example that will play the message on a targeted device
``` yaml
# TTS Notification
service: notify.alexa_media_office_desk_sonos
data:
  data:
    type: tts
  message: Hey
```

</br>

`Sequence` - A small example that will play a preset sequence on a targeted device
``` yaml
# SEQUENCE
service: media_player.play_media
data:
  media_content_type: sequence
  media_content_id: Alexa.Joke.Play
target:
  entity_id: media_player.office_desk_sonos
```
</br>

`Sound` - A small example that will play a sound effect on a targeted device
``` yaml
# SOUND
service: media_player.play_media
data:
  media_content_type: sound
  media_content_id: amzn_sfx_doorbell_chime_01
target:
  entity_id: media_player.office_desk_sonos
```

</br>

`Sound (Dev Sounds)` - A small example that will play one of the dev sound effects on a targeted device
``` yaml
# DEV SOUND
service: notify.alexa_media_office_desk_sonos
data:
  message: <audio src="soundbank://soundlibrary/doors/doors_glass/glass_02"/>
  data:
    type: tts
 ```   
</br>

`Custom MP3` - A small example that allow you to play a custom Alexa Converted Mp3 on a Nabu Casa Hosted HA
``` yaml
# CUSTOM Mp3
service: notify.alexa_media_office_desk_sonos
data:
  message: >-
    <audio
    src='https://yourURL.ui.nabu.casa/local/mp3/potato.mp3'/>
  data:
    type: tts
```

</br>

`Announcement` - A small example will give you an idea of how to use Announcements
``` yaml
# ANNOUNCEMENT
service: notify.alexa_media
data:
  message: hello
  target: media_player.all_echos
  data:
    type: announce
```
