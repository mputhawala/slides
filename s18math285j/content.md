## Optimally Relaxed
## Randomized Kaczmarz

&nbsp;

Jacob Moorman




-vertical-

Here there be MathJax

\\(
\def\argmin#1{\underset{#1}{\arg\min}}
\def\norm#1{\lVert#1\rVert}
\def\Norm#1{\Bigg\lVert#1\Bigg\rVert}
\def\R{\mathbb{R}}
\def\P{\mathbf{P}}
\def\E{\mathbb{E}}
\def\e{\mathbf{e}}
\def\x{\mathbf{x}}
\def\z{\mathbf{z}}
\def\y{\mathbf{y}}
\def\A{\mathbf{A}}
\def\b{\mathbf{b}}
\def\t{\intercal}
\def\xexact{\x^\ast}
\def\dd#1#2{\frac{\mathrm{d} #1}{\mathrm{d} #2}}
\def\innerprod#1#2{\langle #1 , #2 \rangle}
\\)




-horizontal-

## Problem

Seek the least-squares solution of \\(\A\x\approx\b\\)

\\[\xexact = \argmin{\x} \norm{\b-\A\x}^2 \\]

In the overdetermined **inconsistent** case

\\[A \in \R^{M \times N}, \; M \gt\gt N\\]
\\[ \norm{\b-\A\xexact}^2 \gt 0 \\]




-horizontal-

## Randomized Kaczmarz (RK)

1. Pick \\(i\\) with \\(\P(i=j) \propto \norm{\A\_j}^2\\)

1. Set \\(\x^{(k+1)} = \x^{(k)} + \frac{(b\_i-\A\_i \x^{(k)})}{\norm{\A\_i}^2}\A\_i^\t\\)

1. Repeat




-vertical-

## Convergence Horizon

\\[
\E \norm{\x^{(k)}-\xexact}^2 \le r^k \norm{\x^{(0)} - \xexact}^2 + \frac{\norm{\b-\A\xexact}^2}{\sigma\_\min^2}
\\]

Where \\(r = 1-\frac{\sigma\_\min^2}{\sum\_{l=1}^N \sigma\_l^2}\\)




-horizontal-

## Relaxed RK

Replace \\(\frac{(b\_i-\A\_i \x^{(k)})}{\norm{\A\_i}^2}\\) with \\(\gamma\_k\\)

\\[
\x^{(k+1)} = \x^{(k)} + \gamma\_k \A\_i^\t
\\]




-vertical-

## Optimal Step Size

Ideally, \\(\gamma\_k = \argmin{}\norm{\b-\A\x^{(k+1)}}^2\\)




-vertical-

\\[
\begin{align}
\mathbf 0 &=\dd{}{\gamma\_k}\norm{\b-\A\x^{(k+1)}}^2 \\\\
&=\dd{}{\gamma\_k}\norm{\b-\A(\x^{(k)} + \gamma\_k \A\_i^\t)}^2 \\\\
&= -2\A\_i\A^\t\left[\b-\A\left(\x^{(k)} + \gamma\_k \A\_i^\t\right)\right] \\\\
& \propto \gamma\_k \norm{\A\_i \A^\t}^2 - \A\_i \A^\t \left(\b-\A\x^{(k)}\right)
\end{align}
\\]




-vertical-

\\[
\begin{align}
\gamma\_k &= \frac{A\_i A^\t (\b-\A\x^{(k)})}{\norm{\A\_i \A^\t}^2} \\\\
\end{align}
\\]




-horizontal-

## Optimally Relaxed RK

1. Pick \\(i\\) with \\(\P(i=j) \propto \norm{\A\_j \A^\t}^2\\)

1. Set \\(\x^{(k+1)} = \x^{(k)} + \frac{\A\_i \A^\t (\b-\A\x^{(k)})}{\norm{\A\_i \A^\t}^2}\A\_i^\t\\)

1. Repeat




-vertical-

## Convergence

Define \\(\e^{(k)}=\x^{(k)} - \xexact\\)

\\[
\begin{align}
\e^{(k+1)} &= \e^{(k)} + \frac{A\_i A^\t (\b-\A\xexact - \A\e^{(k)})}{\norm{\A\_i \A^\t}^2}\A\_i^\t \\\\
&= \left[I - \frac{\A\_i^\t \A\_i \A^\t \A}{\norm{\A\_i \A^\t}^2}\right]\e^{(k)}
\end{align}
\\]

\\[
\A \e^{(k+1)} = \left[I - \frac{\A\A\_i^\t \A\_i \A^\t }{\norm{\A\_i \A^\t}^2}\right]\A\e^{(k)}
\\]




-vertical-

\\[
\begin{align}
\E \norm{\A\e^{(k+1)}}^2 &= \E \Norm{ \left[I - \frac{\A\A\_i^\t \A\_i \A^\t }{\norm{\A\_i \A^\t}^2}\right]\A\e^{(k)}} ^2 \\\\
&= \E \left[\norm{\A\e^{(k)}}^2 - \Norm{\frac{\A\A\_i^\t \A\_i \A^\t }{\norm{\A\_i \A^\t}^2} \A\e^{(k)}}^2 \right]\\\\
&= \norm{\A\e^{(k)}}^2 - \E \Norm{\frac{\A\A\_i^\t \A\_i \A^\t }{\norm{\A\_i \A^\t}^2} \A\e^{(k)}}^2 \\\\
&= \norm{\A\e^{(k)}}^2 - \E \frac{\|\A\_i \A^\t \A\e^{(k)}\|^2}{\norm{\A\_i \A^\t}^2} \\\\
&= \norm{\A\e^{(k)}}^2 - \frac{\norm{\A \A^\t \A\e^{(k)}}^2}{\norm{\A \A^\t}\_F^2} \\\\
\end{align}
\\]




-vertical-

\\[
\E \norm{\x^{(k)}-\xexact}^2 \le \frac{\sigma\_\max^2}{\sigma\_\min^2}r^k \norm{\x^{(0)} - \xexact}^2
\\]

Where \\(r = 1 - \frac{\sigma\_\min^4}{\sum\_{l=1}^N \sigma\_l^4}\\)




-horizontal-

## Optimally Relaxed RK
#### Efficient Updates

Can we reorganize updates to run more efficiently?




-vertical-

\\[\x^{(k+1)} = \x^{(k)} + \frac{\A\_i \A^\t (\b-\A\x^{(k)})}{\norm{\A\_i \A^\t}^2}\A\_i^\t\\]




-vertical-

\\[\x^{(k+1)} = \x^{(k)} + \gamma\_k \A\_i^\t\\]

\\[
\begin{align}
\gamma\_k &= \frac{\A\_i \A^\t (\b-\A\x^{(k)})}{\norm{\A\_i \A^\t}^2} \\\\
&= \frac{\A\_i \z^{(k)}}{\norm{\A\_i \A^\t}^2}
\end{align}
\\]

\\[
\begin{align}
\z^{(k+1)} &= \A^\t (\b-\A\x^{(k+1)}) \\\\
&= \z^{(k)} - \gamma\_{k}\A^\t \A\A_i^\t
\end{align}
\\]




-vertical-

## An Efficient Update

\\[\gamma\_k = \frac{\A\_i \z^{(k)}}{\norm{\A\_i \A^\t}^2}\\]

\\[\x^{(k+1)} = \x^{(k)} + \gamma\_k \A\_i^\t\\]

\\[\z^{(k+1)} = \z^{(k)} - \gamma\_{k}\A^\t \A\A_i^\t\\]

Costs only \\(O(N)\\)




-vertical-

## Initialization

\\[\z^{(0)} = \A^\t (\b-\A\x^{(0)})\\]

Costs \\(O(MN)\\)




-vertical-

## Precompute

Row norms of \\(\A\A^\t\\)

\\[\A^\t \A\\]

\\[\A^\t \A \A^\t\\]

Costs \\(O(M^2 N)\\)




-horizontal-

## Experimental Results

100 x 10 Inconsistent Gaussian System




-vertical-

<img class="plain" src="images/opt_vs_vanilla_errs.svg" width="100%"/>




-vertical-

<img class="plain" src="images/vanilla_vs_bound_errs.svg" width="100%"/>




-vertical-

<img class="plain" src="images/opt_vs_bound_errs.svg" width="100%"/>




-horizontal-

## Why are the bounds
## So loose?

\\[
\begin{align}
\E\norm{\e^{(k+1)}}^2 &= \norm{\e^{(k)}}^2 - \frac{\norm{\A \e ^{(k)}}^2}{\norm{\A}\_F^2}
\end{align}
\\]




-vertical-

\\[\left(1-\frac{\sigma\_\max^2}{\sum\_{l=1}^N \sigma\_l^2}\right) \norm{\e^{(k)}} \le\\]

\\[\E\norm{\e^{(k+1)}}^2\\]

\\[\le \left(1-\frac{\sigma\_\min^2}{\sum\_{l=1}^N \sigma\_l^2}\right) \norm{\e^{(k)}}\\]




-horizontal-

## Experimental Results

1000 x 10 Inconsistent Gaussian System




-vertical-

<img class="plain" src="images/opt_vs_vanilla_errs2.svg" width="100%"/>




-vertical-

<img class="plain" src="images/opt_vs_bound_errs2.svg" width="100%"/>




-horizontal-

## Experimental Results

10000 x 10 Inconsistent Gaussian System




-vertical-

<img class="plain" src="images/opt_vs_vanilla_errs3.svg" width="100%"/>




-vertical-

<img class="plain" src="images/opt_vs_bound_errs3.svg" width="100%"/>




-horizontal-

## Future Work

Consider optimally relaxed block updates

Compare to other methods: REK, etc

Write-up




-horizontal-

## Thanks for Listening