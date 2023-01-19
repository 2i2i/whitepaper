# WORK IN PROGRESS

# <b><p align="center">2i2i ~ the fairest market model</p></b>
#### <p align="center">[1m1@2i2i.app](https://github.com/2i2i/whitepaper/blob/main/Notes.md#acknowledgement)</p>

<br></br>
## <p align="center">Abstract</p>
<p align="center">This <a href="https://github.com/2i2i/whitepaper/blob/main/Notes.md#whitepaper">whitepaper</a> describes a novel, multi-dimensional, infinitely inclusive market model. The described model yields infinite types of new market dynamics and traditional markets as special cases, based on very few parameters. As the market allows any supply of arbitrarily small or large value to be traded in any currency, incl. subjective value currencies, any resulting liquid market must then find the optimal value of the supply, making this the fairest market model possible. </p>
<br></br>

# <b>I. Definitions</b>



<br></br>
## Market

Assume we have a **seller** with a finite **supply** $\mathcal{S}$ and there exists a **demand** $\mathcal{D}$ consisting of **bid**s.

A **market** $\mathcal{M}$ is a function that determines the next **bid** to be [serviced](https://github.com/2i2i/whitepaper/blob/main/Notes.md#all-trade-is-sequential). Formally,

$$\mathcal{M}(\mathcal{S}, \mathcal{D}) = B$$

where $B \in \mathcal{D}$ is a **bid**.


More generally, we add a parameter to the **market** $\mathcal{M}$ to output the **bid** *next after* some given **bid** $B$.

$$\mathcal{M}(\mathcal{S}, \mathcal{D}, B) = B_\text{next}$$

$$B, B' \in \mathcal{D} \cup \\\{∅\\\}$$

$∅$ represents an end, as follows. Simplifying $\mathcal{M}(\mathcal{S}, \mathcal{D}, B)$ to $\mathcal{M}(B)$.

$$\mathcal{M}(∅)=B_\text{first}$$
 $$\mathcal{M}(B_\text{last})=∅$$


This then allows for an ordering of the **bid**s

$$\mathcal{D} = [\mathcal{M}^1(∅), \mathcal{M}^2(∅), \ldots, \mathcal{M}^N(∅)] = [B_1, \ldots, B_N]$$

In this paper, we will define a partial ordering and a total ordering that is **[fairest](https://github.com/2i2i/whitepaper/blob/main/Notes.md#fairest)**, most **[inclusive](https://github.com/2i2i/whitepaper/blob/main/Notes.md#most-inclusive)** and accomodates [all](https://github.com/2i2i/whitepaper/blob/main/Notes.md#all-markets) types of **market**s, as well as innovating new types of **market**s with a generic framework.

<br></br>
## Parameters

The **seller** sets the following **parameters** $\mathcal{P}$:

$$\mathcal{P} = (\underline{M}, \mathcal{I})$$

$$\underline{M} \ge 0 \text{ minimum value that a bid needs to have}$$

$$\mathcal{I} = \text{importance}$$

The **importance** $\mathcal{I}$ will be explained later. It is a setting of the **seller** defining the importance of the different categories of **bid**s.

<br></br>
## Bid

Each **bid** $B$ looks as follows:

$$B = (T, A, \mathcal{P})$$

$$T = \text{time}$$

$$A = \text{(q, ccy, FX)} \text{ is the amount of the bid}$$

$$\mathcal{P} = \text{ the sellers parameters } T$$

The **amount** $A$ contains a quantity $q$, a **currency** $\text{ccy}$ and an exchange rate to a **base currency** $\text{FX}$, all fixed at time $T$.

<br></br>
## Rank
The **rank** of a **bid** $B$ is defined as the number of times a next has to be chosen to arrive at $B$

$$\mathcal{M}^\text{rank}(∅) = B$$

<br></br>
## Currency and FX

A [**currency**](https://github.com/2i2i/whitepaper/blob/main/Notes.md#currency) $\text{ccy}$ is defined as a bundle of [energy and information](https://github.com/2i2i/whitepaper/blob/main/Notes.md#energy-and-info). Let $\mathcal{C}$ be the universe of all existing currencies.

Then

$$\mathcal{C} = \mathcal{C}_\text{obj} \text{  } \dot{\cup} \text{  } \mathcal{C}_\text{sub}$$

that is, any **currency** either has [objective value xor subjective value](https://github.com/2i2i/whitepaper/blob/main/Notes.md#objective-vs-subjective-value).

We choose some

$$\text{ccy}_\text{base} \in \mathcal{C}_\text{obj}$$

as the **base currency** and we define

$$\text{FX}(\text{ccy}) = \text{FX}(\text{ccy}, T) = \text{FX}(\text{ccy}, \text{ccy}_\text{base}, T)$$

as the fair exchange rate between $\text{ccy}$ and $\text{ccy}_\text{base}$, i.e.

$$1  [\text{ccy}] = \text{FX}(\text{ccy})  [\text{ccy}_\text{base}]$$

and

$$\text{FX(ccy)} = ∅ \text{  if ccy}\in\mathcal{C}_\text{sub}$$


Now we are going to categorise **bid**s. First, we call a **bid** $B$ **objective**

$$B \text{ is objective} \Leftrightarrow \text{ccy} \in \mathcal{C}_\text{obj}$$

if it is in an objective value currency.


The **amount** $A$ of each **objective** **bid** can be transformed into the chosen **base currency**, as follows:

$$B(T, A = (q, \text{ccy}, \text{FX}), \mathcal{P}) \rightarrow B_\text{base}(T, A = (\text{FX}\cdot q , \text{ccy}_\text{base}, \text{FX}\equiv 1), \mathcal{P})$$

This means, without loss of generality, we can [assume](https://github.com/2i2i/whitepaper/blob/main/Notes.md#assuming) all **objective bids** to be denominated in the **base currency**.

<br></br>
## **Bid** Categories

[Assuming](https://github.com/2i2i/whitepaper/blob/main/Notes.md#assuming) that the **min** value $\underline{M}$ is also in the **base currency**, we [define](https://github.com/2i2i/whitepaper/blob/main/Notes.md#practical-chrony) the following 4 **bid** categories:

$$\text{chrony (CHR)} \Leftrightarrow B \text{ is objective}\land q = \underline{M}$$

$$\text{highroller (HR)} \Leftrightarrow B \text{ is objective}\land q > \underline{M}$$

$$\text{lurker (LURK)} \Leftrightarrow B \text{ is objective}\land q < \underline{M}$$

$$\text{subjective (SUBJ)} \Leftrightarrow B \text{ is subjective}$$

We can denote a **bid** $B$'s **category** as $\text{BC}(B)$.

<br></br>
## **Importance**

The **seller** defines the **importance** per **bid** **category**

$$\mathcal{I} = (\mathcal{I}_\text{CHR}, \mathcal{I}_\text{HR}, \mathcal{I}_\text{LURK}, \mathcal{I}_\text{SUBJ})$$

where each **importace** is a natural number

$$\mathcal{I}_\square\in\mathbb{N}_{\ge 0}, \square\in\\\{\text{CHR}, \text{HR}, \text{LURK}, \text{SUBJ}\\\}$$

the market is activated

$$0 < \sum_\square\mathcal{I}_\square = \sum\mathcal{I}$$

and the **[lurkers](https://github.com/2i2i/whitepaper/blob/main/Notes.md#why-lurkers)** never get serviced

$$\mathcal{I}_\text{LURK} = 0$$


Amongst every subsequence of the ordered **bid**s $[B_n, \ldots, B_m]$ of length $\sum\mathcal{I}$, on average, we get $\mathcal{I}_\square$ many of **bid** **category** $\square$.

E.g. if

$$\mathcal{I} = (\mathcal{I}_\text{CHR} = 2, \mathcal{I}_\text{HR} = 3, \mathcal{I}_\text{LURK} = 0, \mathcal{I}_\text{SUBJ} = 0)$$

then, on average, any subsequence of **bid**s **serviced** should contain 2 **chrony** and 3 **highroller** **bid**s.

<br></br>
<br></br>
# <b>II. The market</b> $\mathcal{M}$

<br></br>
## Characteristics

We want to create a **market** function such that:

- **importance** is respected

- **chrony bid**s are **serviced** chronologically

- **highroller bid**s are **serviced** in order of value

- worst case placement for **chrony bids** are [finite and deterministic](https://github.com/2i2i/whitepaper/blob/main/Notes.md#chrony-only-worst-case-finite)

- the **seller** can use it's own subjective value function to value **subjective bid**s

<br></br>
## Traditional **market**s as special cases

#### Fixed price

$$\underline{M} = \text{fixed price}$$

$$\mathcal{I} = (\mathcal{I}_\text{CHR} = 1, \mathcal{I}_\text{HR} = 0, \mathcal{I}_\text{LURK} = 0, \mathcal{I}_\text{SUBJ} = 0)$$

#### Auction

$$\underline{M} = \text{min price}$$

$$\mathcal{I} = (\mathcal{I}_\text{CHR} = 0, \mathcal{I}_\text{HR} = 1, \mathcal{I}_\text{LURK} = 0, \mathcal{I}_\text{SUBJ} = 0)$$

#### Barter

$$\mathcal{I} = (\mathcal{I}_\text{CHR} = 0, \mathcal{I}_\text{HR} = 0, \mathcal{I}_\text{LURK} = 0, \mathcal{I}_\text{SUBJ} = 1)$$

#### All other cases are mixed, innovative **market**s and would yield differing dynamics whenever changed

<br></br>
## The algorithm
<br></br>
### 1. Sort the **bid**s

We can almost surely assume

$$T_i \ne T_j \text{ if } i \ne j$$

that the **bid**s can be sorted chronologically.

Given this chronological ordering, let's group the **bid**s by creating subsequences of constant **parameters**:

$$\underbrace{B_1, \ldots, B_{i_1}}_{\mathcal{P}_1}, \underbrace{B_{i_1+1}, \ldots, B_{i_2}}_{\mathcal{P}_2}, \ldots, \underbrace{B_{i_{G_N}+1}, \ldots, B_N}_{\mathcal{P}_{G_N}}$$

that is, changing the **parameters** $\mathcal{P}$ fixes the current order.

We are left with the task of ordering the **bid**s given constant **parameters** $\mathcal{P}$.

<br></br>
### 2. Decimal Importance

The **importance** $\mathcal{I}$ can be converted into decimals as follows:

$$\mathcal{I}\rightarrow\nu_\square = \frac{\mathcal{I}_\square}{\sum\mathcal{I}} \in [0;1]$$

$$\square\in\\\{\text{CHR}, \text{HR}, \text{LURK}, \text{SUBJ}\\\}$$

We also know that

$$\nu_\text{LURK} = 0$$

$$\sum_\square\nu_\square = 1$$

$$\implies\nu_\text{SUBJ} = 1 - \nu_\text{CHR} - \nu_\text{HR}$$

which means that $\mathcal{I}$ can be represented as a 2-dim vector:

$$\mathcal{I} = \begin{pmatrix} \nu_\text{CHR} \\ \nu_\text{HR} \end{pmatrix}$$

<br></br>
### 3. Define $\mathcal{M}$

Given the previous max $\sum\mathcal{I}-1$ number of bids $[B_n,\ldots,B_m]$, we want to choose the next **bid** $B_\text{next}$.

First, we choose the next **bid** **category** as the **category** that brings our realized **importance** [closest](https://github.com/2i2i/whitepaper/blob/main/Notes.md#distance) ($\Delta$) to the target **importance** as set by the seller.

Calculate the realized **importance** $\hat{\mathcal{I}}$ including an assumed next **bid** **category** $\text{BC}(B_\text{next})$:

$$\hat{\mathcal{I}}=\begin{pmatrix} \hat{\nu}_\text{CHR} \\ \hat{\nu}_\text{HR} \end{pmatrix}$$

$$\hat{\nu}_\square = \frac{\\\#\\\{\text{BC}(B_i)==\square\\\}_{i=n\ldots m+1}}{m-n+1}$$

$$\text{BC}(B_\text{next})=\underset{\text{BC}(B_\text{next})}{\text{argmin }}\Delta(\mathcal{I}, \hat{\mathcal{I}})$$

If the next **category** should be $\text{CHR}$, then $B_\text{next}$ is the chronogically next $\text{CHR}$ **bid** available.

If the next **category** should be $\text{HR}$, then $B_\text{next}$ is the value ordered next $\text{HR}$ **bid** available.

If the next **category** should be $\text{SUBJ}$, then $B_\text{next}$ can be chosen in the two following ways:

1. $B_\text{next}$ is the chronogically next $\text{SUBJ}$ **bid** available. However, the **seller** can choose to decline the **bid**, using it's subjective value function. This gives a total ordering of the **bid**s.

1. Let the **seller** choose one xor none from all the existing $\text{SUBJ}$ **bid**s. This gives a partial ordering of the **bid**s.

A discussion of the choices is found [here](https://github.com/2i2i/whitepaper/blob/main/Notes.md#full-subj-choice-is-better).


Note the next **category** can never be $\text{LURK}$, as $\nu_\text{LURK}=0$. The **seller** can convert $\text{LURK}$ **bid**s into $\text{CHR}$ or $\text{HR}$ **bid**s by changing the **parameters**.

<br></br>
## Worst case **rank** is deterministic

Any **bid** can always choose to cancel, thereby improving the **rank** of all **bid**s behind it. Hence we only need to talk about the worst case.

*After* the creation of a **bid** $B$, we can simulate, as a mind experiment, the arrival of infinite many **bid**s of all categories possible:

- Worst and best case **rank** for a $\text{LURK}$ bid is $\infty$.

- Worst case **rank** for a $\text{SUBJ}$ bid is $\infty$, the seller uses it's own subjective value function.

- Worst case **rank** for a $\text{HR}$ bid is $\infty$, as other the market could theoretically increase and stay higher.

- Worst case **rank** for a $\text{CHR}$ bid is finite and deterministic, according to the importance $\mathcal{I}$.

<br></br>



<br></br><br></br>
# <b>III. Infinite inclusivity</b>
<br></br>

## The case

We can assume that any possible supply $\mathcal{S}$ has positive value, even if miniscule. The old world did not allow the transfer of smaller values than some threshold.

Using a chain of CFS, defined below, we can transact arbitrarily small (or large) values.

Hence, every kind and quantity of any supply is supported.
The market model is **infinitely inclusive**.

<br></br>
## Smart contracts

Smart contracts are autonomous, decentralized apps. The described market model is implemented as a smart contract for the following reasons: infinite inclusivity, zero credit risk, perfect [transparency](https://github.com/2i2i/whitepaper/blob/main/Notes.md#auditability-is-better), ability to use any kind of currency.

<br></br>
## Fungability

A currency is called fungible if it is available in varying units.

We can define the fungability $\mathbb{F}$ of a currency as the ratio of a base unit to the minimal unit.

E.g. 

$$\mathbb{F}(\text{USD})=10^2$$

$$\mathbb{F}(\text{BTC})=10^8$$

$$\mathbb{F}(\text{NFT})=10^0=1$$

<br></br>
## Constant Factor Stablecoin (CFS)

A CFS is a simple, permissionless smart contract that exchanges 1 unit of a currency $\text{ccy}_1$ for $\phi$ units of $\text{ccy}_2$ and vice-versa, as available.

A CFS never rounds and only makes exact exchanges.

Using a constant factor stablecoin, we can increase the fungability of [any](https://github.com/2i2i/whitepaper/blob/main/Notes.md#fungable-nfts) currency.

A chain of CFS can achieve arbitrary fungability.

<br></br>
<br></br>
# <b>IV. Conclusion</b>
<br></br>

## Provably fairest market

Consider:

- We accomodate any supply of arbitrarily small or large value.
- We allow any currency, whether those with objective value or any other, i.e. of subjective value.
- We define currency as an arbitrarily fungible bundle of energy and information
- We accomodate the entire region of objective value currencies possible (below, at and above the min value).
- We create the fairest (according to importance) sequence of servicing the demand
- We allow for infinite types of dynamics incl. traditional markets as special cases, set via simple parameters.

All these superlatives make this market model the most open possible.

Assuming liquidity, this market model thus provides the fairest valuation of any supply.

By changing the parameters, minimum $\underline{M}$ and importance $\mathcal{I}$, the seller can run a [multi-dim optimisation](https://github.com/2i2i/whitepaper/blob/main/Notes.md#multidim-optimisation) to find the type of market that maximises it's value.

<br></br>
## Maximum value $\Leftrightarrow$ Supply = Time
Everyone has time and everyone knows time is most valuable.
The widest and most valuable supply should run on the provably fairest market model. A v1 implementation is available and a v2 is being built.

As an 1st example application, we have chosen time as the supply. Available @ https://about.2i2i.app

2i2i is provably finds fairest value for time.

Using 2i2i for time makes most sense:
Use the optimal system for the most important

In a futuristic society, people could replace appointments with such a market for its time. Whenever you choose to interact with a person, instead of consulting a appointment schedule, consult the market. Importance and urgency are all expressed via the energy and information contained in every bid. 

When supply=time, all currencies are per $\Delta T$. Current technology already allows $\Delta T \le 1 \text{ sec}$.

Imagine the entire world harvesting the fairest amount of energy in exchange for the whatever information they can provide. 2i2i could in theory jump start the provably fairest economy ever.