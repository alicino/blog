---
layout: single
title: "How to Compute the Volume of an Irregular Swimming Pool Using Integrals – Part 2"
date: 2026-04-12
tags:
  - calculus
  - integrals
  - geometry
  - applied-math
categories:
  - mathematics
---

Let's continue the four-series post. This time I'm going to calculate the Volume C of a swimming pool. Let's review the dimensions.

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

Traditional geometric formulas are not sufficient for this region, which motivates the use of calculus.  
See the draw below I did to show the dimensions. It isn't in scale.

- Length (x-direction): L = 7.70m
- Constant width for Region C (top view rectangle) W = 3.20m
- Depth varies along x:
h(0) = 1.50m
h(L) = 1.30m

In our example h is our y-axis.
So, L = 7.70 we have:

$h(7.70) = 1.30m$ \
or \
$y(7.70) = 1.30m$

We can represent the inclination of the pool using a char in x and y axes, such as:

{% include figure image_path="assets/images/2026-part-2-swimming-pool-chart.png" alt="Chart-part2" class="align-center" width="200" %}

**Observation:**
I flipped the pool shape in the chart (x-axis) to show a straight line in positive numbers when you see the pool depth. But it is only for didactic reasons.

## 1. Start from the geometry: two know points

As you can see, we have two exact points of the line:

$$
\begin{aligned}
P_1 &= (x_1, y_1) = (0, 1.50) \\
P_2 &= (x_2, y_2) = (7.70, 1.30)
\end{aligned}
$$

Where:
- the horizontal coordinate represents the position along the pool length (in meters)
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

Since the pool bottom is a straight slope, the depth varies linearly along the length of the pool. A linear relationship between two variables is described by the equation of a straight line.

### 3.1. The general idea

Any straight line in the plane can be written as:

$y= mx + b$

Where: 
- $m$ is the slope of the line (how fast y changes with x)
- $b$ is the value of $y$ when $x=0$ (the intercept)

In our case:

- $x$ represents the horizontal position along the pool
- $h(x)$ represents the depth at the position

So we are looking for a function of the form:

$h(x)= mx + b$

### 3.2. Using known data instead of guessing $b$

Rather than guessing the value of $b$, we use a form of the line equation that is built directly from a known point and the slope. This is called the **point-slope form**.
The general point-slope equation is:

$$
y - y_1 = m (x - x_1)
$$

It simply say: "the change in $y$  from a known point equals the slope times the change in $x$"


### 3.3. Applying the formula to the pool geometry

From the pool (geometry), we know that:

$$
P_1 = (x_1, y_1) = (0, 1.50)
$$

This means that at the beginning of the pool $(x=0)$, the depth is 1.50m.
Using the point-slope form:

$$
h(x) - 1.50 = m(x - 0)
$$

Since $x-0 = x$, this simplifies naturally to:

$$
h(x) - 1.50 = mx
$$

### 3.4. Substituting the slope

From the previous section, the slope was found to be:

$$
m = - \frac{0.20}{7.70}
$$

Substituting this value:

$$
h(x) - 1.50 = - \frac{0.20}{7.70}x
$$

Finally, solving for $h(x)$:

<div style="border: 1px solid #000000ff; padding: 5x; border-radius: 8px;">
$$
h(x) = 1.50 - \frac{0.20}{7.70}x
$$
</div>

### 3.5. Why is this formula useful?

Writing the depth as a function $h(x)$ allows to:
- compute the depth at any position along the pool
- multiply it by the width to obtain an infinitesimal volume element
- integrate along the length to compute the total volume

## 4. Defining the Infinitesimal Volume Element

Now that we have an explicit expression for the depth function $h(x)$, we can begin constructing the volume calculation.

### 4.1. Slicing the pool along its length

We divide the pool into very thin vertical slices along the x-axis. Each slice has:
- a small thickness $dx$
- a constant width $w$ (for region C)
- a depth that depends on the position $x$, given by $h(x)$

Visually, each slice looks like a thin retangular prism.

### 4.2. Volume of a single slice

For a slice located at position $x$:
- width: $W = 3.20m$
- depth: $h(x)$
- thickness: $dx$

The volume of this infinitesimal slice is:

$$
dV = W \cdot h(x)\, dx
$$

This expression represents a differential volume element, capturing the volume of an infinitesimally thin slice of the pool.

### 4.3. From infinitesimal volume of to Total Volume

To obtain the total volume of Region C, we must sum the volume of all slices along the pool length. Mathematically, this sum becomes an integral:

$$
V_c = \int_0^{L} W.h(x) dx
$$

where:
- the lower limit $0$ corresponds to the deep end
- the upper limit $L = 7.70$ corresponds to the shallow end
- $W$ is a constant ($W = 3.20m$)
- In section 3.4 we defined $h(x)$ as:
$$
h(x) = 1.50 - \frac{0.20}{7.70}x
$$

Substituting into the integral:

$$
V_c = 3.20 \int_0^{7.70} (1.50 - \frac{0.20}{7.70}x) dx
$$

At this point, the geometry problem has been fully translated into a mathematical one.

### 4.4. Evaluating the Integral (Step-by-step)

We will now solve this integral carefully.

**Step 1** - Split the integral into two simpler terms. 
We use linearity of the integral:

$$
\int (a - bx)\, dx = \int a\, dx - \int bx\, dx
$$

So:

$$
V_c = 3.20 \left[ \int_0^{7.70} 1.50\,dx - \int_0^{7.70} \frac{0.20}{7.70}x\,dx \right]
$$

**Step 2** - Compute each integral separately\
**(a)** First term:

$$
\int_0^{7.70} 1.50\,dx = 1.50x \Big|_0^{7.70} = 1.50(7.70) - 1.50(0) = 11.55
$$

**(b)** Second term:\
First, take the constant out.

$$
\int_0^{7.70} \frac{0.20}{7.70}x\,dx = \frac{0.20}{7.70} \int_0^{7.70} x\,dx
$$

Now integrate $x$:

$$
\int x\,dx = \frac{x^2}{2} + C
$$

Evaluating the definite integral:

$$
\int_0^{7.70} x\,dx = \left[ \frac{x^2}{2} \right]_0^{7.70}
$$

**Observation:** The constant $C$ cancels automatically

So: 

$$
\frac{0.20}{7.70} \left( \frac{x^2}{2} \right)\Big|_0^{7.70}
= \frac{0.20}{7.70} \cdot \frac{(7.70)^2}{2}
$$

Simplification:

$$
\frac{(7.70)^2}{7.70} = 7.70
$$

So:

$$
\frac{0.20}{7.70} \cdot \frac{(7.70)^2}{2}
= \frac{0.20 \cdot 7.70}{2}
= \frac{1.54}{2}
= 0.77
$$

**Step 3** - Combine results inside the brackets. Now we subtract the two results:

$$
\int_0^{7.70} \left(1.50 - \frac{0.20}{7.70}x \right)\,dx
= 11.55 - 0.77
= 10.78
$$

So:

$$
V_c = 3.20 \times 10.78
$$

Final Result:

<div style="border: 1px solid rgb(255, 0, 0); padding: 5px; border-radius: 8px;">
$$
V_c = 34.496 \ \text{m}^3
$$
</div>

---

## Quick Sanity Check

Because $h(x)$ is linear, the average depth equals the mean of the endpoints:

$$
h_{\text{avg}} = \frac{1.50 + 1.30}{2} = 1.40
$$

The top-view area of the Region C is:

$A_c = 7.70 \times 3.20 = 24.64\ \text{m}^2$

So:

$$V_c = A_c \times h_{\text{avg}} = 24.64 \times 1.40$$

$$
\boxed{V_c = 34.496 \ \text{m}^3}
$$

### End of Part 2 🎉
