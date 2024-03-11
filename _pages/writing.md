---
permalink: /writing/
title: "Short Form and Ideas"
excerpt: "Nathaniel's short form writing"
author_profile: true
redirect_from: 
  - /shortform/
  - /writing.html
  - /shortform.html
---
This is a place for some ideas I've had which seem worth keeping track of. Some of them may be turned into longer essays at some point. A few were originally written as part of Serimats applications, Alignment 101/201 exercises, or similar things. 

What LLMs know vs what they can produce
------
I want to distinguish between two categories that seem a bit confused to me: what an LLM knows vs what an LLM can produce. By saying an LLM “can produce” something, I mean there is some not-excessively-convoluted prompt which will cause an LLM to respond with the thing. For example, “Who was the first president of the USA?” will cause chatGPT to respond with (something involving) “George Washington”, so I will say it can produce that information. But, as we’ve seen from many hallucinatory examples, it can produce many things which have no correlation with the real world, 

[1]

 and many outright falsehoods. When asked "Is this a valid proof that there are infinitely many primes? Suppose there are only finitely many, and decompose them into two sets, A and B. Then prod(A)+prod(B) isn't divisible by any prime" it responds by claiming this is not a proof. This is not true; chatGPT does not consistently produce correct information about this bit of number theory.

What about knowledge? What does an LLM know?

For people, I would say people know something if it is part of their mental model of the world.

[2]

 While I don't claim to have a good rigorous definition of a world-model, I certainly feel like I have a (limited, incomplete, not-fully-accurate) world-model and (to the extent it is accurate) I have knowledge of the world. I think this idea extends to LLMs: an LLM knows a fact about the world only if there is a representation of the world inside the LLM, which contains that fact. 

[3]

I’m convinced by things like Kenneth Li’s Othello work that a transformer-based architecture can spontaneously generate a representation of the world. And it’s certainly possible that, if we were much better at interpretability work, we would be able to say with confidence that GPT does know, in this sense, that (eg) Washington was the first president. In general, however, I think there is very limited evidence that any LLM knows anything. (Although, as of last month, not no evidence! Gurnee and Tegmark have a paper that I take to show strong evidence of a physical and a temporal world-model). Perhaps if we were much better at interpretability work, we could say with confidence that GPT does know, in this sense, that (eg) Washington was the first president.

Why does the distinction matter? One reason is that understanding what an LLM knows arguably gives a solution to Paul Christiano’s ELK problem. If we could identify causal pathways between “the LLM knows x” and “the LLM can produce x”, I would take that as some evidence that the LLM is “being honest” with us. If we could fully interpret the world-model of the LLM, and completely understand the pathway from world-model to production, we might even have something like a proof of that (although that doesn't seem likely to be achievable anytime soon).

But there's a more interesting possibility here. Consider the four possibilities for a piece of information, 

\(x\)

. An LLM doesn’t know, and can’t produce, 

\(x\)

 is a boring case. An LLM can produce, but doesn’t know, 

\(x\)

 is the case I think we are mostly in now. An LLM can produce, and does know 

\(x\)

 is the case we wish we were assured of. But what about a situation where the LLM knows 

\(x\)

, but cannot produce 

\(x\)

?

For a hypothetical that shows why knowledge without production might be interesting and important, imagine a world with roughly our level (or perhaps a bit more) of ML/AI capabilities and less knowledge of physics. Specifically, imagine Newtonian physics still being the paradigm, with no special relativity (let alone general). I can easily imagine Hypothetical-GPT-5 getting a world representation that correctly understands relativity–there’s a pattern on various astronomy forums of people going “Have you looked at the data for last weeks (eclipse/transit of planet/hypothetical-hubble photos)? It seems a little off, by (amount that Newtonian physics and relativity differ). Huh, weird.” and then dropping it. And H-GPT-5 can predict the numbers in those posts better if it captures the right understanding of physics in its world model. But any prompt of the form “explain everything about physics to me” will probably have H-GPT-5 producing a standard explanation of Newtonian physics. It could very easily know relativity without being able to produce it. I strongly suspect that in the near future, models will know truths they cannot produce in this way (although I expect it to be more sociological or linguistic than physical).

In the last few months, I've seen some critiques of interpretability. I think many make some good points (I was particularly impressed with Stephen Casper's EIS sequence). One point of substantial disagreement I have with them, however, is they claim that (in Stephen Casper's words) "[interpretability is] entirely fungible with other techniques related to describing, evaluating, [and] debugging". While I basically agree for the current successes of interpretability, I think the above example is a convincing case that there could, in theory, be important knowledge hidden within ML models in such a way that interpretability is the best/easiest/(only?) way to access it. I would be willing to bet that, if we had the tools to see it, GPT-4 knows a truth it cannot produce which people haven't formulated, or that GPT-4 possesses a more rigorous statement of something which has only been informally talked about by humans.


Shard theory and decay rates
------
I’m interested in decay rates of unused shards. A potential experiment to investigate this: what if the cheese starts out as “poison”, and then becomes edible after some medium number of time steps $t$? We train a maze-solving AI on small mazes in this regime–it will presumably learn to find the cheese, then wait nearby until the poison fades, then take the cheese. We then shift to a different training distribution of larger mazes, where the cheese is guaranteed to be inaccessible until after the poison has aged out and continue training (possibly two separate models, one with and one without weight decay). In the epochs where we train on the large mazes, we continue to evaluate on small mazes, with no poison. Does the AI maintain “cheese avoidance” before the medium number of time steps? How does this change with more training epochs in the large maze? With and without weight decay?

My assumption is that, with weight decay, we would see “cheese avoidance before t” steadily decrease with training epochs in the large mazes. I’d be very interested in seeing if the avoidance steadily decreased in terms of “how long the AI waits between arriving at the cheese and taking it” vs “chance the AI takes the cheese before t”. I’m also very interested in seeing whether or not this shard is maintained in the version without weight decay. My very-low-confidence guess is that it would vanish, but much more slowly than the version with weight decay.

I think this could be worthwhile for alignment inasmuch as we can learn to what extent model behaviors which are learned early are maintained over time. In humans, if someone is a recovered heroin addict, there is some evidence that they continue to have the reward circuitry associated with their addiction for years afterwards, and are thus more vulnerable to relapse than someone who has never tried heroin. If we have an AI which was quite expensive to train, and we notice undesirable behaviors, then is it easy/possible for mild retraining/fine tuning to eliminate this entirely? Or has the initial training baked the undesirability into the deep structure of the net, and the only way to get something with no remnant of it is to re-initialize and retrain from scratch (possibly after having modified your training set to explicitly reinforce against the undesirability)?

Short term optimism, long term pessimism (relative to other alignment thinkers)
------
Near-term, it seems like a lot of alignment thinkers believe that GPT-7 or something will be…worth being scared of, as an agent. I disagree–my mental model of LLMs with self-supervised training regimes is fundamentally very unlikely to be world-destroying (except possibly as a tool, but I would count that as a problem with Putin/Xi/Kim Jong Un’s alignment, not with the AI’s). I don’t think LLMs have strong emergent desires or goals, and I think we have some evidence against the proposition that they even have coherent world-models. While I think increasing parameter count can certainly increase accuracy, Chinchilla convinced me that we are more limited by high-quality training data, and after using basically the entire internet, it’s not obvious where to go next. I think human intelligence is long-tailed, and while GPT-4 is arguably more intelligent than average people, I believe we are several architectural and training regime revolutions (on the scale of the “RNNs to transformers” revolution) away from AGI that can be consistently 95th percentile intelligence. I also think I have a higher opinion of academia and industry’s success at taking low-hanging fruit than many alignment researchers, so I am more skeptical of recursive self-improvement and extremely fast takeoff. I think before we have misaligned super-intelligent AI, we will have misaligned highly intelligent AI, which will cause problems big enough to be a serious wake-up call, but not to destroy all value.

Longer term, however, I think people are trying hard to make something much, much smarter than us and give it goals, and I think they will eventually be successful, albeit maybe not for another 50+ years. But I think we have no idea, and no framework that looks promising to me for getting an idea, as to how to ensure a system has the goal that we want--Alex Turner's “Reward is not the optimization target” was pretty instrumental in making me realize exactly how true that is. Moreover, I think I am deeply skeptical of humanity’s ability to coordinate on large problems, especially ones where some people think there is a strong benefit to defecting. So I see very little likelihood of much human value remaining in the universe around (say) 100 years from now. This makes me sad, and I really hope I’m wrong.

Confusion on values/goals vs behaviors 
------
Over the course of my time thinking about alignment, I've become increasingly confused about the idea of goals vs behaviors. This probably started with reading Scott Alexander's "Blue minimizing robot". I think this has begun to seem like a pretty fundamental question to me. The two feel very distinguishable for humans, but I haven't been able to formalize the difference (if any!) for AI. (In the RL setting, there is a formalism that distinguishes between them, but I really want an answer which is agnostic to how a system was created/trained/evolved). To make things more concrete, GPT-4 very rarely says racist things (because that was a high priority during the RLHF phase of training). But is it fair to say it has a goal/value of not expressing racism? Or just that its behavior is typically not racist?

Compare with a person showering every day--that person has a behavior, but without more information, it's very difficult to tell if the behavior is due to (a) valuing being clean (b) valuing the feeling of showering (c) having a showering habit and not thinking much about it (d) other. In this human case, I can imagine hypotheticals that can distinguish the three scenarios--if someone was given a hotel room with a shower with chlorinated water (fine for the feel of a shower, might not feel clean afterwards) and a (scifi) closet that cleaned them with nanobots in 5 seconds, then they probably use the closet and no shower if it's (a), and use the shower if it's (b) (and maybe also use the closet if (a&b)). Moreover, I think people have enough self-knowledge that you can just ask a (thoughtful intelligent) person "do you do x because you value it intrinsically, or in pursuit of another goal, or something else?" And get a good (although certainly not great!) answer, in the sense that it is predictive of actions if hypotheticals like the above actually happen. 

I don't know a general way to set up hypotheticals for GPT-4/arbitrary AI that seem informative to me on this axis. (Thanks to Ishita Dasgupta for some insightful conversations which helped me realize how confused I remain on this topic, and for pointing out [this paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3077926/) which is fascinating, and might deserve a post in its own right.)

In defense of interpretability
------
I've been reading some people recently who seem very skeptical of the usefulness of mechanistic interpretability for alignment. While I certainly don't think it is a complete solution, or even anything close to a majority, I do think it seems like a very good thing. In particular, it seems like the only way for us to "check our work" with whatever alignment solution we end up using. I don't expect it to be perfect, but to me it seems like the only candidate for this, and my estimation of our survival chances go monotonically up with our mechinterp knowledge.

Why alignment is hard in five words
------
We have no training data. We have literally no examples of the form "given these inputs, the correct action for a smarter-than-human AI to take is x". We have sentences describing the correct action, but that isn't the same. If we ask chat-GPT for what a batter should do when a pitcher throws a ball, it doesn't matter how good the resulting description of the home run is--if we actually take chat-GPT, it can't hit a baseball.

"Alignment is pre-paradigmatic"
------
One piece of advice I hear often directed to new researchers is the idea that it is important to form your own models of AI risk, or that people should try to come up with solutions to the problems before reading much from the alignment forum. I don't know how true I think this is, but if it is true, it seems like obviously very bad news. In a field where people know roughly what they are doing (eg, almost any academic field more than 50 years old) one of the most important things to do is come to appreciate the common views and assumptions shared by the field. I would argue this is true even if (and perhaps especially if) the ultimate goal is productive criticism of a field. If it is important to "form your own models," that suggests alignment thinkers have made no consensus progress in the field thus far.
