---
title: "A Closer Look at Quantum Measurements: Part 2.1 (Classical Stern-Gerlach Experiments)"
description: "How the classical physics of Stern-Gerlach experiments is surprisingly rich"
categories: [quantum foundations]
tags: [Stern-Gerlach experiments, measurement problem]
---

## Why this post

In [A Closer Look at Quantum Measurements (Slides)]({% post_url 2023-08-03-closer-look-quantum-measurements %}), we looked at an abstract toy model for a quantum system whose associated quantum and classical probabilities (in the sense of ensemble theory) in experiments were interchangeable in a sense. This allowed one to equate, for a pure state, its seemingly impure post-objective-collapse density matrix and the original pure density matrix, automatically giving rise to the Born rule (as otherwise, the former would indeed be impure, leading to contradiction). This result was generalized for impure states prior to objective collapse, generalizing the form of the Born rule to ensembles.

As discussed at the end of the mentioned post, as satisfying as the emergence of the Born rule from such considerations seems to be, such a machinery fails to operate in cases where classical and quantum probabilities simply differ — in fact, this happens when quantum probabilities exhibit *interference*, which has no classical analogue. [^1]

[^1]: As a remark, objective-collapse theories in general share the problem of not having been observed in any experiment as of May 2024. They also share the problem of not being easily reconcilable with special or general relativity. There are results to the effect that spontaneous collapse of ensembles with sufficient quantum randomness would defy relativity rather marginally, which may or may not be a problem depending on one's position amidst the myriad of debates in quantum foundations. 

One of the most important and famous types of experiments which highlights this above quantum weirdness is that of Stern-Gerlach. So, let us start with a clean slate (what one might call a slate's vacuum state) and see why probability and the Born rule manifest themselves in quantum mechanics (as they have historically from Stern-Gerlach-type experiments, among others, in a series of crushing successes).

To do so, this will be a two-subpart addendum to the series *A Closer Look at Quantum Measurements*. This first part will only look at part of what classical physics has to say with regard to Stern-Gerlach experiments.

## Basic setup

Consider a polarized beam of light with a classical wavefunction $$\pmb{\psi}$$, travelling along the $$z$$-axis, striking an analyzer $$\mathcal{A}_{\theta}$$ that selects waves polarized along the vector:

$$\widehat{\pmb{e}}_{\theta} = \cos(\theta) \pmb{e}_x + \sin(\theta) \pmb{e}_y$$

The polarization vector for $$\pmb{\psi}$$ is given by the Jones 2-vector $$\vec{J}$$ when the wavefunction can be represented as,

$$\pmb{\psi}(\pmb{x}, t) = \Psi\left(z \: \widehat{\pmb{e}}_z, t, \vec{\phi}\right) \vec{A} = \Phi\left(z \: \widehat{\pmb{e}}_z, t\right) \vec{J}$$

where $A^x, A^y$ represent the amplitudes of the $$x$$ and $$y$$ polarization states and $$\phi^x, \phi^y$$ are analogous to their phase factors. Furthermore, $$\left\lvert \Phi(z \: \widehat{\pmb{e}}_z, t) \right\rvert = 1$$ for all $$z, t \in \mathbb{R}$$. For plane waves, one can write,

$$
\begin{align*}
\psi^k(z \: \pmb{e}_z, t) & = \Psi\left(z \: \pmb{e}_z, t, \phi^k \: \pmb{e}_k \right) \\
& = \exp\left(i(\omega t - k z + \phi^k)\right) A^k \\
& = \exp\left(i(\omega t - k z)\right) \exp(i \phi^k) A^k \\
& = \Phi(z \: \widehat{\pmb{e}}_z, t) J^k \\
\Phi(z \: \widehat{\pmb{e}}_z, t) & = \exp\left(i(\omega t - k z)\right) \\
J^k & = \exp(i \phi^k) A^k
\end{align*}
$$

The results of such an experiment follow a trend general enough so that we can replace the polarized light ray with a stream of silver atoms possessing magnetic moments, selected by analyzers generating a magnetic field along some orientation, and so on.

Now, let us see what classical physics predicts will happen in such a situation.

## Filtering

According to classical physics, the output of $$\mathcal{A}_{\theta}$$ is a beam travelling along $$\widehat{\pmb{e}}_z$$ and polarized along $$\widehat{\pmb{e}}_{\theta}$$, with an amplitude $$\widehat{\pmb{e}}_{\theta} \cdot \widehat{J}$$. In other words, if the new beam has a wavefunction $$\pmb{\psi}'$$,

$$\pmb{\psi}' = \left( \widehat{\pmb{e}}_{\theta} \cdot \widehat{J} \right) \Phi(z \: \widehat{\pmb{e}}_z, t) R_{\theta - \angle(\vec{J})}\left( \vec{J} \right)$$

where $R_{\phi}$ is the standard 2-rotation by angle $$\phi \in [0, 2 \pi]$$ on the $$xy$$-plane and,

$$\angle(\vec{J}) = \tan^{-1} \left( \frac{J^y}{J^x} \right)$$

Since energy is proportional to amplitude squared in wave mechanics, the energy $$E'$$ of the $$\pmb{\psi}'$$-wave is given in terms of that of the original $\pmb{\psi}$-wave as,

$$E' = \left\lvert \pmb{\psi}' \right\rvert^2 E = \left( \widehat{\pmb{e}}_{\theta} \cdot \widehat{J} \right)^2 E$$

Due to the triangle inequality, $E_{\pmb{\psi}'} \leq E_{\pmb{\psi}}$ and the two are equal if and only if $\vec{J}$ is oriented along $\pm \widehat{\pmb{e}}_{\theta}$.

## Compound setup

Suppose we add onto the basic setup as follows. We first pass a $$\vec{J}$$-polarized $$\pmb{\psi}$$-wave through an analyzer $$\mathcal{A}_{\theta}$$ to yield a $$\vec{J}'$$-polarized $$\pmb{\psi}'$$-wave, and then we again pass it through a second analyzer $$\mathcal{A}_{\theta'}$$ to get a $$\vec{J}''$$-polarized $$\pmb{\psi}''$$-wave as the output.

Schematically,

<iframe class="quiver-embed" src="https://q.uiver.app/#q=WzAsNSxbMiwwLCJcXG1hdGhjYWx7QX1fe1xcdGhldGF9Il0sWzMsMCwiXFxtYXRoY2Fse0F9X3tcXHRoZXRhJ30iXSxbMSwwLCJcXG1hdGhjYWx7QX1fe1xcYW5nbGUoXFx2ZWN7Sn0pfSJdLFs0LDAsIlxcbWF0aGNhbHtNfSJdLFswLDAsIlxcbWF0aGNhbHtTfSJdLFsyLDAsIlxccG1ie1xccHNpfSwgXFx2ZWN7Sn0iXSxbMCwxLCJcXHBtYntcXHBzaX0nLCBKJyBcXHdpZGVoYXR7XFxwbWJ7ZX19X1xcdGhldGEiXSxbMSwzLCJcXHBtYntcXHBzaX0nJywgSicnIFxcd2lkZWhhdHtcXHBtYntlfX1fe1xcdGhldGEnfSJdLFs0LDIsIj8sID8iXV0=&embed" width="698" height="176" style="border-radius: 8px; border: none;"></iframe>

Here, $$\mathcal{S}$$ is a source, whose output is passed through $$\mathcal{A}_{\angle(\vec{J})}$$ to *prepare* the corresponding $$\pmb{\psi}$$-wave (assumed to have a non-zero amplitude). The final $$\pmb{\psi}''$$-wave is directed to a measurement apparatus $$\mathcal{M}$$, such as a beam-splitter followed by perpendicular polarization detectors oriented along incrementing angles (as we shall see, the detector with no output measures the input wave's polarization phase shifted by 90 degrees).

By recursively applying the calculation in the basic setup,

$$
\begin{align*}
\pmb{\psi}' & = \left( \widehat{\pmb{e}}_{\theta} \cdot \widehat{J} \right) \Phi(z \: \widehat{\pmb{e}}_z, t) R_{\theta - \angle(\vec{J})}\left( \vec{J} \right) \\
\pmb{\psi}'' & = \left( \widehat{\pmb{e}}_{\theta'} \cdot \widehat{\pmb{e}}_{\theta} \right) \Phi(z \: \widehat{\pmb{e}}_z, t) R_{\theta' - \theta}\left( \left( \widehat{\pmb{e}}_{\theta} \cdot \widehat{J} \right) R_{\theta - \angle(\vec{J})}\left( \vec{J} \right) \right) \\
& = \cos(\theta' - \theta) \left( \widehat{\pmb{e}}_{\theta} \cdot \widehat{J} \right) \Phi(z \: \widehat{\pmb{e}}_z, t) R_{\theta' - \angle(\vec{J})}\left( \vec{J} \right)
\end{align*}
$$

In fact, for a series of $n$ analyzers $$\mathcal{A}_{\theta_1}, \dots, \mathcal{A}_{\theta_n}$$, one has,

$$\pmb{\psi}_n = \left( \prod_{k=1}^{n-1} \cos(\theta_{k+1} - \theta_k) \right) \left( \widehat{\pmb{e}}_{\theta_1} \cdot \widehat{J} \right) \Phi(z \: \widehat{\pmb{e}}_z, t) R_{\theta_n - \angle(\vec{J})}\left( \vec{J} \right)$$

Clearly, for any positive amount of light to exit from $$\mathcal{A}_{\theta_n}$$, we must never have, for any step comprised of $$\mathcal{A}_{\theta_k}, \mathcal{A}_{\theta_{k+1}}$$, that,

$$\theta_{k+1} = \theta_{k} + \frac{(2l+1) \pi}{2}, \qquad l \in \mathbb{Z}$$

Therefore, up to signature and no flipping of the polarization of waves, information about a wave is conserved between intermediate interaction with filters, as long as none of them in the resultant chain of filters is oriented perpendicular to another.

## Huygens-Fresnel principle for wave impulses

By the definition of the Dirac delta function $$\delta(\pmb{x}')$$ over $$\mathbb{R}^3$$ centred at $$\pmb{x} \in \mathbb{R}$$,

$$\pmb{\psi}(\pmb{x}, t) = \int_{\pmb{x}' \in \mathbb{R}^3} d^3 x' \: \delta(\pmb{x}' - \pmb{x}) \: \pmb{\psi}(\pmb{x}', t)$$

Equivalently, and rather more rigorously, $$d^3 x \: \delta(\pmb{x}' - \pmb{x})$$ can be replaced in the above expression, with the pointwise indicator function $$1_{\pmb{x}}(\pmb{x}')$$ which acts as a measure for integration over $$\mathbb{R}^3$$.

What this means is that classically, a $$\pmb{\psi}$$-wave is a superposition of contributions from all points, which act like sources of $$\pmb{\psi}$$-impulse. This is reminiscent of the Huygens-Fresnel principle, where all points on wavefronts are sources of spherically dispersing waves. The bridge between this case and the one above lies in Fourier optics — where the natural wavefronts are planar, and planar wavefronts for the different sinusoidal contributions of a $$\pmb{\psi}$$-wave add up along different orientations to form more complicated wavefronts. Here, we are merely considering the contributions from individual points and how they add up, hence the need for impulses. One may also say that we are considering 'pointlike wavefronts', although the notion is somewhat paradoxical were it not for the machinery of measure theory.

## Conclusion

Through the above considerations, we have built up a little toolkit for analyzing Stern-Gerlach experiments classically, in a structure that I believe could be helpful to capture deep parallelisms with quantum theory. This will be the subject of the next subpart.