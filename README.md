# Physics-Informed Neural Network for a 1D Elastic Rod

A simple Physics-Informed Neural Network (PINN) implementation for solving the displacement of a one-dimensional elastic rod under a distributed axial load.

This project is based on the rod example from:

**Katsikis, D., Muradova, A. D., & Stavroulakis, G. E. (2022).  
A Gentle Introduction to Physics-Informed Neural Networks, with Applications in Static Rod and Beam Problems.**

## Problem

We consider a rod of length

$$L = 1$$

with distributed axial loading

$$q(x)=cx$$

The governing differential equation is

$$AE\frac{d^2u}{dx^2}=-cx$$

where:

- \(u(x)\): displacement
- \(A\): cross-sectional area
- \(E\): Young's modulus
- \(c\): distributed load constant

The boundary conditions are

$$u(0)=0$$

and

$$\frac{du}{dx}(1)=0$$

## PINN Idea

The neural network approximates the displacement:

$$x \rightarrow NN \rightarrow \hat{u}(x)$$

Automatic differentiation is used to calculate

$$\frac{d\hat{u}}{dx}$$

and

$$\frac{d^2\hat{u}}{dx^2}$$

The physics residual is

$$r(x)=AE\frac{d^2\hat{u}}{dx^2}+cx$$

The total loss contains:


$$L =
L_{\text{physics}}
+
L_{\text{left}}
+
L_{\text{right}}
$$

## Exact Solution

For \(L=A=E=c=1\),


$$u(x)=\frac{3x-x^3}{6}$$

The trained PINN solution is compared with this analytical solution.

## Project Structure

```text
PINN_rod_stretch/
├── notebook.ipynb
├── requirements.txt
├── README.md
└── .gitignore
```