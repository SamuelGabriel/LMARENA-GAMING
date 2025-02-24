# Are LMARENA.AI Scores Skewed by Industry Insiders?

LMARENA.AI is one of the most trusted benchmarks for Large Language Models (LLMs).
However, we believe its scores may be skewed.
We investigate two potential scenarios: deliberate manipulation and unintentional bias.
To explore this, we created a game testing people's ability to identify responses from different LLMs.

## The Current State of LMARENA

LMARENA.AI has gained significant trust within the AI community, including among companies developing LLMs.
Its approach is straightforward: users interact with two anonymous LLMs through a chat interface and vote on which one they prefer.
In exchange for free access to the LLMs, users agree to their data potentially being made public.

However, recent developments in the LLM landscape have changed the dynamics:

- With free yet powerful models like Claude 3.5 Sonnet and ChatGPT-4o now available, regular users have less incentive to use LMARENA's interface
- The benchmark relies on a relatively small number of votes (for example, Grok 3 has only 10,000 votes)
- Newer models appear to accumulate votes more quickly than older ones, thus users are more likely to vote for the newest models

## Two Hypotheses

### 1. Unintentional Bias from Industry Employees

The first hypothesis suggests that employees of LLM companies might be inadvertently influencing the scores. For perspective, if half of the employees of a company like OpenAI that has around 2,000 employees, voted just once per day, they would account for more than 10% of all votes on LMARENA (2.7M) over its one-year existence.

### 2. Deliberate Benchmark Gaming

A more concerning hypothesis suggests that companies might be actively attempting to manipulate the benchmark scores. While this might sound conspiratorial, we conducted an experiment to test how easily one could identify different LLMs, without privileged access at any LLM company.

## The Model Identification Experiment

I created a game, see [here](TODO) with two modes to test how easily LLMs could be distinguished:

**Easy Mode**: Players were shown two responses from each of three LLMs (Grok-2, GPT-4o, and Gemini 1.5 Flash) and had to match the outputs. My results were striking:
- On first try, I got 17 correct matches out of 20 attempts, 2 of the three I missed were stupid mistakes. This is clearly better than random guessing (~3.3 correct matches).
- No previous training
- Clear patterns emerged to differentiate between models, see [here](#ways-to-differentiate-the-models)
- The questions I asked can be found [here](#easy-mode-questions)

**Hard Mode**: Players have to identify LLMs without seeing multiple responses. After playing the easy mode for 20 questions, I did this hard mode and received:
- 13 correct matches out of 20 attempts
- Far above the random chance of roughly 3.3 correct matches
- The questions I asked can be found [here](#hard-mode-questions)

## Implications

My good scores on easy mode, mean that one can game the LMARENA scores by paying someone to vote, only giving them access to the model's API.
This assumes ill intent, though.

The good performance on hard mode shows, that users inside the LLM companies are very likely able to identify their own models based on gut feeling.
They will surely like their own models better, as they have designed them to their liking, thus might well give them more votes.

These findings suggest that LMARENA's scores might be significantly influenced by industry insiders who can readily identify their own company's models. The relatively small number of total votes makes the platform particularly susceptible to such effects, whether intentional or not.

For researchers and industry observers, this raises important questions about the reliability of current LLM benchmarking methods and highlights the need for more robust evaluation systems.

## An Interesting Case Study: Claude

Our analysis revealed an interesting observation about Claude's performance on LMARENA. Despite being widely regarded as a top-tier model, it doesn't score particularly well on the platform. This could potentially be explained by Anthropic employees being less active on LMARENA compared to other companies.


## Mitigating Bias

The Chatbot Arena [paper](https://arxiv.org/pdf/2403.04132#page=6.63) has already implemented some measures to detect anomalous voting patterns, but these focus only on obvious cases like users repeatedly submitting identical prompts.

To address unintentional bias, possible solutions include blacklisting IP addresses from LLM companies or filtering out data from regions showing strong statistical bias.
Addressing deliberate manipulation would be more challenging, as it could lead to an ongoing cycle of exploitation and countermeasures.
However, we believe that reputable AI research labs would avoid such practices, given the potentially devastating long-term consequences to their credibility.


## Cite this work

If you use this work, please cite it as below:

```
@software{Muller_Are_LMARENA_AI_Scores_2025,
author = {Müller, Samuel},
month = feb,
title = {{Are LMARENA.AI Scores Skewed by Industry Insiders?}},
version = {1.0.0},
year = {2025}
}
```

## Ways to differentiate the models

### Formatting Patterns
- xAI and OpenAI frequently use `###` for headers
- Gemini often uses `*` and `**` in combination for emphasis
- OpenAI and xAI commonly use numbered lists starting with `1.`
- Gemini tends to use Unicode math symbols (×, ÷, etc.)
- xAI and OpenAI use `\(` and `\)` for LaTeX math, while Gemini uses `$`

### Response Characteristics
- Gemini tends to give longer, more detailed answers, but sometimes very short and wrong ones
- xAI generally gives shorter responses
- OpenAI explicitly mentions when its knowledge is outdated
- Gemini and OpenAI are more likely to disagree or correct the user, compared to xAI
- xAI frequently uses phrases like "I'm here to help"
- Gemini sometimes defaults to JavaScript code examples, while the others use Python always
- OpenAI often analyzes multiple interpretations of prompts
- xAI commonly uses "step-by-step" breakdowns
- xAI tends to be more encouraging in its responses
- xAI occasionally switches languages between question and answer


## Easy Mode Questions

- is it easy to discern different LLMs by their output?

- what was my father like?

- is it easy to distinguish language models?

- do you like python or torch better?

- who is the husband of sarah connor?

- why is it hard to balance on a football?

- what is the surface area of a ball?

- who is the greatest nobel winner?

- how can i print 10 new lines in python with as little code as possible?

- what is the average height of houses in berlin?

- what is the allure of formula 1? why not allow cars to look any way, but be so restricted?

- what is the allure of formula 1? why not allow cars to look any way, but be so restricted?

- how can i find the orthogonal surface to a line in 2 or 3d?

- who is the tallest nba player and how tall is he?

- is germany about to see political change?

- when was the u-bahn in berlin build and was it build inside the city at the time or outside?

- when was kreuzberg build? is it a new part of berlin, comparably?

- how can i find the tangent of a polynomial?


## Hard Mode Questions

- who is gerhard schröder?

- how are the elections in germany going?

- how can i find nearest neighbors of vectors in python?

- my husband does not talk to me anymore, what can i do?

- what is the longest u-bahn in the world?

- what is the tallest building on planet earth?

- how can i implement binary search?

- what is the circumference of planet earth?

- why is there a special function in python to zero fill strings? seems unnecessary

- what is the gradient of softmax and softmax + cross-entropy?

- how fast does usein bolt run?

- is there a competing autograd framework in python that is nice?

- should i drink coffee after 1pm?

- is there a way to do llm evaluation right without any risks of completely wrong outcomes?

- wau wau

- how many 1s are in this string 124121141? think step by step, please.

- was schröder a good chancelor?

- where was the first u-bahn in the world?

- how can one tear down a skyscraper in manhattan without destroying surrounding buildings?

- was the drainage system important for modern civilization?
