<span class="menu-title" style="display: none">Title</span>

# Azure Durable Functions

Sergey Zavoloka

// TODO: update the title according to finished content, insert contacts, picture etc

Note:
Thank you for comming.

My name is Sergey. 

I'll tell you about Azure Durable functions.

---
<span class="menu-title" style="display: none">Agenda</span>

//TODO: update agenda according to finished content

## Agenda
- Domain
- Durable functions
- Application
- Tips

Note:


---
<span class="menu-title" style="display: none">Tech Days 2012</span>

### TechDays 2012

![Image](./assets/md/assets/techDays2012.png) <!-- .element: class="fragment" -->

Note:
1.
In 2012 I attended TechDays. 
Many talks were dedicated to Windows Phone 7 development and were to inspire people to develop applications.

2.
Like this guy(Rob Miles). Make Stuff and have fun! Bottom line was that when he was young it was difficult to build something and reach a big audence. Now it is simple. 
So, I did and developed (Move to next slide)

---
<span class="menu-title" style="display: none">Smartest Eraser</span>

### Smartest Eraser

![Image](./assets/md/assets/smartest_eraser.png)

Note:
An app that allows you to remove somebody or something from a picture like it never was there.
Here is a demonstration video about the app (Move to the next slide)

---
<span class="menu-title" style="display: none">Smartest Eraser Video Demo</span>

Video Demo

<iframe width="840" height="472" src="https://www.youtube.com/embed/QMWHeGsVjFA?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

Note:
1. Watch video

2. After the release, the app had a success. Many downloads, top positions in its category. Microsoft organized a Next App Star competition. (Next slide)

---
<!-- .slide: data-background-image="./assets/md/assets/nextappstar.png" data-background-size="auto 45%" data-background-color=" " data-background-position="left" -->

<span class="menu-title" style="display: none">NextAppStar</span>

- Next App Star Competition
- 9000 apps participated  <!-- .element: class="fragment" -->
- only 128 in final  <!-- .element: class="fragment" -->
- Smartest Eraser in top 32  <!-- .element: class="fragment" -->

Note:
1. [Comment the bullets]

2. The result was good I was almost happy. **But** since the audence became bigger and many people used app just out of curiosity I got (Next slide)

---

<span class="menu-title" style="display: none">Bad reviews</span>

### Bad reviews!

![Image](./assets/md/assets/bad_reviews.png)

Note:
People commented that the app ruins pictures, distorts them and not smart at all.
And thay were absolutely right. Because the app used Seam Carving algorithm.(Next slide)

---

<span class="menu-title" style="display: none">Seam carving</span>

### Seam Carving

![Image](./assets/md/assets/seams.jpeg)

Note:
The algorithm simply searches a sequence of less important/noticeable pixels (in image processing terms - pixels with minimal energy) and removes them. After that to restore the size it searches for the sequence again and copies it.
 That leads to the distortions (Show examples)


---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">SeamCarving Bridge Sample. Original</span>

![Image](./assets/md/assets/bridge_orig.jpg)

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">SeamCarving Bridge Sample. Marked</span>

![Image](./assets/md/assets/bridge_marked.png)

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">SeamCarving Bridge Sample. Processed</span>

![Image](./assets/md/assets/bridge_sc.png)

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">SeamCarving Cheese Sample. Original</span>

![Image](./assets/md/assets/cheese_orig.jpg)

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">SeamCarving Cheese Sample. Marked</span>

![Image](./assets/md/assets/cheese_marked.png)

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">SeamCarving Cheese Sample. Processed</span>

![Image](./assets/md/assets/cheese_sc.png)

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">SeamCarving Temple Sample. Original</span>

![Image](./assets/md/assets/temple_orig.jpg)

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">SeamCarving Temple Sample. Marked</span>

![Image](./assets/md/assets/temple_marked.png)

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">SeamCarving Temple Sample. Processed</span>

![Image](./assets/md/assets/temple_sc.png)

Note: 

Simplest way at this point was to explain the constraints. 

---

<span class="menu-title" style="display: none">App constraints</span>

### App constraints

<img src="./assets/md/assets/se_restrictions.png"  height="500" /> 

Note:
I started to present the constraints to users before they open a picture.
It helped. **A bit** It felt like they ruine everything around (Next slide)


---
<span class="menu-title" style="display: none">User riots</span>

![Image](./assets/md/assets/riots.jpg)

Note:
Including the rating of the app and because they wanted more intellingent functionality

So I took it serious and started to work really **really** hard (Next slide)

---

<span class="menu-title" style="display: none">Hard working joke</span>

<img src="./assets/md/assets/lazy.jpg"  height="500" /> 

Note:
Ah, wrong picture... (Next slide)

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Hard working</span>

<img src="./assets/md/assets/hardworker.png"  height="500" /> 

Note:
So, I workered really **really** hard!

I was studying scintific papers, I followed different image processing online courses.

It took time, but still I achieved my goal and created a library that allowed (Next slide)

---

<span class="menu-title" style="display: none">Simple inpaint code</span>

```CSharp
var inpainter = new Inpainter();
var result = inpainter.Inpaint(imageArgb, markupArgb, donors);
result
    .FromArgbToBitmap()
    .SaveTo(resultPath, ImageFormat.Png)
    .ShowFile();
```

Note:

To inpaint of to perform the content-aware fill

What happened with the issues? (Next slide)

---

<span class="menu-title" style="display: none">Wexler Bridge Sample. Original</span>

![Image](./assets/md/assets/bridge_orig.jpg)

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Wexler Bridge Sample. Marked</span>

![Image](./assets/md/assets/bridge_marked.png)

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Wexler Bridge Sample. Processed</span>

![Image](./assets/md/assets/bridge_wex.png)

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Wexler Cheese Sample. Original</span>

![Image](./assets/md/assets/cheese_orig.jpg)

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Wexler Cheese Sample. Marked</span>

![Image](./assets/md/assets/cheese_marked.png)

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Wexler Cheese Sample. Processed</span>

![Image](./assets/md/assets/cheese_wex.png)

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Wexler Temple Sample. Original</span>

![Image](./assets/md/assets/temple_orig.jpg)

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Wexler Temple Sample. Marked</span>

![Image](./assets/md/assets/temple_marked.png)

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Wexler Temple Sample. Processed</span>

![Image](./assets/md/assets/temple_wex.png)

Note:
The results were satisfying. I was anticipating how users of Smartest Eraser will be happy.

The only thing I needed to do is to use my new library. **But** (Next slide)

---
<span class="menu-title" style="display: none">Slow mobiles</span>

<img src="./assets/md/assets/slow_mobiles.gif"  height="500" /> 

Note: 
Mobiles are not capable of required computation power

The reason is the complexity of the new method. Let me explain it shortly.
Suppose we have following image (Next slide)

---
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process001.png"  height="500" /> 

Note:
And we want to remove this gear

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process002.png"  height="500" /> 

Note:
So we need to find the values of these pixels. 

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process003.png"  height="500" /> 

Note:
There are more, but for the sake of simplicity we imagine that these are only six these.

How do we do that?

Let's start with finding a value of the pixel in the middle.(Next slide)

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process004.png"  height="500" /> 

Note:
In order to do that we will analize patches that contain this pixel. 

For the simplicity we will use patches of size 3x3  (Next slide)

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process005.gif"  height="500" /> 

Note:
The pixel is a part of 9 different patches. And what we going to do now. We will find a similar patch for each of these 9 at the picture and reconstruct the value based on statistics of the 9 patches. (Next slide)

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process006.png"  height="500" /> 

Note:
We have found a similar patch for one of the 9.


---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process007.png"  height="500" /> 

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process008.png"  height="500" /> 

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process009.png"  height="500" /> 

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process010.png"  height="500" /> 

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process011.png"  height="500" /> 

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process012.png"  height="500" /> 

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process013.png"  height="500" /> 

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process014.png"  height="500" /> 

Note:
We have now patches that suggest us the value of the pixel

These are the values.(Next slide)

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process015.png"  height="500" /> 

Note:
And if we will take an average of their value(Next slide)

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process016.png"  height="500" /> 

Note:
We will get the more or less reliable value of the pixel

Lets set this value(Next slide)

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process017.png"  height="500" /> 

Note:
The process is repeated (Next slide)


---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process_rest.gif"  height="500" /> 

Note:
for the each pixel in the area until all the values are not calculated
In the reality the image is bigger and pixels are smaller. That is why the whole process is done on an image pyramid.

---
<span class="menu-title" style="display: none">Image Pyramids</span>

<img src="./assets/md/assets/inpaint/pyramids.png"  height="500" /> 

Note:
Image pyramid is built by scaling down the original image by factor 2. After that we run the algorithm at the lowest scale and after that propagate results to the upper level and perform processing.

---
<span class="menu-title" style="display: none">Patch Match</span>

### Critical part
- Nearest Neighbour Field (NNF) <!-- .element: class="fragment" -->
- Amount of Patches = Amount of pixels <!-- .element: class="fragment" -->
  - 800 * 600 = 480 000
- Use PatchMatch <!-- .element: class="fragment" -->
  - Requires ~ 5 iterations

Note:
The most time consuming part of this approach is to find best match for every patch at the entire image. To build a mapping of a patch to its best match. This mapping is called (Show first bullet) 

Nearest Neighbour Field. In order to build this mapping we need to go thru the enentire image **for each patch** and find its best match. Image contains (Next bullet) 

A plenty of patches. It could be a quadratic complexity. But (Next bullet)

There is a nice PatchMatch algorithm that allows to speed up his process significantly. More iterations we perform the precisier NNF becomes.

Now we should be able to outline the entire process (Next slide)

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Wex algorithm</span>

<pre>







    for j < nnfBuildIterations
      nnf = ImproveNnf(nnf, image ..);


    



</pre>

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Wex algorithm</span>

<pre>







    for j < nnfBuildIterations
      nnf = ImproveNnf(nnf, image ..);

    image = Inpaint(image, removeArea, nnf, ..);
    



</pre>

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Wex algorithm</span>

<pre>




  for i < inpaintIterations
  {

    for j < nnfBuildIterations
      nnf = ImproveNnf(nnf, image ..);

    image = Inpaint(image, removeArea, nnf, ..);
    
  }


</pre>


---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Wex algorithm</span>

<pre>
foreach level in pyramid.Levels
{
  image = level.GetImage();

  for i < inpaintIterations
  {

    for j < nnfBuildIterations
      nnf = ImproveNnf(nnf, image ..);

    image = Inpaint(image, removeArea, nnf, ..);
    
  }
  nnf = nnf.ScaleUp(..);
}
</pre>

Note:
I think now it should be obvious that the method is to expensive to be ran on a mobile device.

---
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/use_cloud.png"  height="500" /> 

Note:
It worth to make a service and host it somewhere in a cloud. 

---
<span class="menu-title" style="display: none">Service Arhitecture</span>

<img src="./assets/md/assets/inpaint/pyramids.png"  height="500" /> 

Note:


---

Note:

I wanted to pay only for what I used and to be able to scale the service when the load increases.

It would be possible with the following archetecture - 

TODO: make picture with worker role

So that client uploads image and markup to the blob storage and calls a WebAPI that puts a message into a queue. Worker role processes the image puts it back to the blob and sends updates via SignalR.

The problem is that when there are multiple requests and only one worker role other users have to wait. We can configure scaling so that additional worker roles are deployed but it takes minutes for new Worker Role to be deployed.

What would be possible is to split the whole processing into smaller jobs like this 

TODO: make computation graph picture

And process jobs from different requests. That would simulate some multitasking.

In that case I would spend a lot of time inventing orchestration and ballancing logic instead of concentrating on important things.

Moreover you pay for the time when the Worker Role is deployed. So it can do nothing but you still will pay for that.

---

Note:
Later Microsoft turned their web jobs into Azure Functions.  Azure Function in my case is a really good alternative to worker roles.

New instance of a function will immidiately react on a message in the queue, but 
- function is not powerfull enough to handel the whole process
- it is limited in time
- in case of failure the whole process needs to be started from the beggining

We can build pipeline, but then we still have an issue that we need to implement quite complicated orchestration logic.

---

Note:

Luckly we have now a new Durable Functions!


---

TODO: What are the possible solutions?

---

- Azure Cloud Services
  - Worker roles

---

TODO: How difficult to use worker
- one worker many users  <!-- .element: class="fragment" -->
- new worker instance deploy time
- reacts on message in a queue  <!-- .element: class="fragment" -->
- difficult to scale  <!-- .element: class="fragment" -->

---

| INSTANCE	| CORES |	RAM	| PRICE |
| ---|---|---|---|
| A0 | 1 | 0.75 GB | $0.02/hour |
| A1 | 1 | 1.75 GB | $0.08/hour |
| A2 | 2 | 3.50 GB | $0.16/hour |
| A3 | 4 | 7.00 GB | $0.32/hour |
| A4 | 8 | 14.00 GB | $0.64/hour |

---

| instance | price per month|
| --- | ---|
| A0 | 24 &ast; 30 &ast; $0.02 = $14.4|
| A1 | 24 &ast; 30 &ast; $0.08 = $57.6|
| A2 | 24 &ast; 30 &ast; $0.16 = $115.2|

---

- Azure functions
  - Pay for usage (real)  <!-- .element: class="fragment" -->
  - Scale  <!-- .element: class="fragment" -->

---

TODO: How to orchestrate

---

- Limited lifetime  <!-- .element: class="fragment" -->
- Difficult to orchestrate  <!-- .element: class="fragment" -->

---

TODO: Durable functions - what it is?

- description
- prerelease version
- how to reference the NuGet

---

TODO: How to orchestrate

---

TODO: Converted app into Durable without Activities. 

---

TODO: Reasons to use Activities

- Parallalization
- Restores in case of failure

---

TODO: How I failed to switch to Activities

- No awaits within Orcestrate  <!-- .element: class="fragment" -->
- Serializable inputs  <!-- .element: class="fragment" -->
- 60KB payloads  <!-- .element: class="fragment" -->

---

TODO: Replay functionality (strips)

 - how stupid is the orchestration
 
---

TODO: Demonstration of reply in Azure

---

TODO: Explain how Durable works under the hood

---

TODO: Use of sub orchestrations

---

TODO: Possible optimizations
- Sub Orchestrations  <!-- .element: class="fragment" -->
- Minimize reads from storage  <!-- .element: class="fragment" -->
- Use in-memory (REDIS)  <!-- .element: class="fragment" -->

---

TODO: Diagnostics

---

TODO: Deployments

- I had issue referencing a project

---

|||
|---|--|
| Cost of one minute | 0.128GB * 60000ms = 7680 Gs|
| Free GB-s per month | 400,000 free ~ 52 min |
| Free executions | 1,000,000 |
| Avg Time of one erase| 2 min |
| One erase cost | $0.000016 * 120,000ms ~ $0.2|
| Cost of one hour | $7.3 |
| Cost of one mln exec | $0.20|

---

## Key take aways
- item1 

---

# Q&A
Thank you!

// TODO: insert contacts, picture etc