---
layout: single
title: "How to Compute the Volume of an Irregular Swimming Pool Using Integrals – Part 3"
tags:
  - calculus
  - integrals
  - geometry
  - applied-math
category:
  - mathematics
---

Title: How to Compute the Volume of an Irregular Swimming Pool Using Integrals – Part 3

It is not typical for this blog (so far) addressing topics outside IT, Cyber, code, or technology. But I'm a curious person and I love Math for some reason: I studied Engineering, I worked with Business Analysis, and I statistics and probability is a good area to review some concepts. I'm not a gambler, but you can use it as well.

**Some background facts and whys**

It is a real case iin my life. When my Dad was planning a pool to our farm house, he bring the dimensions and I did all study to check the total volume. And I got it when I was at College studying Calculus. Now, and several years later, I got this exercise again, and with a new detail: The dimensions are different, I had to consider curves in each edge.

However, why am I doing it again? Because I got it, but ignored (or better, I didn't know the pool had some peculiar dimensions). Each border had a curve with an expressive volume and I just calculated as a trapezoid.<br>
So, let's discuss it and I promise I will explain each step for everyone. Welcome to the Math!

> This is Part 1 of a 4-post series in which I will show, step by step, how to compute the volume of a swimming pool with an irregular shape using integrals.  
> The goal is not only to show *how* to calculate it, but also to help you understand *why* integrals are the right tool for the job.

# 1. Overview of the Problem

We want to compute the exact volume of a swimming pool with the following characteristics:

- **Length:** 7.70 m + 0.10 m curvature on each side  
- **Width:** 3.20 m + 0.10 m curvature on each side  
- **Depths:** 1.50 m (deep end), 1.30 m (shallow end)

The pool includes:
1. A central rectangular region  
2. Two lateral curved borders  
3. Two curved end caps  

I regret to inform you, but traditional formulas will not help us here. We need calculus.  
See the draw below about the dimensions. It isn't in scale.

{% include figure image_path="assets/images/2025-11-25-swimming-pool-dimensions.png" alt="Swimming Pool Dimensions" class="align-center" width="400" %}

Depth changes only in x-direction — this is crucial to understand.

# 2. Intuition Through Diagrams

To be more didactical, we are splitting the Pool into A, B, C, D areas.

{% include figure image_path="assets/images/2025-11-25-swimming-pool-dimensions-color.png" alt="Swimming Pool Dimensions" class="align-center" width="400" %}

We compute:

$$
V_{\text{total}} =
\underbrace{V_A}_{\text{left cap}} +
\underbrace{2.V_B}_{\text{two lateral curves}} +
\underbrace{V_C}_{\text{central region}} +
\underbrace{V_D}_{\text{right cap}}
$$

Don't forget. Each area gets its own post. Here we are calculating the C area. As the C area is the easiest, it appears to be a trapezoid with little complexity.

Now you are aware about the dimensions and the problem, we can deep dive in the next post starting the formulas andm ore considerations.

### Coming Next (Part 2)

- Deriving depth function h(x)  
- Computing Region C (simplest)  
- First integral demonstration  

See you on the next post, Part 2!
