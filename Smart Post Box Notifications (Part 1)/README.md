  <br>
  <h1 align="center">Creating a Smart Post Box (Part 1 - Notifications)</h1>
  <br>
 <h2 align="center">
<img src="https://github.com/MarkWattTech/MarkWattTech-Tutorials/blob/main/Images/thumbnails/AlexaPt2.png" width="500">
  </br>
                                                                                                                                          
<p>This is the first video in my Smart Post Box Mini series. In this video I am adding some sensors to the Brizebox Post Box to allow it to notify me when I have post.<a href="https://youtu.be/M3-m2fDttmg" target="_blank">Here</a></p> 
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

