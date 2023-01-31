# Lowerthird-casparcg-template-bodymovin
!This read me is in process, so some parts of it may changed continuously.

This is a lower third template example for CasparCG. 
The animation is exported from After Effects with bodymovin plugin(ver. 5.9.6), and then played in the html template with lottie player(ver. 5.10.1).

In this repo there are 2 examples, the only differens between them are the json files, the bodymovin plugin exports. The AE project is also here.

The js and html files are the same - index.js handles the animation, lottie is the player and webcg-framework.umd.js manages the input and control from CasparsCG

The lowerthird looks like this:<br>
![template](https://user-images.githubusercontent.com/61490904/215807027-f6f5bd25-5fa6-4f50-b03f-a5d0f7e20a3b.JPG)

The "Name", "Title" and a image(casparcg logo) are dynamic, and can be replaced.
It's possible to add as many dynamic text fields and images you like.

It´s the naming of the layers in after effects that makes them dynamic in this template, so it looks like this in AE:<br>
![names](https://user-images.githubusercontent.com/61490904/215814464-2f0f93e0-faf5-414a-a894-070aa41cf364.JPG)

Dynamic text or images will have to start with a dot and then the layer name.<br>
Here the names used are ".f0",".f1" & ".image" for the image, and to connect to those fields in the official CasparCG client, the key/values will look like this:<br>
![client - Copy](https://user-images.githubusercontent.com/61490904/215815595-ae321658-41fb-40f4-b73b-5a00ac42596e.jpg)<br>
To test the image replacing you can try to type "images/img_1.png" in the key: image

To determine which part of animation to play, some markers needs to be put on the timeline in AE.<br>
![timeline_framesa](https://user-images.githubusercontent.com/61490904/215841759-381487b5-e436-40df-a6ce-9373a2eeec37.JPG)<br>

There has to be a "play" and a "stop". They follow play and stop called from casparcg.
So set a marker on the first frame of the given part of the animation, and in the naming box type "play"(if it's play), and type in the duration. <br>
![play](https://user-images.githubusercontent.com/61490904/215842190-422ef16d-9721-4511-923a-014128a5b825.JPG)<br>

Do the same for stop - So if your template only has to have the dynamic fields updated on load, and there is no loop animation in it, see the fonts section of this readme<br>

Update animation<br>
If you need to update the template after the first load'n'play you have to add a marker and name it "update" like play and stop. The duration of the update marker could be 2-3 frames. Then the template will update, when update is called from casparcg. In this example the update animation look like this<br>
![update_](https://user-images.githubusercontent.com/61490904/215846389-9caa6f67-f0d7-4069-90bc-8d35288db52a.gif)

So the update needs a delay so the text can animate out before the template updates, and it is possible to add that delay in the marker dialogbox. But the the format has to be changed a bit<br>
![update_settings](https://user-images.githubusercontent.com/61490904/215847891-a169c8ce-4eed-42a5-b9b3-87fc84e64bd0.JPG)<br>
Instead of "update", type "name: update" and on next line type "updateDelay: (the delay in frames, in this case 5)" <br>
If there is a loop defined, it will ends its cycle, before the update animation runs.

Loop animation<br>
If you want a loop animation, you can make your loop as part of your timeline, just like play, stop, etc.<br>![loop](https://user-images.githubusercontent.com/61490904/215852678-5abe4d43-8071-4fe2-be25-a5ef33b26059.gif)
<br> Then right after play, the loop will start until stop is called. If you have a loop defined, but no update marker, the template will update when the loop plays. If stop is called, the loop will finish its cycle before the stop animation. <br>It is also possible to have a break between each loop, but then the format should look like update:<br>
![loop settings](https://user-images.githubusercontent.com/61490904/215850429-3e171826-3193-4a7c-9468-c2f5de5a6092.JPG)<br>
"name: loop", "loopDelay: (the pause in frames between each loop)" <br>
You only have to type in the line loopExternal: true, if the loop is external...  <br>
So if you want to have the loop as an external animation, you make the line: loopExternal: true<br>
If you have the loop external, the update animation(if you have one) will update immediately, and the loop just keeps runinng, but if you stop it, the loop will finish first. <br>
The external loop has to be named "loop.json", when you export it. And in that timeline, you will have to as minimum put in a marker named: "loop", and set the duration of the loop. In this example, there is also a play and stop animation.<br>
Loop delay, is set in the loop marker in the main timeline.

!!disclaimer!! this will be changed in a update<br>
When there is a loop running, and a update(if defined) is called, the template calculates how many frames left of the loops cycle and delays the update with the correct time. But right now that duration(only for the calculation) is taken from the main animation, so if you have a external loop, you will have to set the duration of the main loop marker, and in the loop timeline, to the same time.<br>

Export:<br>
Export the animation, and name it: data.json, and have all the js files from on of the templates in this repo, and give it a spin. If you have any images, bodymovin will create a folder named: "images" and make a copy of the images used(this can be changed in bodymovin settings) and then lottie player when playing will look for that folder/images, if the images are not dynamic.<br>
Fonts<br>
There are different ways to control fonts with bodymovin and this template.<br> Here are the 2 ways I use:<br>
Glyphs: Add a text layer to the animation, type in all letters, numbers, etc. for every font used. Move that text layer(s) out the visible area, and make sure when you export it with bodymovin, that glyphs is checked.<br>

Fonts paths
Uncheck glyphs<br>
![glyphs - Copy](https://user-images.githubusercontent.com/61490904/215886889-d00748a2-ce1f-462c-92cf-734f55ec7097.JPG) <br>
And when the fonts dialogbox popup during export do like this: <br>
![naming_fonts - Copy](https://user-images.githubusercontent.com/61490904/215887302-0c3390f7-6b1a-48be-99e7-8df55d9bfc25.png)<br>

Rename the “Font Famliy”, so it is the same as the name in the red dotted box, and then write the path in the “Font Path”
For each font used, with a path typed in in the export, the template adds a “@font-face” to the style with the font-family and the path, when its loaded.

I made a fonts folder in the template, so here the path is "./fonts/nameOfFont.ttf"

This is just a example, a starting point. There is a lot way to do things different, to fit other kinds of templates. So let me know if there anything not working as it should or you have any questions about the templates.

Further reading about bodymovin/lottie:<br>

























































