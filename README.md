# Final Project!

## Design Doc
[Click here to view the design doc!](https://docs.google.com/document/d/1dWmwpq-6FkHq4MmlyaFJkvPfyQh6L1r4fYkhGaTlGOI/edit?usp=sharing)

For this project, we want to explore tools like Unreal Engine and Houdini to create a procedurally generated underwater environment. We were primarily inspired by Atlantis concept art made by various artists. 

**Specifications:**
- Different styles of procedural buildings; Greek-inspired architecture
- Big landmarks such as coliseums
- Breaking simulations on architecture
- City structure with walkways
- Niagara system fish flocks
- Different fish such as jellyfish, stingray, sharks, etc.
- Ornaments like benches, streetlights, etc.
- L system kelp & coral
- Water caustics
- Procedural materials: Mossy & damaged marble; Sand w/ starfish, barnacles, fossils etc.

## Milestone 1: Implementation part 1

### Ray's Milestone 1
For this milestone, I implemented some basic building structure to work with the map layout. 

Each building is built off a base, which is an irregular polygon with some number of vertices. Each cell generated by the voronoi structure from Neha's implementation this week is used as a base for a building. 

To start with, I calculate the area of the base, which will determine the type of building spawned by the voronoi cell. These sizes are small, medium, and large. Small "buildings" are basic park structures with plants/benches, medium buildings are normal houses, and large buildings are houses with courtyards. This week I implemented houses with courtyards because those are the most difficult, and I can build medium-sized buildings from them.

In this example, I'm hard-coding the base as a 20-sided circle, and generating a large building on top of it.

![image](https://github.com/user-attachments/assets/bf1e4750-a930-4d5d-a6ef-2a1932b301ff)

First, I do some extrusions to get the base thickness of the wall. Then I search around the input base for an appropriate area to place the entrance to the courtyard, which is pictured here.

![image](https://github.com/user-attachments/assets/bf689699-c9e8-4cc9-a697-9f62f04c9eed)

Using more extrusions and a chain node around the perimeter of the base shape, I generate walls and windows. I made sure to add a check for the courtyard entrance so that no windows get placed there. Also, I decided to create each individual wall, since I plan on adding a destruction simulation later and want to show the structure of the house where the roof caves in.

![image](https://github.com/user-attachments/assets/42483867-d8ff-4579-a84e-efba9aa5069a)

Here's the draft for a tiled roof, along with placements for plants and such in the courtyard! I plan on polishing the building up much more in the next milestone.

![image](https://github.com/user-attachments/assets/45136982-e8c5-4f63-b5dd-c4a9f56d8f90)

Here's another draft for a pillar tool that I plan on using in the next milestone.

![image](https://github.com/user-attachments/assets/77f1aec9-32e5-4b54-8dd8-43678d9b591c)


## Neha's Milestone 1

For the first milestone, I followed along with this <a href="https://www.sidefx.com/tutorials/foundations-build-a-city-with-pdg/" />tutorial</a> about PDG's in Houdini. This tutorial went over how to construct a stereotypical grid-based city using Houdini PDG's. In order to follow our Atlantis theme, rather than a grid, we used two circles that were broken up by different Voronoi fractures. The bigger voronoi fracture created the overall layout of the city, while the smaller voronoi fracture further split the larger shape and created smaller streets and tiles on which to place our buildings/structures. 

<img src="https://github.com/sgmq0/underwater-city/blob/main/Screenshot%202024-11-13%20212405.png?raw=true" />

The process of creating buildings on the tiles was done via a topnet. Which can be seen here:

<img src="https://github.com/sgmq0/underwater-city/blob/main/Screenshot%202024-11-13%20213153.png?raw=true" />

Here is a picture of the buildings in our city grid! 

<img src="https://github.com/sgmq0/underwater-city/blob/main/Screenshot%202024-11-13%20203454.png?raw=true" />
<img src="https://github.com/sgmq0/underwater-city/blob/main/Screenshot%202024-11-13%20213020.png?raw=true" />

I also made some additional assets (that are not yet in our city): 

Lamppost: 

<img src="https://github.com/sgmq0/underwater-city/blob/main/Screenshot%202024-11-13%20173257.png?raw=true" />

Window (from Homework 3): 

<img src="https://github.com/sgmq0/underwater-city/blob/main/Screenshot%202024-11-13%20222632.png?raw=true" />

## Milestone 2: Implementation part 2

### Ray's Milestone 2
Although I originally planned to model some fish and create the materials this week, I actually spent all of it working on the house geometry (and offloaded the fish models to Neha, sorry...). Right now, the houses are built off voronoi cells, but Elyssa suggested that I use labs subdivision to create more rectangular lots which I think would be much easier to work with. 

This week I realized a pretty big thing I didn't like about the scene, which was that scale-wise, it felt more like a "village" than a town. So I also expanded on the city structure by giving it some sick walls to add scale to the scene. 

![image](https://github.com/user-attachments/assets/2481412c-f5fe-4826-bb27-f2a681ef5c2e)
![image](https://github.com/user-attachments/assets/b3ae2248-f0c0-4c64-8e34-637ce78661e0)

Next week I'll refactor the house-generating code to have it work with the new rectangular lots. Here's what the houses look like currently (without Neha's assets). They're not included yet so all you see are empty lots, but they'll be added in the final output.

![image](https://github.com/user-attachments/assets/dc979109-61b0-4dda-983e-0df99e2885e7)

Finally, I threw the model into Unreal to do some lighting and rendering stuff. I created a distance fog material to make it look more like it's underwater. Here's a demo video as well as a screenshot!

https://github.com/user-attachments/assets/73a48263-dff8-4f6e-a5d7-031990f8ea78

![image](https://github.com/user-attachments/assets/3660a262-a3fc-4df2-a755-29552eae22da)


I'll probably also add lots to the more distant parts of the city, as well as include Neha's awesome assets in the house generation! After that, all that's left is the environment, rendering wizardry and texturing. 

### Neha's Milestone 2

Unfortunately, I did not make as much progress as I had hoped due to being away at a conference (my apologies, Ray : ( )), but I plan on getting more things done during break! 

I mainly worked on some additional asset creation:

![img](https://github.com/sgmq0/underwater-city/blob/main/Screenshot%202024-11-16%20160504.png?raw=true)

https://github.com/user-attachments/assets/db23a7e5-a1ae-4f7c-8aa1-59f4b7e22f44

(The kelp was created with the help of this tutorial series: https://www.youtube.com/watch?v=c8vst8202dI&t=236s ) 

I will focus on adding more vegetation (like coral, perhaps) and fish! I will be modeling and rigging a shark, which will be fun. 

### Ray's Milestone 3

This week I finalized the house condtruction and city generator, implementing Neha's wonderful assets. I also did a bunch of UV unwrapping.

I created three different types of houses to give the scene visual variety!

I also created a roof tile and stone block material for the houses.

Actually, the most important part of this week's tasks was to get everything into Unreal. I already got the pipeline figured out in in the last milestone so I didn't run into many major issues, but I found it really tedious...

In Unreal, I messed with more of the shading, applied the textures, made niagara system fish schools, and planted foliage to create a niceish scene.

![image](https://github.com/user-attachments/assets/b36dc66e-1077-4600-b396-f7a8b54c9889)
![image](https://github.com/user-attachments/assets/2df5d925-6547-45f6-b294-bf935f640032)
![image](https://github.com/user-attachments/assets/624486f8-58e7-4756-abff-329ae7c1597c)
![image](https://github.com/user-attachments/assets/f0d74ab5-2b63-4829-af32-0625102da761)
![image](https://github.com/user-attachments/assets/f179c9db-4ca2-40ca-9aa5-28907b55a967)
![image](https://github.com/user-attachments/assets/849db1b5-7e36-46af-a595-9cfd643a1241)


### Neha's Milestone 3

I added some additional elements to our city! 
The following were not procedurally made but rather modeled and textured using blender and zbrush:
![Screenshot 2024-11-30 235545](https://github.com/user-attachments/assets/d14e8d9a-1f5c-488b-a328-9d63985e707a)
![Screenshot 2024-11-29 214127](https://github.com/user-attachments/assets/bf754073-cc05-4f48-b8b6-9b65cf8e933b)
![Screenshot 2024-11-29 151405](https://github.com/user-attachments/assets/aaee108c-f23c-45a0-90bf-e5227a596913)
![Screenshot 2024-12-03 150300](https://github.com/user-attachments/assets/ce875db1-b44e-4340-8f2b-b2fb34a0b81d)


There is also now a procedural coral generator (which uses an l-system):
![Screenshot 2024-12-01 153708](https://github.com/user-attachments/assets/85464cd1-769a-4359-a653-fdfedead62b1)


## Final submission 

### Breakdown of our work 
Can be found here: https://docs.google.com/presentation/d/1kqFuRXgb6lPP4pP7EWAIM0FR_dFDIZgKtF1_NOb8s4E/edit?usp=sharing

Here is a quick summary of what we accomplished: 

We first created a city layout for our buildings to be placed on. This layout was created using PDGs in Houdini. We followed the official PDG tutorial and modified it to our liking. We mainly added logic to create the grid procedurally (the original tutorial used a PNG). 

Our logic involves using a Voronoi fracture to create the general shape and then lots subdivision to ensure we still have a city or town-like structure, but with an added degree of organicness.

Ray designed three greek-inspired procedural buildings to populate the city, which build off of the generated lots, as well as a wall around the city's perimeter. 

Neha created some additional assets for the city/general atmosphere of an underwater environment. These included procedural assets (coral, kelp, lamppost, building window, building door) and non-procedural assets (whale, shark, clownfish, bench). The procedural assets are all parameterized. 

Then, we both created procedural textures using Substance 3D Designer. These materials include: sand, marble, stone, roof tiles, and aged wood. 

Finally, our project came together in Unreal! 

### Final Results 

https://github.com/user-attachments/assets/fd97d639-1ee2-46ca-be51-3519c6e4a809

### Post-Mortem 

We are happy with what we accomplished overall for this project! We fulfilled most of our initial objectives and have a finished result that we are both very proud of. It was also a fun experience to try new software and explore new workflows in software we are comfortable with. (In Neha's case, I have never used a substance designer before, and I definitely want to explore it more in the future.) (In Ray's case, I'm pretty new to doing lighting and rendering in Unreal.)

For future work or aspects that we wish we had time to include, we originally had a vision of a ruined or abandoned city. However, the destruction sims would have been beyond the capability of our computers (sadly). We were also hoping to game-ify the project slightly to allow a player to be able to traverse our city and possibly interact with various elements. We also hoped to have a 'town center' that would be a coliseum. Our PDG does allow for a town center; however, we unfortunately did not have the time to create the coliseum (either procedurally or non-procedurally). We additionally decided not to rig our fish in order to focus on polishing/fine-tuning other aspects of our project. 

### Attribution 

Tutorial for the kelp:
https://www.youtube.com/watch?v=T2Xmff4WqPc

Tutorial for coral:
https://www.youtube.com/watch?v=h8cEtur8_Sw&t=3s

Tutorial for procedural wood texture:
https://www.adobe.com/learn/substance-3d-designer/web/creating-old-wood-planks-in-substance-3d-designer?locale=en&learnIn=1

Tutorial for procedural marble texture:
https://www.youtube.com/watch?v=zGOLLSQnvYo

Tutorial for procedural sand texture:
https://www.youtube.com/watch?v=oPauF1fwZuU

References to create stone bench:
https://p3dm.ru/files/furniture/other_furniture/11266-stone-bench.html

References to create the whale: 
- https://uk.pinterest.com/pin/366832332142578260/
- https://stock.adobe.com/images/blue-big-whale-top-view-watercolor-painting/146278230

References to create the shark: 
- https://www.istockphoto.com/photo/great-white-shark-isolated-gm863397250-143145391
- https://www.alamy.com/great-white-shark-illustration-on-white-background-image459614990.html?imageid=11ECBDD0-B6A5-497A-8318-5DB602B985E7&p=1250975&pn=1&searchId=6c25fd81538205d40c7e6285a16d448f&searchtype=0

References to create the clownfish: 
- https://www.nationalgeographic.com/animals/fish/facts/clownfish
- https://www.shutterstock.com/image-photo/two-clown-fishes-saltwater-aquarium-top-218322091
