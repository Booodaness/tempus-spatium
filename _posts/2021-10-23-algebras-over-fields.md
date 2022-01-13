---
title: "Algebra Done Tensorially: Part 2 (Algebras Over Fields)"
description: "A look at 'algebras' and their structure"
categories: [abstract algebra, representation theory, tensor algebra]
tags: [tensors]
---

Welcome to Part 2 of '_Algebra done Tensorially_'. If you haven't already done so, make sure to check out [Part 1 (Bilinear Products)]({% post_url 2021-10-18-bilinear-products %}) before reading this post :) I will start right from where we stopped in Part 1.

## Recap: bilinear products as linear maps

We had learnt in the previous post that passing only one argument to a bilinear product makes it a linear map on the vector space characterized by the remaining argument. In the component form, given a tensor $$\Phi^I_{\phantom{I} J}$$ and bilinear product $$B^{J \phantom{I} L \phantom{K} M}_{\phantom{J} I \phantom{L} K \phantom{M} N}$$,

<a name="bilinear_product_linear_map"></a>

$$\Phi^I_{\phantom{I} J} \: B^{J \phantom{I} L \phantom{K} M}_{\phantom{J} I \phantom{L} K \phantom{M} N} = \Lambda^M_{\phantom{M} K} \Lambda^{L}_{\phantom{L} N}$$

Recall that we are using the [tuple index notation](https://booodaness.github.io/tempus_spatium/2021/10/bilinear-products.html#components), where capital letters for indices represent tuples, e.g. $$I \equiv i_1 i_2 \dots i_p$$. The only exception to this rule lies in the notation for the Jacobian, where $$\Lambda^{I^\prime}_{\phantom{I^\prime} I} = \Lambda^{i_1^\prime}_{\phantom{i_1^\prime} i_1} \Lambda^{i_2^\prime}_{\phantom{i_2^\prime} i_2} \dots \Lambda^{i_p^\prime}_{\phantom{i_p^\prime} i_p}$$.

<a name="bilinear_product_linear_map_mixed_indices"></a>

You will have noticed that generally, a Jacobian is of the form $$\Lambda^{i^\prime}_{\phantom{i^\prime} i}$$, since it maps the unprimed vector space to the primed vector space. In contrast, there are no primed indices in the [component form for a linear map constructed from a bilinear product](#tuple_notation). Let us fix this little ambiguity,

$$\Phi^K_{\phantom{K} L} \: B^{L \phantom{K} J \phantom{I} I^\prime}_{\phantom{L} K \phantom{J} I \phantom{I^\prime} J^\prime} = \Lambda^{I^\prime}_{\phantom{I^\prime} I} \Lambda^{J}_{\phantom{L} J^\prime}$$

<a name="primed_to_unprimed"></a>

However, the components of the bilinear product now have both primed and unprimed indices. This can be resolved by transforming the primed indices to unprimed ones,

$$
\begin{align}
\Phi^K_{\phantom{K} L} \: B^{L \phantom{K} J \phantom{I} M}_{\phantom{L} K \phantom{J} I \phantom{M} N} & = \Lambda^{M}_{\phantom{M} I^\prime} \Lambda^{J^\prime}_{\phantom{J^\prime} N} \Lambda^{I^\prime}_{\phantom{I^\prime} I} \Lambda^{J}_{\phantom{L} J^\prime} \\
\Phi^K_{\phantom{K} L} \: B^{L \phantom{K} J \phantom{I} M}_{\phantom{L} K \phantom{J} I \phantom{M} N} & = \Delta^M_{\phantom{M} I} \Delta^J_{\phantom{J} N}
\end{align}
$$

This is very similar to the original equation, but with the Kronecker delta in place of the Jacobian, which isn't surprising as a map from unprimed to unprimed indices is strictly speaking, an identity map.

However, the 'strictly unprimed' form is not as interesting as the one with both unprimed and primed indices, as we shall see. To take that route, we must modify our notion of a bilinear product. Since it will have both unprimed and primed indices, the components of a bilinear product no longer make sense in a _single_ coordinate system. Just like the Jacobian, its components depend on _both_ the sets of coordinates we are mapping between.

## Gamma tensor

### Definition

In the [component representation of bilinear products as linear maps](#bilinear_product_linear_map_mixed_indices), we have a product of Jacobian components on the right hand side:

$$\Lambda^{I^\prime}_{\phantom{I^\prime} I} \Lambda^{J}_{\phantom{L} J^\prime} = \Lambda^{i_1^\prime}_{\phantom{i_1^\prime} i_1} \dots \Lambda^{i_p^\prime}_{\phantom{i_p^\prime} i_p} \Lambda^{j_1}_{\phantom{j_1} j_1^\prime} \dots \Lambda^{j_q}_{\phantom{j_q} j_q^\prime}$$

Does the above expression transform like a tensor? To answer this question, let us first define a tensor $$\pmb{\Gamma}$$ so that its components are the same as the above product of Jacobian components,

$$\pmb{\Gamma} = \Lambda^{I^\prime}_{\phantom{I^\prime} I} \Lambda^{J}_{\phantom{L} J^\prime} \: \pmb{E}_{I^\prime J} \pmb{\Theta}^{I J^\prime}$$

The components of the above tensor are as expected,

$$\Gamma^{I^\prime \phantom{I} J}_{\phantom{I^\prime} I \phantom{J} J^\prime} = \Lambda^{I^\prime}_{\phantom{I^\prime} I} \Lambda^{J}_{\phantom{L} J^\prime} $$

As usual, capital letters for indices represent their tuples, except for the Jacobian. To verify that the above components transform like a tensor, instead of doing so manually, we can transform all primed indices to unprimed ones and verify that $$\pmb{\Gamma}$$ is a tensor. From the [previous such endeavour](#primed_to_unprimed), we know that doing so means replacing Jacobians by Kronecker deltas,

$$\Gamma^{I \phantom{J} K}_{\phantom{I} J \phantom{K} L} = \Delta^{I}_{\phantom{I} J} \Delta^{K}_{\phantom{K} L}$$

Since an identity map is always invariant, $$\pmb{\Gamma}$$ is a tensor.

### Basis

We have seen that the basis for a gamma tensor is of the form $$\pmb{E}_{I^\prime J} \pmb{\Theta}^{I J^\prime}$$. However, we can use bilinear products to construct a different basis for gamma tensors:

$$
\begin{align}
\pmb{\Gamma} & = \Lambda^{I^\prime}_{\phantom{I^\prime} I} \Lambda^{J}_{\phantom{L} J^\prime} \: \pmb{E}_{I^\prime J} \pmb{\Theta}^{I J^\prime} \\
 & = \Phi^K_{\phantom{K} L} \: B^{L \phantom{K} J \phantom{I} I^\prime}_{\phantom{L} K \phantom{J} I \phantom{I^\prime} J^\prime} \: \pmb{E}_{I^\prime J} \pmb{\Theta}^{I J^\prime} \\
 & = \Phi^K_{\phantom{K} L} \left\langle \pmb{\mathcal{B}} \left( \pmb{E}_K \pmb{\Theta}^L, \pmb{E}_I \pmb{\Theta}^J \right), \pmb{E}_{I^\prime} \pmb{\Theta}^{J^\prime} \right\rangle \pmb{E}_{I^\prime J} \pmb{\Theta}^{I J^\prime} \\
 & = \Phi^K_{\phantom{K} L} \: \pmb{\mathcal{B}} \left( \pmb{E}_K \pmb{\Theta}^L, \pmb{E}_I \pmb{\Theta}^J \right) \pmb{E}_J \pmb{\Theta}^I
\end{align}
$$

Therefore, in the basis $$\pmb{\mathcal{B}} \left( \pmb{E}_K \pmb{\Theta}^L, \pmb{E}_I \pmb{\Theta}^J \right) \pmb{E}_J \pmb{\Theta}^I$$, the coordinates of $$\pmb{\Gamma}$$ are $$\Phi^{K}_{\phantom{K} L}$$.

The basis above is not a covariant one. Therefore, it is instead a set of basis functions for the map $$\pmb{\Gamma}$$.

### As a vector space

Since $$\pmb{\Gamma}$$ has a basis $$\pmb{\mathcal{B}} \left( \pmb{E}_K \pmb{\Theta}^L, \pmb{E}_I \pmb{\Theta}^J \right) \pmb{E}_J \pmb{\Theta}^I$$, a corresponding vector space can be constructed from the span of the basis. Elements belonging to the vector space, by definition, can be added with each other and multipled by scalars:

$$
\begin{align}
\sum_n \pmb{\Gamma}_{\left( n \right)} & = \sum_n \Phi^{\phantom{\left( n \right)} K}_{\left( n \right) \phantom{K} L} \: \pmb{\mathcal{B}} \left( \pmb{E}_K \pmb{\Theta}^L, \pmb{E}_I \pmb{\Theta}^J \right) \pmb{E}_J \pmb{\Theta}^I \\
\lambda \cdot \pmb{\Gamma} & = \left( \lambda \: \Phi^K_{\phantom{K} L} \right) \pmb{\mathcal{B}} \left( \pmb{E}_K \pmb{\Theta}^L, \pmb{E}_I \pmb{\Theta}^J \right) \pmb{E}_J \pmb{\Theta}^I
\end{align}
$$

The subscript $$n$$ has been enclosed in brackets to remind us that it labels different gamma tensors, not any index.

## Algebra

### Definition

An _algebra_ $$\left( U, \mathcal{B} \right)$$ is a vector space $$U$$ equipped with a bilinear product $$\mathcal{B}:U \mapsto U$$.

For our interests, $$U$$ is the vector space corresponding to $$\Gamma$$ and $$\mathcal{B}$$ is a bilinear product on the tensors associated with $$\Gamma$$.

### Characterization

An algebra is characterized by any two of the following three objects:

1. A vector space parameterized in a basis $$\Phi^K_{\phantom{K} L}$$ by components $$\pmb{E}_K \pmb{\Theta}^L$$

2. A bilinear operator $$\pmb{\mathcal{B}}$$ whose action on basis vectors is defined by its components,

$$\pmb{\mathcal{B}} \left( \pmb{E}_K \pmb{\Theta}^L, \pmb{E}_I \pmb{\Theta}^J \right) = B^{L \phantom{K} J \phantom{I} I^\prime}_{\phantom{L} K \phantom{J} I \phantom{I^\prime} J^\prime} \: \pmb{E}_{I^\prime} \pmb{\Theta}^{J^\prime}$$

3. The Jacobian $$\pmb{\Lambda}$$ for the unprimed and primed coordinates, or equivalently, the corresponding Gamma tensor $$\pmb{\Gamma}$$

The reason we need only _two_ of the above objects is that the three objects have a multilinear relationship, allowing any unknown object to be determined from the remaining two when they are known:

<a name="multilinear_relationship"></a>

$$\Phi^K_{\phantom{K} L} B^{L \phantom{K} J \phantom{I} I^\prime}_{\phantom{L} K \phantom{J} I \phantom{I^\prime} J^\prime} = \Lambda^{I^\prime}_{\phantom{I^\prime} I} \Lambda^{J}_{\phantom{L} J^\prime} = \Gamma^{I^\prime \phantom{I} J}_{\phantom{I^\prime} I \phantom{J} J^\prime}$$

<a name="implicit_relationships"></a>

### Implicit relationships

If two of the three objects that can be used to characterize an algebra have a multilinear relationship of their own (an '_implicit relationship_'), then one necessarily needs only _one_ object to characterize the algebra, as the other two can be obtained from the [usual multilinear relationship](#multilinear_relationship) and the implicit relationship.

<a name="degrees_of_freedom"></a>

## Degrees of freedom

### Definition

The _degrees of freedom_ of a tensor are its independent components. The number of degrees of freedom of a tensor remains the same no matter the basis.

For example, consider (without loss of generality) a rank-2 tensor whose components in some basis are $$T^i_{\phantom{i} j} = T^i_{\phantom{i} f \left( i \right)}$$. Since the second index, $$j = f \left( i \right)$$ is related to $$i$$, there is only one independent index. If we transform the coordinates to a primed frame, this fact isn't changed,

$$
\begin{align}
T^{i^\prime}_{\phantom{i^\prime} j^\prime} & = \Lambda^{i^\prime}_{\phantom{i^\prime} i} T^i_{\phantom{i} j} \Lambda^{j}_{\phantom{j} j^\prime} \\
 & = \Lambda^{i^\prime}_{\phantom{i^\prime} i} T^i_{\phantom{i} f \left( i \right)} \Lambda^{f \left( i \right)}_{\phantom{f \left( i \right)} f \left( i^\prime \right)}
\end{align}
$$

### Representation theory

_Representation theory_ is a discipline in which algebra is studied by representing elements of algebraic structures as multilinear relationships.

We will represent $$\pmb{\Gamma}$$ as a tensor in an implicit basis. Our little 'magic trick' will be to identify the degrees of freedom in $$\Gamma^{I^\prime \phantom{I} J}_{\phantom{I^\prime} I \phantom{J} J^\prime}$$ with a vector space parameterized by $$\Phi^K_{\phantom{K} L}$$. All remaining components of $$\pmb{\Gamma}$$ will be some function of some component(s) of $$\pmb{\Phi}$$.

Thus, we are establishing an [implicit relationship](#implicit_relationships) between $$\pmb{\Gamma}$$ and $$\pmb{\Phi}$$, thereby reducing the characterization of algebra to only one object of the three we have seen.

### The Jacobian

Geometry is an important aspect of algebra. We will formally define it in the next post, but until then, it is useful to know that the geometry of an algebra is determined by its Jacobian. In representation theory, the degrees of freedom of the Jacobian carry all the information necessary to determine the geometry of an algebra.

It had been said in the previous subsection that we are considering the degrees of freedom of a gamma tensor. Since it is built using the Jacobian in a reversible manner, the number of degrees of freedom remain the same in both. But the Jacobian, a rank-2 tensor, can have no more than $$D^2$$ components $$\Lambda^{i^\prime}_{\phantom{i^\prime} i}$$, and hence those many degrees of freedom, given a $$D$$ dimensional vector space.

This means that to represent $$\pmb{\Lambda}$$ by $$\pmb{\Phi}$$ in an implicit basis, $$\pmb{\Phi}$$ need not have a higher rank than that of the Jacobian, 2, as higher-rank terms become redundant! Furthermore, even rank-2 representations are redundant, as we already have the components of the Jacobian in its rank-2 tensor.

This severe restriction implies that it is useful to only study algebras whose underlying Jacobian in $$D$$ dimensions has $$D$$ degrees of freedom. In other words, $$\Lambda^{i^\prime}_{\phantom{i^\prime} i}$$ must be characterized entirely by some vector $$\phi^k$$ (or its dual).

## Vector algebra

### Structure

As per the restriction of algebra to vectors (or covectors) to reduce redundancy, we will require one of the following elements to characterize a _vector algebra_:

1. A Jacobian $$\Lambda^{i^\prime}_{\phantom{i^\prime} i}$$. Since we are dealing with a rank-1 algebra i.e. vector algebra, the Jacobian _is_ the gamma tensor for the algebra.

2. A vector $$\phi^k$$ which packs the degrees of freedom of $$\Lambda^{i^\prime}_{\phantom{i^\prime} i}$$.

3. A bilinear product $$\pmb{\mathcal{B}}$$ which operates on basis vectors as, $$\pmb{\mathcal{B}} \left( \pmb{e}_k, \pmb{e}_i \right) = B^{i^\prime}_{\phantom{i^\prime} ki} \pmb{e}_{i^\prime}$$.

As usual, the multilinear relationship between the above elements is,

$$\phi^k B^{i^\prime}_{\phantom{i^\prime} ki} = \Lambda^{i^\prime}_{\phantom{i^\prime} i}$$

And the action of the linear map above on a vector $$x^i$$ is,

$$\phi^k B^{i^\prime}_{\phantom{i^\prime} ki} x^i = \Lambda^{i^\prime}_{\phantom{i^\prime} i} x^i = x^{i^\prime}$$

### Characterization

Now that we know one of the three usual objects will be required to characterize a vector algebra, which one do we choose?

An algebra is described by its underlying Jacobian. Therefore, the form of the Jacobian is a sensible parameter for an algebraic structure. Due to the whole [degrees of freedom jargon](#degrees_of_freedom), the form of the vector space representing the Jacobian comes for free. This means that to complete our description of an algebra, we must find the bilinear product from the Jacobian.

## Wrapping up

This completes the basic concepts we will require to work with algebras tensorially. The exact procedure to do so will be described in the next post, [Algebra Done Tensorially: Part 3a (Clifford Algebras)]().