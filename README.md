# Lowerthird-casparcg-template-bodymovin
!This read me in process, so futher info will be added continuously.

This is a lower third template example for CasparCG. 
The animation is exported from After Effects with bodymovin plugin(ver. 5.9.6), and then played in the html template with lottie player(ver. 5.10.1).

In this repo there are 2 examples, the only differens between them are the json files, the bodymovin plugin exports. The AE project is also here.

The js and html files are the same - index.js handles the animation, lottie is the player and webcg-framework.umd.js manages the input and control from CasparsCG

The lowerthird looks like this:<br>
![template](https://user-images.githubusercontent.com/61490904/215807027-f6f5bd25-5fa6-4f50-b03f-a5d0f7e20a3b.JPG)

The "Name", "Title" and a image(casparcg logo) are dynamic, and can be replaced.
It's possible to add as many dynamic text fields and images you like (limit not found yet)

It´s the naming of the layers in after effects that makes them dynamic in this template, so it looks like this in AE:<br>
![names](https://user-images.githubusercontent.com/61490904/215814464-2f0f93e0-faf5-414a-a894-070aa41cf364.JPG)

Dynamic text or images will have to start with a dot and then the name.<br>
Here the names use are ".f0",".f1" & ".image" for the image, in the official CasparCG client, the key/values will look like this:<br>
![client - Copy](https://user-images.githubusercontent.com/61490904/215815595-ae321658-41fb-40f4-b73b-5a00ac42596e.jpg)

To determine which part of animation to play, some markers need to be put on the timeline.<br>
![timeline_framesa](https://user-images.githubusercontent.com/61490904/215841759-381487b5-e436-40df-a6ce-9373a2eeec37.JPG)<br>

There has to be a "play" and a "stop". They follow play and stop called from casparcg.
So set a marker on the first frame of the given part of the animation, and in the naming box type "play"(if it's play), and type in the duration. <br>
![play](https://user-images.githubusercontent.com/61490904/215842190-422ef16d-9721-4511-923a-014128a5b825.JPG)<br>

Do the same for stop - So if your template only has to have the dynamic fields updated on load, and there is no loop animation in it, see the export section of this readme<br>

Update animation<br>
If you need to update the template after the first load'n'play you have to add a marker and name it "update" like play and stop. The duration of the update markercould be 2-3 frames. Then the template will update, when update is called from casparcg. In this example the update animation look like this<br>
![update_](https://user-images.githubusercontent.com/61490904/215846389-9caa6f67-f0d7-4069-90bc-8d35288db52a.gif)

So the update needs a delay so the text can animate out before the template updates, and it is possible to add that delay in the marker dialog. But the the format has to be changed a bit<br>
![update_settings](https://user-images.githubusercontent.com/61490904/215847891-a169c8ce-4eed-42a5-b9b3-87fc84e64bd0.JPG)<br>
Instead of  "update", type name: update and on next line type updateDelay: (the delay in frames, in this case 5) <br>
If there is a loop defined, it will ends its cycle, before the update animation runs.

Loop animation<br>
If you want a loop animation, you can make your loop as part of your timeline, just like play, stop, etc. Then right after play, the loop will start until stop is called. If you have a loop defined, and and you don't have need a have a update marker, the template will update when the loop plays. If stop is called, the loop will finish its cycle before the stop animation. <br>It is also possible to have a break between each loop, but then the format should look like update:<br>
![loop settings](https://user-images.githubusercontent.com/61490904/215850429-3e171826-3193-4a7c-9468-c2f5de5a6092.JPG)<br>
name: loop, loopDelay: (the pause in frames between each loop) <br>
You only have to type in the line loopExternal: true, if the loop is external...  <br>
So if you want to have the loop as an external animation, you make the line: loopExternal: true<br>
If you have the loop, external the update animation(if you have one, will be runing )










































