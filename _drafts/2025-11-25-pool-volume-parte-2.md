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

Let's continue the four-serie post. This time I'm going to calculate the Volume C of a swimming pool. Let's review the dimensions.

> The goal is not only to show *how* to calculate it, but also to help you understand *why* integrals are the right tool for the job.

# 1. The Dimensions

{% include figure image_path="assets/images/2025-11-25-swimming-pool-dimensions-color.png" alt="Swimming Pool Dimensions" class="align-center" width="400" %}

- **Length:** 7.70 m + 0.10 m curvature on each side  
- **Width:** 3.20 m + 0.10 m curvature on each side  
- **Depths:** 1.50 m (deep end), 1.30 m (shallow end)

# 2. Problem Statement (Region C)

Region C includes:
1. A central rectangular region  
2. Two lateral curved borders  

I regret to inform you, but traditional formulas will not help us here. We need calculus.  
See the draw below I did to show the dimensions. It isn't in scale.

- Length (x-direction): L = 7.70m
- Constant width for Region C (top view rectangle) W = 3.20m
- Depth varies along x:
h(0) = 1.50m
h(L) = 1.30m

In our example h is our y-axy.
So, L = 7.70 we have:
$h(7.70) = 1.30m$
$y(7.70) = 1.30m$

We can represent the inclination of the pool using a char in x and y axies, such as:









************ D R A F T ************

Depth changes only in x-direction — this is crucial.

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

# 3. Why Integrals?

If the pool were a simple box:

```
V = length × width × depth
```

But here both width and depth vary.

Integrals allow us to sum infinitely small “volume slices.”

# 4. Slicing the Pool

```
   |‾‾‾‾|‾‾‾‾|‾‾‾‾|‾‾‾‾|
   |    |    |    |    |
   |____|____|____|____|
       Δx  Δx  Δx  Δx
```

Each slice:  
```
ΔV ≈ h(x) · w(x) · Δx 
```

As Δx → 0:

```
V = ∫ h(x) w(x) dx
```

# 5. Double Integral (Formal Version)


V = ∬ h(x,y) dA


Since depth depends only on x:

h(x,y) = h(x)


So:

```
V = ∫ h(x) w(x) dx
```

# 6. Splitting the Pool into A, B, C, D

We compute:

$$
V_{\text{total}} =
\underbrace{V_A}_{\text{left cap}} +
\underbrace{2.V_B}_{\text{two lateral curves}} +
\underbrace{V_C}_{\text{central region}} +
\underbrace{V_D}_{\text{right cap}}
$$

Each part gets its own post.

# 7. Coming Next (Part 2)

- Deriving depth function h(x)  
- Computing Region C (simplest)  
- First integral demonstration  

---

# 8. MathJax for Equations

Inline (apenas um $):


$$
h(x) = 1.5 - \frac{0.2x}{7.7}
$$

Outra forma com expoente:

$ h(x) = 1.5 - \frac{0.2x}{(7.7)^2} $

Display (com dois $):


$$
V = \int_0^{7.7} h(x) w(x) dx
$$


Double integral:


$$
V = \iint_A h(x,y)\, dA
$$


# 9. Enabling MathJax in Jekyll

Add this to `_includes/head/custom.html`:

```
<script>
  MathJax = {
    tex: {
      inlineMath: [['$', '$'], ['\(', '\)']],
      displayMath: [['$$', '$$'], ['\[', '\]']]
    }
  };
</script>
<script id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>
```

# End of Part 1 🎉
