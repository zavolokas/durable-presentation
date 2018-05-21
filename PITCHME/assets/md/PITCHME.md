<span class="menu-title" style="display: none">Title</span>

## Durable Functions
# Complexity behind Simplicity

Note:
Thank you for comming.

Many of you already used Azure Functions, right?

---
<span class="menu-title" style="display: none">Motivation</span>


Note:
Those of you who already have heard about the Durable Extensions already know that they are very powerful and at the same time they are quite intuitive and simple to use.

However this simplicity may give you an **illusion of understanding** how it actually works. But in the reality **there are** some constraints that are not obvious at all and violation of these constraints leads to a poor performance and confustion.

Today I will show you how durable functions actually work. That will 

// TODO: **SAVE YOUR TIME**

e.g:
help to avoid spending many hours hitting walls (like I did) when you start to do something more advanced than running the sample code that is provided with the durable functions.

---
<span class="menu-title" style="display: none">Serverless refresher</span>

// TODO: serverless refresher

---
<span class="menu-title" style="display: none">Azure functions</span>

// TODO: azure functions

Note:
- Event (Triggered)
  - timers
  - HTTP
- Code
- Outputs

---
<span class="menu-title" style="display: none">What is still hard?</span>

// TODO: chain functions

---
<span class="menu-title" style="display: none">Durable functions intro</span>

## Durable Functions
- Simplify orchestration <!-- .element: class="fragment" -->
- Code your workflow  <!-- .element: class="fragment" -->
- 100% reliability  <!-- .element: class="fragment" -->

Note:

Durable Functions! (Next bullet)

They help to orchestrate functions in a way that all the parts play nicely together in a synchronized and consistent way.
 (Next bullet)

Workflow is now can be defined in code. No JSON schemas or designers. Easier to understand since everything is defined in one place.(Next bullet)

One of the key features of Durable functions is that they are 100% reliable. The progress is not lost when VM is restarting.

Let's jump into code and see how cool durable functoins are.

---
<span class="menu-title" style="display: none">Coding. Demonstration of simplicity</span>

## Demo coding I

Note:

As a coding excersice I took one of my open source image processing projects that implements a content aware fill. In simple words it allows to remove somebody or something from a photo as if it never was there.

Firs of all what we need to do is to prepare a so-called image pyramid by scaling the image down several times. After the scaling we need to reduce the noise on each of them by applying a blur filter. That can be done in parallel. So let's do it.

// TODO: explain the code

---
<span class="menu-title" style="display: none">Easy</span>

# Easy!

<img src="./assets/md/assets/wow.gif"  width="800" />

Note:
That was pritty easy!

You just call your function like you usually call any other method pass parameters, save results in some local variables and then process it further.

Who would agree that it fills like a usual coding experiance?

When this is familiar we just extrapolate our previous experiance to this new circumstances. That is the way how the illusion of understanding arises.

By the way. This was an example almost identical to one that Microsoft provides. 

After that you say - aha! I got it! And you try to apply this new powerful tool in your project.

What can go wrong?

---
<span class="menu-title" style="display: none">Coding. Violating the constraints</span>

Demo coding II

Note:
What we will do - is actually build the pyramid. 
1. Take a bitmap from a blob storage. 
2. Determine how many times we need to scale it down
3. Scale it down and Blur

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">What?!</span>

### What?!

<img src="./assets/md/assets/confusion.gif"  width="800" />

Note:
Don't know how about you, but I've got a lot of questions.

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Unclear moments</span>

### Why?!

<img src="./assets/md/assets/confusion.gif"  width="400" />

- Requires storage account
- Requires serialization <!-- .element: class="fragment" -->
- Doesn't allow async calls <!-- .element: class="fragment" -->
- Requires determinism <!-- .element: class="fragment" -->

Note:
- Why does it requires storage account for orchestrator and activity functions? (next bullet)
- Serialization is the simplest one - we can assume that it transfer object between functions that way (next bullet)
- Why it complains about async calls that done without using context?
- Why it complains about non-determenistic code?

We need to learn how durable functions work under the hood

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">How it works. 1</span>

<img src="./assets/md/assets/durable/duarable-process01.png"  width="800" />

Note:

Suppose we have our orchestrator function. When it comes to an execution of an activity function

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">How it works. 2</span>

<img src="./assets/md/assets/durable/duarable-process02.png"  width="800" />

Note:
It sends a message to a WorkItems queue and after that

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">How it works. 3</span>

<img src="./assets/md/assets/durable/duarable-process03.png"  width="800" />

Note:
it's execution stops, it can be unloaded from memory (so you stop paying for it) . At the same time 

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">How it works. 4</span>

<img src="./assets/md/assets/durable/duarable-process04.png"  width="800" />

Note:
An activity function listens to the WorkItem queue and once a message appears there,
the activity is got triggered.

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">How it works. 5</span>

<img src="./assets/md/assets/durable/duarable-process05.png"  width="800" />

Note:


After it's job is done it sends a message to Control queue

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">How it works. 6</span>

<img src="./assets/md/assets/durable/duarable-process06.png"  width="800" />

Note:
It triggers an execution of orchestrator function again

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">How it works. 7</span>

<img src="./assets/md/assets/durable/duarable-process07.png"  width="800" />

Note:
And after the process is repeated 

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">How it works. 8</span>

<img src="./assets/md/assets/durable/duarable-process08.png"  width="800" />

Note:
until the orchestrator function

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">How it works. 9</span>

<img src="./assets/md/assets/durable/duarable-process09.png"  width="800" />

Note:
comes to it's end

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">How it works. 10</span>

<img src="./assets/md/assets/durable/duarable-process10.png"  width="800" />

Note:

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">How it works. 11</span>

<img src="./assets/md/assets/durable/duarable-process11.png"  width="800" />

Note:
You may ask here - If the orchestrator function stops after calling 
an activity and even is unloaded from the memory

---
<span class="menu-title" style="display: none">Checkpoint replay</span>

How state is restored?
- Checkpoint/Replay <!-- .element: class="fragment" -->

Note:
how does it restore its state and proceed the execution from the right place? 

For that purpose durable functions use one of the Event Sourcing technique (next bullet)

Chckpoint/Replay

Every time orchestrator function calls an Activity - it's state is checkpointed into a
History table  (next slide)

---
<span class="menu-title" style="display: none">History table</span>

#### History table

<img src="./assets/md/assets/history_table.png" width="800" />

Note:
under your storage account. When Activity function is finished, the history is replayed 
to rebuild the state of the orchestrator function.

Since Orchestrator and Activities may be run on different VMs in some environment that is not 100% reliable,
this approach guaranties reliability - because in a case of a failure the state will be resored and continued.

However this repay process leads to an interesting execution behaviour. Let me show it on an example(next example)

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Minions intro</span>

<img src="./assets/md/assets/minions/pre_giphy.png"  width="540" />

Note:
with the help of this guys. Let them practice in origami and ask them to make a plane in a way how a durable function would do this.

one of the them will be orchestrator and another one activity

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Who Orchestrate?</span>

<img src="./assets/md/assets/minions/pre_giphy02.png"  width="540" />

Note:
Like this

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Minions reaction</span>

<img src="./assets/md/assets/minions/giphy.gif"  width="540" />

Note:
The reaction is strange.

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Plan</span>

<img src="./assets/md/assets/minions/checkpoint-replay-start.png"  height="600" />

Note:
This instructions are executed by the orchestrator and all the folding operations are done by the activity.

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 1</span>

<img src="./assets/md/assets/minions/checkpoint-replay-step0.png"  height="600" />

Note:
So, the ochestrator encounters first folding action and it calls an activity
to perform this step.

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 1. Ok</span>

<img src="./assets/md/assets/minions/checkpoint-replay-ok.png"  height="600" />

Note:
Activity agrees. Orchestrator kind of sleeps. Then activity

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 1. Done</span>

<img src="./assets/md/assets/minions/checkpoint-replay-finished.png"  height="600" />

Note:
finishes it's task and returns the results to the orchestrator (via a message in a queue)

Then orchestrator wakes up and replays the history to restore it's state.

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 1</span>

<img src="./assets/md/assets/minions/checkpoint-replay-step1.png"  height="600" />

Note:
So it looks like it asks an activity to perform the first step again. 

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 1. Done</span>

<img src="./assets/md/assets/minions/checkpoint-replay-done.png"  height="600" />

Note:
But since it was already done and results are captured, the activity is 
not called again. The orchestrator moves 

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 2</span>

<img src="./assets/md/assets/minions/checkpoint-replay-step2.png"  height="600" />

Note:
forward
with the execution and asks the activity to perform the second step.

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 2. Ok</span>

<img src="./assets/md/assets/minions/checkpoint-replay-ok.png"  height="600" />

Note:
Activity agrees. Orchestrator kind of sleeps. Then activity

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 2. Done</span>

<img src="./assets/md/assets/minions/checkpoint-replay-finished.png"  height="600" />

Note:
finishes it's task and returns the results to the orchestrator (via a message in a queue)

Then orchestrator wakes up and replays the history to restore it's state.

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 1</span>

<img src="./assets/md/assets/minions/checkpoint-replay-step1.png"  height="600" />

Note:
So it looks like it asks an activity to perform the first step again. But since it was 
already done and 

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 1. Done</span>

<img src="./assets/md/assets/minions/checkpoint-replay-done.png"  height="600" />

Note:
results are captured, the activity is not called again. The orchestrator moves forward
with the execution 

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 2</span>

<img src="./assets/md/assets/minions/checkpoint-replay-step2.png"  height="600" />

Note:
and asks the activity to perform the second step again. But since it was 
already done and 

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 2. Done</span>

<img src="./assets/md/assets/minions/checkpoint-replay-done.png"  height="600" />

Note:
results are captured, the activity is not called again. The orchestrator moves forward
with the execution and asks the activity to perform the third step

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 3</span>

<img src="./assets/md/assets/minions/checkpoint-replay-step3.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 3. Ok</span>

<img src="./assets/md/assets/minions/checkpoint-replay-ok.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 3. Done</span>

<img src="./assets/md/assets/minions/checkpoint-replay-finished.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 1</span>

<img src="./assets/md/assets/minions/checkpoint-replay-step1.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 1. Done</span>

<img src="./assets/md/assets/minions/checkpoint-replay-done.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 2</span>

<img src="./assets/md/assets/minions/checkpoint-replay-step2.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 2. Done</span>

<img src="./assets/md/assets/minions/checkpoint-replay-done.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 3</span>

<img src="./assets/md/assets/minions/checkpoint-replay-step3.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

<span class="menu-title" style="display: none">Replay. Step 3. Done</span>

<img src="./assets/md/assets/minions/checkpoint-replay-done.png"  height="600" />

Note:
Realizing the fact that the state is always replayed in that way is very important to avoid some stupid performance issues.

If you wonder how can it affect performance, let me convert this example with 6 chained Fold actions into (next slide)

---
<span class="menu-title" style="display: none">Folding code</span>

```CSharp
for (var i = 0; i< 6; i++)
{
  await ctx.CallActivityAsync("Fold", input);
}
```

How many ctx.CallActivityAsync() calls? <!-- .element: class="fragment" -->

Note:
the following code(next bullet)

What do you think - given that the state is alwas replayed - how many times the method call activity async method will be called?

It is an arithmetic progression (next slide)

---
<span class="menu-title" style="display: none">Number of calls</span>

((a1 + an) * N) / 2 = ((1 + 6) * 6) / 2 = 21

Note:
TODO: put propper formula

and can be calculated as follows.

---
<span class="menu-title" style="display: none">Amount of calls</span>

### Calls to Activity
<img src="./assets/md/assets/triangle_number.png"  height="200" />

- 7 - 28
- 10 - 55
- 20 - 210
- 100 - 5050

Note:
that means that if we have a loop with 20 iterations -  210

It becomes really noticable when 
---
<span class="menu-title" style="display: none">Heavy code</span>

```CSharp
for (var i = 0; i< 6; i++)
{
  DoSomethingHeavy();
  await ctx.CallActivityAsync("Fold", input);
}
```

Note:

We have some code in the Orchestrator that is kind of heavy. This code will be executed 21 times while Fold only 6.

---
<span class="menu-title" style="display: none">Heavy code</span>

```CSharp
for (var i = 0; i< 6; i++)
{
  await ctx.CallActivityAsync("DoSomethingHeavy", null);
  await ctx.CallActivityAsync("Fold", input);
}
```

Note:
Perform all the heavy code within activity functions.

---
<span class="menu-title" style="display: none">Back to code</span>

Note:
Now we can see that what used to look alright turns out to be completely wrong. 

Basically during the each replay we load different bitmap that is twice smaller in size. Also properly cropped. That makes the code indeed non-determenistic.

Let's reiterate the constrains of the Orchestrator function.

---
<span class="menu-title" style="display: none">Restrictions</span>

### Constrains

- Determenstic <!-- .element: class="fragment" -->
- No async calls <!-- .element: class="fragment" -->
- No infinite loops <!-- .element: class="fragment" -->

Note:
It will be replayed multiple times and must produce the same result each time. For example, no direct calls to get the current date/time, get random numbers, generate random GUIDs, or call into remote endpoints. (next bullet)

The Durable Task Framework executes orchestrator code on a single thread and cannot interact with any other threads that could be scheduled by other async APIs. (next bullet)

saves execution history as the orchestration function progresses, an infinite loop could cause an orchestrator instance to run out of memory.

---
<span class="menu-title" style="display: none">Inpaint demo</span>

### Demo

Note:

I have a proper implementation of the inpainting on GitHub. For those who are interested in here is a link.

Let's run it.

---
<span class="menu-title" style="display: none">Recap</span>

### Recap
- State is checkpointed in Starage Table
- State is replayed multiple times
- No heavy code in Orchestrator
- Orchestrator should be determenistic

