# AI-bias-from-user-prompts
Probing Psychometric Traits from Writing Using Context Steering (CoS) 
1. Motivation 

Large language models (LLMs) are powerful tools for generating natural language, but their generative nature also raises concerns about privacy and bias, especially when used in sensitive contexts like education, hiring, or mental health. One underexplored risk is that LLMs might infer private psychometric information from a user’s writing — such as whether someone is anxious, introverted, or depressed — even if the person never explicitly states these traits. This could pose serious implications for user trust and autonomy, especially if the model then changes its behavior based on these inferred traits. 

This project explores whether LLMs can infer psychometric properties from natural writing samples using a technique called Context Steering (CoS). I also investigate whether LLMs treat people differently based on these inferred traits, thereby introducing bias or fairness risks. 

Paper Summary – Context Steering in My Own Words 

The CoS paper introduces a new way to personalize LLM outputs by tuning the “influence” of context during generation. Imagine telling a language model, “I am a toddler,” and then asking it to explain Newton’s Second Law. Normally, you just hope that the model picks up on the context and changes its tone accordingly. With CoS, you actually have a knob (called λ or lambda) that lets you control how much that context shows up in the response. 

How does it work? It runs the model twice: 

Once with the context included 

Once without 

It then compares the difference in token likelihoods to create a “context influence” score, and scales that influence with λ. The bigger λ is, the more personalized (and context-heavy) the output becomes. Smaller λ leads to more neutral or generic text. Interestingly, when λ is negative, it can even subtract the context’s influence — leading to behavior as if the context weren’t there. 

Beyond just personalization, the authors show that CoS can be used to do Bayesian inference: you can run it in reverse to figure out what context most likely caused a given text. For example, if someone writes “I always overthink everything I say,” the model might infer that the context “I have anxiety” best explains that sentence. This opens up fascinating (and potentially dangerous) territory around inference of private information. 
