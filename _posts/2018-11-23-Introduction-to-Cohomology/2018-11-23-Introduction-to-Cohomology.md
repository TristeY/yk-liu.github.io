---
title: Introduction to de Rham Cohomology
edit: 2018-11-23
categories: Topology
tags: de-Rham-Cohomology Topology Stokes'-Theorem
keywords: cohomology exact
description: My study notes on cohomology, as a preparation for K-theory.
status: Writing
---

$$
\newcommand{\spl}[1]{\langle{#1}\rangle}
\newcommand{\inner}[2]{\left\langle{#1,#2}\right\rangle}
\newcommand{\form}{\tilde}
\newcommand{\abs}[1]{\left\vert{#1}\right\vert}
%\renewcommand{\vec}{\mathbf}
\newcommand{\bra}[1]{\left\langle{#1}\right\vert }
\newcommand{\ket}[1]{\left| {#1}\right\rangle}
\newcommand{\braket}[2]{\left\langle {#1} \; \middle|\;{#2} \right\rangle }
\newcommand{\mani}{\mathcal}
\newcommand{\field}{\mathscr}
\newcommand{\Tspace}[1]{T\! {#1}}
\newcommand{\d}{\mathrm{d}}
\newcommand{\R}{\mathbb{R}}
\newcommand{\D}[2]{\frac{\d {#1}}{\d {#2} }}
\newcommand{\Partial}[2]{\frac{\partial {#1} }{\partial {#2} }}
\newcommand{\op}{\hat}
\newcommand{\uvec}{\hat}
\newcommand{\dfdas}{: =}
\newcommand{\Eqn}[1]{\text{(Eqn. }\ref{#1}\text{)}}
\newcommand{\dual}{\tilde}
\newcommand{\vard}{\mathfrak{d}}
\newcommand{\vare}{\mathfrak{e}}
\newcommand{\e}{\mathrm{e}}
\newcommand{\i}{\mathrm{i}}
\newcommand{\blue}{\color{blue}}
\newcommand{\red}{\color{red}}
\newcommand{\norm}[1]{\left\|{#1}\right\|}
\newcommand{\set}[1]{\left\lbrace{#1}\right\rbrace}
\newcommand{\sgn}{\operatorname{sgn}}
\newcommand{\Z}{\mathbb{Z}}
\newcommand{\nint}{\int\!\!\!\cdot\!\!\cdot\!\!\cdot\!\!\!\int}
\notag
$$

This post follows [Nakahara](http://stringworld.ru/files/Nakahara_M._Geometry_topology_and_physics_2nd_ed..pdf).

# The Name

"de Rham Cohomology" is translated in Chinese as "德拉姆上同调", where "同调" stands for "same tune". I suppose this is related to the musical isomorphism between one forms and vectors. As for the meaning of "co-", here are my thoughts. 

| English                  | Chinese           | Meaning                  |
| ------------------------ | ----------------- | ------------------------ |
| **co**sine/**co**tangent | **余**弦/**余**切 | adding up to $\pi /2$    |
| **co**set                | **陪**集          | dual in the same space   |
| **co**homology           | **上**同调        | dual in different spaces |

# Body and Boundary

The cohomology is a relationship defined on forms. We will find how to define chains, boundaries and cycles on differential forms. 

## The celebrated $\operatorname{d}$

Remember the homology relations? It's very similar to the diagram we found in differential forms and tensors.

$$
\begin{array}{ccccccc}
&\text{0-forms} & \xrightarrow{\d}{} &\text{$1$-forms} & \xrightarrow{\d}{} & \text{$2$-forms} & \xrightarrow{\d}{}& \text{$3$-forms}\\
&\downarrow &&\downarrow&&\downarrow&&\downarrow   \\
&\text{ {functions} } &\xrightarrow{\nabla}{} &\text{ {vector fields} } &\xrightarrow{\nabla\times}{} &\text{ {vector fields} } &\xrightarrow{\nabla\cdot}{} &\text{ {functions} }\\
& function & & divergence & & curl & & gradient
\end{array}
$$

Hence we have the following diagram.

<img src="https://raw.githubusercontent.com/yk-liu/yk-liu.github.io/master/_posts/2018-11-23-Introduction-to-Cohomology/assets/FormsComplex.png" width="80%">

The differences exists but the symbol $\d$ still stands for "take the edge". 

|                                          | Homology                            | Cohomology                            | Notes                                                        |
| ---------------------------------------- | ----------------------------------- | ------------------------------------- | ------------------------------------------------------------ |
| boundary operator                        | $\partial $ means "take boundaries" | $\d$ stands for "exterior derivative" |                                                              |
|                                          | chains                              | differential forms                    |                                                              |
| $\d \omega = 0$                          | cycle                               | closed form                           | "Closed" forms has no boundary, hence the name.              |
| $\omega=\d\eta$                          | boundary                            | exact form                            | Exact forms are "exactly" the exterior derivative of a higher form. |
| $\substack{\d^2=0\newline \partial^2=0}$ | boundaries have no boundary         | boundaries have no boundary           |                                                              |

From differential forms, we can tell if the space has a whole like we did in homology groups. Still, we need to define the reverse map of $\d$, namely integration, in order to find the $\operatorname{img} 0$.

## Definition of Integration

The integration of a differential form over what? A simplex!

Recall that a simplex of dimension $r$ is defined in $\R^r$ as 

$$
\sigma _ r=\set{x\in\R^N \mid x=\sum _ {i=0}^n c _ ip _ i, c _ i\ge0, \sum _ {i=0}^n c _ i=1},
$$

and an $r$-from is now written as

$$
\omega=w(\vec x)\, \d x^1 \wedge \d x^2\wedge\cdots\wedge\d x^r
$$

Integration of a form over a simplex is defined as

$$
\begin{align}
\int_{\sigma_r}\omega &=\int _{\sigma_r} w(\vec x)\d x^1 \wedge \d x^2\wedge\cdots\wedge\d x^r\\
&\dfdas \nint _{\sigma_r}w(\vec x)\d x^1 \d x^2 \cdots\d x^r
\end{align}
$$

# Definition of the de Rham Cohomology Group

Now with necessary mathematical machineries defined, finally we will give a definition of cohomology group.

The set of closed $r$-forms on manifold $M$ are called the **co-cycle group**, denoted $Z^r(M)$, not to be confused with cycle group $Z _ r(M)$. The set of exact $r$-forms on manifold $M$ are called the **co-boundary group**, denoted $B^r(M)$.

The $r​$th **de Rham cohomology group** is defined as 

$$
H^r(M)\dfdas Z^r(M)/B^r(M)
$$


# Stokes' Theorem and Cohomology

## Stokes' Theorem

The cohomology group is the dual vector space of homology space. This dual relationship is best represented by the Stokes' theorem as

$$
\int _{\sigma_r} \d \omega = \int_{\partial\sigma _r} \omega
$$

If we take $\omega = a \d x + b \d y + c \d z$, and $w=(a,b,c)$, we have

$$
\int_S \vec\nabla\times w \cdot \d \vec S =\oint_C\vec w\cdot\d \vec l
$$

If we take $\psi=\frac{1}{2}\psi _ {\mu\nu}\d x^\mu \wedge\d x^\nu$, and $F^\mu=\varepsilon^{\lambda \mu\nu } \psi_ {\mu\nu}$, we have

$$
\int_V \vec\nabla\cdot \vec F   \d V =\oint_S\vec F\cdot\d \vec S
$$

## Duality of Homology and Cohomology

As in the beginning of this post, "co-" means dual, and cohomology group is a dual space of homology group.

## Exactness

Now the exactness is well defined. 

# Make Homology out of Cohomology
