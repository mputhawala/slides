## Approximately Optimally
## Relaxed Randomized Kaczmarz

&nbsp;

Jacob




-vertical-

Here there be MathJax

\\(
\def\argmin#1{\underset{#1}{\arg\min}}
\def\norm#1{\lVert#1\rVert}
\def\R{\mathbb{R}}
\def\P{\mathbf{P}}
\def\E{\mathbb{E}}
\def\e{\mathbf{e}}
\def\x{\mathbf{x}}
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

In the overdetermined inconsistent case

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
\E \norm{\x^{(k)}-\xexact}^2 \le r^k \norm{\x^{(0)} - \xexact}^2 + \frac{\norm{\b-\A\xexact}^2}{\sigma\_{N}^2}
\\]

Where \\(r = 1-\frac{\sigma\_N^2}{\sum\_{l=1}^N \sigma\_l^2}\\)




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




-vertical-

\\[
\A \e^{(k+1)} = \left[I - \frac{\A\A\_i^\t \A\_i \A^\t }{\norm{\A\_i \A^\t}^2}\right]\A\e^{(k)}
\\]

Borrowing the convergence of RK

\\[
\E \norm{\A\e^{(k)}}^2 \le \left(1 - \frac{\sigma\_N^4}{\sum\_{l=1}^N \sigma\_l^4}\right)^k \norm{\A\e^{(0)}}^2
\\]




-vertical-

\\[
\E \norm{\x^{(k)}-\xexact}^2 \le \frac{\sigma\_1^2}{\sigma\_N^2}r^k \norm{\x^{(0)} - \xexact}^2
\\]

Where \\(r = 1 - \frac{\sigma\_N^4}{\sum\_{l=1}^N \sigma\_l^4}\\)




-horizontal-

## Approximately
## Optimally Relaxed RK

Let \\(\tau\\) be a random set of indices and consider

\\[
\gamma\_k = \frac{\A\_i \A\_\tau^\t (\b\_\tau-\A\_\tau\x\_k)}{\norm{\A\_i \A\_\tau^\t}^2}
\\]




-vertical-

If \\(\tau = \\{i\\}\\) we recover standard RK:

\\[
\begin{align}
\gamma\_k &= \frac{A\_i A\_\tau^\t (\b\_\tau-\A\_\tau\x\_k)}{\norm{\A\_i \A\_\tau^\t}^2} \\\\
&= \frac{\A\_i \A\_i^\t (\b\_i-\A\_i\x\_k)}{\norm{\A\_i \A\_i^\t}^2} \\\\
&= \frac{\b\_i-\A\_i\x\_k}{\norm{\A\_i}^2}
\end{align}
\\]




-vertical-

While if \\(\tau = \\{1, 2, \dots, M\\}\\)

\\[
\begin{align}
\gamma\_k &= \frac{A\_i A\_\tau^\t (\b\_\tau-\A\_\tau\x\_k)}{\norm{\A\_i \A\_\tau^\t}^2} \\\\
&= \frac{\A\_i \A^\t (\b-\A\x\_k)}{\norm{\A\_i \A^\t}^2}
\end{align}
\\]

we recover optimally relaxed RK





-horizontal-

## Experimental Results




-vertical-

<img class="plain" src="images/consistent_gaussian_errs.svg" width="100%"/>




-vertical-

<img class="plain" src="images/inconsistent_gaussian_errs.svg" width="100%"/>




-vertical-

<img class="plain" src="images/step_size_vs_n_rows_hist.svg" width="100%"/>




-vertical-

<img class="plain" src="images/step_size_vs_n_terms_hist.svg" width="100%"/>




-horizontal-

## Future Work

Prove convergence results for approximate method




-vertical-

## Thanks for Listening




-vertical-

## Convergence (Consistent)

Define \\(\e^{(k)}=\x^{(k)} - \xexact\\)

\\[
\e^{(k+1)} = \left[I - \frac{\A\_i^\t \A\_i \A\_\tau^\t \A\_\tau}{\norm{\A\_i \A\_\tau^\t}^2}\right]\e^{(k)}
\\]

\\[
\A\_\tau \e^{(k+1)} = \left[I - \frac{\A\_\tau \A\_i^\t \A\_i \A\_\tau^\t}{\norm{\A\_i \A\_\tau^\t}^2}\right]\A\_\tau \e^{(k)}
\\]




-vertical-

\\[
\begin{align}
\norm{\A\_\tau \e^{(k+1)}}^2 &= \norm{\A\_\tau \e^{(k)}}^2 - \norm{\frac{\A\_\tau \A\_i^\t \A\_i \A\_\tau^\t}{\norm{\A\_i \A\_\tau^\t}^2}\A\_\tau \e^{(k)}}^2 \\\\
&= \norm{\A\_\tau \e^{(k)}}^2 - \frac{\|\A\_i \A\_\tau^\t\A\_\tau \e^{(k)}\|^2}{\norm{\A\_i \A\_\tau^\t}^2}
\end{align}
\\]