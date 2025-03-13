---
title: "Notes to Computational Approach to Language and Mind (CALM)"
date: 2025-02-05T15:38:14+08:00
draft: false

---

# Week 1

- **Jargon checklist**: [View](Jargon_checklist.pdf)
- **Reading: AI-pocalypse**: [View](AI-pocalypse.pdf)

# Week 2: LSA to SRNs

In this seminar, we shall take one particular view of what "meaning" is, and see it "in action" as embodied in Latent Semantic Analysis (LSA). Concepts will include: words-as-vectors, semantic space, semantic distance/similarity. We shall then consider how the same kinds of semantic space can be induced using a Simple Recurrent Network (SRN). Concepts: distributed representation, spreading activation, weight change, recurrence, the prediction task, emergent representation. In the folder, you will find the slides (if they've been uploaded!) in movie format (showing the transitions and animations) AND in PDF. The movie can be slowed down or sped up as desired!

- **Slides: SRN_1**: [View](SRN_1.pdf)
- **Reading: Chapter 13_The Ascent of Babel**: [View](Chap13_TheAscentofBabel.pdf)

## Other Resources

- **Video Tutorial**: [Neural Network Simply Explained](https://www.youtube.com/watch?v=ER2It2mIagI)
- **But what is a neural network? | Deep learning chapter 1**: [View](https://www.youtube.com/watch?v=aircAruvnKk&t=0s)
- **What is a neuron? | Deep Learning Tutorial 3 (Tensorflow Tutorial, Keras & Python)**: [View](https://www.youtube.com/watch?v=VhRtaziEWd4)

# Week 3: From Backprop to Word2Vec

In this seminar, we shall learn how to modify the weights in a multi-layer network so that "what you get" is closer to "what you want". This is "backpropagation". We shall see how a combination of recurrence and backprop makes it very difficult (impossible, in fact) for an SRN to scale up to very large vocabularies (and more complex sentences). Word2Vec offers a solution to the scaling problem and can generate a semantic space for large vocabularies. The recommended reading can be found in the folder, together with the lecture slides (once uploaded!).

## Video Tutorials

- **What is Word2Vec? A Simple Explanation | Deep Learning Tutorial 41 (Tensorflow, Keras & Python)**: [View](https://www.youtube.com/watch?v=hQwFeIupNP0&t=45s)

## Slides and Notes

- **Slides about Word2Vec**: [View](Word2Vec.pdf)
- **A brief note on "Back propagation through time"**: [View](Backpropagation_through_time.pdf)

## Additional Resources

- **Recurrent Neural Networks (RNNs), Clearly Explained!!!**: [View](https://www.youtube.com/watch?v=AsNTP8Kwu80)

# Week 4: Amplify the Echoes

In this seminar, we shall attempt to consolidate key concepts from the previous two content-intensive seminars. Taking a multi-layer network, setting weights to random, and then expecting it to learn through back-propagation and converge on near-correct mappings between input and output is a little like expecting those infinite monkeys to come up with the works of Shakespeare. But that's ok, and understanding that is key to understanding how deep learning works. There's a large element of trust here! Long Short Term Memory units (LSTMs), and Gated Recurrent Units (GRUs) are the final conceptual step towards having everything you need going forward. Open up the folder and read my description that accompanies the "more advanced" introduction...

## Video Tutorials

- **Simple Explanation of GRU (Gated Recurrent Units) | Deep Learning Tutorial 37 (Tensorflow & Python)**: [View](https://www.youtube.com/watch?v=tOuXgORsXJ4)

  **Note**: This has a really nice and simple explanation of GRUs and LSTMs. These are the key to enabling a recurrent network (an RNN) to remember those echoes long enough without them fading from the network's memory. He has a nice example of the difference between having to remember something (i.e., keep it going through successive states) or having to forget something (stop it from going through successive states). He does put up, near the end of the section I want you to watch, an equation for a weighted sum (and then a related equation) but you can ignore those. Only watch until 6:18. It breaks down after that point!

- **A simplified description (by GA) of what a GRU is/does**: [View](simplistic_GRU.pdf)

- **What is LSTM (Long Short Term Memory)?**: [View](https://www.youtube.com/watch?v=b61DPVFX03I)

  **Note**: This is a very simplistic approach to LSTMs. It's made by someone at IBM. Oddly, there is one slight error - he describes (at 3:060 the recurrence as occurring between the output and the hidden layer (i.e., the output feeding back into the hidden layer) but in fact, the key recurrence is between the hidden layer and itself (i.e., the hidden layer feeds both to the output AND, at the next timestep, to itself).

- **Illustrated Guide to LSTM's and GRU's: A step by step explanation**: [View](https://www.youtube.com/watch?v=8HyCNIVRbSU&t=32s)

  **Note**: DO NOT PANIC! The concept is remarkably simple. It's just that it is described in a really complex way, AND there is no account of how these things LEARN... so it seems like magic - how on earth can it know that certain input is more relevant than certain other input such that it passes one through intact but forgets the other (in fact, it passes one through to some extent and passes the other through to a lesser extent)? We'll leave the learning part to the class, but what I've just described is really all that these things are doing (whether LSTMs or GRUs) - when receiving the hidden activation state from the prior time-step, it multiplies that state by a number from zero (it completely forgets it and nothing of that state passes through...

# Week 5: Event representation as comprehension

This is based on a paper by myself and a colleague, Forrest Davis. It's a computational modeling paper showing how RNNs can encode important aspects of event knowledge. It also sets out a bit of an agenda for understanding what kinds of information propagate through a sentence as it unfolds in time. One question we shall consider is whether these RNNs capture the essence of language understanding, at least insofar as it is applied to event comprehension.

## Reading

- **Finding event structure in time: What recurrent neural networks can tell us about event structure in mind**: [View](Davis_Altmann_2021.pdf)

# Week 6: Attending to the context

In this session, we shall focus primarily on the concept of Attention, but we will also be exposed to Transformers and Bert.

## Video Tutorials

- **A primer on Attention (super simple and clear)**: [What is Attention in Language Models?](https://www.youtube.com/watch?v=j10yrR6PPfg)
- **A simple introduction to Transformers and Context**: [What are Transformer Models and How do they Work?](https://www.youtube.com/watch?v=tsbRdJbJi9U)

## Reading

- **How LLMs Work ? Explained in 9 Steps**: [View](How_LLMs_Work_Explained_in_9_Steps.pdf)

  **Note**: This is a super simple introduction to what transformers do after they've been trained. I recommend you look at this, but just know that the "magic", so to speak, is in the training for Step 5. But to cut the much longer story short: The transformer learns the appropriate attention weights through back-prop or equivalent algorithms - the weights are adjusted in tiny increments so that the network converges on better predictions. It actually isn't magic after all!

- **The Narrated Transformer Language Model**: [View](https://www.youtube.com/watch?v=-QH8fRhqFHM&t=4s)
- **BERT 101**: [View](BERT101.pdf)

  **Note**: A very high-level introduction to BERT, an early example of a transformer architecture that underpins much of Google's natural language processing (NLP) applications.

## Slides

- **Recap_II_and_Transformers**: [View](Recap_II_and_Transformers.pdf)

  **Note**: These are slightly annotated versions of the slides that I should have presented on Monday. But I'd ran out of time! But don't worry, as usual, we shall recap on Monday...

# Week 7: How fine-tuning creates chatbots

If you've managed to get through The Illustrated Transformer (or The Narrated Transformer) you'll have a really good grounding on how Large Language Models work. But turning them into chatbots is another matter. That's where fine-tuning comes in. The links inside this folder are fairly high-level descriptions of Chatbots, and although the final one (from the maker of Mathematica – he knows his stuff!) looks long and daunting, it IS long, but less daunting if you ignore some of the visuals.

## General Overview

- **How Large Language Models work: From zero to ChatGPT**: [View](How_LLMs_Work_From _Zero_to_ChatGPT.pdf)

  **Note**: This is a very general overview of LLMs that ends on chatbots and how they're trained. It's very readable.

## Mastering LLMs

- **LLM Training: A Simple 3-Step Guide You Won’t Find Anywhere Else!**: [View](LLM_Training.pdf)

  **Note**: This is a shorter but slightly more detailed description of WHY one needs to fine-tune, and what it accomplishes.

## What ChatGPT is doing

- **What Is ChatGPT Doing … and Why Does It Work?**: [View](What_is_ChatGPT_doing.pdf)

  **Note**: This is quite long. It looks complex, but it's not. Just ignore some of the graphics! It's written by the creator of Mathematica - Stephen Wolfram. I thought it would be dreadfully complex, but it is neither too complex nor too dreadful.

## Llama-2

- **How does Llama 2 work?**: [View](https://www.ibm.com/think/topics/llama-2#:~:text=Llama%202%20is%20a%20family%20of%20transformer%2Dbased%20autoregressive%20causal,the%20next%20word(s).0)

  **Note**: This is a highly readable description of a ChatGPT competitor developed originally by Meta AI and now released as open source. Llama-2 is notable for being a relatively small LLM that nonetheless outperforms many competitors.

## Slides

- **Key_concepts**: [View](Key_concepts.pdf)

  **Note**: These slides summarize the key concepts for this week's theme. NOTE: These are from 2024 - the 2025 slides will be updated over the next few days.

