PREP is a mnemonic I created to help you remember the steps involved in solving whiteboard coding problems. It stands for **P**arameters, **R**eturn, **E**xample, **P**seudocode.

![](https://cdn-media-1.freecodecamp.org/images/1*vbQ8FGNAlEC4jnxg8Z7Ceg.png)

The mnemonic is new, but the underlying technique is battle tested. This is essentially a beginner-friendly version of [test-driven development](https://en.wikipedia.org/wiki/Test-driven_development) that lends itself well to coding challenges.

Let’s get right to it and learn PREP through an example problem. We’ll use JavaScript, but this technique works for just about any programming language.

### Your interviewer asks you to w**rite a function that accepts a sentence and returns the longest word. What do you do?**

#### “P” is for Parameters

Most problems involve writing a function. In this step you need to determine what parameters your function should accept. Then you need to give them meaningful names.

Keywords like “takes in” or “accepts” in the problem statement will guide you here. If it’s unclear, you can also ask the interviewer for clarification. In your case, the statement “accepts a sentence” tells you that the function should accept a single string parameter.

So you’ve determined the _type_ of your parameter. But what should you name it? It might sound simple, but good naming is a crucial programming skill, and it takes practice.

You could call yours “sentenceString,” but calling it “sentence” is more concise and still makes it clear we’re dealing with a string.

Since this is your first step, you also need to think of a meaningful name for your function itself. In your case, “longestWord” is both concise and descriptive. Now that you’ve decided this, you can write the shell for your function like this:

#### “R” is for Return

What does this function _return_? Is it a number? A boolean? A string?

Remember: the value a function returns is not the same as what it might display in a print/log statement.

Once again, you can look at the problem statement for clarification. “Returns the longest word” tells you that you’re returning a _word,_ and you know that words are strings. Let’s make this crystal clear by creating a variable to represent this return value and rigging up your function to return it. Even though you aren’t returning the correct answer yet, you’re set up to return the correct type. You have created a placeholder that will make the next steps easier.

#### “E” is for Example

Even for expert developers, static code is harder to understand than running code. You want to make your code runnable and “alive” as soon as possible. You can breathe life into your function with an example test invocation.

You know that if your function accepts the sentence, “I saw a hippopotamus,” it _should_ return the string “hippopotamus” once it’s properly working. But for now, you just want to see your placeholder value from the last step to confirm your code is runnable and setup correctly.

#### The last “P” is for Pseudocode

While it’s tempting to just dive in and start coding now, it would be too easy to get caught up in a detail that could distract you from the bigger picture. You need to devise a strategy first, and _pseudocoding_ is just the tactic for this.

Pseudocode is a series of precise statements written in spoken language comments that describe what you need to do.

### You’ve finished PREP. Now you can code!

The four steps in PREP helped you clearly frame the problem and think about how to solve it. In truth, accurate framing is half the battle. Most interviewers will already be impressed to see your methodical approach. At this point, your goal is to just write code that will make your examples and tests pass. You’ll do this by encoding each of your pseudocode steps.

You know you’ve got a working solution when you can run your code and see the correct output.

You’ve made it through the hardest part now. You can breathe a sigh of relief that you’ve at least gotten to a working solution. At this point, there are just two more questions to think about:

-   Are there any edge cases that would break the code? For example, do you need to take into account sentences that have a period at the end of them? You’ll write more test cases for these edge cases, then fix the code if necessary.
-   Can you make the code cleaner or more efficient now? You should discuss ideas with the interviewer so that they know your thoughts before risking breaking the solution.

That’s it! This process might seem overly mechanical at first, but trust me, it will become second nature — much like the steps in learning to drive. Even after programming for more than 12 years, this is still roughly the sequence I follow when I’m problem solving. I’d more likely use a formal testing framework instead of log statements like we did here, but the steps are the same either way.

Now you try it! Here are a few beginner-level problems you can practice with, in roughly ascending order of difficulty:

1.  Suppose you have an array of string like [ “adios”, “bye”, “ciao” ]. Your task is to write a function called total_characters that accepts such an array as a parameter and returns the summed number of characters across all the strings in the array.
2.  Write a function to flip a coin n times that returns the numbers of times a “heads” was flipped.
3.  _(From [Free Code Camp](https://www.freecodecamp.com/challenges/sum-all-numbers-in-a-range))_ We’ll pass you an array of two numbers. Return the sum of those two numbers, and all numbers between them. The lowest number will _not_ always come first. Try using PREP to set this up yourself first, but then feel free to confirm your setup and finish solving it [here](https://www.freecodecamp.com/challenges/sum-all-numbers-in-a-range).

PREP has already helped several [First Step Coding](https://firststepcoding.com/) learners ace their coding interviews, and I hope it can help you too. Happy coding!


-------------------

## Whiteboarding

Given that tech firms will err on the side of not hiring (wanting to avoid false-positives), you want to stack the odds in your favor and give them no doubts. These points might seem obvious, but they are problems I’ve seen come up time and time again.

### Slow Down

Slow-down, chill-out, and try to write as neatly as possible. This will help you stay organized and focussed and will also helps the interviewer understand whether the code actually does what it is meant to.

### Ask questions

Many interview questions are intentionally vague; the interviewer wants to see how you handle uncertainty and what assumptions you make. If you are implementing an algorithm, what are the constraints? Memory, runtime, size of inputs, etc.

As you are answering the question talk through what you are doing and what your thought process is. The interview is as much about the how you get to the answer as the answer itself.

### Code how you’d normally code

One of the most common mistakes I saw was candidates getting lost in their answer. Hopefully you wouldn’t write a 50-line function in “real” life, so don’t do it in an interview. In many ways it is even more important to break up your code when working on the whiteboard; you don’t get to cut-and-paste, and in the heat of an interview it is easy to lose track of state.

### Check your work

When you think you are done, check your work.

Most errors will happen at the termination cases. The best way to do this is to take a minute to run through the code with some sample input. It’s not unlikely you’ll have missed a case or introduced an off-by-one error, your interviewer won’t mind you taking time to do this, in fact, they’ll probably be impressed.

Also, check how your code handles unusual inputs and edge cases? Think about how you would unit test the code and write them up on the board.

### Practice

When preparing for an interview you’ll likely be brushing up on algorithms and reading about the latest technologies and best practices. You may as well take an hour and code something up on a whiteboard (or even on paper if you don’t have a whiteboard).

Think about how you’d implement a JQuery helper or a method from your favorite language’s standard library. Search the web for sample questions—ignoring any site that talks about manhole covers.

When you think you’re done, take your code and see if it actually runs. Learn from what didn’t work.

### Research

Presumably you want to work at the company you are interviewing at, so try and seem interested and enthusiastic about what they do.

You’ll undoubtedly get asked about the company’s products and “why you want to work here”. It _can_ be hard to come up with good answers on the spot, so research the company and figure out what you’d say ahead of time.

### Have fun

More than anything, try to have fun. Be curious and enjoy the challenge. You’ll get more out of process and probably come across better all the more because of it. As well as seeing whether you are capable, the interviewer is also looking to see if they would _want_ to work with you.