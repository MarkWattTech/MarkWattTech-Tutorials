  <br>
  <h1 align="center">Building a Smart Post Box (Notifications)</h1>
  <br>
 <h2 align="center">
<img src="https://github.com/MarkWattTech/MarkWattTech-Tutorials/blob/main/Images/thumbnails/BrizeBox.png" width="500">
  </br>
                                                                                                                                          
<p>This is the first video in my Smart Post Box Mini series. In this video I am adding some sensors to the Brizebox Post Box to allow it to notify me when I have post. Watch the full video <a href="" target="_blank">Here</a></p> 
</h2>	

<p> My post box has two methods for receiving post : </p>
 <ul>
  <li>Letterbox</li>
  <li>Mail draw</li>
</ul>
    <p>The only way to get the post out of the box is via the locked backdoor (Brizebox doors are reversible so it can be on the front if you wish).</p>
 <p> The simplest soloution I had was to attatch contact sensors to each three openings (letterbox, mail draw, backdoor). This allows me to then detect which input is open. I created a toggle helper entity called "<b>Post to Collect</b>". This acts as a switch to tell me if there is any post to collect.</p>
 
 <p> Opening the letterbox or mail draw runs an automation that turns the <b>Post to collect</b> boolean on. This signals there is post to be collected.</p>
 

`Turn on Post to Collect` - An automation to turn on the post to collect boolean if the letterbox or mail draw is opened
``` yaml
# Post Box Mail Draw Opened
mode: single
trigger:
  - platform: state
    entity_id:
      - binary_sensor.post_box_maildraw_contact
    to: "on"
condition: []
action:
  - service: input_boolean.turn_on
    data: {}
    target:
      entity_id: input_boolean.post_to_collect

# Post Box Letterbox Opened
mode: single
trigger:
  - platform: state
    entity_id:
      - binary_sensor.post_box_letter_contact
    to: "on"
condition: []
action:
  - service: input_boolean.turn_on
    data: {}
    target:
      entity_id: input_boolean.post_to_collect
```
</br>

<p> Since creating the video I have opted to move post box notifications into a node red flow to make them visually easier to see.</p>
</br>
<img src="https://github.com/MarkWattTech/MarkWattTech-Tutorials/blob/main/Images/images/post_box_node_red.png" width="500">
</br>


`Announcements for Mail` - An automation to send a series of announcemenrts/notifications in parallel on mail delivery

``` yaml
# Announcements for mail
alias: You have mail announcement
description: ""
trigger:
  - platform: state
    entity_id:
      - input_boolean.post_to_collect
    to: "on"
condition: []
action:
  - service: notify.mobile_app_marks_iphone
    data:
      message: There's some post waiting for you.
      title: You have mail!
  - service: tts.cloud_say
    data:
      entity_id: media_player.kitchen_sonos
      message: "Congratulations, you have mail! "
  - service: notify.mobile_app_rachels_iphone_11pro_2
    data:
      message: >-
        You have some post to collect from the outside postbox. Maybe you could
        collect it? 
      title: You have Post!
  - service: notify.marks_lametric
    data:
      message: There's Post in the Postbox!
      data:
        icon: "2659"
        sound: positive2
        cycles: 0
mode: parallel
max: 10
```
