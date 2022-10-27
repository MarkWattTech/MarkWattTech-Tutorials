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
# Turn on Post to Collect

```
<p> Since creating the video I have opted to move post box notifications into a node red flow to make them visually easier to see.
<img src="https://github.com/MarkWattTech/MarkWattTech-Tutorials/blob/main/Images/images/post_box_node_red.png" width="500">
</br>

