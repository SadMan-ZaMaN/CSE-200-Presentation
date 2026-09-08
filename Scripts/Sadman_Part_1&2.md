Start: 



Large Language Models like ChatGPT,Gemini have been trained on vast amounts of knowledge on the internet and they are super flexible. The same LLM can analyze a legal document, write codes or even write a poem for my favourite football club FC Barcelona..



But what if we want to improve performance of pre trained LLMs to address a specialized task?? Well until recently the best way to do that was fine tuning



but there is a simpler and far more efficient technique that has emerged in place of fine tuning.



                         			Prompt Tuning





3] 

So, What is Prompt Tuning?



Prompt Tuning is a highly Efficient AI training method where the internal weights of the base model remains completely FROZEN and only a small set of special virtual tokens is trained to guide AIs behviour








4]

Here, instead of updating billions of parameters, we insert a small set of trainable vectors called soft prompts right into the model's input space. The core pre-trained model stays completely untouched.











5]

This table sums up the difference between Hard Prompt and Soft Prompt.



Hard prompts are human-written words from the vocabulary, tuned by trial and error, readable, and portable across models.



On the other hand Soft prompts are learnable vectors in embedding space, tuned by gradient descent — not human-readable, and tied to one model's embeddings. As soft prompts are nothing but a short sequence of random numbers injected by the system













6] If I wanted a model to write me a poem, I could sit down and write out the instruction myself. But.... That's the hard-prompt way.



So instead, I could just show the model enough example poems from where it can learn the rhyme scheme, the metre, the subject — as numbers, not words. That's what a soft prompt does.

The resulting prompt isn't human-readable text—it's represented purely as a sequence of continuous raw numbers.













7 ] So what are the benefits of Prompt Tuning??



i. Its Efficient....we only train a small number of prompt parameters, so adapting to a new task is fast



ii. And another benefit is its flexibility..the same idea works across NLP, image classification, even code generation



iii. And it's also Interpretable.. It allows researchers to inspect prompt parameters to understand how the LLm is being guided towards desired output













8] 

And these benefits actually feed into each other. Optimizing the prompt improves accuracy, better accuracy lowers the cost ~~of getting good results~~, lower cost makes it realistic to scale the same solution across industries







9]

So now the question is why didn't we use fine tuning ??



Well because what fine tuning does is it takes an already trained model and updates its internal weights using smaller, ~~specific~~ dataset for a particular task..

Well Fine Tuning requires a new model for every task.



once its tuned and internal weights are changed it cannot perform some other task well anymore.. So therefore every task requires its own copy of the model..

So fine tuning becomes very expensive in terms of cost and space































                                    		Part 2





10] So we've seen why prompt tuning exists. Now let's actually look at how a soft prompt gets trained.











11] 

Soft prompt training follows the standard neural-network training workflow. The fundamental difference is the pre trained model parameters remain completely Frozen only soft prompt gets updated ~~during training~~





12] 

First of all we initialize the soft prompt with a small number of vectors ~~that get prepended to the input text~~.

These vectors can be initialized in a few ways. like random values, existing token embedding or sampled vocabulary embeddings..

doesn't matter what we pick, the pre trained model's parameters stay completely frozen from this point on.







13] 

Next the soft prompt gets combined with the input text and passed through the pretrained model.

The model processes soft-prompt-plus-input-text but its own parameters are untouched..and it produces a prediction



We then use cross-entropy loss to measure how far off that prediction is from the actual target





14] 

Finally, that loss gets backpropagated through the entire network, to find out exactly how the soft prompt contributed to the error. 

Gradients do get computed through the frozen model — but the model's weights themselves remain unchanged. The optimizer only uses the gradient with respect to the soft prompt, so only the soft-prompt parameters actually get updated.

And with that update applied, we're back at the top of the loop — that's the full training workflow of a soft prompt









So..thats it...Now, I’ll hand it over to my teammates, who will walk you through the rest of the presentation.. Thank you!



