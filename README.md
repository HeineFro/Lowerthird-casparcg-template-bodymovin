# Lowerthird-casparcg-template-bodymovin
!This read me in process, so futher info will be added continuously.

This is a lower third template example for CasparCG. 
The animation is exported from After Effects with bodymovin plugin(ver. 5.9.6), and then played in the html template with lottie player(ver. 5.10.1).

In this repo there are 2 examples, the only differens between them are the json files, the bodymovin plugin exports. The AE project is also here.

The js and html files are the same - index.js handles the animation, lottie is the player and webcg-framework.umd.js manages the input and control from CasparsCG

The animation looks like this:<br>
![template](https://user-images.githubusercontent.com/61490904/215807027-f6f5bd25-5fa6-4f50-b03f-a5d0f7e20a3b.JPG)

The "Name", "Title" and the image used are dynamic, and can be replaced.
It's possible to add as many dynamic text fields and images you like (limit not found yet)

It´s the naming of the layers in after effects that makes them dynamic in this template, so it looks like this in AE:<br>
![names](https://user-images.githubusercontent.com/61490904/215814464-2f0f93e0-faf5-414a-a894-070aa41cf364.JPG)

Dynamic text or images will have to start with a dot and then the name.<br>
Here the names use are ".f0",".f1" & ".image" for the images, in the official CasparCG client, the key/values will look like this:<br>
![client - Copy](https://user-images.githubusercontent.com/61490904/215815595-ae321658-41fb-40f4-b73b-5a00ac42596e.jpg)




















