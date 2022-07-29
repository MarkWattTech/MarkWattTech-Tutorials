  <br>
  <h1 align="center">3 TV Automations YOU NEED!</h1>
  <br>
 <h2 align="center">
<img src="https://github.com/MarkWattTech/MarkWattTech-Tutorials/blob/main/Images/thumbnails/x" width="500">
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
