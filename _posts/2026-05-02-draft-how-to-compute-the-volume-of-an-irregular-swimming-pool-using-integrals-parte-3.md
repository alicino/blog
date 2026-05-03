---
layout: single
title: "Draft How to Compute the Volume of an Irregular Swimming Pool Using Integrals – Part 3"
tdate: 2026-05-02
tags:
  - calculus
  - integrals
  - geometry
  - applied-math
categories:
  - mathematics
---

Title: How to Compute the Volume of an Irregular Swimming Pool Using Integrals – Part 3

# 1. Scope of this Post
 In this part of the series, we compute the volume of the lateral curved regions, labeled as **Region B**.

 The regions:
- appear on both sides of the pool
- are geometrically identical
- contribute additional volume beyond the central rectangle (Region C)

For this reason, we will compute the volume of one lateral region and then multiply the results by two.

# 2. Geometry of Region B

## 2.1. Top View Interpretation

In the top view, Region B corresponds to the outward curvature of the pool walls.
Key observations:
- The pool width is no longer constant
- At each position $x$, the pool extends outward by a small amount due to the curvature
This extension reaches a maximum of 0.10 m at the center of the length and vanishes at both ends

This behavior strongly suggests a **parabolic profile**. See the picture:

{% include figure image_path="assets/images/2026-swimming-pool-dimensions-region-b.png" alt="Chart-part2" class="align-center" width="200" %}

# 3. Modeling the Lateral Curvature

## 3.1. Choice of coordinate system

We reuse the same coordinate system as before:

- $ x = 0$ at one end of the pool
- $ x = L = 7.70$ at the other end

Let $w_B (x)$ denote the extra width contributed by one lateral bulge at position $x$

## 3.2. Parabolic Model

From the geometry, the bulge disappears at the ends:

$w_B (0) = 0$ 

$w_B (7.70) = 0$ 

$w_B (\frac{7.70}{2}) = 0.10$

## 3.3. Parabolic Model

A simple parabola that satisfies zero values at both ends is:

$$
w_B(x) = K . x (L - x)
$$

Where $K$ is a constant to be determined. At the midpoint, $x = \frac{7.70}{2}$.

Substituting the midpoint condition:

$$
0.10 = K \left( \frac{7.70}{2} \right) \left( 7.70 - \frac{7.70}{2} \right)
$$

Since both factors are equal:

$$
0.10 = K \left( \frac{7.70}{2} \right)^2
$$

Solving for $K$:

$$
K =  \frac {0.10} {\left({\frac{7.70}{2}} \right)^2}
$$

Simplifying the constant:

$$
\frac{0.10}{\left(\frac{L}{2}\right)^2}
=
\frac{0.10}{\frac{L^2}{4}}
=
\frac{0.40}{L^2}
$$

So the lateral width function becomes:

$$
\boxed{w_B(x) = \frac{0.40}{L^2} \cdot x (L - x)}
$$

# 4. Constructing the Volume Element

At position $x$, a thin slice of Region B has:

- depth $h(x)$, already derived in [**Post 2**](https://alicino.me/blog/mathematics/how-to-compute-the-volume-of-an-irregular-swimming-pool-using-integrals-parte-2/#34-substituting-the-slope)

$$
h(x) = 1.50 - \frac{0.20}{7.70}x
$$

- thickness $d(x)$. So the infinitesimal volume is:

$$
dV = h(x) w_B(x) dx
$$

# 5. Integral for One Lateral Region

The volume of one lateral curved region is:

$$
V_B = \int_{0}^{7.70} h(x)\cdot w_B(x)\, dx 
$$

Substituting the expressions:

$$
V_B =
\int_{0}^{7.70}
\left(1.50 - \frac{0.20}{7.70}x\right) .
\left(
\frac{0.10}{\left(\frac{7.70}{2}\right)^2}
\,x(7.70-x)
\right)
\,dx
$$

This integral contains only polynomials and can be expanded and evaluated directly.

# 6. Total Contribution of Region B

Since there are two identical lateral regions, their combined contribution is:

$ V_{B,Total} = 2 . V_B $

# 7. Solving the Integral for the Lateral Regions (Region B)

We are now ready to compute the volume of **one lateral curved** region using the integral derived earlier.

Recall from Item 5 that the volume of a single Region B is given by:

$$
V_B = \int_{0}^{L} h(x)\cdot w_B(x)\, dx 
$$

where:
- the depth function is:

$ h(x) = 1.50 - \frac{0.20}{L}\, x $

$ w_B(x) = \frac{0.40}{L^2} x (L - x) $ 

### 7.1. Expanding the Integrand

To make the integration straightforward, we first expand the product inside the integral.

Start by expanding the parabolic term:

$ x(L - x) = Lx - x^2 $

Substituting this into the expression for $ w_B(x) $:

$$
w_B(x) = \frac{0.40}{L^2} (Lx - x^2) = \frac{0.40}{L}x - \frac{0.40}{L^2}x^2 
$$

Now multiply this by the depth function $h(x)$:

$$
h(x)\cdot w_B(x) = \left(1.50 - \frac{0.20}{L}x\right) . \left( \frac{0.40}{L}x - \frac{0.40}{L^2}x^2 \right)
$$

Expanding term by term:

$$
[1]\quad
1.50\left(\frac{0.40}{L}x\right)
=
\frac{0.60}{L}x
$$

$$
[2]\quad
1.50\left(-\frac{0.40}{L^2}x^2\right)
=
-\frac{0.60}{L^2}x^2
$$

$$
[3]\quad
\left(-\frac{0.20}{L}x\right)
\left(\frac{0.40}{L}x\right)
=
-\frac{0.08}{L^2}x^2
$$

$$
[4]\quad
\left(-\frac{0.20}{L}x\right)
\left(-\frac{0.40}{L^2}x^2\right)
=
+\frac{0.08}{L^3}x^3
$$

Combining like terms, the integrand becomes:

$$
h(x)\cdot w_B(x) =
\frac{0.60}{L}x
- \frac{0.68}{L^2}x^2
+ \frac{0.08}{L^3}x^3
$$

### 7.2. Integrating term by term

We now integrate this polynomial expression from $x=0$ to $x=L$:

Each term is integrated independently:

$$
\int x\,dx = \frac{x^2}{2}, \quad
\int x^2\,dx = \frac{x^3}{3}, \quad
\int x^3\,dx = \frac{x^4}{4}
$$

Applying this:

$$
V_B =
\left[
\underbrace{\frac{0.60}{L}\cdot\frac{x^2}{2}}_{(a)}
-
\underbrace{\frac{0.68}{L^2}\cdot\frac{x^3}{3}}_{(b)}
+
\underbrace{\frac{0.08}{L^3}\cdot\frac{x^4}{4}}_{(c)}
\right]_0^L
$$

## 7.3 Evaluating the limits

Evaluating the expression at $x = L$ (the lower limit evaluates to zero):

- First term:

$$
V_B =
\underbrace{\frac{0.60}{L}\cdot\frac{L^2}{2}}_{(a)}
-
\underbrace{\frac{0.68}{L^2}\cdot\frac{L^3}{3}}_{(b)}
+
\underbrace{\frac{0.08}{L^3}\cdot\frac{L^4}{4}}_{(c)}
$$

Now simplify each term:

$$
(a)\quad \frac{0.60}{L}\cdot\frac{L^2}{2} = 0.30L
$$

$$
(b)\quad -\frac{0.68}{L^2}\cdot\frac{L^3}{3} = -\frac{0.68}{3}L
$$

$$
(c)\quad \frac{0.08}{L^3}\cdot\frac{L^4}{4} = 0.02L
$$

Combining all terms:

$$
V_B = \left( 0.30 - \frac{0.68}{3} + 0.02 \right)L
\approx 0.09333 L
$$

Substituting $L=7.70$

$$
V_B \approx 0.7187 \, m^3
$$

**Obs:** this is the volume of one lateral curved region.

## 7.4. Total contribution of the Lateral Curvature

Since the pool has two identical lateral regions, the total contribution is:

<div style="border: 1px solid rgb(255, 0, 0); padding: 5px; border-radius: 8px;">
$$
{V_{B,total} = 2 \cdot V_B} \simeq 1.437 \, m^3
$$
</div>

## 7.5. Relative Contribution

From [Post 2](https://alicino.me/blog/mathematics/how-to-compute-the-volume-of-an-irregular-swimming-pool-using-integrals-parte-2/), the volume of the central region was:

$$
V_C = 34.496 m^3
$$

Comparing both:

$$
\frac{V_{B,total}}{V_C} \simeq 4.2\%
$$

What this tells us:

- Most of the volume comes from the central footprint and depth
- The lateral curvature adds a **small but meaningful** correction
- Ignoring it would slightly underestimate the total volume
- This reinforces why decomposition into regions is useful
- It allows us to quantify how much each geometric feature contributes


### End of Part 3 🎉

