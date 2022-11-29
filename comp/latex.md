---
layout: default
---

# Latex style guide

An excellent editor for Latex is [TeXStudio](https://texstudio.org). VSCode with LaTeX Workshop plugin is also good.

<ol>

<li>
Put some comment lines between sections, etc., for easier reading and navigation, e.g.,
<pre>
%------------------------------------------------------------------------------
</pre>
</li>

<li>
Do not use any indenting or tab in the tex files.
</li>

<li>
Do not put explicit line break using <code>\\</code>  unless you have a really good reason to do so.
</li>

<li>
A blank line creates a new paragraph. Put a blank line only if you need a new paragraph.
</li>

<li>
Do not use <code>~</code>, <code>\hspace</code> and <code>\vspace</code> unless it is absolutely required. Spacing must be automatically determined by Latex.
</li>

<li>
Do not use bold font unless really needed to highlight an important point.
</li>

<li>
Section headings must be lower case except the first letter and proper nouns
<pre>
\section{Rising thermal bubble}
\section{Radial Raleigh-Taylor instability}
</pre>
</li>

<li>
How to put a figure
<pre>
\begin{figure}
\begin{center}
\includegraphics[width=0.8\textwidth]{figure}
\caption{This is a figure}
\label{fig:figlabel}
\end{center}
\end{figure}
</pre>
DO NOT PUT FILENAME EXTENSION.
</li>

<li>
Always use <code>\textwidth</code> to specify figure size.
</li>

<li>
NEVER specify both width and height, unless you have a really good reason to do so.
</li>

<li>
Figure file formats must be either eps or pdf; NEVER use png or jpg files.
</li>

<li>
Use tabular within figure to put several figures side-by-side
<pre>
\begin{figure}
\begin{center}
\begin{tabular}{cc}
\includegraphics[width=0.48\textwidth]{fig1} &
\includegraphics[width=0.48\textwidth]{fig2} \\
(a) & (b)
\end{tabular}
\caption{This is a figure: (a) pressure, (b) Mach}
\label{fig:figlabel}
\end{center}
\end{figure}
</pre>
The sum of widths must not exceed one.
</li>

<li>
How to put a table
<pre>
\begin{table}
\begin{center}
\begin{tabular}{|c|c|c|}
\hline
% other stuff
\hline
\end{tabular}
\caption{This is a table}
\label{tab:tablabel}
\end{center}
\end{table}
</pre>
</li>

<li>
Do not use <code>[h]</code> or <code>[ht]</code> for tables and figures; they must be allowed to float.
</li>

<li>
Equation, figure and table labels must be of the form <code>\label{eq:foo}</code>, <code>\label{fig:foo}</code>, <code>\label{tab:foo}</code>, respectively. Do not use spaces in label names.
</li>

<li>
While quoting figure, table, etc., add a tilde to make the number appear on same line.
<pre>
as shown in figure~(\ref{fig:foo}), the solution ...
as shown in table~(\ref{tab:foo}), the solution ...
</pre>
</li>

<li>
Do not put comma/dot/period/full stop at end of equations.
</li>

<li>
Do not put comma/period inside inlined equations. This is not correct
<pre>
... we define <span style="color:red;">$a=(1,1).$</span> Then we can see that ...
</pre>
Put it like this
<pre>
... we define <span style="color:red;">$a=(1,1)$.</span> Then we can see that ...
</pre>
</li>

<li>
A un-numbered equation can be put as
<pre>
\[
a = b + c
\]
</pre>
or
<pre>
\begin{equation*}
a = b + c
\end{equation*}
</pre>
</li>

<li>
An equation must be numbered ONLY if you refer to the equation number within the text.
</li>

<li>Inline math must be completely enclosed in dollars
<pre>
... and the EOS is $p = \rho R T$ ...
... where we use the value $\gamma = 1.4$ and $R = 1.0$ in the computations ...
</pre>
</li>

<li>
To put space in equation

<pre>
\[
a = b + c, \quad x = y + z
\]
</pre>

To put more space

<pre>
\[
a = b + c, \qquad x = y + z
\]
</pre>
</li>

<li>
To use bigger brackets do
<pre>
a = \left[ 1 + \frac{1}{2}b \right]
</pre>
Do not use <code>\bigg[</code>, etc. unless there is a good reason to do so (may be required inside eqnarray).
</li>

<li>
To use bold math fonts, use the <code>bm</code> package and then
<pre>
\bm{v} = \frac{d \bm{x}}{dt}
</pre>
</li>

<li>
To put a conditional equation, use cases
<pre>
\[
u(x) = \begin{cases}
1, & \textrm{if } x < 0 \\
0, & \textrm{otherwise}
\end{cases}
\]
</pre>
</li>

<li>
Different equation styles

<pre>
\[
a = b
\]

\begin{equation}
a = b
\end{equation}

\begin{equation}
\begin{aligned}
a &= b \\
c &= d
\end{aligned}
\end{equation}

\begin{equation}
\begin{split}
a &= b \\
c &= d
\end{split}
\end{equation}

\begin{eqnarray}
a &=& b \\
c &=& d
\end{eqnarray}

\begin{align}
a &= b \\
c &= d
\end{align}

\begin{align}
a &= b   &   f &= g \\
c &= d   &   h &= k
\end{align}

\begin{gather}
a = b \\
c = d
\end{gather}

\begin{multline}
a = b + c + e \\
    + f + g + h
\end{multline}
</pre>
</li>

</ol>
