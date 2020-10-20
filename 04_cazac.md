---
layout: page
title: CAZACs
permalink: /cazac/
---
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    extensions: [
      "MathMenu.js",
      "MathZoom.js",
      "AssistiveMML.js",
      "a11y/accessibility-menu.js"
    ],
    jax: ["input/TeX", "output/CommonHTML"],
    TeX: {
      extensions: [
        "AMSmath.js",
        "AMSsymbols.js",
        "noErrors.js",
        "noUndefined.js",
      ]
    }
  });
</script>

<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

**Note:** 
*This page is under construction so much of the page will likely be incomplete
at time of viewing. Sorry!*


Constant amplitude zero autocorrelation sequences, or CAZAC sequences, are
complex vectors in $$\mathbb{C}^n$$ which have properties particularly
useful for radar and communication theory. Mathematically, they have
several equivalent definitions, each of which connects them to completely
different areas of mathematics! Check out the sections below to explore
these definitions and the known theory.

## Definitions and Properites
<details>
  <summary><b>Definition</b></summary>
  Let `T` denote the translation operator on `\mathbb{C}^n`, i.e. `(Tx)_j = 
  x_{j-1}`. A sequence `x \in \mathbb{C}^n` is <b>CAZAC</b>  if the
  following two properties are satisfied: <br/>
  <hr style ="height:1em; visibility:hidden;" />
  &nbsp;&nbsp; 1. `|x_j| = 1` for all `j \in [n]`. (Constant Amplitude) <br/>
  &nbsp;&nbsp; 2. `\langle x, T^k x \rangle = 0` for all `k \in [n-1]`. 
  (Zero Autocorrelation) <br/>
  <hr style ="height:1em; visibility:hidden;" />
  By Parseval's identity, this definition is equivalent to `x` and 
  `\hat{x}` simultaneously satisfying the constant amplitude property. 
  As such, these sequences are also known as <b>biunimodular sequences</b>.
</details> 
<details>
  <summary><b>Equivalence to circulant Hadamard Matrices</b></summary>
  An `n \times n` matrix `H` is a <b>(complex) Hadamard matrix</b> if 
  `HH^\ast = n I` and `|H_{ij}| = 1` for every `i` and `j`.
  Moreover, `H` is a <b>circulant Hadamard matrix</b> if it is Hadamard and
  if each row is a shift of the previous row by one element to the right.
  A sequence `x \in \mathbb{C}^n` is a CAZAC sequence if and only if
  the circulant matrix
  $$
  \begin{pmatrix}
  x_1 & x_2 & \cdots & x_n \\
  x_n & x_{1} & \cdots & x_{n-1} \\
  \cdots & \cdots & \cdots & \cdots \\
  x_2 & x_3 & \cdots & x_1 \\
  \end{pmatrix}
  $$
  is also a Hadamard matrix. This establishes a one-to-one correspondence
  between CAZAC sequences and circulant Hadamard matrices.
</details>
<details>
  <summary><b>Equivalence to Cyclic `n`-roots and connection to algebraic 
  geometry</b></summary>
  Let `x \in \mathbb{C}^d` and define `z \in \mathbb{C}^d` by `z_j = x_{j+1}` / 
  `x_j`. We say `z` is a <b>cyclic `n`-root</b> if:
  $$
  \begin{align}
  z_1 + z_2 + \cdots + z_n & = 0 \\
  z_1 z_2 + z_2 z_3 + \cdots + z_n z_1 & = 0 \\
  z_1 z_2 z_3 + z_2 z_3 z_4 + \cdots + z_n z_1 z_2 & = 0 \\
  \cdots \\
  z_1 z_2 \cdots z_n & = 1. \\
  \end{align}
  $$
  Then, `x` is CAZAC if and only if `z` is a cyclic `n`-root. This establishes
  a one-to-one correspondence between CAZAC sequences and cyclic `n`-roots. 
  Note that
  the definition of a cyclic `n`-root defines an algebraic variety!
</details>
<details>
  <summary><b>Invariances</b></summary>
  Let `x \in \mathbb{C}^n` be a CAZAC sequence. The following operations
  preserve the CAZAC property: <br/>
<hr style ="height:1em; visibility:hidden;" />
  &nbsp;&nbsp; <b>1. Rotation: </b> `cx` for any complex scalar `c` where
  `|c| = 1`. <br/>
  &nbsp;&nbsp; <b>2. Translation:</b> 
  `(T_k x)_j = x_{j-k}`, for all `k \in \{ 1,\cdots, n-1 \}`. <br/>
  &nbsp;&nbsp; <b>3. Modulation:</b> 
  `(M_l x)_j = \exp({2 \pi l j i} / n) x_j`, for all `l \in \{ 1,\cdots, n-1 
   \}`. <br/>
  &nbsp;&nbsp; <b>4. Decimation:</b> `(\pi_m x)_j = x_{mj}` for all `m`
  relatively prime to `n`. <br/>
  &nbsp;&nbsp; <b>5. Conjugation:</b> `\bar{x}`.
</details>
<details>
  <summary><b>How many are there?</b></summary>
  We say two CAZAC sequences in `\mathbb{C}^n`, `x` and `y`, are equivalent
  if there exists a complex scalar `c` such that `y = cx`. Given this
  definition, we have 3 cases:
<hr style ="height:1em; visibility:hidden;" />
  &nbsp;&nbsp;<b>1.</b> If `n` is prime, then there are at most
  `C(2p-2,p-1)` many equivalence classes. In particular, the number
  of equivalence classes is finite. The proof of this uses 
  the fact that a compact algebraic variety in `\mathbb{C}^n` is finite.
  <b>[Ha08]</b> <br/>
  &nbsp;&nbsp;<b>2.</b> If `n` is composite, and is not square-free, i.e.
  there exists `m` such that `m^2 | n`, then there are infinitely many
  equivalence classes. This is shown by explicitly constructing an infinite
  family. See the Bj&ouml;rck-Saffari construction below. <b>[BS95]</b><br/>
  &nbsp;&nbsp;<b>3.</b> If `n` is composite, and is square-free, then
  it is <b> not known </b> if the number of equivalence classes is finite
  or infinite. <br/>
<hr style ="height:1em; visibility:hidden;" />
</details>
<hr style ="height:1em; visibility:hidden;" />

## Constructions
<details>
  <summary><b>Zadoff-Chu</b></summary>
  <i> Coming soon! </i>
</details>
<details>
  <summary><b>P4</b></summary>
  <i> Coming soon! </i>
</details>
<details>
  <summary><b>Wiener</b></summary>
  <i> Coming soon! </i>
</details>
<details>
  <summary><b>Bj&ouml;rck</b></summary>
  <i> Coming soon! </i>
</details>
<details>
  <summary><b>Bj&ouml;rck-Saffari</b></summary>
  <i> Coming soon! </i>
</details>
<details>
  <summary><b>Milewski</b></summary>
  <i> Coming soon! </i>
</details>
<hr style ="height:1em; visibility:hidden;" />
## Open Problems and Literature
<details>
  <summary><b>Open Problems</b></summary>
  <b>1.</b> Up to rotation, are there finitely many CAZAC sequences 
  of composite square-free length? If so, how many are there? <br/>
  <b>2.</b> Besides Bj&ouml;rck's construction, are there other CAZAC sequences
  which are not essentially given by roots of unity?
</details>
<details>
  <summary><b>Literature</b></summary>
  <b>[BCM19]</b> John J. Benedetto, Katherine Cordwell, and Mark Magsino. "CAZAC
  sequences and Haagerup's Characterization of Cyclic N-roots". <i>New Trends
  ind Applied Harmonic Analysis, Volume 2</i>. Birkh&auml;user, 2019: 1-43.
  <br/>
  <b>[BKR09]</b> John J. Benedetto, Ioannis Konstantinidis, and Muralidhar
  Rangaswamy. "Phase-coded waveforms and their design." <i>IEEE Signal
  Processing Magazine</i>. Vol. 26.1, 2009: 22-31. <br/>
  <b>[BS95]</b> G&ouml;ran Bj&ouml;rck and Bahman Saffari. "New classes of
  finite unimodular sequences with unimodular Fourier transforms. Circulant
  Hadamard matrices with complex entries." <i>Comptes rendus de 
  l'Acad&eacute;mie des sciences. S&eacute;rie 1, Math&eacute;matique</i>.
  Vol. 320, no. 3, 1995: 319-324. <br/>
  <b>[Ha96]</b> Uffe Haagerup. "Orthogonal maximal abelian-subalgebras of
  the n x n matrices and cyclic n-roots". <i>Odense Universitet</i>.1996. <br/>
  <b>[Ha08]</b> Uffe Haagerup. "Cyclic p-roots of prime lengths p and related
  complex Hadamard matrices." <i>arXiv preprint arXiv:0803.2629</i>. 2008. <br/>
  <b>[Ma16]</b> Mark Magsino. "Constructing tight Gabor frames using CAZAC 
  sequences". <i>Sampling Theory in Signal and Image Processing</i>. Vol. 16, 
  2016: 73-99.
</details>
