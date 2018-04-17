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

It worth to make a service and host it somewhere in a cloud. (Next slide)

---
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/use_cloud.png"  height="500" /> 

Note:
So the app just uses a WebApi and sends a request to process an image.

I choose a Azure since I was familiar with it and it sounded kind of natural to choose this cloud for the .NET application.

The architecture for the service should be as following

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/WorkerRole/worker_role_solution001.png"  height="500" /> 

Note:
We have a WebRole that is also a SignalR server so that service can update the client easyly

So when the client requests to process an image. The web role (Next slide)

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/WorkerRole/worker_role_solution002.png"  height="500" /> 

Note:
Puts the images into the Blob storage and after that (Next slide)

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/WorkerRole/worker_role_solution003.png"  height="500" /> 

Note:
It pushes a message into the queue that an image in the blob container needs to be processed

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/WorkerRole/worker_role_solution004.png"  height="500" /> 

Note:
We have a worker role that listens to the queue and once it gets a message (Next Slide)

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/WorkerRole/worker_role_solution005.png"  height="500" /> 

Note:
It downloads the images from the blob storage and starts to process it

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/WorkerRole/worker_role_solution006.gif"  height="500" /> 

Note:
Is saves intermidiate results to the blob storage and notifies client via SignalR about the update

But what will happen if at the same time (Next slide)

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/WorkerRole/worker_role_solution011.png"  height="500" /> 

Note:
another client will send the request?

The same (Next slide) 

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/WorkerRole/worker_role_solution012.png"  height="500" /> 

Note:
Web Role will put the data into the blob storage

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/WorkerRole/worker_role_solution013.png"  height="500" /> 

Note:
And send a message into the queue

---
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/WorkerRole/worker_role_solution014.gif"  height="500" /> 

Note:
But the worker role is still busy with processing the first request. So another user have to wait.

We can scale and deploy another worker role when there are certain amount of messages in the queue, but it takes a lot of time to deploy a new worker role.

It is quite difficult because we deploy the whole application. However we need at least to emulate multitasking and process all the requests simultaniously. 

How can we do it?

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/WorkerRole/worker_role_solution020.png"  height="500" /> 

Note:
We can buld a complete processing pipeline based on the input. Where we will have separate steps of: 

- building an NNF in parallel for a different part of image
- merging NNFs into one
- inpaint etc

After that we can tear appart this pipeline into small pieces

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/WorkerRole/worker_role_solution021.png"  height="500" /> 

Note:
After that we siply register them in a storage and 

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/WorkerRole/worker_role_solution022.png"  height="500" /> 

Note:
push a message for each one to the queue. Messages will only trigger a Worker Role to check the registry which job should be done next, from which user etc. 

So it should ballance them.

---
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/WorkerRole/worker_role_solution023.gif"  height="500" /> 

Note:
Process a piece of work for one user then for another then agan for the first etc.


---
<span class="menu-title" style="display: none">Service Arhitecture</span>

### Disadvantages
- Difficult to scale <!-- .element: class="fragment" -->
- Complicated workflow <!-- .element: class="fragment" -->
- Pricing <!-- .element: class="fragment" -->

Note:
It is difficult to scale. We need to 
- build a pipeline, 
- store individual pieces
- keep track of inputs and outputs
- decide whick pice of work to take next

Lots of supporting code that doesn't relate to the actual problem

That all leads to complicated workflow

The pricing model is also disadvantage since you pay for worker role for the whole time it is deployed. No matter was it doing something or not. And we have to keep one continue running to react imedeatelly on the incoming request.

Another possible solution can be based on Docker containers.

---
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/docker_solution.png"  height="500" /> 

Note:
Truelly saying I didn't try it yet. We could simply pack pure processing app in a container and spinup more instances when needed.

Might be a good solution. I don't know yet.

What happend later is that Microsoft turned their web jobs into 

---
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/azure_function_solution001.png"  height="500" /> 

Note:
Azure Functions.
- They are really good for scalability
- Can be triggered by an HTTP request

I could put the whole processing logic into a function (Next slide)

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/azure_function_solution002.png"  height="500" /> 

Note:
Then for each user a separate instance of function will be ran almost immedatelly.

Pricing model is also nice - you pay for what you use.

But(Next slide)

---
<span class="menu-title" style="display: none">Move to Cloud</span>

### Disadvantages
- Failure => lost results <!-- .element: class="fragment" -->
- No SignalR Hub<!-- .element: class="fragment" -->
- Not powerful <!-- .element: class="fragment" -->
- 5 min limit <!-- .element: class="fragment" -->

Note:
In any case of failure a user will get no response. - we still want to put requests into a queue

We need a SignalR hub to update the client - we still want to have a WebRole

Functions are not powerful as Worker Role can be and processing will take more time.

The problem is that the functions are limeted by 5 minutes of time, after 5 minutes they are killed.

---
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/azure_function_solution003.png"  height="500" />

Note:
It will solve the issue with failure, function will try to process image again and it will update the client. Another users don't have to wait.

---
<span class="menu-title" style="display: none">Move to Cloud</span>

### Disadvantages
- Not powerful <!-- .element: class="fragment" -->
- 5 min limit <!-- .element: class="fragment" -->
- Failure => lost progress <!-- .element: class="fragment" -->

Note:
But still the functions are not powerfull enough and the processing will be slow and after 5 minutes processing will be stopped and after that function will start to process a request again, from the very begining - because the functions are stateless

What we could do, is to split the inpainting process into separate functions. Do you remember the pipeline?

---
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/azure_function_solution004.png"  height="500" />

Note:
We can build create functions for each type of steps in this pipeline

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/azure_function_solution005.png"  height="500" />

Note:
Then the Build will be scaled automatically. And NNF will be built in parallel. Sounds Nice!

Output from one function needs to be sent as an input to another function - and making sure that all the parts play nicely together in a synchronized and consistent way.

In other words we need to build some sofisticated orchestration of these functions.

// TODO: place to show ARGGGGHHHHH

---

## Durable Functions
- Simplify orchestration <!-- .element: class="fragment" -->
- Code your workflow  <!-- .element: class="fragment" -->
  - Save output to local variables
- Stateful functions  <!-- .element: class="fragment" -->
  - State is never lost

Note:

Luckly now we have Durable Functions! (Next bullet)

The main use case for Durable Functions is simplifying complex orchestration problems in serverless applications. (Next bullet)

Workflow is now can be defined in code. No JSON schemas or designers. (Next bullet)

They are statefull. The progress is not lost when VM is restarting.

Let's jump into coding and see how does it work in practice

---

## Demo coding

Note:

The Azure Durable Function library adds two function bindings that are used by the system to find which functions should be treated as Durable:

- OrchestrationTrigger – All orchestrator functions must use this trigger type. This input binding is connected to the
  - DurableOrchestrationContext class that is used by the orchestrator to call durable-activities and create durable control flow
- ActivityTrigger – marks a function as activity, which allows it to be called by an orchestrator function. 
This input binding is connected to the DurableActivityContext class which allows the activity function to get the input and set the output.

+++

### Http Trigger
```CSharp
[FunctionName("Inpaint")]
public static async Task<HttpResponseMessage> Inpaint(
    [HttpTrigger(AuthorizationLevel.Anonymous, "get", "inpaint")]
    HttpRequestMessage request,
    [OrchestrationClient]
    DurableOrchestrationClient orchestrationClient,
    TraceWriter log
    )
{
    log.Info("Start inpainting");

    // get input
    var input = (Container: "009", Picture: "t009.png", RemoveMarkup: "m009.png");

    var instanceId = await orchestrationClient.StartNewAsync("Process", input);

    log.Info($"Orchestrator({instanceId}) - started to inpaint an input");

    return orchestrationClient.CreateCheckStatusResponse(request, instanceId);
}
```

Note:
In this example, I created an HTTP triggered function and bound one of its parameters to the `DurableOrchestrationClient` by specifying the `OrchestrationClient` attribute.

The function is invoked by sending an `HTTP GET` request to the address http://{host}/api/inpaint . 

The Inpaint function starts a new instance of the `Process` orchestrator function by calling the `DurableOrchestrationClient.StartNewAsync()` method, and passing it the name of the function and an input, which is empty in this case.

+++

### Orchestrator
```CSharp
[FunctionName("Process")]
public static async Task<bool> Process(
    [OrchestrationTrigger]
    DurableOrchestrationContext ctx
    )
{
    (string Container, string Picture, string RemoveMarkup) input = ctx.GetInput<(string, string, string)>();

    string[] blobNames = new []{ input.Picture, input.RemoveMarkup};

    var tasks = new Task<bool>[blobNames.Length];

    for (var i = 0; i < blobNames.Length; i++)
    {
        tasks[i] = ctx.CallActivityAsync<bool>("Validate", blobNames[i]);
    }

    await Task.WhenAll(tasks);

    return tasks.All(t => t.Result);
}
```

+++

### Activity
```CSharp
[FunctionName("Validate")]
public static async Task<bool> Validate(
    [ActivityTrigger] string blobName)
{
    var task = Task.Delay(TimeSpan.FromSeconds(10));
    await task;

    return true;
}
```

+++

<img src="./assets/md/assets/demo001.png"  height="500" />

+++

<img src="./assets/md/assets/demo002.png"  height="500" />

+++

<img src="./assets/md/assets/demo003.png"  height="500" />

+++

<img src="./assets/md/assets/demo004.png"  height="500" />

---

# Easy!

<img src="./assets/md/assets/wow.gif"  width="800" />

Note:
That was pritty easy!

These are samples that are provided by Microsoft (Next slide)

---

### Function chaining

<img src="./assets/md/assets/function-chaining.png"  width="800" />

Note:
call one function after another and it is allso possible to store results in a variable and pass results to a next function in the chain

---

### Fan-out/fan-in

<img src="./assets/md/assets/fan-out-fan-in.png"  width="800" />

Note:
Call functions in parallel, gather result and do something else.

There are 3 more patterns on official documentation.

As I said - what we saw is the samples from Microsoft, but usuall your case is a bit different and when you go a bit different direction you experiance some issues. Let's do more coding

---

## Demo coding 2

---
<!-- .slide: data-background-image="./assets/md/assets/confusion.gif" data-background-size="auto 45%" data-background-color=" " data-background-position="left" -->

### Questions

- Storage account <!-- .element: class="fragment" -->
- Not supported async calls <!-- .element: class="fragment" -->
- Serialization <!-- .element: class="fragment" -->
- 60K limit <!-- .element: class="fragment" -->

---
<!-- .slide: data-background-image="./assets/md/assets/confusion.gif" data-background-size="auto 45%" data-background-color=" " data-background-position="left" -->

| ### Questions ||
|---|:--:|
|  | Storage account|
|  | Not supported async calls|
|  | Serialization|
|  | 60K limit|

---

Should not be more than 60K!

---

Because it maintains queues and input params goes in a message of the queue

---

Behind the scenes, Azure Durable Functions will create Queues and Tables on your behalf and hide the complexity from your code so you can concentrate on the real problem you’re trying to solve.

---

- the orchestrator function must be determenstic
- avoid calling I/O operations

Note:
This means that function must avoid running code with side-effects (for example using DateTime.Now) except for using the functionality provided by the DurableOrchestrationContext (for example CurrentUtcDateTime that provides the current date/time in a safe and durable way

The correct way to run this non-deterministic code or I/O bound code, is to put it inside a durable-activity function.

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