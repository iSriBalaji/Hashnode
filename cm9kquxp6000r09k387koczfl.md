---
title: "Microsoft BitNet Explained: My Learnings, Insights, and Why It Matters in the LLM Race"
seoTitle: "Microsoft BitNet: My Thoughts, Learnings, and Real-World Implications"
seoDescription: "Explore Microsoft BitNet through hands-on learnings and key takeaways. Understand how BitNet fits into the growing LLM ecosystem and what makes it different"
datePublished: Thu Apr 17 2025 02:31:28 GMT+0000 (Coordinated Universal Time)
cuid: cm9kquxp6000r09k387koczfl
slug: microsoft-bitnet
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1744859160493/ef94afbd-4059-4c4e-9d56-011797124d61.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1744859728904/ce4de1f8-37b4-44c3-8d6a-808fc4ed5572.png
tags: artificial-intelligence, microsoft, opensource, machine-learning, nlp, deep-learning, transformers, llm, bitnet

---

Try it Live: [BitNet](https://bitnet-demo.azurewebsites.net/)

Microsoft launched a language model called BitNet with 2 billion parameters trained on 4 trillion tokens. The specialty of this model is how the parameters values are stored. BitNet b1.58 only uses about 1.58 bits per parameter

## Parameters

As we know most LLM use 16 or 32 bit for storing the parameters\[those are like knobs of an antenna to tune and adjust to get the respective TV channel signal better\]

Basically each parameters in the model has either of these 3 values: +1, 0, -1

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1744856206831/2eeefa70-1417-4eac-bd41-e34affc9b479.png align="center")

This is how it got the value 1.58 bits per parameter. With these 3 values in the parameters , it eliminates the usual complex matrix or tensor multiplications and replace the computation with just addition and subtraction. As we know Addition and subtraction is much faster and easier for computers.

## Why and What is the big deal?

By using only 3 values for the parameter, the model is made much smaller and faster, They also use less memory and energy compared to traditional models. More detailed info on the performance on their GitHub Repo: [Microsoft BitNet](https://github.com/microsoft/BitNet)

Also they say, even they use fewer bits, they can match or even many times perform better than the traditional models of similar size which uses usual float based parameters

In there hugging face, model description I noticed the memory and latency is significantly less compared to other state of the art models! They also measure the energy usage in Joules which is also less, making the model more accessible and sustainable

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1744856741343/de6e92a0-12db-4474-a817-9d74f0adc2be.png align="center")

For other performance evaluation metrics please refer their hugging face page: [Hugging Face Link](https://huggingface.co/microsoft/bitnet-b1.58-2B-4T)

This basically makes the model to run in local computers on CPU and GPU easily. In their Hugging face model page I noticed, **to get the most efficient performance use it in the bitnet.cpp**

## Formats of the model

In the page, they introced the model in 3 formats,

* 1.58bit format
    
* BF16 - Bfloat16 format
    
* GGUF - GPT Generated Unified Format