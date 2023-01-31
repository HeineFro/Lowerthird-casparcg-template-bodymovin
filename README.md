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






























