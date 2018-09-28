---
src       : src/plfa/Assignment1.lagda
title     : "Assignment1: TSPL Assignment 1"
layout    : page
permalink : /Assignment1/
---

<pre class="Agda">{% raw %}<a id="111" class="Keyword">module</a> <a id="118" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}" class="Module">plfa.Assignment1</a> <a id="135" class="Keyword">where</a>{% endraw %}</pre>

## YOUR NAME AND EMAIL GOES HERE

## Introduction

This assignment is due **4pm Thursday 4 October** (Week 3).

You must do _all_ the exercises labelled "(recommended)".

Exercises labelled "(stretch)" are there to provide an extra challenge.
You don't need to do all of these, but should attempt at least a few.

Exercises without a label are optional, and may be done if you want
some extra practice.

Submit your homework using the "submit" command.
Please ensure your files execute correctly under Agda!

## Imports

<pre class="Agda">{% raw %}<a id="687" class="Keyword">import</a> <a id="694" href="https://agda.github.io/agda-stdlib/Relation.Binary.PropositionalEquality.html" class="Module">Relation.Binary.PropositionalEquality</a> <a id="732" class="Symbol">as</a> <a id="735" class="Module">Eq</a>
<a id="738" class="Keyword">open</a> <a id="743" href="https://agda.github.io/agda-stdlib/Relation.Binary.PropositionalEquality.html" class="Module">Eq</a> <a id="746" class="Keyword">using</a> <a id="752" class="Symbol">(</a><a id="753" href="https://agda.github.io/agda-stdlib/Agda.Builtin.Equality.html#83" class="Datatype Operator">_≡_</a><a id="756" class="Symbol">;</a> <a id="758" href="https://agda.github.io/agda-stdlib/Agda.Builtin.Equality.html#140" class="InductiveConstructor">refl</a><a id="762" class="Symbol">;</a> <a id="764" href="https://agda.github.io/agda-stdlib/Relation.Binary.PropositionalEquality.html#1056" class="Function">cong</a><a id="768" class="Symbol">;</a> <a id="770" href="https://agda.github.io/agda-stdlib/Relation.Binary.PropositionalEquality.Core.html#838" class="Function">sym</a><a id="773" class="Symbol">)</a>
<a id="775" class="Keyword">open</a> <a id="780" href="https://agda.github.io/agda-stdlib/Relation.Binary.PropositionalEquality.html#3840" class="Module">Eq.≡-Reasoning</a> <a id="795" class="Keyword">using</a> <a id="801" class="Symbol">(</a><a id="802" href="https://agda.github.io/agda-stdlib/Relation.Binary.PropositionalEquality.html#3941" class="Function Operator">begin_</a><a id="808" class="Symbol">;</a> <a id="810" href="https://agda.github.io/agda-stdlib/Relation.Binary.PropositionalEquality.html#3999" class="Function Operator">_≡⟨⟩_</a><a id="815" class="Symbol">;</a> <a id="817" href="https://agda.github.io/agda-stdlib/Relation.Binary.PropositionalEquality.html#4058" class="Function Operator">_≡⟨_⟩_</a><a id="823" class="Symbol">;</a> <a id="825" href="https://agda.github.io/agda-stdlib/Relation.Binary.PropositionalEquality.html#4239" class="Function Operator">_∎</a><a id="827" class="Symbol">)</a>
<a id="829" class="Keyword">open</a> <a id="834" class="Keyword">import</a> <a id="841" href="https://agda.github.io/agda-stdlib/Data.Nat.html" class="Module">Data.Nat</a> <a id="850" class="Keyword">using</a> <a id="856" class="Symbol">(</a><a id="857" href="https://agda.github.io/agda-stdlib/Agda.Builtin.Nat.html#97" class="Datatype">ℕ</a><a id="858" class="Symbol">;</a> <a id="860" href="https://agda.github.io/agda-stdlib/Agda.Builtin.Nat.html#115" class="InductiveConstructor">zero</a><a id="864" class="Symbol">;</a> <a id="866" href="https://agda.github.io/agda-stdlib/Agda.Builtin.Nat.html#128" class="InductiveConstructor">suc</a><a id="869" class="Symbol">;</a> <a id="871" href="https://agda.github.io/agda-stdlib/Agda.Builtin.Nat.html#230" class="Primitive Operator">_+_</a><a id="874" class="Symbol">;</a> <a id="876" href="https://agda.github.io/agda-stdlib/Agda.Builtin.Nat.html#433" class="Primitive Operator">_*_</a><a id="879" class="Symbol">;</a> <a id="881" href="https://agda.github.io/agda-stdlib/Agda.Builtin.Nat.html#320" class="Primitive Operator">_∸_</a><a id="884" class="Symbol">;</a> <a id="886" href="https://agda.github.io/agda-stdlib/Data.Nat.Base.html#742" class="Datatype Operator">_≤_</a><a id="889" class="Symbol">;</a> <a id="891" href="https://agda.github.io/agda-stdlib/Data.Nat.Base.html#765" class="InductiveConstructor">z≤n</a><a id="894" class="Symbol">;</a> <a id="896" href="https://agda.github.io/agda-stdlib/Data.Nat.Base.html#807" class="InductiveConstructor">s≤s</a><a id="899" class="Symbol">)</a>
<a id="901" class="Keyword">open</a> <a id="906" class="Keyword">import</a> <a id="913" href="https://agda.github.io/agda-stdlib/Data.Nat.Properties.html" class="Module">Data.Nat.Properties</a> <a id="933" class="Keyword">using</a> <a id="939" class="Symbol">(</a><a id="940" href="https://agda.github.io/agda-stdlib/Data.Nat.Properties.html#7678" class="Function">+-assoc</a><a id="947" class="Symbol">;</a> <a id="949" href="https://agda.github.io/agda-stdlib/Data.Nat.Properties.html#7834" class="Function">+-identityʳ</a><a id="960" class="Symbol">;</a> <a id="962" href="https://agda.github.io/agda-stdlib/Data.Nat.Properties.html#7575" class="Function">+-suc</a><a id="967" class="Symbol">;</a> <a id="969" href="https://agda.github.io/agda-stdlib/Data.Nat.Properties.html#8011" class="Function">+-comm</a><a id="975" class="Symbol">;</a>
  <a id="979" href="https://agda.github.io/agda-stdlib/Data.Nat.Properties.html#1804" class="Function">≤-refl</a><a id="985" class="Symbol">;</a> <a id="987" href="https://agda.github.io/agda-stdlib/Data.Nat.Properties.html#1997" class="Function">≤-trans</a><a id="994" class="Symbol">;</a> <a id="996" href="https://agda.github.io/agda-stdlib/Data.Nat.Properties.html#1854" class="Function">≤-antisym</a><a id="1005" class="Symbol">;</a> <a id="1007" href="https://agda.github.io/agda-stdlib/Data.Nat.Properties.html#2109" class="Function">≤-total</a><a id="1014" class="Symbol">;</a> <a id="1016" href="https://agda.github.io/agda-stdlib/Data.Nat.Properties.html#10952" class="Function">+-monoʳ-≤</a><a id="1025" class="Symbol">;</a> <a id="1027" href="https://agda.github.io/agda-stdlib/Data.Nat.Properties.html#10862" class="Function">+-monoˡ-≤</a><a id="1036" class="Symbol">;</a> <a id="1038" href="https://agda.github.io/agda-stdlib/Data.Nat.Properties.html#10706" class="Function">+-mono-≤</a><a id="1046" class="Symbol">)</a>
<a id="1048" class="Keyword">open</a> <a id="1053" class="Keyword">import</a> <a id="1060" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Relations.md %}{% raw %}" class="Module">plfa.Relations</a> <a id="1075" class="Keyword">using</a> <a id="1081" class="Symbol">(</a><a id="1082" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Relations.md %}{% raw %}#17433" class="Datatype Operator">_&lt;_</a><a id="1085" class="Symbol">;</a> <a id="1087" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Relations.md %}{% raw %}#17460" class="InductiveConstructor">z&lt;s</a><a id="1090" class="Symbol">;</a> <a id="1092" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Relations.md %}{% raw %}#17517" class="InductiveConstructor">s&lt;s</a><a id="1095" class="Symbol">)</a>{% endraw %}</pre>

## Naturals

#### Exercise `seven` {#seven}

Write out `7` in longhand.


#### Exercise `+-example` {#plus-example}

Compute `3 + 4`, writing out your reasoning as a chain of equations.


#### Exercise `*-example` {#times-example}

Compute `3 * 4`, writing out your reasoning as a chain of equations.


#### Exercise `_^_` (recommended) {#power}

Define exponentiation, which is given by the following equations.

    n ^ 0        =  1
    n ^ (1 + m)  =  n * (n ^ m)

Check that `3 ^ 4` is `81`.


#### Exercise `∸-examples` (recommended) {#monus-examples}

Compute `5 ∸ 3` and `3 ∸ 5`, writing out your reasoning as a chain of equations.


#### Exercise `Bin` (stretch) {#Bin}

A more efficient representation of natural numbers uses a binary
rather than a unary system.  We represent a number as a bitstring.
<pre class="Agda">{% raw %}<a id="1934" class="Keyword">data</a> <a id="Bin"></a><a id="1939" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#1939" class="Datatype">Bin</a> <a id="1943" class="Symbol">:</a> <a id="1945" class="PrimitiveType">Set</a> <a id="1949" class="Keyword">where</a>
  <a id="Bin.nil"></a><a id="1957" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#1957" class="InductiveConstructor">nil</a> <a id="1961" class="Symbol">:</a> <a id="1963" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#1939" class="Datatype">Bin</a>
  <a id="Bin.x0_"></a><a id="1969" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#1969" class="InductiveConstructor Operator">x0_</a> <a id="1973" class="Symbol">:</a> <a id="1975" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#1939" class="Datatype">Bin</a> <a id="1979" class="Symbol">→</a> <a id="1981" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#1939" class="Datatype">Bin</a>
  <a id="Bin.x1_"></a><a id="1987" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#1987" class="InductiveConstructor Operator">x1_</a> <a id="1991" class="Symbol">:</a> <a id="1993" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#1939" class="Datatype">Bin</a> <a id="1997" class="Symbol">→</a> <a id="1999" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#1939" class="Datatype">Bin</a>{% endraw %}</pre>
For instance, the bitstring

    1011

standing for the number eleven is encoded, right to left, as

    x1 x1 x0 x1 nil

Representations are not unique due to leading zeros.
Hence, eleven is also represented by `001011`, encoded as

    x1 x1 x0 x1 x0 x0 nil

Define a function

    inc : Bin → Bin

that converts a bitstring to the bitstring for the next higher
number.  For example, since `1100` encodes twelve, we should have

    inc (x1 x1 x0 x1 nil) ≡ x0 x0 x1 x1 nil

Confirm that this gives the correct answer for the bitstrings
encoding zero through four.

Using the above, define a pair of functions to convert
between the two representations.

    to   : ℕ → Bin
    from : Bin → ℕ

For the former, choose the bitstring to have no leading zeros if it
represents a positive natural, and represent zero by `x0 nil`.
Confirm that these both give the correct answer for zero through four.

## Induction

#### Exercise `operators` {#operators}

Give another example of a pair of operators that have an identity
and are associative, commutative, and distribute over one another.

Give an example of an operator that has an identity and is
associative but is not commutative.


#### Exercise `finite-+-assoc` (stretch) {#finite-plus-assoc}

Write out what is known about associativity of addition on each of the first four
days using a finite story of creation, as
[earlier]({{ site.baseurl }}{% link out/plfa/Naturals.md%}#finite-creation)


#### Exercise `+-swap` (recommended) {#plus-swap} 

Show

    m + (n + p) ≡ n + (m + p)

for all naturals `m`, `n`, and `p`. No induction is needed,
just apply the previous results which show addition
is associative and commutative.  You may need to use
the following function from the standard library:

    sym : ∀ {m n : ℕ} → m ≡ n → n ≡ m

<pre class="Agda">{% raw %}<a id="swap"></a><a id="3784" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3784" class="Function">swap</a> <a id="3789" class="Symbol">:</a> <a id="3791" class="Symbol">∀</a> <a id="3793" class="Symbol">(</a><a id="3794" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3794" class="Bound">m</a> <a id="3796" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3796" class="Bound">n</a> <a id="3798" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3798" class="Bound">p</a> <a id="3800" class="Symbol">:</a> <a id="3802" href="https://agda.github.io/agda-stdlib/Agda.Builtin.Nat.html#97" class="Datatype">ℕ</a><a id="3803" class="Symbol">)</a> <a id="3805" class="Symbol">→</a> <a id="3807" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3794" class="Bound">m</a> <a id="3809" href="https://agda.github.io/agda-stdlib/Agda.Builtin.Nat.html#230" class="Primitive Operator">+</a> <a id="3811" class="Symbol">(</a><a id="3812" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3796" class="Bound">n</a> <a id="3814" href="https://agda.github.io/agda-stdlib/Agda.Builtin.Nat.html#230" class="Primitive Operator">+</a> <a id="3816" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3798" class="Bound">p</a><a id="3817" class="Symbol">)</a> <a id="3819" href="https://agda.github.io/agda-stdlib/Agda.Builtin.Equality.html#83" class="Datatype Operator">≡</a> <a id="3821" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3796" class="Bound">n</a> <a id="3823" href="https://agda.github.io/agda-stdlib/Agda.Builtin.Nat.html#230" class="Primitive Operator">+</a> <a id="3825" class="Symbol">(</a><a id="3826" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3794" class="Bound">m</a> <a id="3828" href="https://agda.github.io/agda-stdlib/Agda.Builtin.Nat.html#230" class="Primitive Operator">+</a> <a id="3830" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3798" class="Bound">p</a><a id="3831" class="Symbol">)</a>
<a id="3833" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3784" class="Function">swap</a> <a id="3838" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3838" class="Bound">m</a> <a id="3840" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3840" class="Bound">n</a> <a id="3842" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3842" class="Bound">p</a> <a id="3844" class="Keyword">rewrite</a> <a id="3852" href="https://agda.github.io/agda-stdlib/Relation.Binary.PropositionalEquality.Core.html#838" class="Function">sym</a> <a id="3856" class="Symbol">(</a><a id="3857" href="https://agda.github.io/agda-stdlib/Data.Nat.Properties.html#7678" class="Function">+-assoc</a> <a id="3865" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3838" class="Bound">m</a> <a id="3867" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3840" class="Bound">n</a> <a id="3869" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3842" class="Bound">p</a><a id="3870" class="Symbol">)</a> <a id="3872" class="Symbol">|</a> <a id="3874" href="https://agda.github.io/agda-stdlib/Data.Nat.Properties.html#8011" class="Function">+-comm</a> <a id="3881" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3838" class="Bound">m</a> <a id="3883" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3840" class="Bound">n</a> <a id="3885" class="Symbol">|</a> <a id="3887" href="https://agda.github.io/agda-stdlib/Data.Nat.Properties.html#7678" class="Function">+-assoc</a> <a id="3895" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3840" class="Bound">n</a> <a id="3897" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3838" class="Bound">m</a> <a id="3899" href="{% endraw %}{{ site.baseurl }}{% link out/plfa/Assignment1.md %}{% raw %}#3842" class="Bound">p</a> <a id="3901" class="Symbol">=</a> <a id="3903" class="Symbol">{!!}</a>{% endraw %}</pre>

#### Exercise `*-distrib-+` (recommended) {#times-distrib-plus}

Show multiplication distributes over addition, that is,

    (m + n) * p ≡ m * p + n * p

for all naturals `m`, `n`, and `p`.

#### Exercise `*-assoc` (recommended) {#times-assoc}

Show multiplication is associative, that is,

    (m * n) * p ≡ m * (n * p)

for all naturals `m`, `n`, and `p`.

#### Exercise `*-comm` {#times-comm}

Show multiplication is commutative, that is,

    m * n ≡ n * m

for all naturals `m` and `n`.  As with commutativity of addition,
you will need to formulate and prove suitable lemmas.

#### Exercise `0∸n≡0` {#zero-monus}

Show

    zero ∸ n ≡ zero

for all naturals `n`. Did your proof require induction?

#### Exercise `∸-+-assoc` {#monus-plus-assoc}

Show that monus associates with addition, that is,

    m ∸ n ∸ p ≡ m ∸ (n + p)

for all naturals `m`, `n`, and `p`.

#### Exercise `Bin-laws` (stretch) {#Bin-laws}

Recall that 
Exercise [Bin]({{ site.baseurl }}{% link out/plfa/Naturals.md%}#Bin)
defines a datatype `Bin` of bitstrings representing natural numbers
and asks you to define functions

    inc   : Bin → Bin
    to    : ℕ → Bin
    from  : Bin → ℕ

Consider the following laws, where `n` ranges over naturals and `x`
over bitstrings.

    from (inc x) ≡ suc (from x)
    to (from n) ≡ n
    from (to x) ≡ x

For each law: if it holds, prove; if not, give a counterexample.


## Relations


#### Exercise `orderings` {#orderings}

Give an example of a preorder that is not a partial order.

Give an example of a partial order that is not a preorder.


#### Exercise `≤-antisym-cases` {#leq-antisym-cases} 

The above proof omits cases where one argument is `z≤n` and one
argument is `s≤s`.  Why is it ok to omit them?


#### Exercise `*-mono-≤` (stretch)

Show that multiplication is monotonic with regard to inequality.


#### Exercise `<-trans` (recommended) {#less-trans}

Show that strict inequality is transitive.

#### Exercise `trichotomy` {#trichotomy}

Show that strict inequality satisfies a weak version of trichotomy, in
the sense that for any `m` and `n` that one of the following holds:
  * `m < n`,
  * `m ≡ n`, or
  * `m > n`
Define `m > n` to be the same as `n < m`.
You will need a suitable data declaration,
similar to that used for totality.
(We will show that the three cases are exclusive after we introduce
[negation]({{ site.baseurl }}{% link out/plfa/Negation.md%}).)

#### Exercise `+-mono-<` {#plus-mono-less}

Show that addition is monotonic with respect to strict inequality.
As with inequality, some additional definitions may be required.

#### Exercise `≤-iff-<` (recommended) {#leq-iff-less}

Show that `suc m ≤ n` implies `m < n`, and conversely.

#### Exercise `<-trans-revisited` {#less-trans-revisited}

Give an alternative proof that strict inequality is transitive,
using the relating between strict inequality and inequality and
the fact that inequality is transitive.

#### Exercise `o+o≡e` (stretch) {#odd-plus-odd}

Show that the sum of two odd numbers is even.

#### Exercise `Bin-predicates` (stretch) {#Bin-predicates}

Recall that 
Exercise [Bin]({{ site.baseurl }}{% link out/plfa/Naturals.md%}#Bin)
defines a datatype `Bin` of bitstrings representing natural numbers.
Representations are not unique due to leading zeros.
Hence, eleven may be represented by both of the following

    x1 x1 x0 x1 nil
    x1 x1 x0 x1 x0 x0 nil

Define a predicate

    Can : Bin → Set

over all bitstrings that holds if the bitstring is canonical, meaning
it has no leading zeros; the first representation of eleven above is
canonical, and the second is not.  To define it, you will need an
auxiliary predicate

    One : Bin → Set

that holds only if the bistring has a leading one.  A bitstring is
canonical if it has a leading one (representing a positive number) or
if it consists of a single zero (representing zero).

Show that increment preserves canonical bitstrings.

    Can x
    ------------
    Can (inc x)

Show that converting a natural to a bitstring always yields a
canonical bitstring.

    ----------
    Can (to n)

Show that converting a canonical bitstring to a natural
and back is the identity.

    Can x
    ---------------
    to (from x) ≡ x

\end{code}
(Hint: For each of these, you may first need to prove related
properties of `One`.)
