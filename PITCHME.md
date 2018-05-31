@title[Title]

## Durable Functions
# Complexity behind Simplicity

---
@title[Serverless refresher]

## What is serverless?
- Abstraction of servers
- Event-driven
- Micro-billing
---
@title[Azure functions]

<img src="./assets/azurefunction.png"  />

---
<!-- .slide: data-transition="none" -->

@title[What is still hard?]

<img src="./assets/durable_function_problem1.png"  />


---
<!-- .slide: data-transition="none" -->

@title[What is still hard?]

<img src="./assets/durable_function_problem2.png"  />


---
<!-- .slide: data-transition="none" -->

@title[What is still hard?]

<img src="./assets/durable_function_problem3.png"  />

---
<!-- .slide: data-transition="none" -->

@title[What is still hard?]

<img src="./assets/durable_function_problem4.png" />

---
@title[Overhead]

<img src="./assets/write_code.gif"  />

---
@title[Durable functions intro]

## Durable Functions
- Simplify orchestration <!-- .element: class="fragment" -->
- Code your workflow  <!-- .element: class="fragment" -->
- 100% reliability  <!-- .element: class="fragment" -->

---
<!-- .slide: data-transition="none" -->

@title[New triggers]

<img src="./assets/durable_function_solution1.png" />


---
<!-- .slide: data-transition="none" -->

@title[New triggers]

<img src="./assets/durable_function_solution2.png" />


---
@title[Coding. Demonstration of simplicity]

## Demo coding I

---
@title[Easy]

# Easy!

<img src="./assets/wow.gif"  width="800" />

---
@title[Coding. Violating the constraints]

## Demo coding II


---
<!-- .slide: data-transition="none" -->

@title[What?!]

### Why?!

<img src="./assets/confusion.gif"  width="800" />


---
<!-- .slide: data-transition="none" -->

@title[Unclear moments]

### Why?!

<img src="./assets/confusion.gif"  width="400" />

- Requires storage account
- Requires serialization <!-- .element: class="fragment" -->
- Doesn't allow async calls <!-- .element: class="fragment" -->
- Requires determinism <!-- .element: class="fragment" -->


---
<!-- .slide: data-transition="none" -->

@title[How it works. 1]

<img src="./assets/durable/duarable-process01.png"  width="800" />


---
<!-- .slide: data-transition="none" -->

@title[How it works. 2]

<img src="./assets/durable/duarable-process02.png"  width="800" />

---
<!-- .slide: data-transition="none" -->

@title[How it works. 3]

<img src="./assets/durable/duarable-process03.png"  width="800" />

---
<!-- .slide: data-transition="none" -->

@title[How it works. 4]

<img src="./assets/durable/duarable-process04.png"  width="800" />

---
<!-- .slide: data-transition="none" -->

@title[How it works. 5]

<img src="./assets/durable/duarable-process05.png"  width="800" />

---
<!-- .slide: data-transition="none" -->

@title[How it works. 6]

<img src="./assets/durable/duarable-process06.png"  width="800" />

---
<!-- .slide: data-transition="none" -->

@title[How it works. 7]

<img src="./assets/durable/duarable-process07.png"  width="800" />

---
<!-- .slide: data-transition="none" -->

@title[How it works. 8]

<img src="./assets/durable/duarable-process08.png"  width="800" />

---
<!-- .slide: data-transition="none" -->

@title[How it works. 9]

<img src="./assets/durable/duarable-process09.png"  width="800" />

---
<!-- .slide: data-transition="none" -->

@title[How it works. 10]

<img src="./assets/durable/duarable-process10.png"  width="800" />

Note:

---
<!-- .slide: data-transition="none" -->

@title[How it works. 11]

<img src="./assets/durable/duarable-process11.png"  width="800" />


---
@title[Checkpoint replay]

How state is restored?
- Checkpoint/Replay <!-- .element: class="fragment" -->

---
@title[History table]

#### History table

<img src="./assets/history_table.png" width="800" />


---
<!-- .slide: data-transition="none" -->

@title[Replay. Minions intro]

<img src="./assets/minions/pre_giphy.png"  width="540" />

---
<!-- .slide: data-transition="none" -->

@title[Replay. Who Orchestrate?]

<img src="./assets/minions/pre_giphy02.png"  width="540" />


---
<!-- .slide: data-transition="none" -->

@title[Replay. Minions reaction]

<img src="./assets/minions/giphy.gif"  width="540" />


---
<!-- .slide: data-transition="none" -->

@title[Replay. Plan]

<img src="./assets/minions/checkpoint-replay-start.png"  height="600" />

---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 1]

<img src="./assets/minions/checkpoint-replay-step0.png"  height="600" />


---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 1. Ok]

<img src="./assets/minions/checkpoint-replay-ok.png"  height="600" />


---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 1. Done]

<img src="./assets/minions/checkpoint-replay-finished.png"  height="600" />


---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 1]

<img src="./assets/minions/checkpoint-replay-step1.png"  height="600" />

---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 1. Done]

<img src="./assets/minions/checkpoint-replay-done.png"  height="600" />

---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 2]

<img src="./assets/minions/checkpoint-replay-step2.png"  height="600" />

---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 2. Ok]

<img src="./assets/minions/checkpoint-replay-ok.png"  height="600" />

---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 2. Done]

<img src="./assets/minions/checkpoint-replay-finished.png"  height="600" />

---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 1]

<img src="./assets/minions/checkpoint-replay-step1.png"  height="600" />

---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 1. Done]

<img src="./assets/minions/checkpoint-replay-done.png"  height="600" />

---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 2]

<img src="./assets/minions/checkpoint-replay-step2.png"  height="600" />

---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 2. Done]

<img src="./assets/minions/checkpoint-replay-done.png"  height="600" />

---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 3]

<img src="./assets/minions/checkpoint-replay-step3.png"  height="600" />

---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 3. Ok]

<img src="./assets/minions/checkpoint-replay-ok.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 3. Done]

<img src="./assets/minions/checkpoint-replay-finished.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 1]

<img src="./assets/minions/checkpoint-replay-step1.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 1. Done]

<img src="./assets/minions/checkpoint-replay-done.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 2]

<img src="./assets/minions/checkpoint-replay-step2.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 2. Done]

<img src="./assets/minions/checkpoint-replay-done.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 3]

<img src="./assets/minions/checkpoint-replay-step3.png"  height="600" />

Note:

---
<!-- .slide: data-transition="none" -->

@title[Replay. Step 3. Done]

<img src="./assets/minions/checkpoint-replay-done.png"  height="600" />

---
@title[Folding code]

```CSharp
for (var i = 0; i< 6; i++)
{
  await ctx.CallActivityAsync("Fold", input);
}
```

How many ctx.CallActivityAsync() calls? <!-- .element: class="fragment" -->

---
@title[Number of calls]

((a1 + an) * N) / 2 = ((1 + 6) * 6) / 2 = 21


---
@title[Amount of calls]

### Calls to Activity
<img src="./assets/triangle_number.png"  height="200" />

- 7 - 28
- 10 - 55
- 20 - 210
- 100 - 5050


---
@title[Heavy code]

```CSharp
for (var i = 0; i< 6; i++)
{
  DoSomethingHeavy();
  await ctx.CallActivityAsync("Fold", input);
}
```


---
@title[Heavy code]

```CSharp
for (var i = 0; i< 6; i++)
{
  await ctx.CallActivityAsync("DoSomethingHeavy", null);
  await ctx.CallActivityAsync("Fold", input);
}
```


---
@title[Back to code]



---
@title[Restrictions]

### Constrains

- Determenstic <!-- .element: class="fragment" -->
- No async calls <!-- .element: class="fragment" -->
- No infinite loops <!-- .element: class="fragment" -->

---
@title[Inpaint demo]

### Demo

---
@title[Recap]

### Recap
- State is checkpointed in Starage Table
- State is replayed multiple times
- No heavy code in Orchestrator
- Orchestrator should be determenistic

