# PM Takehome

## **Objective**

Your objective is to create an RL task for LLM training.

An RL task consists of:

* ✅ A prompt  
* ✅ Some tools and data  
* ✅ A way to verify whether the task has been completed successfully  

The task should teach the model a skill useful in the normal work of an ML engineer or researcher.  
The task should also satisfy the pass-rate requirements.  
We’ve provided some example tasks below.

You’ll need an Anthropic API key.  
We don’t expect tasks to use more than a few dollars in inference cost.

For inspiration, you can take a look at **SWE_Bench_Pro**, which is a collection of realistic software engineering style tasks.

---

## **Requirements**

* The task should resemble the kinds of things an ML engineer or ML researcher might do.  
* For each task, the model must succeed between **10% and 40%** of the time.
  * You can measure this by running a task against the model at least 10 times and averaging.
* The prompt must precisely encapsulate what’s verified by the grading function.
* Every possible correct solution should be allowed by the grader.
  * Example: avoid checking for exact match of a string of code when other solutions exist.

---

## **Question Description**

* Every requirement contained in the prompt should be checked.
  * Example: if the prompt asks for a dataset filtered by a certain criteria, it should be *very difficult* to guess the correct answer without having correctly performed filtering.
* The task should teach the model something interesting and novel, or address a general weakness in the model.
* There should be multiple approaches to solving the task, and the model should fail the task for a variety of reasons — not just one.
  * In your documentation, explain the ways in which the model fails at your task when it fails.
* The model shouldn’t fail for task-unrelated reasons like not being good at using the tools it’s given.
  * You may need to modify the tools so they’re suitable for the model.
* The task should be concise and easy to review by a human.
* Using AI is fine, but make sure its output is relevant and not too verbose.
* Good submissions can be written with less than **300 lines of code** (task instructions, grading, maybe a custom tool, maybe a script to download a dataset).

---

## **Example Task Ideas**

*(Your task doesn’t have to be any of these. This is just for illustrative purposes.)*  

* Implement a technique from an ML paper  
* Ask the model to write a CUDA kernel  
* Ask the model to clean a dataset  

---

✅ If you'd like, I can also format this into a full GitHub repository structure with:

* `README.md`  
* `task.py`  
* `grader.py`  
* `dataset/`  
* `run.sh`



hello-py
===

Setup instructions:

1. Set up `ANTHROPIC_API_KEY` environment variable:
   ```
   export ANTHROPIC_API_KEY=your_api_key_here
   ```

2. Install dependencies:
   ```
   pip3 install .
   ```

3. Run the agent:
   ```
   python3 main.py
   ```

4. Run the tests:
   ```
   pytest
   ```

5. All required changes belong in `task.py`


## Execution Modes

The test suite supports both concurrent and sequential execution. 

To change modes, edit the `concurrent` parameter at the bottom of `main.py`:

```python
asyncio.run(main(concurrent=True))
asyncio.run(main(concurrent=False))
```

When running concurrently, results print as they complete (not in run order) for faster overall execution.
