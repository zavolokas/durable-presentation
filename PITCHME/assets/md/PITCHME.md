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

#### Video Disabled

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

---

TODO: Explain New algorithm and show examples

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