---
layout: single
title: "How to Compute the Volume of an Irregular Swimming Pool Using Integrals – Part 1"
tags:
  - calculus
  - integrals
  - geometry
  - applied-math
category:
  - mathematics
---

It’s not typical for this blog (so far) to address topics outside IT, cybersecurity, code, or technology. However, I’m a naturally curious person, and for some reason I’ve always enjoyed mathematics. I studied engineering, worked with business analysis, and statistics and probability have always been areas I like to revisit. I’m not a gambler—but those topics certainly show up there too.

**Some background and motivation**

This post is based on a real situation from my own life. When my father was planning a swimming pool for our farmhouse, he brought me the dimensions and I did the full study to estimate the total volume. At the time, I had just learned calculus in college, so the problem felt natural.

Years later, I revisited this same exercise—but with an important new detail: the pool dimensions were not purely straight. Each edge included curved sections, which meant the geometry was more complex than I had originally assumed.

Why do this again? Because my original calculation was incomplete. I treated the pool as a simple trapezoidal prism, ignoring the curved borders. At the time, I either overlooked—or didn’t fully understand—how much volume those curved sections actually added.

So let’s do it properly this time. I’ll walk through the entire process step by step, with as little hand-waving as possible. Welcome to some applied mathematics.

> This is Part 1 of a four-post series in which I show, step by step, how to compute the volume of a swimming pool with an irregular shape using integrals.  
> The goal is not only to show *how* to calculate it, but also to explain *why* integrals are the right tool for the job.

# 1. Overview of the Problem

We want to compute the exact volume of a swimming pool with the following characteristics:

- **Length:** 7.70 m + 0.10 m of curvature on each end  
- **Width:** 3.20 m + 0.10 m of curvature on each side  
- **Depth:** 1.50 m at the deep end and 1.30 m at the shallow end  

The pool can be decomposed into:
1. A central rectangular region  
2. Two lateral curved borders  
3. Two curved end caps  

Unfortunately, traditional volume formulas won’t help us here. We need calculus.

The diagram below shows the pool dimensions. It is **not drawn to scale**.

{% include figure image_path="assets/images/2026-swimming-pool-dimensions.png" alt="Swimming Pool Dimensions" class="align-center" width="400" %}

A key observation is that the depth varies only along the **x-direction**, which will greatly simplify our integrals later.

# 2. Intuition Through Diagrams

For clarity, we split the pool into four regions, labeled **A, B, C, and D**.

{% include figure image_path="assets/images/2026-swimming-pool-dimensions-color.png" alt="Swimming Pool Regions" class="align-center" width="400" %}

The total volume can then be written as:

$$
V_{\text{total}} =
\underbrace{V_A}_{\text{left cap}} +
\underbrace{2V_B}_{\text{two lateral curves}} +
\underbrace{V_C}_{\text{central region}} +
\underbrace{V_D}_{\text{right cap}}
$$

Each region deserves its own discussion and its own set of integrals. In this first post, we focus on **Region C**, the central portion of the pool. It is the simplest part and can be modeled as a trapezoidal prism, making it an ideal starting point.

Now that the geometry and the problem setup are clear, we’re ready to dive into the math in the next post.

### Coming Next (Part 2)

- Deriving the depth function h(x)  
- Computing the volume of Region C  
- Our first integral, step by step  

See you in Part 2!
