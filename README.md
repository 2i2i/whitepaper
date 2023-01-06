# WORK IN PROGRESS

Assume we have an seller with a finite supply $\mathcal{S}$ and there exists a demand $\mathcal{D}$ consisting of bids.

A market $\mathcal{M}$ is a function that determines the next bid to be serviced[^alltradeissequential]. Formally,

$$\mathcal{M}(\mathcal{S}, \mathcal{D}) = B$$

where $B \in \mathcal{D}$ is a bid.


More generally, we add a parameter to the market $\mathcal{M}$ to output the bid after some given bid. 

$$\mathcal{M}(\mathcal{S}, \mathcal{D}, B') = B$$

$$B, B' \in \mathcal{D} \cup \\\{∅\\\}$$

$\mathcal{M}(\mathcal{S}, \mathcal{D}, ∅)$ gives the first bid to be serviced and $\mathcal{M}(\mathcal{S}, \mathcal{D}, B') = ∅$ means $B'$ is the last bid to be serviced.

This then allows for an ordering of the bids.

$$\mathcal{D} = [B_1, \ldots, B_N]$$

In this paper, we will define a partial ordering and a full ordering that is fairest[^fairest], most inclusive[^mostinclusive] and accomodates all[^allmarkets] types of markets, as well as innovating new types of markets with a generic framework.



The sellers sets the following parameters $\mathcal{P}$:

$$\mathcal{P} = (\underline{M}, \mathcal{I})$$

$$\underline{M} \ge 0 \text{ minimum value that a bid needs to have}$$

$$\mathcal{I} = \text{importance}$$

The importance $\mathcal{I}$ will be explained later. It is a setting of the seller defining the importance of the different categories of bids.



Each bid $B$ looks as follows:

$$B = (T, A, \mathcal{P})$$

$$T = \text{time}$$

$$A = \text{(q, ccy, FX)} \text{ is the amount of the bid}$$

$$\mathcal{P} = \text{ the sellers parameters } T$$

The amount $A$ contains a quantity $q$, a currency $\text{ccy}$ and an exchange rate to a universal base currency $\text{FX}$, all fixed at time $T$.

A currency $\text{ccy}$ is defined as a bundle of energy and information[^energyandinfo]. Let $\mathcal{C}$ be the universe of all existing currencies.

Then

$$\mathcal{C} = \mathcal{C}_\text{obj} \text{  } \dot{\cup} \text{  } \mathcal{C}_\text{sub}$$

that is, any currency either has objective value xor subjective value.

We choose some

$$\text{ccy}_\text{base} \in \mathcal{C}_\text{obj}$$

as the universal base currency and we define

$$\text{FX}(\text{ccy}) = \text{FX}(\text{ccy}, T) = \text{FX}(\text{ccy}, \text{ccy}_\text{base}, T)$$

as the fair exchange rate between $\text{ccy}$ and $\text{ccy}_\text{base}$, i.e.

$$1  [\text{ccy}] = \text{FX}(\text{ccy})  [\text{ccy}_\text{base}]$$

and

$$\text{FX(ccy)} = ∅ \text{  if ccy}\in\mathcal{C}_\text{sub}$$


Now we are going to categorise bids. First, we call a bid $B$ $\text{objective}$

$$B \text{ is objective} \Leftrightarrow \text{ccy} \in \mathcal{C}_\text{obj}$$

if it is in an objective value currency.


The amount $A$ of each objective bid can be transformed into the chosen base currency, as follows:

$$B(T, A = (q, \text{ccy}, \text{FX}), \mathcal{P}) \rightarrow B_\text{base}(T, A = (\text{FX}\cdot q , \text{ccy}_\text{base}, \text{FX}\equiv 1), \mathcal{P})$$

This means, without loss of generality, we can assume[^assuming] all objective bids to be dominated in the base currency.

Assuming[^assuming] that the min value $\underline{M}$ is also in the base currency, we define[^practicalchrony] the following 4 bid categories:

$$\text{chrony (CHR)} \Leftrightarrow B \text{ is objective}\land Q = \underline{M}$$

$$\text{highroller (HR)} \Leftrightarrow B \text{ is objective}\land Q > \underline{M}$$

$$\text{lurker (LURK)} \Leftrightarrow B \text{ is objective}\land Q < \underline{M}$$

$$\text{subjective (SUBJ)} \Leftrightarrow B \text{ is subjective}$$

We can denote a bid $B$'s category as $\text{BC}(B)$.

### Importance

The seller defines the importance per bid category

$$\mathcal{I} = (\mathcal{I}_\text{CHR}, \mathcal{I}_\text{HR}, \mathcal{I}_\text{LURK}, \mathcal{I}_\text{SUBJ})$$

where each importace is a natural number

$$\mathcal{I}_\square\in\mathbb{N}_{\ge 0}, \square\in\\\{\text{CHR}, \text{HR}, \text{LURK}, \text{SUBJ}\\\}$$

the market is activated

$$0 < \sum_\square\mathcal{I}_\square = \sum\mathcal{I}$$

and the lurkers[^whylurkers] never get serviced

$$\mathcal{I}_\text{LURK} = 0$$


Amongst every subsequence of the ordered bids $[B_n, \ldots, B_m]$ of length $\sum\mathcal{I}$, on average, we get $\mathcal{I}_\square$ many of bid category $\square$.

E.g. if

$$\mathcal{I} = (\mathcal{I}_\text{CHR} = 2, \mathcal{I}_\text{HR} = 3, \mathcal{I}_\text{LURK} = 0, \mathcal{I}_\text{SUBJ} = 0)$$

then, on average, any subsequence of bids serviced should contain 2 chrony and 3 highroller bids.

### Market function goals

We want to create a market function such that:

- importance is respected

- chrony bids are serviced chronologically

- highroller bids are serviced in order of value

- worst case placement for objective bids are finite and deterministic

- the seller can use it's own subjective value function to value subjective bids

### Traditional markets as special cases

#### Fixed price

$$\underline{M} = \text{fixed price}$$

$$\mathcal{I} = (\mathcal{I}_\text{CHR} = 1, \mathcal{I}_\text{HR} = 0, \mathcal{I}_\text{LURK} = 0, \mathcal{I}_\text{SUBJ} = 0)$$

#### Bidding

$$\underline{M} = \text{min price}$$

$$\mathcal{I} = (\mathcal{I}_\text{CHR} = 0, \mathcal{I}_\text{HR} = 1, \mathcal{I}_\text{LURK} = 0, \mathcal{I}_\text{SUBJ} = 0)$$

#### Barter

$$\mathcal{I} = (\mathcal{I}_\text{CHR} = 0, \mathcal{I}_\text{HR} = 0, \mathcal{I}_\text{LURK} = 0, \mathcal{I}_\text{SUBJ} = 1)$$

#### All other cases are mixed, innovative markets and would yield differing dynamics whenever changed

## $\mathcal{M}$

### Sort the bids

We can almost surely assume

$$T_i \ne T_j \text{ if } i \ne j$$

that the bids can be sorted chronologically.

Given this chronological ordering, let's group the bids by creating subsequences of constant parameters:

$$\underbrace{B_1, \ldots, B_{i_1}}_{\mathcal{P}_1}, \underbrace{B_{i_1+1}, \ldots, B_{i_2}}_{\mathcal{P}_2}, \ldots, \underbrace{B_{i_{G_N}+1}, \ldots, B_N}_{\mathcal{P}_{G_N}}$$

that is, changing the parameters $\mathcal{P}$ fixes the current order.

We are left with the task of ordering the bids given constant parameters $\mathcal{P}$.

#### Decimal Importance

The importance $\mathcal{I}$ can be converted into decimals as follows:

$$\mathcal{I}\rightarrow\nu_\square = \frac{\mathcal{I}_\square}{\sum\mathcal{I}} \in [0;1]$$

$$\square\in\\\{\text{CHR}, \text{HR}, \text{LURK}, \text{SUBJ}\\\}$$

We also know that

$$\nu_\text{LURK} = 0$$

$$\sum_\square\nu_\square = 1$$

$$\implies\nu_\text{SUBJ} = 1 - \nu_\text{CHR} - \nu_\text{HR}$$

which means that $\mathcal{I}$ can be represented as a 2-dim vector:

$$\mathcal{I} = \begin{pmatrix} \nu_\text{CHR} \\ \nu_\text{HR} \end{pmatrix}$$

#### Define $\mathcal{M}$

Given the previous max $\sum\mathcal{I}-1$ number of bids $[B_n,\ldots,B_m]$ with $0\le m-n<\sum\mathcal{I}-1$, we want to choose the next bid $B_\text{next}$.

First, we choose the next bid category as the category that brings our realized importance closer($\Delta$[^distance]) to the target importance as set by the seller.

Calculate the realized importance $\hat{\mathcal{I}}$ including an assumed next bid category $\text{BC}(B_\text{next})$:

$$\hat{\mathcal{I}}=\begin{pmatrix} \hat{\nu}_\text{CHR} \\ \hat{\nu}_\text{HR} \end{pmatrix}$$

$$\hat{\nu}_\square = \frac{\\\#\\\{\text{BC}(B_i)==\square\\\}_{i=n\ldots m+1}}{m-n+1}$$

$$\text{BC}(B_\text{next})=\underset{\text{BC}(B_\text{next})}{\text{argmin }}\Delta(\mathcal{I}, \hat{\mathcal{I}})$$

If the next category should be $\text{CHR}$, then $B_\text{next}$ is the chronogically next $\text{CHR}$ bid available.

If the next category should be $\text{HR}$, then $B_\text{next}$ is the value ordered next $\text{HR}$ bid available.

If the next category should be $\text{SUBJ}$, then $B_\text{next}$ can be chosen in the two following ways:

1. $B_\text{next}$ is the chronogically next $\text{SUBJ}$ bid available. However, the seller can choose to decline the bid, using it's subjective value function.

1. Let the seller choose one xor none from all the existing $\text{SUBJ}$ bids. This gives a partial ordering of the bids.

A discussion of the choices is found here: [^fullsubjchoiceisbetter].


Note the next category can never be $\text{LURK}$, as $\nu_\text{LURK}=0$. The seller can convert $\text{LURK}$ bids into $\text{CHR}$ or $\text{HR}$ bids by changing the parameters[^whylurkers].

### Worst placement

### Fairest market = optimal price

## Supply = Time
Everyone has time
Time is most valuable

# Smart contracts

## Zero credit risk

## Infinite inclusivity

## Currency



[^fullsubjchoiceisbetter]: todo

[^distance]: We can choose any 2-dim distance measure, e.g. the Euclidean metric.

[^practicalchrony]: todo

[^whylurkers]: todo

[^assuming]: These are not real 'assumptions'. These prerequisites that we are asking for are trivial and hence we are "assuming" them to be true already. Real 'assumptions' can be wrong.

[^mostinclusive]: todo

[^fairest]: todo

[^energyandinfo]: Energy and information as defined by the Sciences, as two fundamental elements of nature.

[^minvalue]: Every seller has the right to define it's own minimum value for a trade

[^allmarkets]: Is this a formal statement? No, but it seems that it could be formalised, but perhaps with some relaxation, i.e. making the absolute "all" statement still false.

[^alltradeissequential]: Having a finite supply requires ordering of demand. All selling of any supply is approximately sequential. Even selling digital copies of a product that seems unlimited, is in fact limited due to network bandwidth being limited and servers usually order demand on a "first-come, first-serve" basis. When supply is very large vs demand, then modeling a simultaneous trading sequentially, is not any loss at all, as the sequence can simply move very fast, giving the illution of simultaneouity.