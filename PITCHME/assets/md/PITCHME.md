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
It started when in 2012 I attended TechDays. 
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

2. After the release, the app had a success. Many downloads, top positions in its category. 

Later, Microsoft organized a Next App Star competition. (Next slide)

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
And they were absolutely right. Because the app used Seam Carving algorithm.(Next slide)

---

<span class="menu-title" style="display: none">Seam carving</span>

### Seam Carving

![Image](./assets/md/assets/seams.jpeg)

Note:
The algorithm simply searches a sequence of less important/noticeable pixels (in image processing terms - pixels with minimal energy) and removes them. After that to restore the size it searches for the sequence again and copies it.
 
But That leads to the distortions, It works fine for pictures made at nature, but for others it might be a problem (Show examples)


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
Including the rating of the app because they wanted more intellingent functionality

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

To inpaint or to perform the content-aware fill

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
Mobiles were not capable of required computation power (and it is still the case)

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

Here I'd like to make a small remark about how do we find patches (Next slide)

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

### Patch search
- Nearest Neighbour Field (NNF) <!-- .element: class="fragment" -->
- Amount of Patches = Amount of pixels <!-- .element: class="fragment" -->
  - 800 * 600 = 480 000
- Use PatchMatch <!-- .element: class="fragment" -->
  - Requires ~ 5 iterations

Note:
This part is basically the most time consuming in this method. We have to find a patch that is similar. We build a mapping that is called (Show first bullet) 

Nearest Neighbour Field. In order to build this mapping we need to go thru the enentire image **for each patch** and find its best match. Image contains (Next bullet) 

A plenty of patches. Naive approach suggests an algorithm that has a quadratic complexity. But (Next bullet)

There is a nice PatchMatch algorithm that allows to speed up his process significantly. More iterations we perform the precisier NNF becomes. 

Let's go back(Next slide)

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Inpainting alg</span>

<img src="./assets/md/assets/inpaint/process007.png"  height="500" /> 

Note:
We get another similar patch using our NNF

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
And if we will take an average of the values(Next slide)

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
for the each pixel in the area until all the values are not calculated (wait for it)

In the reality the image is bigger and pixels are smaller. That is why the whole process is done on an image pyramid.

---
<span class="menu-title" style="display: none">Image Pyramids</span>

<img src="./assets/md/assets/inpaint/pyramids.png"  height="500" /> 

Note:
It is built by scaling down the original image by factor 2. After that we run the algorithm starting from the lowest scale and propagate the results to the upper level and perform processing.

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
I think now it should be obvious that the method is too expensive to be ran on a mobile device.

It worth to make a service and host it somewhere in a cloud. (Next slide)

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/azure_function_solution001.png"  height="500" /> 

Note:
So the app just uses a WebApi and sends a request to process an image.

Initially I choose Azure, experemented with WebRole, but for many reasons it didn't work out.

With availability of serverless and Azure functions in particular I got back to this idea.

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/azure_function_solution002.png"  height="500" /> 

Note:
Because Azure functions are triggered quite fast and at the same time you don't pay for the time it's deployed but only for the resources you use. 

On the other hand functions are not very powerful and processing time can easily exceed the 5 minutes limit, after which the function is got killed basically.

What we could do, is to split the inpainting process into separate functions.

---
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/function-split.png"  height="500" />

Note:
It would also allow to scale individual steps of the inpainting process which is really nice.

However the question is (next slide)

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Move to Cloud</span>

<img src="./assets/md/assets/function-split-issues.png"  height="500" />

Note:
How to orchestrate all these functions that all the parts play nicely together in a synchronized and consistent way.

Output from one function needs to be sent as an input to another function, or some of them needs to be executed in a loop.

The answer is that we can use (Next slide)

---

## Durable Functions
- Simplify orchestration <!-- .element: class="fragment" -->
- Code your workflow  <!-- .element: class="fragment" -->
  - Save output to local variables
- Stateful functions  <!-- .element: class="fragment" -->
  - State is never lost

Note:

Durable Functions! (Next bullet)

The main use case for Durable Functions is simplifying complex orchestration problems in serverless applications. (Next bullet)

Workflow is now can be defined in code. No JSON schemas or designers. (Next bullet)

They are statefull. The progress is not lost when VM is restarting.

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

These are samples that are provided by Microsoft

As I said - what we saw is the samples from Microsoft, but usually your case is a bit different and when you go a bit different direction you experiance some issues. 

---

## Demo coding 2

---
<!-- .slide: data-transition="none" -->

### What?!

<img src="./assets/md/assets/confusion.gif"  width="800" />

Note:
Don't know how about you, but I've got a lot of questions.

---
<!-- .slide: data-transition="none" -->

### What?!

<img src="./assets/md/assets/confusion.gif"  width="400" />

- Storage account
- Not supported async calls <!-- .element: class="fragment" -->
- Serialization <!-- .element: class="fragment" -->
- Starnge execution <!-- .element: class="fragment" -->

Note:
Why does it requires storage account for orchestrator and activity functions? (next bullet)

Why it complains about async calls that done without using context? (next bullet)

Serialization is the simplest one - we can assume that it transfer object between functions that way (next bullet)

Why when we debug the orchestration it does everything from start?

It used to have another issue - it didn't allow payload more than is 60K?

We need to learn how durable functions work under the hood.

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/durable/duarable-process01.png"  width="800" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/durable/duarable-process02.png"  width="800" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/durable/duarable-process03.png"  width="800" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/durable/duarable-process04.png"  width="800" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/durable/duarable-process05.png"  width="800" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/durable/duarable-process06.png"  width="800" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/durable/duarable-process07.png"  width="800" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/durable/duarable-process08.png"  width="800" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/durable/duarable-process09.png"  width="800" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/durable/duarable-process10.png"  width="800" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/durable/duarable-process11.png"  width="800" />

Note:
The question now (Next slide)

---

**How Orchestrator restores execution?**
- Checkpoint/Replay <!-- .element: class="fragment" -->

Note:
How the orchestrator function restores it's state and understands that it needs to proceed with execution from the point where it ended execution last time?

It uses one of the Event Sources technique - Chckpoint/Replay

There are checkpoints are created for the orchestrator function during it's execution and after it awakes it Replays the checkpoints and restores the latest state.

---

#### History table

<img src="./assets/md/assets/history_table.png" width="800" />

Note:
Here are a History table 

---

<!-- <img src="./assets/md/assets/clear_now.gif"  height="300" /> -->

|Why?| Answer|
|----|-------|
| Storage account | to maintain queues and tables |
| Not supported async calls | to make checkpoints |
| Serialization | to send messages |
| 60K limit | queue message size limit|

Note:
Because it maintains queues and input params goes in a message of the queue.

Behind the scenes, Azure Durable Functions will create Queues and Tables on your behalf and hide the complexity from your code so you can concentrate on the real problem you’re trying to solve.


---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/pre_giphy.png"  width="540" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/giphy.gif"  width="540" />

Note:


---

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-start.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-step0.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-ok.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-finished.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-step1.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-done.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-step2.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-ok.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-finished.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-step1.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-done.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-step2.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-done.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-step3.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-ok.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-finished.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-step1.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-done.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-step2.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-done.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-step3.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<img src="./assets/md/assets/minions/checkpoint-replay-done.png"  height="600" />

Note:

---

Restrictions

- the orchestrator function must be determenstic
- avoid calling I/O operations

Note:
This means that function must avoid running code with side-effects (for example using DateTime.Now) except for using the functionality provided by the DurableOrchestrationContext (for example CurrentUtcDateTime that provides the current date/time in a safe and durable way

The correct way to run this non-deterministic code or I/O bound code, is to put it inside a durable-activity function.

---

TODO: Possible optimizations
- Sub Orchestrations  <!-- .element: class="fragment" -->
- Minimize reads from storage  <!-- .element: class="fragment" -->
- Use in-memory (REDIS)  <!-- .element: class="fragment" -->

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