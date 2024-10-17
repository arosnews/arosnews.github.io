---
layout: post
title: 64-bit Odyssey 2.0 and JavaScript story
subtitle: by Deadwood
lang: en
ref: 1024a1
---

In this short article I'm going to show you different ways that upcoming 64-bit version Odyssey 2.0 can execute JavaScript code and performance implications of these choices. Some of the results are quite interesting, coming very close to modern-day (October 2024) Firefox performance. This is especially important taking into account that Odyssey 2.0 WebKit engine has been released in February 2019.  

## Background

I'll start with giving some background. All tests were performed on 4-core AMD Ryzen 3 2200G capped at 2.3Ghz running Linux Mint 21. Reference Firefox used was in version 131. Three benchmarks were used for testing. Octane 2.0 and Kraken 1.1 are mainly computational performance benchmarks which do not involve test of user experience. Last benchmark, Speedometer 2.0 simulates dynamic UI of modern web application and can be used as proxy for user experience. You will find links to benchmarks at the bottom of the article.  

On Odyssey side, two run configurations were used. First, running Odyssey from AROS linux-hosted, which like other NG operating systems is a single processor environment. In second configuration, same Odyssey has been running under AxRuntime which supports use of multiple host processor cores. Additionally three different JavaScript settings were benchmarked. First running without an Just-In-Time compilation, which resulted in JavaScript interpreter handling all the code. Next tests with JavaScript standard JIT were ran and lastly tests with JavaScript concurrent JIT were executed. Concurrent JIT is an approach where compilation of JavaScript is being done by one or more helper tasks, so that main JavaScript task is not burdened with it.  

## Results

Following this introduction, here are the results.  

![Results](/assets/img/art.png)
*Results*

Odyssey 2.0 is capable of closing the gap with modern day browser. The key is being able to use multiple processor cores, but also further updates of the engine are needed as well as solving the rendering bottleneck will be necessary.There are a few interesting conclusion visible in the above table.  

First, let's look at situation where there is no JIT. This is the scenario that is present in Odyssey 2.0 32-bit, as JIT is no longer supported on 32-bit WebKit engine. Additionally, existing WebKit-based browsers running on other NG operating systems should also show similar results. What is visible in results of CPU-intensive benchmarks is that this scenario reaches only around 5% of performance of modern day browser! When it comes to user experience, which of course counts more than pure CPU, the results are around 25% of reference. This unfortunately makes for a visible slowdown when browsing heavy JavaScript pages.  

So what changes when standard JIT is enabled? A lot when it comes to CPU-intensive benchmarks. We can see a 10x performance improvement in both Cyclone and Kraken, reaching around 50% of reference. When it comes to user experience test, JIT also brings improvements and they are around of additional 20% above no JIT case. We are looking at another bottleneck here, probably with rendering code which is not accelerated.  

Finally, the Concurrent JIT shows very intriguing results. With CPU benchmarks it gives between 80% and 90% of reference on AxRuntime but only 30% to 40% on AROS. Similar situation is visible with user experience benchmark where it is an improvement under AxRuntime but degradation under AROS. Why is this happening? The answer lies in underlying architecture. Currently AROS can utilize only one processor core, meaning that the task of running JavaScript and the task of compiling JavaScript are constantly fighting over same resource and switching between each other. This makes it worse then when these two operations are being done by one task. In AxRuntime situation there is no such switching. Task of running JavaScript is allocated to one processor core and tasks of compiling JavaScript can be allocated to other existing core and run in parallel!  

## Conclusions

Based on the above results, there are conclusions I’d like to share.   

First, Odyssey 2.0 32-bit lack of JIT shows that line of 32-bit system is coming to an end. If we, as AROS community, want to experience good browsing experience, we need to migrate to 64-bit environment and use the power of improvements in hardware and software.  

The other conclusion is that 64-bit Odyssey 2.0 is capable of closing the gap with modern day browser. The key is being able to use multiple processor cores, but also further updates of the engine are needed as well as solving the rendering bottleneck will be necessary.  


References:  

https://chromium.github.io/octane/  
https://mozilla.github.io/krakenbenchmark.mozilla.org/kraken-1.1/driver.html  
https://browserbench.org/Speedometer2.0/  


