---
layout: single
title: "How to Compute the Volume of an Irregular Swimming Pool Using Integrals – Part 2"
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

{% include figure image_path="assets/images/2026-swimming-pool-dimensions-color.png" alt="Swimming Pool Dimensions" class="align-center" width="400" %}

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

{% include figure image_path="assets/images/2026-part-2-swimming-pool-chart.png" alt="Chart-part2" class="align-center" width="200" %}

## 1. Start from the geometry: two know points

As you can see, we have two exact points of the line:

$$
\begin{aligned}
P_1 &= (x_1, y_1) = (0, 1.50) \\
P_2 &= (x_2, y_2) = (7.70, 1.30)
\end{aligned}
$$

Where:
- the horizontal coordinate represents the position along the pool lenght (in meters)
- the vertical coordinate represents the water depth (in meters)

## 2. Compute the slope of the line

The slope $m$ of a straight line passing through two points is:

$$
m = \frac{y_2 - y_1}{x_2 - x_1}
$$

Substituting the values, we have:

$$
\boxed{m = \frac{1.30 - 1.50}{7.70 - 0} = \frac{-0.20}{7.70}}
$$

Obs.: the negative sign correctly indicates that the depth decreases as $x$ increases.

## 3. Write the equation of the line

Using the point-slope form:

$$
\begin{aligned}
h(x) - h(0) = m(x - 0) \\
\end{aligned}
$$

We already know:

$h(0) = 1.50$ \\
and \\
$m = - \frac{0.20}{7.70}$

which gives:

<div style="border: 1px solid #000000ff; padding: 5x; border-radius: 8px;">
$$
h(x) = 1.50 - \frac{0.20}{7.70}x
$$
</div>

This is the depth function we will use in all subsequent calculations.


---
************ D R A F T ************







# Example: Splitting the Pool into A, B, C, D

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




# End of Part 1 🎉
