# Chapter 2 - The Natural Numbers

## 2.1 - The Peano Axioms

### Axioms

1. 0 is a natural number
2. If $n$ is a natural number, then $n\texttt{++}$ is also a natural number.
3. 0 is not the successor of any natural number
    - $n\texttt{++} \ne 0$ for every natural number $n$
4. Different natural numbers must have different successors
    - if $n, m$ are natural numbers and $n \ne m$, then $n\texttt{++} \ne m\texttt{++}$
5. **Induction**: Let $P(n)$ be any property pertaining to a natural number $n$.  Suppose $P(0)$ is true, and suppose that whenever $P(n)$ is true, $P(n\texttt{++})$ is also true. Then $P(n)$ is true for all natural numbers $n$.

### Remarks

- With (1) and (2), we establish that any number of increments applied to 0
    yields a natural number
- (3) prevents wrap-arounds to 0
- (4) prevents wrap-arounds to any other non-zero number
- Having (3) and (4) may appear redundant, but any non-zero wrap-around can be
    traced back to a zero-based wrap-around, so (4) requires (3).
    - Ex (p.19): $6 \ne 2$
    - Suppose $6 = 2 \implies 5++ = 1++$
    - By (4), we have $5 = 1 \implies 4++ = 0++$
    - By (4), we have $4 = 0 \implies 3++ = 0$
    - By (3), this is a **contradiction**, since 3 is a natural number (by (1)
        and (2)) and therefore cannot have 0 as its successor
    - Hence $6 \ne 2$

---

### Recursive Definitions

Suppose for each natural number $n$, we have some function $f_n : \mathbb{N}
\rightarrow \mathbb{N}$ from the natural numbers to the natural numbers. Let $c$
be a natural number. Then we can assign a unique natural number $a_n$ to each
natural number $n$, such that $a_0 = c$ and $a_{n\texttt{++}} = f_n (a_n)$ for
each natural number $n$. (p.23)
- In other words, for each natural number $n$, there is a function $f_n$ that
    "bridges" the successive pair of elements $n$ and $n\texttt{++}$ together;
    i.e., $f_n(n) = n\texttt{++}$.

### Proof

*This is informal, since we have not yet introduced the concept of functions
(footnote 3, p.23).*

[Source](https://math.stackexchange.com/a/2287393)

Let $P(n)$ be the property:

Given a countable family of functions
$\{f_n | f_n : \mathbb{N} \rightarrow \mathbb{N}, \forall n \in
\mathbb{N}\}$, then, by choosing an initial seed value $c \in
\mathbb{N}$, we can always define a **unique** sequence of natural
numbers $\{a_k\}_{k\in\mathbb{N}}$ given by:

- $a_0 = c$
- $a_{n\texttt{++}} = f_n(a_n)$ otherwise


> Note: "Unique" does *not* mean that each $a_k$ is distinct, but rather that
> every $a_k$ has exactly one value.

#### Base Case

- $a_0 = c$ is uniquely defined; i.e., $a_0$ will not be the input to any $f_n$
- Axiom (3) prevents wrap-around of the *subscripts* (which are the natural
    numbers themselves)
- So if we followed the connecting "bridges" starting from $f_1$, we will never
    find ourselves back at $a_0$
    - I.e., there is no $n \in \mathbb{N}$ such that $n\texttt{++} = 0$, so
        $f_n(a_n) \ne a_0$, for all $n \in \mathbb{N}$
- Therefore, $P(0)$ is true

#### Inductive Step

- Suppose $P(n)$ is true, which means $a_n$ is uniquely defined
- $a_{n\texttt{++}} = f_n(a_n)$ is also unique because $f_n$ is a function
    (hence the "informal" proof)
- Furthermore, by (4), there is no future wrap-around that will redefine
     $a_{n\texttt{++}}$
- Therefore, $P(n\texttt{++})$ is true


---

## 2.2 - Addition
