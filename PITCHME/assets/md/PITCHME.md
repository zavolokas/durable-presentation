<span class="menu-title" style="display: none">Title</span>

# Azure Durable Functions

Note:
Thank you for comming.

Many of you already used Azure Functions, right?

---
<span class="menu-title" style="display: none">Motivation</span>

- Simple to use
- Difficult to orchestrate <!-- .element: class="fragment" -->

Note:
I'm sure you like the simplicity they provide.
They are really nice!

However it becomes painful (next bullet)

when you want functions to interact with each other:
- Pass results as an input to another function, 
- Call functions in a loop
- Call them in parallel, accumulate the resultsand act on them

Today we will talk about Durable functions that will help you to simplify the orchestration.

I'll also share my expeciance so that you don't spend many hours hitting walls (like I did)
because there is not that much information is available yet.

You'll leave this meetup with one more tool at your disposal that you are comfortable with 
and that will help you to takle your challanges.

As I already mentioned the functions are easy to use. If we take a look at the Azure functions 
website we will see that (next slide)

---
<img src="./assets/md/assets/scenarios/function_use_case.png"  width="900" />

Note:
in the examples it provides functions don't call another function.

+++
<img src="./assets/md/assets/scenarios/file-processing_scenario.png"  width="900" />

Note:



+++
<img src="./assets/md/assets/scenarios/stream-processing_scenario.png"  width="900" />

Note:



+++
<img src="./assets/md/assets/scenarios/web-app_scenario.png"  width="900" />

Note:



---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Function for every step</span>

<img src="./assets/md/assets/image-processing_scenario00.png"  width="900" />

Note:
What should we do in the following scenario? 

Suppose our function takes an image from BlobStorage, extract some features 

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Function for every step</span>

<img src="./assets/md/assets/image-processing_scenario01.png"  width="900" />

Note:
Then process them

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Function for every step</span>

<img src="./assets/md/assets/image-processing_scenario02.png"  width="900" />

Note:
Then process features in parallel

---
<!-- .slide: data-transition="none" -->
<span class="menu-title" style="display: none">Function for every step</span>

<img src="./assets/md/assets/image-processing_scenario03.png"  width="900" />

Note:
Then accumulates the results and perform something

You can achieve it by putting a queues in between, so that one function puts results there
another gets them and process.

That is a valid solution, but what if you need to chain many functions? How many additional 
queues you have to maintain? 

Or what if you want to process results in parallel and then act on them?
You end up 

---
<span class="menu-title" style="display: none">Function for every step</span>

<img src="./assets/md/assets/write_code.gif"  height="500" />

Note:
writing some boilerplate code and maintain lots of queues

How could we simplify such complex orchestration problems? The answer is (Next slide)

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

Workflow is now can be defined in code. No JSON schemas or designers. (Next bullet)

One of the key features of Durable functions is that they are 100% reliable. The progress is not lost when VM is restarting.

Durable Functions fit well (next slide)

---
<span class="menu-title" style="display: none">Patterns. Chaining</span>

### Function chaining

<img src="./assets/md/assets/function-chaining.png"  width="800" />

Note:
// TODO: update image

When we need to chain functions.

1. We can call one function within our orchestrator
2. save the results in a local variable
3. call another function passing the result 

Or another pattern called (next side)

---
<span class="menu-title" style="display: none">Patterns. Fan-out/fan-in</span>

### Fan-out/fan-in

<img src="./assets/md/assets/fan-out-fan-in.png"  width="800" />

Note:
// TODO: update image

Fan-out/fan-in

allows to call functions in parallel, gather result and do something else.

Sounds cool, right? Let's jump into coding so that you'll really appriciate the simplicity

---
<span class="menu-title" style="display: none">Demo coding I</span>

## Demo coding

Note:

For the coding excercise, I'd like to implement the following scenario.

// TODO: describe what you are going to do

---
<span class="menu-title" style="display: none">Easy</span>

# Easy!

<img src="./assets/md/assets/wow.gif"  width="800" />

Note:
That was pritty easy!

This was an example almost identical to one that Microsoft provides - so it should work

but usually your case is a bit different and when you go a bit different direction you experiance some issues. 

---
<span class="menu-title" style="display: none">Demo coding II</span>

## Demo coding 2

Note:
So let's go further and 

// TODO: describe what you are going to do

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

Note:
- Why does it requires storage account for orchestrator and activity functions? (next bullet)
- Serialization is the simplest one - we can assume that it transfer object between functions that way (next bullet)
- Why it complains about async calls that done without using context?

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
with the help of this guys. Let them practice in origami and ask them to make a plane 

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
You should keep in mind that kind of behaviour because it really can lead to a poor performance. Simply because of serialization/deserialization.

This example with 6 chained Fold actions can(next slide)

---
<span class="menu-title" style="display: none">Folding code</span>

```CSharp
for (var stepIndex = 0; stepIndex< 6; stepIndex++)
{
  await ctx.CallActivityAsync("Fold", input);
}
```

How many ctx.CallActivityAsync() calls? <!-- .element: class="fragment" -->

Note:
be respresented in code like this (next bullet)

How many times the call activity async method will be called?

This is a triangular number that(next slide)

---
<span class="menu-title" style="display: none">Triangular Number</span>

(N \* (N+1)) / 2 = 6 \* 7 / 2 = 21

Note:
TODO: put propper formula

can be calculated as follows.

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
for (var stepIndex = 0; stepIndex< 6; stepIndex++)
{
  DoSomethingHeavy();
  await ctx.CallActivityAsync("Fold", input);
}
```

Note:

We have some code in the Orchestrator that is kind of heavy. This code will be executed 15 times while Fold only 6.

That leads us to another topic - optimizations

---
<span class="menu-title" style="display: none">Clarifications</span>

### How it works 
- Creates queues <!-- .element: class="fragment" -->
- Passes result serialized <!-- .element: class="fragment" -->
- Checkpoints and replays state <!-- .element: class="fragment" -->
- Should be deterministic <!-- .element: class="fragment" -->

Note:
Now we can answer some of our questions

As we saw Azure Durable Functions will create Queues under our storage account, that is why it is required(next bullet)

It is indeed serializes/deserializes objects to send them between functions

Why doesn't support async calls?!

---

<span class="menu-title" style="display: none">Optimizations</span>

### Possible optimizations
- Avoid heavy code in Orchestrator <!-- .element: class="fragment" -->
- Use sub Orchestrations  <!-- .element: class="fragment" -->
- Minimize reads from storage  <!-- .element: class="fragment" -->

---
<span class="menu-title" style="display: none">Restrictions</span>

### Restrictions

- Avoid non-determenstic <!-- .element: class="fragment" -->
- Avoid async calls <!-- .element: class="fragment" -->
- Avoid infinite loops <!-- .element: class="fragment" -->

Note:
It will be replayed multiple times and must produce the same result each time. For example, no direct calls to get the current date/time, get random numbers, generate random GUIDs, or call into remote endpoints. (next bullet)

The Durable Task Framework executes orchestrator code on a single thread and cannot interact with any other threads that could be scheduled by other async APIs. (next bullet)

saves execution history as the orchestration function progresses, an infinite loop could cause an orchestrator instance to run out of memory.

But still problems can happen and you might be stuck (next slide)

---
<span class="menu-title" style="display: none">Support</span>

### Support
- GitHub
- StackOverflow
- Twitter

Note:
then Post the issue on stack overflow also tweet about it, put hash tag Azure, Azure Functions and usually you get help quite fast

---
<span class="menu-title" style="display: none">Summary</span>

## Key take aways
- Statefull orchestration <!-- .element: class="fragment" -->
- 100% reliable <!-- .element: class="fragment" -->
- Orchestrator restrictions <!-- .element: class="fragment" -->
- Checkpoint/Replay <!-- .element: class="fragment" -->
- Sub Orchestrators <!-- .element: class="fragment" -->
- Prerelease <!-- .element: class="fragment" -->
- Heavy computations? <!-- .element: class="fragment" -->

Note:
- What are the key take aways? (next bullet)
- Durable extension allows to orchestrate azure functions (next bullet)
- It is 100% reliable. You need to remember (next bullet)
- about the restrictions, that the orchestrator code should be detemenistic, you cannot use async calls other than via durable context (next bullet)
- Keep in mind the Checkpoint/Replay technique that is used by Orchestrator and use (next bullet)
- sub orchestors in order to improve performance
- It is still pre release, many things can go wrong, many things can change. Don't hesitate to ask for advice on SO etc.
- If you want to port some performance critical computations think twice as you'll spend a lot of time to serialization and desirialization

---
<span class="menu-title" style="display: none">Questions</span>

# Questions

Note:
- Pricing
  - GB-s $0.000016
  - Cost of one mln exec $0.20
  - Cost of one minute => 0.128GB * 60000ms = 7680 Gs
  - Free GB-s per month => 400,000 free ~ 52 min 
  - Free executions => 1,000,000 