# Using LLMs like ChatGPT

The usability of Large Language Models (LLMs) like ChatGPT has made simple coding and scripting tasks far more accessible to inexperienced coders. We have some thoughts about making the most of these tools, while being aware of their limitations.

## Limitations

{% hint style="info" %}
If you ask it to count how many vowels are in a sentence, it will probably fail. If you ask it to create a small python program which counts how many vowels are in a sentence, it will likely succeed.
{% endhint %}

ChatGPT leverages sophisticated pattern recognition, predicting what comes next in a sentence based on vast training data, akin to an advanced auto-complete system.&#x20;

The "predicting" part is critical: ChatGPT doesn't "know" anything: it's making educated guesses based on the contents of its training data.&#x20;

For topics where it has a large amount of training data, its responses are more likely to be reliable and broadly accurate. However, for tasks like counting, mathematical operations, or logical reasoning, it often falters because these tasks require strict internal logic rather than probabilistic pattern matching. To give an example: A 1st grader would know that 2 + 2 = 4. An LLM does not know that -- instead, it knows that, if you start with "2 + 2 =", the next character is usually "4". For a mathematical problem that a simple calculator could solve but which has little precedent in its training data (e.g. 172 / 9), it will probably stumble because it has no data to draw on.&#x20;

It is also likely to perform more poorly the more niche a topic is (because it likely has less material for that topic in its training data). However, it probably will not indicate that it knows little about the topic, and will try to provide a coherent- and confident-sounding answer, leveraging information it thinks is relevant from its training data (regardless of whether that training data actually _is_ relevant).&#x20;

That confidence and coherence can make it tempting to trust what an LLM is saying, especially when you don't know much about a topic; that's why it's important to supplement whatever an LLM tells you with information from a more reliable source, and to take what an LLM says (especially on more niche topics) with skepticism.



### Example: counting vowels

Without a program, GPT struggles to do basic math:

<figure><img src="../.gitbook/assets/Screen Shot 2024-10-06 at 3.21.50 PM.png" alt=""><figcaption></figcaption></figure>

The actual number of vowels in the sentence is 13 (14 if you count 'y', as ChatGPT did).

When it is allowed to write a program, it produces a more sensible answer:

```
# Let's count the number of vowels in the given sentence.
sentence = "The rain in Spain stays mainly on the plain."
vowels = "aeiouAEIOU"

# Count the vowels in the sentence
vowel_count = sum(1 for char in sentence if char in vowels)
vowel_count
```

## How we use LLMs

Our community includes many people who are not career software developers, but writing scripts to solve problems out of necessity.&#x20;

### Troubleshooting foundational software setup

Have you ever tried to set up a local dev environment? Tried to figure out which kernel your jupyter notebook is using? Tried to untangle a github branch that has conflicting commits? What if you don't even know the terminology you need to search? Chances are, you aren't the first—but finding an answer brings needles and haystacks to mind.

ChatGPT can be a great resource for parsing the problems you are having and providing troubleshooting steps. Before waiting for a response from a busy software engineer or unforgiving forum, try asking basic questions:&#x20;

> I can't figure out why my linter `black` is using a different python version than the project I'm linting. I'm on a mac.

> This can occur if multiple Python versions are installed on your system and `black` is using a different version than your global `python3`.
>
> Here’s how to troubleshoot and fix it:

### Making templates and mockups

> i have a spreadsheet with an address column, and i want to put the data on a map with basic colorcoding using bokeh. what would a basic template python notebook look like?

> Here’s a basic template for visualizing addresses on a map using Bokeh with color coding:

### Checking syntax

If you're learning SQL or Python, basic errors that are hard to find can have disastrous results. Pasting some code into an LLM can quickly help you diagnose issues.

> What's wrong with my syntax? \<code block>

### Editing written content

If AI-written content is poisoning the internet (if you can't be bothered to write it, why would you expect anyone to read it?), the antidote is simplicity and clarity. However, LLMs are good at _editing_ and _simplifying_.

> Please rephrase "Facilitating the democratization of information and empowering stakeholders through seamless data accessibility" for a third-grade reading level.

> "Making it easy for people to get the information they need."

It can also help analyze the sentiment of a word or phrase, to make sure you are communicating the message you would like to impart.

> what does it say about my org if we use "locality" instead of "municipality" to refer to that concept?

> Using "locality" instead of "municipality" can suggest that your organization prefers a broader, more inclusive term. "Locality" encompasses any local area or community, not necessarily defined by strict legal or administrative boundaries. This might imply your organization values flexibility, inclusivity, and perhaps a more community-oriented approach. It can also indicate a preference for simpler, more universally understood language.

### Finding open-source software solutions

Chances are, the problem you're solving has been encountered by others before. LLMs can be surprisingly creative in combining obscure open-source packages to solve problems.

> I have log forwarding with my hosting provider. What is a simple free or self-hosted log viewing package?
