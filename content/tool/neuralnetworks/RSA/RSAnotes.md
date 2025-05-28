---
title: "Rational Speech Act-learning notes"
date: 2025-05-06T11:41:54-04:00
draft: false
math: true
---


"... one of my avowed aims is to see talking as a special case or variety of purposive, indeed rational, behavior" (Grice, 1975: 47)  

---


### I. Background of RSA

The Rational Speech Act (RSA) framework was developed within the broader enterprise of **Probabilistic Pragmatics**, a rapidly growing approach in the study of meaning.

**Probabilistic pragmatics** integrates insights from formal and experimental semantics and pragmatics, psycholinguistics, and computational cognitive science. It offers a unified framework for modeling how speakers produce and listeners interpret language in context.

#### Key Characteristics of Probabilistic Pragmatics

- **Formal Framework**: Provides a structure for implementing hypotheses about how speakers contextually choose among utterance alternatives and how listeners arrive at context-sensitive interpretations.
- **Formalizing Conversational Principles**: Captures principles such as relevance, brevity, and helpful informativeness (closely aligned with Gricean maxims) in a formal and testable way.
- **Probabilistic Processes**: Treats language production and interpretation as fundamentally probabilistic, allowing for **_gradience and variability_** that classic models struggle to explain.
- **Bounded Rationality**: Models speakers and listeners as boundedly rational agents, integrating information in ways consistent with general cognitive constraints.
- **Integration of Factors**: Allows linguistic knowledge to interact with communicative pressures and **subjective prior beliefs** (world knowledge), acknowledging their central role in interpretation.
- **Bridging Theoretical Traditions**: Seeks to unify "language-as-product" (representational structure) and "language-as-action" (context-sensitive decision-making).
- **Methodology**: Strongly computational and data-driven—models are implemented as algorithms and tested against empirical data.
- **Contrast with Classic Views**: In contrast to categorical interpretations in classic models, probabilistic pragmatics treats meaning, informativeness, and alternatives as **gradient** and **context-dependent**.

#### Types of Theories within Probabilistic Pragmatics

- **_Game-theoretic approaches_** (e.g., Benz & Stevens, 2018)
- **_Probabilistic but not fully Bayesian accounts_** (e.g., Qing & Franke, 2014; Russell, 2012)

The **Rational Speech Act (RSA)** framework stands out as arguably the **most influential probabilistic model of pragmatic interpretation**, integrating many of the features described above.

### II. classical view of meaning vs. RSA view of meaning

| **Aspect**                          | **The Classic View of Meaning**                                                                                                                                                                                                                                                                                                                                                          | **The RSA View of Meaning**                                                                                                                                                                                                                                                                                                                                                                                                                 |
|------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Nature of Interpretation**       | Meaning is treated as **categorical**. Implicatures either arise or not; presuppositions either project or not. No room for gradience or interpretational uncertainty.                                                                                                                                                                              | Interpretation is **probabilistic**. Listeners hold posterior probability distributions over meanings, capturing uncertainty. The model supports variability and gradience in interpretation.                                                                                                                                                                                                       |
| **Informativeness**                | Defined **categorically** using entailment-based alternatives. One statement is more informative if it entails another. No contextual modulation.                                                                                                                                                                                                 | Defined **gradually** and **contextually**. Informativeness reflects how much a literal listener would learn after hearing the utterance (minimizing surprisal). It varies based on the context.                                                                                                                                                                                                   |
| **Alternatives**                   | Treated as **static and lexicalized** (e.g., scales like <all, some>). The set of alternatives is fixed and not derived from context.                                                                                                                                                                                                             | Treated as **flexible and context-sensitive**. RSA is not a theory of alternatives but a framework for testing hypotheses. Alternatives can be adjusted based on data, and costly or complex alternatives can be penalized.                                                                                                                                                                         |
| **World Knowledge (Prior Beliefs)** | **Not integrated**. Classic models often exclude prior beliefs or world knowledge from formal reasoning, viewing them as nonlinguistic.                                                                                                                                                                                                            | **Formally integrated**. RSA uses Bayes’ rule to model how listeners use **subjective prior beliefs** (world knowledge) to infer intended meaning. These priors do not need to be objectively accurate.                                                                                                                                                                                            |
| **Inference Process**              | Gricean reasoning involves fixed premises. If these are met, an implicature is derived categorically; if not, it doesn’t arise. The speaker is assumed to choose the stronger alternative if it is true.                                                                                                                                            | RSA models interpretation as a **signaling game**. The speaker selects utterances balancing informativeness and cost. The listener uses **Bayesian inference** over utterances, context, and prior beliefs. This allows for **gradient** and variable inference.                                                                                                                                   |

### III. The basic/standard/vanilla RSA model
The basic **Rational Speech Act (RSA)** model treats language use as a **signaling game**. Speakers and listeners are modeled as agents who reason about:
- a space of utterances: $ U $
- a space of possible meanings: $ M $

> What Is a Signaling Game?  
>The RSA model builds on the idea that language use is a kind of **signaling game** — a concept borrowed from game theory (Lewis, 1969).  
>A **signaling game** models communication as an interaction between two rational agents:  
>- A **speaker** (or sender) who wants to convey a particular meaning.
>- A **listener** (or receiver) who observes the speaker’s utterance and tries to infer what meaning was intended.   
>
> Key Ingredients of a Signaling Game
>| Role         | Description                                                                 |
>|--------------|-----------------------------------------------------------------------------|
>| **Sender**   | Knows some private information (e.g., a meaning) and sends a signal (utterance). |
>| **Signal**   | The utterance or message the speaker chooses to send.                      |
>| **Receiver** | Observes the signal and makes an inference about the speaker’s intended meaning. |
>| **Goal**     | Successful communication: the listener correctly infers the speaker’s intended meaning. |


#### 3.1 Semantic Foundation (Denotation Functions)
RSA begins with a **literal semantics**, defined by a denotation function (see SECTION 4.1 for more explanations):

$$
\llbracket \cdot \rrbracket : U \rightarrow M
$$

This function specifies the set of meanings that are **literally compatible** with each utterance. It is assumed to be shared by both speaker and listener, grounding the recursive pragmatic reasoning that follows.

#### 3.2 Recursive Probabilistic Rules
Building on literal semantics, RSA defines a **recursive hierarchy** of production and interpretation rules. These involve probabilistic reasoning at each level and encode pragmatic inference.

#### 3.3 Literal Listener $ P_{L_0} $
The **literal listener** interprets utterances based on their literal meaning (See SECTION 4.2 for its components and calculations). Their interpretation rule is:

$$ 
P_{L_0}(m \mid u) = \delta_{m \in \llbracket u \rrbracket} \cdot P(m) 
$$

This means the listener updates their prior beliefs $P(m)$
only for meanings that are **literally compatible** with the utterance _u_. Here, $ \delta_{m \in \llbracket u \rrbracket} $ is an indicator function that returns 1 if $ m \in \llbracket u \rrbracket $, and 0 otherwise.

This step enforces the **Gricean Quality maxim**, ruling out meanings that are literally false.

#### 3.4 Pragmatic Speaker $\ P_{S_1} \$

The **pragmatic speaker** reasons about the literal listener’s interpretation to choose an utterance that best conveys the intended meaning $m$ (See SECTION 4.3 for more details). The speaker is modeled as a utility-maximizing agent:

$$
P_{S_1}(u \mid m) \propto \exp\left(\alpha \cdot U(u, m)\right)
$$

The **utility function** balances informativeness and cost:

$$
U(u, m) = \log P_{L_0}(m \mid u) - \text{Cost}(u)
$$

- **Informativeness**: How well $u$ communicates $m$, i.e., how likely the literal listener is to infer $m$.
- **Cost**: A penalty for utterances that are longer, less frequent, or harder to retrieve.
- **α** (alpha): A rationality parameter controlling how strongly the speaker optimizes utility.

This step reflects **Gricean Quantity** (informativeness) and **Manner** (cost) maxims.


#### 3.5 Pragmatic Listener  $P_{L_1}$

The **pragmatic listener** inverts the speaker model to infer the likely intended meaning:

$$
P_{L_1}(m \mid u) \propto P_{S_1}(u \mid m) \cdot P(m)
$$

This is a **Bayesian inference** over possible meanings, integrating:
- A model of the speaker’s utterance choice $ P_{S_1} $
- The listener’s **prior beliefs** about likely meanings $ P(m) $

These **priors** encode **world knowledge** and subjective expectations about communicative goals.


#### Key Insight

"RSA models replace Grice's maxims with a single, utility-theoretic version of the cooperative principle" (Goodman & Frank, 2016: 821)  

RSA treats language understanding as a **probabilistic inference problem**, in contrast to classical models which assume categorical interpretation. The pragmatic listener arrives at a **posterior probability distribution** over meanings, capturing the inherent uncertainty in language comprehension.

This recursive reasoning structure links production and interpretation in a unified, probabilistic framework.


### IV. More on the mathematical notations (for those not good at mathematical formalization, like me) (you may find it a bit repetitive)


To facilitate the explanation, a Scalar Implicature Game is used as an example:

> BASIC SCALAR IMPLICATURE GAME
> In this context, there were Alex and 4 cookies on a plate.   
> Meaning space: $ M = \\{ m_0, m_1, m_2, m_3, m_4 \\} $
>
> Utterance space: $ U = \\{ u_{\text{all}}, u_{\text{some}}, u_{\text{none}} \\} $
>
>Semantics:  $ u_{\text{all}}  = \\{ m_4 \\}$ 
>
>            $ u_{\text{some}}  = \\{ m_1, m_2, m_3, m_4 \\} $
>
>            $ u_{\text{none}}  = \\{ m_0 \\} $
>
> Prior beliefs: $P(m_0)$ = $P(m_1)$ = $P(m_2)$ = $P(m_3)$ = $P(m_4)$ = $0.2$

### 4.1 Denotation Function
The **denotation function** is a foundational concept in formal semantics and the Rational Speech Act (RSA) framework. In the RSA framework, the **denotation function** is written as:

$$
\llbracket \cdot \rrbracket : U \rightarrow M
$$
This means:

> The denotation function _maps each utterance $ u $ from the set of possible utterances $ U $ to a set of meanings $ M $ — specifically, the meanings for which the utterance is **literally true**_.  


#### 4.1.1  Step-by-Step Logic of the Indicator

Step 1: Evaluate Whether $m$ Is Literally Compatible with $u$

   - Ask: *Does this meaning make the utterance true according to its literal meaning?*

Step 2: Output the Result

   - If **YES** → Output **1** (keep this meaning for further consideration).
   - If **NO** → Output **0** (eliminate this meaning from consideration).

#### 4.1.2 Meaning of Components
An **utterance** $ u $ is something a speaker might say.  
Example:  
> “Alex ate some of the cookies.” 

A **meaning** $ m $ refers to a possible state of the world — what might be true or false.  
For example: (in a context where there were four cookies)
- $ m_0 $: Alex ate 0 cookie.  
- $ m_1 $: Alex ate 1 cookie.  
- $ m_2 $: Alex ate 2 cookies.
- $ m_3 $: Alex ate 3 cookies.
- $ m_4 $: Alex ate 4 cookies.

These meanings represent different situations the utterance might refer to.


#### 4.1.3  What does the denotation function do?
It defines which of those meanings ($m_0$, $m_1$, $m_2$, $m_3$, $m_4$) make the utterance **literally true**.  

For the utterance:
$
u = \text{“Alex ate some of the cookies.”}
$

The denotation is:
$
\llbracket u \rrbracket = \{ m_1, m_2, m_3, m_4 \}
$
, because the statement is true in those situations, but **not** in $\ m_{0} \$, where Alex ate no cookies.

#### 4.1.4 Why Is This Important in RSA?

- It directly enforces Grice’s **Quality Maxim** at the literal level: Only meanings that make the utterance literally true are considered.
- It performs an efficient filtering step before any deeper probabilistic reasoning.
- This grounding in literal truth ensures that **pragmatic reasoning starts from a shared semantic base**.
- It makes the RSA framework **compositional** and **grounded in literal semantics**.

#### 4.1.5 Summary Table

| Concept                   | Explanation                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| Utterance $ u $         | A sentence a speaker might say (“Some of the apples are red”)              |
| Meaning $ m $           | A possible state of the world (e.g., all red, some red, none red)          |
| Denotation $ \llbracket u \rrbracket $ | The set of meanings for which the utterance is literally true         |
| Role in RSA               | Helps the literal listener filter out meanings that are literally impossible |
---

### 4.2 Literal Listener $L_0$

The **Literal Listener** — denoted as $L_0$ — interprets an utterance based solely on its **literal semantics**, without considering the speaker’s goals or alternative utterances.


#### 4.2.1 Literal Listener Equations

#### 1. Simplified (Proportional) Equation

$$
P_{L_0}(m \mid u) \propto \delta_{m \in \llbracket u \rrbracket} \cdot P(m)
$$

This means:   
> The probability that the **Literal Listener** $L_0$ interprets utterance $u$ as meaning $m$ is proportional to whether the meaning $m$ is compatible with the literal semantics of $u$, multiplied by the prior probability of $ m $.

- This computes **unnormalized scores**.

#### 2. Full Normalized Equation
$$
P_{L_0}(m \mid u) = \frac{\delta_{m \in \llbracket u \rrbracket} \cdot P(m)}{\displaystyle \sum_{m'} \delta_{m' \in \llbracket u \rrbracket} \cdot P(m')}
$$

- The denominator ensures that final probabilities **sum to 1**.
- $\displaystyle \sum_{m'}$ sums over all possible meanings $m'$.

NOTE: 
> Denominator
>
> $$
> \sum_{m'} \delta_{m' \in \llbracket u \rrbracket} \cdot P(m')
> $$
>
> - This computes the total **weight** of all **and only** remaining possible meanings that make the utterance true (the meanings that make the utterance false would be **left out**).
> - It’s the sum over all possible meanings $ m' $ that are **compatible with the utterance**.
> - This ensures the final probabilities **sum to 1** — this is the **normalization step**.

#### Why Are There Two Versions?

| Version       | Purpose          |
|----------------|------------------|
| Proportional  | Computes unnormalized values. Useful for comparing relative likelihoods before normalization. |
| Normalized    | Computes final, interpretable probabilities that sum to 1. Required for reporting and decision-making. |


#### 4.2.2 Explanation of Each Component

(1) $ P_{L_0}(m \mid u) $  
This is the **posterior belief** of the Literal Listener:
> How likely is it that the intended meaning is $ m $, given that the utterance $ u $ was heard?

This represents the listener’s literal interpretation of the utterance: $ \llbracket u \rrbracket $

(2) $ \llbracket u \rrbracket $  

The set of meanings where $ u $ is literally true.

(3) $ \delta_{m \in \llbracket u \rrbracket} $

This is an **indicator/delta function**. It returns 1 if the meaning $m$ is **compatible** with the literal meaning of the utterance; 0 otherwise

> In effect, this acts as a **truth filter** — it rules out meanings that are not literally possible.

(4) $ P(m) $

This is the **prior probability** of each possible meaning, representing the listener’s **expectations** about the world **before** hearing the utterance.

#### 4.2.3 How the Literal Listener Computes Interpretation

In the RSA model, the **Literal Listener** $ L_0 $ updates beliefs about the world after hearing an utterance $ u $, based purely on **literal semantics** and **prior expectations**.

#### Example 1: “Alex ate some of the cookies.”


#### Step 1: Define the Possible Meanings $M$

| Meaning      | Description            |
|---------------|------------------------|
| $ m_0 $     | Alex ate 0 cookies     |          
| $ m_1 $     | Alex ate 1 cookie      |          
| $ m_2 $     | Alex ate 2 cookies     |          
| $ m_3 $     | Alex ate 3 cookies     |          
| $ m_4 $     | Alex ate 4 cookies     |          

Assume a **uniform prior**:

$$
P(m_i) = 0.2 \quad \text{for all } i \in \{0, 1, 2, 3, 4\}
$$

#### Step 2: Determine Literal Semantics (Define $\llbracket u \rrbracket$)

Utterance:  
> $ u = $ "Alex ate some of the cookies."

Literal semantics:

$$
\llbracket u \rrbracket = \{ m_1, m_2, m_3, m_4 \}
$$


#### Step 3
#### Option 1: Calculation Using the **Simplified (Proportional) Equation**

$$
P_{L_0}(m \mid u) \propto \delta_{m \in \llbracket u \rrbracket} \cdot P(m)
$$

#### Compute Unnormalized Values:

<!--$$
\delta_{m \in \llbracket u \rrbracket} = 
\begin{cases}
0 & \text{if } m = m_0 \\ 
1 & \text{if } m \in \{ m_1, m_2, m_3, m_4 \}
\end{cases}
$$ -->

<div align="center">
$$
\delta_{m \in \llbracket u \rrbracket} = 
\begin{cases}
0 & \text{if } m = m_0, \\
1 & \text{if } m \in \{ m_1, m_2, m_3, m_4 \}.
\end{cases}
$$
</div>

- $P_{L_0}(m_0 \mid u) = \delta_{m_0 \in \llbracket u \rrbracket} \cdot P(m_0) = 0 \cdot 0.2 = 0$ 
- $P_{L_0}(m_i \mid u) = \delta_{m_i \in \llbracket u \rrbracket} \cdot P(m_i) = 1 \cdot 0.2 = 0.2$  for $i \in \{1, 2, 3, 4\}$

At this stage, these values are **unnormalized scores**.


#### Compute the Denominator When You Normalize

- The sum of unnormalized scores **is the denominator**:

$$
\text{Denominator} = 0.2 + 0.2 + 0.2 + 0.2 = 0.8
$$

#### **Final Step: Normalize to Get Probabilities**

$$
P_{L_0}(m_i \mid u) = \frac{\text{Unnormalized Score}}{\text{Denominator}} = \frac{0.2}{0.8} = 0.25 \quad \text{for } m_i \in \{1, 2, 3, 4\}
$$



#### Option 2: Calculation Using the Full Normalized Equation

$$
P_{L_0}(m \mid u) = \frac{\delta_{m \in \llbracket u \rrbracket} \cdot P(m)}{\displaystyle \sum_{m'} \delta_{m' \in \llbracket u \rrbracket} \cdot P(m')}
$$

#### Compute Numerators:

| Meaning  | $\delta_{m \in \llbracket u \rrbracket}$ | $P(m)$ | Numerator ($\delta \cdot P(m)$) |
|-----------|-------------------------|--------|---------------------------|
| $m_0$     | 0 (ruled out)            | 0.2    | 0                         |
| $m_1$     | 1                        | 0.2    | 0.2                       |
| $m_2$     | 1                        | 0.2    | 0.2                       |
| $m_3$     | 1                        | 0.2    | 0.2                       |
| $m_4$     | 1                        | 0.2    | 0.2                       |

#### Compute Denominator (Normalization Constant):

$$
\displaystyle \sum_{m'} \delta_{m' \in \llbracket u \rrbracket} \cdot P(m') = P(m_1) + P(m_2) + P(m_3) + P(m_4) = 0.2 + 0.2 + 0.2 + 0.2 = 0.8
$$

#### Compute Final Probabilities:

- For $m_0$ (ruled out):  
  $$ P_{L_0}(m_0 \mid u) = 0 $$
- For $m_i$ where $i \in \{1, 2, 3, 4\}$:  
  $$ P_{L_0}(m_i \mid u) = \frac{0.2}{0.8} = 0.25 $$


#### Final Interpretation

| Meaning      | Final Probability $P_{L_0}(m \mid u)$ |
|---------------|--------------------------------------|
| $m_0$: 0 cookies | 0.0 (ruled out)                  |
| $m_1$: 1 cookie  | 0.25                             |
| $m_2$: 2 cookies | 0.25                             |
| $m_3$: 3 cookies | 0.25                             |
| $m_4$: 4 cookies | 0.25                             |

---

#### Example 2: “Alex ate none of the cookies.”

#### Step 1: Define the Possible Meanings $M$

| Meaning      | Description            |
|---------------|------------------------|
| $ m_0 $     | Alex ate 0 cookies     |          
| $ m_1 $     | Alex ate 1 cookie      |          
| $ m_2 $     | Alex ate 2 cookies     |          
| $ m_3 $     | Alex ate 3 cookies     |          
| $ m_4 $     | Alex ate 4 cookies     |          

Assume a **uniform prior**:

$$
P(m_i) = 0.2 \quad \text{for all } i \in \{0, 1, 2, 3, 4\}
$$

#### Step 2: Determine Literal Semantics (Define $\llbracket u \rrbracket$)

Utterance:  
> $ u = $ "Alex ate none of the cookies."

Literal semantics:

$$
\llbracket u \rrbracket = \{ m_0 \}
$$


#### Calculation Using the **Simplified (Proportional) Equation** (option 1)

$$
P_{L_0}(m \mid u) \propto \delta_{m \in \llbracket u \rrbracket} \cdot P(m)
$$

#### Compute Unnormalized Values:

| Meaning  | $\delta_{m \in \llbracket u \rrbracket}$ | $P(m)$ | Unnormalized Score |
|-----------|-----------------------|--------|---------------------|
| $m_0$     | 1 (kept)               | 0.2    | 0.2                 |
| $m_1$–$m_4$ | 0 (ruled out)         | 0.2    | 0                   |

At this stage, the values are **unnormalized scores**.

#### Calculation Using the **Full Normalized Equation** (option 2)

$$
P_{L_0}(m \mid u) = \frac{\delta_{m \in \llbracket u \rrbracket} \cdot P(m)}{\displaystyle \sum_{m'} \delta_{m' \in \llbracket u \rrbracket} \cdot P(m')}
$$

#### Compute the Denominator (Normalization Constant):

$$
\text{Total} = P(m_0) = 0.2
$$

#### Compute Final Probabilities:

- For $m_0$:  
  $$ P_{L_0}(m_0 \mid u) = \frac{0.2}{0.2} = 1.0 $$
- For all other $m_i$:  
  $$ P_{L_0}(m_i \mid u) = 0 \quad \text{for } i \in \{1, 2, 3, 4\} $$

#### Final Interpretation

| Meaning      | Final Probability $P_{L_0}(m \mid u)$ |
|---------------|--------------------------------------|
| $ m_0 $: 0 cookies | 1.0 (certain)                |
| $ m_1 $ to $ m_4 $ | 0.0 (ruled out)               |

---

#### Example 3: “Alex ate all of the cookies.”

#### Step 1: Define the Possible Meanings $M$

| Meaning      | Description            |
|---------------|------------------------|
| $ m_0 $     | Alex ate 0 cookies     |          
| $ m_1 $     | Alex ate 1 cookie      |          
| $ m_2 $     | Alex ate 2 cookies     |          
| $ m_3 $     | Alex ate 3 cookies     |          
| $ m_4 $     | Alex ate 4 cookies     |          

Assume a **uniform prior**:

$$
P(m_i) = 0.2 \quad \text{for all } i \in \{0, 1, 2, 3, 4\}
$$

####  Step 2: Determine Literal Semantics (Define $\llbracket u \rrbracket$)

Utterance:  
> $ u = $ "Alex ate all of the cookies."

Literal semantics:

$$
\llbracket u \rrbracket = \{ m_4 \}
$$

#### Calculation Using the **Simplified (Proportional) Equation** (option 1)

$$
P_{L_0}(m \mid u) \propto \delta_{m \in \llbracket u \rrbracket} \cdot P(m)
$$

#### Compute Unnormalized Values

| Meaning  | $\delta_{m \in \llbracket u \rrbracket}$ | $P(m)$ | Unnormalized Score |
|-----------|-----------------------|--------|---------------------|
| $m_4$     | 1 (kept)               | 0.2    | 0.2                 |
| $m_0$–$m_3$ | 0 (ruled out)         | 0.2    | 0                   |

At this stage, the values are **unnormalized scores**.

#### Calculation Using the **Full Normalized Equation** (option 2)

$$
P_{L_0}(m \mid u) = \frac{\delta_{m \in \llbracket u \rrbracket} \cdot P(m)}{\displaystyle \sum_{m'} \delta_{m' \in \llbracket u \rrbracket} \cdot P(m')}
$$

#### Compute the Denominator (Normalization Constant):

$$
\text{Total} = P(m_4) = 0.2
$$

#### Compute Final Probabilities:

- For $m_4$:  
  $$ P_{L_0}(m_4 \mid u) = \frac{0.2}{0.2} = 1.0 $$
- For all other $m_i$:  
  $$ P_{L_0}(m_i \mid u) = 0 \quad \text{for } i \in \{0, 1, 2, 3\} $$


#### Final Interpretation

| Meaning    |  | Final Probability $P_{L_0}(m \mid u)$ |
|-------------|--|--------------------------------------|
| $ m_4 $: 4 cookies| | 1.0 (certain)                |
| $ m_0 $ to $ m_3 $|   | 0.0 (ruled out)               |

- The simplified equation identifies that only $m_4$ is possible but doesn’t directly provide the final, normalized probability.
- The full equation confirms that after normalization, the listener is **completely certain** the intended meaning is $m_4$.

---

#### What These Examples Show

| Utterance      | Remaining Possible Meanings | Final Distribution |
|----------------|------------------------------|--------------------|
| “Some”         | $ m_1 $ to $ m_4 $            | Evenly distributed (0.25 each) |
| “None”         | $ m_0 $ only                  | Certain (prob = 1) |
| “All”          | $ m_4 $ only                  | Certain (prob = 1) |





#### 4.2.3  A more detailed example based on the full equation (for "Alex ate some of the cookies.")

#### What Are $m$ and $m'$ in the Literal Listener Formula?

$$
P_{L_0}(m \mid u) = \frac{\delta_{m \in \llbracket u \rrbracket} \cdot P(m)}{\displaystyle \sum_{m'} \delta_{m' \in \llbracket u \rrbracket} \cdot P(m')}
$$


| Symbol  | Meaning  |
|---------|----------|
| $m$     | A **specific possible meaning** the listener is considering. Example: "Alex ate 2 cookies." |
| $m'$    | A **placeholder variable** for summing over **all possible meanings**. |

- The numerator computes the contribution of one particular meaning $m$.
- The denominator sums over **all meanings $m'$** to calculate the normalization constant.


#### Example: “Alex ate some of the cookies”

#### Step 1: Define Possible Meanings

| Meaning  | Description              | Prior $P(m)$ |
|-----------|--------------------------|--------------|
| $m_0$     | Alex ate 0 cookies       | 0.2          |
| $m_1$     | Alex ate 1 cookie        | 0.2          |
| $m_2$     | Alex ate 2 cookies       | 0.2          |
| $m_3$     | Alex ate 3 cookies       | 0.2          |
| $m_4$     | Alex ate 4 cookies       | 0.2          |

#### Step 2: Determine Literal Semantics

$$
\llbracket \text{“some”} \rrbracket = \{ m_1, m_2, m_3, m_4 \}
$$

- “Some” means **at least one cookie** was eaten, so $m_0$ is ruled out.

#### Step 3: Compute the Denominator (Normalization)

$$
\sum_{m'} \delta_{m' \in \llbracket u \rrbracket} \cdot P(m') = 1 * P(m_1) + 1 * P(m_2) + 1 * P(m_3) + 1 * P(m_4) 
$$

$$
\text{Total} = 1 * 0.2 + 1 * 0.2 + 1 * 0.2 + 1 * 0.2 = 0.8
$$

#### Step 4: Compute Final Probabilities for Each Meaning

$$
P_{L_0}(m \mid u) = \frac{P(m)}{0.8} \quad \text{if } m \in \llbracket u \rrbracket
$$

| Meaning  | $P_{L_0}(m \mid u)$ Calculation  | Final Probability $P_{L_0}(m \mid u)$  |
|-----------|----------------------------------|-------------------|
| $m_0$     | Ruled out by literal meaning    | 0.0               |
| $m_1$     | $\frac{0.2}{0.8}$               | 0.25             |
| $m_2$     | $\frac{0.2}{0.8}$               | 0.25             |
| $m_3$     | $\frac{0.2}{0.8}$               | 0.25             |
| $m_4$     | $\frac{0.2}{0.8}$               | 0.25             |

- $m$: The **specific meaning** you are evaluating.
- $m'$: The **variable used to sum over all meanings** during normalization.
- The literal listener **rules out incompatible meanings** and redistributes prior beliefs over the remaining possibilities.



#### 4.2.4 Why normalize?
 In the RSA model (and probabilistic modeling more broadly), **normalization** is the process of turning raw or unnormalized scores into a **valid probability distribution** — one where all values are between 0 and 1 and **sum to exactly 1**.  
  
Probabilities must satisfy two conditions: (1) They must be **non-negative**; (2) They must **sum to 1**.    

However, RSA agents (like the Literal Listener or Pragmatic Speaker) often compute values that are **proportional to probabilities**, not properly normalized. So we apply **normalization** to make them valid.  

Normalization is needed whenever probabilities are defined **up to proportionality**.   
Normalization: 
 
 (1) Converts raw scores into valid probabilities   
 (2) Filters and redistributes prior beliefs based on literal truth   
 (3) Is essential for computing meaningful results in RSA and Bayesian models    
 
It is the final — and often implicit — step in probabilistic interpretation.



#### 4.2.5  Summary table

| Symbol                             | Description                                                              |
|------------------------------------|--------------------------------------------------------------------------|
| $ P_{L_0}(m \mid u) $             | Posterior belief about meaning $ m $ after hearing utterance $ u $   |
| $ \llbracket u \rrbracket $       | Literal denotation: set of meanings where $ u $ is true                |
| $ \delta_{m \in \llbracket u \rrbracket} $ | Truth filter: 1 if $ m $ is compatible with $ u $, else 0             |
| $ P(m) $                          | Prior probability of each meaning $ m $                                |


The Literal Listener **does not** reason about why the speaker chose one utterance over another. It simply filters meanings based on:

- Literal truth conditions (defined by $ \llbracket u \rrbracket $)  
- Prior beliefs about what is likely

This **provides the foundation** for higher levels of reasoning in RSA, where more sophisticated listeners and speakers reason about each other recursively.

---

### 4.3 Pragmatic Speaker $ S_1 $

The **Pragmatic Speaker** (denoted as $ S_1 $) models the speaker as a **rational agent** who chooses utterances strategically. The speaker's goal is to:

- Communicate the intended meaning effectively (**informativeness**).
- Minimize production effort or cost (**cost**).

This balances the **Gricean Quantity Maxim** (be informative) and the **Manner Maxim** (avoid unnecessary effort).

#### 4.3.1 The Pragmatic Speaker Formula

#### 1. Simplified (Proportional) Equation

$$
P_{S_1}(u \mid m) \propto \exp \left( \alpha \cdot U(u, m) \right)
$$  where $ U(u, m) = \log P_{L_0}(m \mid u) - \text{cost}(u) $

This means:
> "The probability that the **Pragmatic Speaker** $ S_1 $ will produce utterance $ u $ given that they want to communicate meaning $ m $, is proportional to the exponential of $ \alpha $ times the utility of utterance $ u $ for meaning $ m $."

> This formula defines the speaker's production $ u $ as softmax optimizing $ u $'s utility for communicating $ m $, $ U (u, m) $. 

Meaning of its components
- $ P_{S_1}(u \mid m) $: Probability the speaker chooses utterance $ u $ to communicate meaning $ m $.
- $ \alpha $: Rationality parameter controlling how strongly the speaker optimizes utility.
- $ U(u, m) $: Utility of utterance $ u $ for communicating meaning $ m $.
- **$ \propto $** is read as **“proportional to”**. It is used in equations to express that one quantity **scales with another**, but the exact value is not yet determined — because we still need to compute a normalization step.


- This computes **unnormalized scores** for each utterance $u$.
- $\alpha$ controls how strongly the speaker prefers higher-utility utterances.
- $U(u, m)$ is the **utility** of utterance $u$ for conveying meaning $m$.


#### 2. Full Normalized Equation (Softmax Function)

$$
P_{S_1}(u \mid m) = \frac{\exp \left( \alpha \cdot U(u, m) \right)}{\displaystyle \sum_{u'} \exp \left( \alpha \cdot U(u', m) \right)}
$$

- This computes the final probabilities by normalizing the unnormalized scores.
- The denominator ensures that probabilities **sum to 1**.

---

#### 4.3.2 Understanding Utility $U(u, m)$

The utility function balances **informativeness** and **cost**:

An utterance's utility $ U (u, m) $ is defined as a trade-off between the utterance's **informativeness** as characterized by $ P_{L_0}(m \mid u) $ --how likely it si that a lieral listener will corectly infer $ m $ from $ u $'s literal semantics alone-- and its cost, as defined in the utility function:

$$
U(u, m) = \log P_{L_0}(m \mid u) - \text{cost}(u)
$$

- $ \log P_{L_0}(m \mid u) $: **Informativeness** — how well the literal listener would infer $ m $ from $ u $.
- $ \text{cost}(u) $: **Cost** of producing utterance $ u $ (e.g., effort, complexity, length).

 

#### How Does This Work?

(1) **Informativeness**:  
   - The informativeness term captures the spirit of the Gricean Quantity Maxims (even Relation).
   - If the utterance makes the intended meaning very likely for the literal listener, its utility is high.
   - Example: “All the cookies were eaten” perfectly conveys the state where all cookies are gone.

(2) **Cost**:  
   - The cost term captures the spirit of part of the Gricean Maxim of Mnner: the cheaper (e.g., shorter) the utterance, the better. 
   - Longer or more complex utterances may have higher cost.
   - Example: “Alex ate all four cookies” might be costlier than simply saying “Alex ate all.”

(3) **Balancing**:  
   - The pragmatic speaker prefers utterances that are **informative but low in cost**.
   - If two utterances are equally informative, the speaker prefers the cheaper one.



#### 4.3.3 The Rationality Parameter $\alpha$

 - $ \alpha $ is a utlity-scaling parameter, which governs the extent to which the speaker is a utility-maximizing agent.
  - If $ \alpha = 0 $: The speaker chooses utterances **randomly**.
  - If $ \alpha = 1 $: The speaker chooses utterances **proportionally to utility** (probability matching).
  - If $ \alpha \to \infty $: The speaker ceases to choose utterances probabilistically and always chooses the **utterance with the highest utility** (fully rational).

This softmax function makes the model flexible, allowing for varying levels of rationality in speaker behavior.

To compute pragmatic speaker probabilities, we must set a value for $ \alpha $ and define the cost of utterances. 

| $\alpha$ Value  | Speaker Behavior      |
|-----------------|-----------------------|
| 0               | Random utterance choice. |
| 1               | Probability matches utility. |
| $\to \infty$    | Always chooses the utterance with the highest utility. |


#### 4.3.4 Understanding $\propto$ and Why Normalize?

**$\propto$** means **“proportional to”**.  
  It indicates the values are relative but not yet normalized.

> The probability of choosing utterance \$ u \$ to express meaning \$ m \$ is **proportional to** the exponentiated utility, but this is **not yet the final probability**.

#### Why Normalize?

- Probabilities must sum to **1**.
- The full normalized equation ensures this by dividing unnormalized scores by their total sum.


#### 4.3.5 Worked Example: Cookie Scenario

Suppose the speaker wants to communicate that **Alex ate all the cookies**.

#### Step 1: Compute Literal Listener Beliefs

$$
P_{L_0}(m_4 \mid u_{\text{all}}) = 1.0, \quad P_{L_0}(m_4 \mid u_{\text{some}}) = 0.25
$$

#### Step 2: Compute Utilities

Assume $\text{cost}(u) = 0$ for simplicity.

- $U(u_{\text{all}}, m_4) = \log(1.0) = 0$
- $U(u_{\text{some}}, m_4) = \log(0.25) \approx -1.386$

#### Step 3: Compute Unnormalized Scores (Assume $\alpha = 1$)

- $P_{S_1}(u_{\text{all}} \mid m_4) \propto \exp(1 \cdot 0) = 1$
- $P_{S_1}(u_{\text{some}} \mid m_4) \propto \exp(1 \cdot -1.386) \approx 0.25$


#### Step 4: Normalize

$$
\text{Total} = 1 + 0.25 = 1.25
$$

- $P_{S_1}(u_{\text{all}} \mid m_4) = \frac{1}{1.25} = 0.8$
- $P_{S_1}(u_{\text{some}} \mid m_4) = \frac{0.25}{1.25} = 0.2$

#### Final Interpretation

| Utterance       | Final Probability $P_{S_1}(u \mid m_4)$ |
|-----------------|-----------------------------------------|
| "All"           | 0.8                                     |
| "Some"          | 0.2                                     |

- The speaker is **four times more likely** to say "all" than "some" when Alex ate all the cookies.

#### 4.3.6 Visualizing Speaker Behavior (Figure 2)

<p align="center">
  <img src="/images/figure2Degen2023.png" alt="Figure 2: Pragmatic Speaker Production Probabilities" width="300px">
</p>

- **Y-Axis**: Probability of each utterance.
- **X-Axis**: Rationality parameter $\alpha$.
- As $\alpha$ increases, the speaker increasingly prefers more informative utterances.

#### 4.3.7 A Complete Example: Cookies Scenario**

**Possible Meanings (M):**
- $ m_1 $: Alex ate **all** the cookies.  
- $ m_2 $: Alex ate **some but not all** cookies.  
- $ m_3 $: Alex ate **none** of the cookies.

**Possible Utterances (U):**
- $ u_{\text{some}} $: “Alex ate some cookies.”
- $ u_{\text{all}} $: “Alex ate all the cookies.”

> #### Step 1: Compute Literal Listener’s Belief
> 
> Assume:
> 
> $$
> P_{L_0}(m_1 \mid u_{\text{all}}) = 1.0,\quad P_{L_0}(m_1 \mid u_{\text{some}}) = 0.25
> $$
> 
> This means:
> 
> - “All” perfectly communicates that Alex ate all cookies.
> - “Some” leaves uncertainty.
> 
> #### Step 2: Compute Utility
> 
> Assume cost is zero for simplicity.  
> 
> $$  U(u_{\text{all}}, m_1) = \log(1.0) = 0  $$   
> 
> $$ U(u_{\text{some}}, m_1) = \log(0.25) = -1.386  $$
> 
>  #### Step 3: Compute Production Probabilities (Assume $ \alpha = 1 $)
> 
> $$ P_{S_1}(u_{\text{all}} \mid m_1) \propto \exp(1 \cdot 0) = 1  $$
> 
> $$
> P_{S_1}(u_{\text{some}} \mid m_1) \propto \exp(1 \cdot -1.386) \approx 0.25
> $$
> 
> Normalize:
> 
> $$ P_{S_1}(u_{\text{all}} \mid m_1) = \frac{1}{1 + 0.25} = 0.8   $$
> $$
> P_{S_1}(u_{\text{some}} \mid m_1) = \frac{0.25}{1 + 0.25} = 0.2
> $$
> 
> **Interpretation**:  
> - The speaker is **four times more likely** to say “all” than “some” when Alex ate all cookies.

#### 4.3.8 How to understand Figure 2?

#### **Figure 2: RSA Speaker Production Probabilities**

<p align="center">
  <img src="/images/figure2Degen2023.png" alt="Figure 2: Pragmatic Speaker Production Probabilities" width="300px">
</p>

Figure 2 in Degen (2023) visualizes how the **Pragmatic Speaker's production probabilities** change as a function of the **rationality parameter $\alpha$**, assuming the intended meaning is that Alex ate all the cookies ($m_4$).

#### RSA Model Equation for the Pragmatic Speaker

$$
P_{S_1}(u \mid m) \propto \exp \left( \alpha \cdot U(u, m) \right)
$$

- $U(u, m)$ is the **utility** of utterance $u$ for expressing meaning $m$.
- $\alpha$ controls how strongly the speaker favors high-utility utterances.


#### Utility Calculation

$$
U(u, m) = \log P_{L_0}(m \mid u) - \text{cost}(u)
$$

- For the meaning $m_4$ (Alex ate all cookies):  
  - $P_{L_0}(m_4 \mid u_{\text{all}}) = 1$ (perfectly informative)  
  - $P_{L_0}(m_4 \mid u_{\text{some}}) = 0.25$ (less informative)


#### How to Read the Figure

- **Y-Axis**: Probability of choosing each utterance ($P_{S_1}(u \mid m_4)$).
- **X-Axis**: Value of the rationality parameter $\alpha$.
  - Low $\alpha$: The speaker is less rational and chooses utterances almost randomly.
  - High $\alpha$: The speaker strongly prefers the more informative utterance (“all”).

As $\alpha$ increases, the model predicts the speaker will overwhelmingly prefer to say **“all”** rather than **“some”**.

---

#### What This Demonstrates

- The figure shows the effect of the **softmax function**:  
  Higher utilities lead to higher probabilities, but this relationship is smoothed and modulated by $\alpha$.
- This accounts for graded, probabilistic behavior rather than hard, deterministic choices.
- The RSA model predicts that humans adjust their speech behavior depending on context, goals, and cognitive resources (modeled by $\alpha$).


#### 4.3.8 Understanding $\exp()$ in the Pragmatic Speaker Equation

In the Pragmatic Speaker formula:

$$
P_{S_1}(u \mid m) \propto \exp\left( \alpha \cdot U(u, m) \right)
$$

The $\exp()$ function plays a critical role in transforming **utilities into positive values** suitable for computing probabilities.

---

#### What Does $\exp()$ Mean?

- $\exp(x)$ is the **exponential function**, equivalent to $e^x$, where $e \approx 2.718$.
- It converts utility values (which can be negative or positive) into **positive scores**.
- This ensures that all computed scores for probabilities remain **non-negative**, which is required for valid probability calculations.

---

#### Why Use $\exp()$?

1. **Transforms Utilities into Positive Scores**  
   - Since utilities can be negative, exponentiation ensures that all scores used for probability calculations are positive.

2. **Amplifies Differences Between Utilities**  
   - Larger utilities result in exponentially larger scores, making higher-utility utterances significantly more likely.

3. **Creates Smooth, Graded Probabilities (Softmax Function)**  
   - Even utterances with lower utility still have a non-zero chance of being selected, depending on the value of $\alpha$.

---

#### Example Calculations

| Utility $U(u, m)$  | $\exp(U(u, m))$  | Interpretation |
|--------------------|------------------|----------------|
| 0                  | 1.0              | Baseline value. |
| -1.386             | 0.25             | Lower utility, lower score. |
| 2                  | $\exp(2) \approx 7.389$ | High utility, very large score. |

---

#### Key Takeaways

- $\exp()$ ensures that probabilities are **positive and differentiable**, enabling the use of softmax for probabilistic choices.
- It reflects the intuition that the speaker is exponentially more likely to choose high-utility utterances, but not exclusively.
- This function, combined with $\alpha$, controls how deterministic or probabilistic the speaker’s choices are.

---


#### 4.3.9 Summary Table

| Component          | Meaning                                  |
|--------------------|------------------------------------------|
| $ P_{S_1}(u \mid m) $ | Speaker’s probability of choosing $ u $ given $ m $ |
| $ U(u, m) $       | Utility of utterance $ u $ for meaning $ m $ |
| $ \alpha $        | Rationality parameter controlling how deterministic the speaker is |
| Cost $ \text{cost}(u) $ | Production effort or complexity of the utterance |


In sum, the pragmatic speaker chooses utterances strategically, balancing informativeness and cost. This formalization explains why speakers might sometimes **avoid perfectly informative utterances** when they are costly, or why they might **choose simpler alternatives** when the difference in informativeness is

---

### 4.4 Pragmatic Listener $ L_1 $

The **Pragmatic Listener** in RSA, often denoted as $L_1$, performs **Bayesian inference** to reason about what meaning $m$ the speaker likely intended after hearing the utterance $u$. 

This listener doesn't just rely on literal meaning; it also considers how likely the speaker would have chosen the utterance $u$ under each possible meaning $m$.

#### 4.4.1 Equation for Pragmatic Listener $ L_1 $

#### **1. Simplified (Proportional) Form**

$$
P_{L_1}(m \mid u) \propto P_{S_1}(u \mid m) \cdot P(m)
$$

- This tells us that the posterior belief about meaning $m$ is **proportional** to:
  - The probability that the pragmatic speaker would choose $u$ to express $m$.
  - The prior probability of meaning $m$ before hearing the utterance.

- This equation computes **unnormalized scores**. To turn them into probabilities, we need to normalize.

#### **2. Full Normalized Equation**

$$
P_{L_1}(m \mid u) = \frac{P_{S_1}(u \mid m) \cdot P(m)}{\sum_{m'} P_{S_1}(u \mid m') \cdot P(m')}
$$

- The denominator ensures that the final probabilities **sum to 1**.
- $\sum_{m'}$ sums over all possible meanings $m'$.


#### **Explanation of Components**

| Component                   | Explanation |
|------------------------------|-------------|
| $P_{L_1}(m \mid u)$          | The **posterior probability** that the intended meaning is $m$ after hearing utterance $u$. |
| $P_{S_1}(u \mid m)$          | The **pragmatic speaker’s probability** of choosing utterance $u$ when intending meaning $m$. Computed via softmax over utilities. |
| $P(m)$                       | The **prior probability** of meaning $m$ before hearing any utterance (reflects world knowledge or expectations). |
| Denominator (Normalization)  | Ensures the final probabilities sum to 1 by dividing by the total unnormalized probability mass. |


#### **How Does This Work Conceptually?**

1. The listener hears $u$ and asks:  
   > *“How likely would a rational speaker have said this if they intended each possible meaning?”*

2. The listener also considers how likely each meaning was **before** hearing $u$ (using the prior $P(m)$).

3. Combining these two factors, the listener updates their beliefs and computes the final probabilities over meanings.

#### **Why Are There Two Versions of the Equation?**

| Version       | Purpose          |
|----------------|------------------|
| Proportional  | Used to calculate relative likelihoods before normalization. Efficient for intermediate steps. |
| Normalized    | Produces valid probabilities that sum to 1. Required for final interpretation and reporting results. |




#### 4.4.2 Case Study: Scalar Implicature for "Some" (Likelihood of $m_4$ being true when $u_{\text{some}}$ is heard)

- **Utterance space**:  
  $U = \{ u_{\text{all}}, u_{\text{some}}, u_{\text{none}} \}$
  
- **Possible meanings**:  
  $M = \{ m_0, m_1, m_2, m_3, m_4 \}$  
  - $m_0$: Alex ate 0 cookies  
  - $m_1$: Alex ate 1 cookie  
  - $m_2$: Alex ate 2 cookies  
  - $m_3$: Alex ate 3 cookies  
  - $m_4$: Alex ate all 4 cookies  

- Assume a **uniform prior**:  
  $P(m_i) = 0.2$ for all $i$.

- Utterance heard:  
  $u = u_{\text{some}}$ ("Alex ate some of the cookies.")

#### Step 1: Compute the Pragmatic Speaker’s Probabilities of choosing an utterance when $m_4$ is true [$P_{S_1}(u \mid m_4)$]

#### Literal Listener’s Interpretations:

**For $u_{\text{all}}$**
- $P_{L_0}(m_4 \mid u_{\text{all}}) = \delta_{m_4 \in \llbracket u_{\text{all}} \rrbracket} \cdot P(m_4) = 1 \cdot 0.2 = 0.2 $ (This is Unnormalized probability)

Normalization Step

$$
\sum_{m'} \delta_{m' \in \llbracket u_{\text{all}} \rrbracket} \cdot P(m') = P(m_4) = 0.2
$$

Final probability:

$$
P_{L_0}(m_4 \mid u_{\text{all}}) = \frac{0.2}{0.2} = 1.0
$$

>> Step-by-Step Expansion

- Recall that $\llbracket u_{\text{all}} \rrbracket = \{ m_4 \}$, because the utterance "all" is only literally true if Alex ate all the cookies.

- So the indicator function $\delta_{m' \in \llbracket u_{\text{all}} \rrbracket}$ evaluates as:

| $m'$   | $\delta_{m' \in \llbracket u_{\text{all}} \rrbracket}$ | $P(m')$ | Contribution |
|---------|------------------------------------------------------|---------|--------------|
| $m_0$   | 0 (ruled out)                                        | 0.2     | $0 \cdot 0.2 = 0$ |
| $m_1$   | 0 (ruled out)                                        | 0.2     | $0 \cdot 0.2 = 0$ |
| $m_2$   | 0 (ruled out)                                        | 0.2     | $0 \cdot 0.2 = 0$ |
| $m_3$   | 0 (ruled out)                                        | 0.2     | $0 \cdot 0.2 = 0$ |
| $m_4$   | 1 (kept)                                              | 0.2     | $1 \cdot 0.2 = 0.2$ |

- Summing all contributions:

$$
\text{Total} = 0 + 0 + 0 + 0 + 0.2 = 0.2
$$


**For $u_{\text{some}}$**
- $P_{L_0}(m_4 \mid u_{\text{some}}) = 0.25$

--- 


#### Utility Calculation:

Using $U(u, m) = \log P_{L_0}(m \mid u)$ and assuming no cost:

- $U(u_{\text{all}}, m_4) = \log(1) = 0$  
- $U(u_{\text{some}}, m_4) = \log(0.25) \approx -1.386$

#### Compute $P_{S_1}(u \mid m_4)$:

- Unnormalized:
  - $P_{S_1}(u_{\text{all}} \mid m_4) \propto \exp(0) = 1$
  - $P_{S_1}(u_{\text{some}} \mid m_4) \propto \exp(-1.386) \approx 0.25$

- Normalize:
  - Total = $1 + 0.25 = 1.25$
  - $P_{S_1}(u_{\text{all}} \mid m_4) = \frac{1}{1.25} = 0.8$
  - $P_{S_1}(u_{\text{some}} \mid m_4) = \frac{0.25}{1.25} = 0.2$


#### Step 2: Compute the Pragmatic Listener’s Posterior $P_{L_1}(m \mid u_{\text{some}})$

Apply Bayes’ Rule:

$$
P_{L_1}(m \mid u_{\text{some}}) \propto P_{S_1}(u_{\text{some}} \mid m) \cdot P(m)
$$

Compute unnormalized scores for all meanings:

| Meaning  | $P_{S_1}(u_{\text{some}} \mid m)$ | $P(m)$ | Product |
|-----------|-------------------------------|--------|---------|
| $m_0$     | 0 (ruled out by literal meaning) | 0.2    | 0.0     |
| $m_1$     | Assume 0.4                       | 0.2    | 0.08    |
| $m_2$     | Assume 0.3                       | 0.2    | 0.06    |
| $m_3$     | Assume 0.2                       | 0.2    | 0.04    |
| $m_4$     | 0.2 (computed above)              | 0.2    | 0.04    |

Total sum = $0.08 + 0.06 + 0.04 + 0.04 = 0.22$

#### Final Posterior Probabilities:

| Meaning  | Final $P_{L_1}(m \mid u_{\text{some}})$ |
|-----------|---------------------------------------|
| $m_0$     | 0.0 (ruled out)                       |
| $m_1$     | $\frac{0.08}{0.22} \approx 0.364$     |
| $m_2$     | $\frac{0.06}{0.22} \approx 0.273$     |
| $m_3$     | $\frac{0.04}{0.22} \approx 0.182$     |
| $m_4$     | $\frac{0.04}{0.22} \approx 0.182$     |


#### **Interpretation**

- After hearing "some of the cookies were eaten," the listener assigns the highest probability to $m_1$ (Alex ate only 1 cookie).
- Although $m_4$ is possible, it’s less likely because if Alex had eaten all the cookies, the speaker would have likely said “all” instead.
- This demonstrates how the RSA model formally derives the **scalar implicature** that “some” often implies “not all.”

---

### V. A complete illustration of pragmatic reasoning in RSA
This section, building on the previous sections, offers a complete demonstration of how listensers interpret scalar utterances, like "Alex ate some of the cookies."

#### Common Setup and Assumptions

| Meaning      | Description            | Prior $P(m)$ |
|---------------|------------------------|--------------|
| $m_0$         | Alex ate 0 cookies     | 0.2          |
| $m_1$         | Alex ate 1 cookie      | 0.2          |
| $m_2$         | Alex ate 2 cookies     | 0.2          |
| $m_3$         | Alex ate 3 cookies     | 0.2          |
| $m_4$         | Alex ate 4 cookies     | 0.2          |

Utterance space:

$$
U = \{ u_{\text{none}}, u_{\text{some}}, u_{\text{all}} \}
$$

Literal Semantics:

- $\llbracket u_{\text{none}} \rrbracket = \{ m_0 \}$
- $\llbracket u_{\text{some}} \rrbracket = \{ m_1, m_2, m_3, m_4 \}$
- $\llbracket u_{\text{all}} \rrbracket = \{ m_4 \}$

Assume **$\alpha = 1$** and **$\text{cost}(u) = 0$** for all utterances.


#### REASONING LEVEL #1 **Literal Listener ($L_0$)**

#### Step 1: Apply the Full Equation

$$
P_{L_0}(m \mid u_{\text{some}}) = \frac{\delta_{m \in \llbracket u_{\text{some}} \rrbracket} \cdot P(m)}{\displaystyle \sum_{m'} \delta_{m' \in \llbracket u_{\text{some}} \rrbracket} \cdot P(m')}
$$  

Compute Denominator:

$$
\text{Total} = 0.2 + 0.2 + 0.2 + 0.2 = 0.8
$$

Compute Final Probabilities:

- $P_{L_0}(m_0 \mid u_{\text{some}}) = 0$
- $P_{L_0}(m_i \mid u_{\text{some}}) = \frac{0.2}{0.8} = 0.25$ for $i \in \{1, 2, 3, 4\}$

#### $L_0$ Final Belief Distribution

| Meaning      | $P_{L_0}(m \mid u_{\text{some}})$ |
|---------------|----------------------------|
| $m_0$         | 0.0 (ruled out)             |
| $m_1$         | 0.25                        |
| $m_2$         | 0.25                        |
| $m_3$         | 0.25                        |
| $m_4$         | 0.25                        |


#### REASONING LEVEL #2 **Pragmatic Speaker ($S_1$)**

The speaker reasons about how the Literal Listener interprets utterances to decide which utterance to produce.

#### Step 1: Compute Utility for Each Utterance When Meaning = $m_4$

Using:

$$
U(u, m) = \log P_{L_0}(m \mid u) - \text{cost}(u)
$$

| Utterance        | $P_{L_0}(m_4 \mid u)$ | $U(u, m_4)$         |
|------------------|------------------------|---------------------|
| $u_{\text{all}}$ | 1.0                    | $\log(1) = 0$       |
| $u_{\text{some}}$| 0.25                   | $\log(0.25) = -1.386$|
| $u_{\text{none}}$| 0 (ruled out)           | $-\infty$            |

#### Step 2: Compute Unnormalized Scores

$$
P_{S_1}(u \mid m_4) \propto \exp\left( \alpha \cdot U(u, m_4) \right)
$$

| Utterance        | $\exp(\alpha \cdot U)$ | Unnormalized Score |
|------------------|------------------------|--------------------|
| $u_{\text{all}}$ | $\exp(0) = 1$          | 1.0                |
| $u_{\text{some}}$| $\exp(-1.386) \approx 0.25$ | 0.25            |
| $u_{\text{none}}$| 0                      | 0                  |

Total Sum = $1 + 0.25 = 1.25$

#### Step 3: Normalize to Get Final Speaker Probabilities

- $P_{S_1}(u_{\text{all}} \mid m_4) = \frac{1}{1.25} = 0.8$
- $P_{S_1}(u_{\text{some}} \mid m_4) = \frac{0.25}{1.25} = 0.2$


#### $S_1$ Final Production Probabilities (Given $m_4$)

| Utterance        | $P_{S_1}(u \mid m_4)$ |
|------------------|-----------------------|
| "All"            | 0.8                   |
| "Some"           | 0.2                   |
| "None"           | 0                     |


#### REASONING LEVEL #3 **Pragmatic Listener ($L_1$)**

The listener now reasons about what meaning the speaker most likely intended after hearing the utterance.

#### Step 1: Apply the Full Equation

$$
P_{L_1}(m \mid u_{\text{some}}) = \frac{P_{S_1}(u_{\text{some}} \mid m) \cdot P(m)}{\displaystyle \sum_{m'} P_{S_1}(u_{\text{some}} \mid m') \cdot P(m')}
$$  

#### Step 2: Compute $P_{S_1}(u_{\text{some}} \mid m)$ for All Meanings

We already computed this for $m_4$:

- $P_{S_1}(u_{\text{some}} \mid m_4) = 0.2$

Assume for this example:

| Meaning    | $P_{S_1}(u_{\text{some}} \mid m)$ |
|------------|-----------------------------------|
| $m_0$      | 0 (ruled out by literal semantics)|
| $m_1$      | 0.4                               |
| $m_2$      | 0.3                               |
| $m_3$      | 0.2                               |
| $m_4$      | 0.2                               |

#### Step 3: Compute Numerator and Denominator

| Meaning  | $P_{S_1}(u_{\text{some}} \mid m)$ | $P(m)$ | Product |
|-----------|-------------------------------|--------|---------|
| $m_0$     | 0                             | 0.2    | 0       |
| $m_1$     | 0.4                           | 0.2    | 0.08    |
| $m_2$     | 0.3                           | 0.2    | 0.06    |
| $m_3$     | 0.2                           | 0.2    | 0.04    |
| $m_4$     | 0.2                           | 0.2    | 0.04    |

Denominator (Normalization Constant):  
$$
\text{Total} = 0.08 + 0.06 + 0.04 + 0.04 = 0.22
$$

#### Step 4: Compute Final $L_1$ Posterior Beliefs

- $P_{L_1}(m_1 \mid u_{\text{some}}) = \frac{0.08}{0.22} \approx 0.364$
- $P_{L_1}(m_2 \mid u_{\text{some}}) = \frac{0.06}{0.22} \approx 0.273$
- $P_{L_1}(m_3 \mid u_{\text{some}}) = \frac{0.04}{0.22} \approx 0.182$
- $P_{L_1}(m_4 \mid u_{\text{some}}) = \frac{0.04}{0.22} \approx 0.182$
- $P_{L_1}(m_0 \mid u_{\text{some}}) = 0$

#### $L_1$ Final Interpretation

| Meaning    | $P_{L_1}(m \mid u_{\text{some}})$ |
|--------------|------------------------------|
| $m_0$: 0 cookies | 0.0 (ruled out)            |
| $m_1$: 1 cookie  | 0.364                      |
| $m_2$: 2 cookies | 0.273                      |
| $m_3$: 3 cookies | 0.182                      |
| $m_4$: 4 cookies | 0.182                      |


#### **Overall Takeaways**

| Agent        | Main Process          |
|---------------|----------------------|
| $L_0$         | Filters meanings based on literal truth. |
| $S_1$         | Chooses utterances to maximize utility.  |
| $L_1$         | Infers intended meaning based on the utterance and speaker model. |

- Each level of reasoning in the RSA model refines the interpretation process using both **prior knowledge** and **rational inference**.


---

### VI. Reference Games
This section presents how RSA explains language production and comprehension in Reference Games based on Franke & Jäger (2016). 

### 5.1 What Are Reference Games?

**Reference Games** are simplified experimental tasks designed to study how speakers choose expressions to refer to objects and how listeners interpret those expressions.

#### Key Features of Reference Games

- **Interactive Setting**: Involves a speaker and a listener.
- **Goal**:  
  - The speaker must communicate a specific referent (target object) to the listener.  
  - The listener must infer which object the speaker is referring to based on the utterance.

#### Typical Experimental Setup
Here is an example: 

<p align="center">
  <img src="/images/referencegameexample.png" alt="Reference Game Example" width="600px">
</p>

- Objects in Context:  
  Example:  
  - Green Square  
  - Green Circle  
  - Blue Circle  

- Possible Utterances:  
  - "green"  
  - "square"  
  - "circle"
  - "blue"  

Task:   
**If the target is the *Green Square*, should the speaker say "green" or "square"?**  
    - "Square" is more **informative** because it uniquely identifies the referent.

#### Connection to Gricean Maxims

- **Maxim of Quantity**: Be as informative as required.  
  → Speakers prefer utterances that best help the listener identify the referent.

- **Maxim of Manner**: Avoid unnecessary effort.  
  → Speakers also tend to avoid overly complex or costly expressions.

#### What Makes Reference Games Powerful?

- They provide a simple, controlled environment for testing:
  - How speakers balance **informativeness** and **production cost**.
  - How listeners reason about speaker choices (**pragmatic inference**).
- Reference games form the foundation for formal models of language use like the **RSA model**.


### 5.2 Reference Games — Formal Modeling

In this section, we explore how the RSA model accounts for reasoning in reference games, following the mathematical formalizations used in **Franke & Jäger (2016)**.

#### 1. Literal Listener ($L_0$)
$$
P_{\text{literal}}(r \mid p) = 
\begin{cases}
\frac{1}{|\{r' : p \text{ is true of } r'\}|} & \text{if } p \text{ is true of } r \\\\
0 & \text{otherwise}
\end{cases}
$$

- This assigns **uniform probability** over all referents that literally satisfy the utterance.
- The Literal Listener does **not** consider why the speaker chose this utterance—only whether it’s true of a referent.


#### Explanation of Formula Components
- $r$: Referent (target object)  
- $p$: Property or utterance  
- $\{ r' : p \text{ is true of } r' \}$  
  → This is the **set of all referents** for which the property $p$ holds true.  
  *Example*: If $p$ is "green", this set contains all green objects.

- $|\{ r' : p \text{ is true of } r' \}|$  
  → This is the **size of that set**, i.e., how many referents have the property $p$.

- $\frac{1}{|\{ \dots \}|}$  
  → This means that **each compatible referent is assigned equal probability**, based on the total number of compatible referents.

- $\text{if } p \text{ is true of } r$  
  → This part of the case condition says that the formula only applies if $r$ is actually compatible with the utterance $p$.



#### What Does $r'$ Represent?
| Symbol  | Meaning                         |
|---------|---------------------------------|
| $r$     | The specific referent the listener is considering. |
| $r'$    | A variable representing **all possible referents** in the context. Used for counting how many referents are compatible with the utterance. |

- The notation $\{ r' : p \text{ is true of } r' \}$ defines the set of **all referents where the utterance $p$ is literally true**.
- The term $| \dots |$ counts how many referents are in that set.

> #### **Example: Listener Hears “green”**
> | Referent | Properties        |
> |----------|-------------------|
> | $r_1$    | Green, Square     |
> | $r_2$    | Green, Circle     |
> | $r_3$    | Blue, Circle      |
>
> - $\{ r' : p = \text{"green"} \text{ is true of } r' \} = \{ r_1, r_2 \}$  
> - $|\{ \dots \}| = 2$
>
> #### Compute Probabilities:
>
> - $P_{\text{literal}}(r_1 \mid \text{"green"}) = \frac{1}{2} = 0.5$
> - $P_{\text{literal}}(r_2 \mid \text{"green"}) = 0.5$
> - $P_{\text{literal}}(r_3 \mid \text{"green"}) = 0$



#### 2. Pragmatic Speaker ($S_1$)

$$
P_{prod}(p \mid r; \lambda, f) = 
\frac{\exp\left(\lambda \cdot EU_{speaker}(r, p; f)\right)}{\sum_{p'} \exp\left(\lambda \cdot EU_{speaker}(r, p'; f)\right)}
$$

- $ EU_{speaker}(r, p; f) = P_{literal}(r \mid p) + f(p) $
- $f(p)$: Utterance bias or cost  
- $\lambda$: Rationality parameter (inverse temperature)


#### 3. Pragmatic Listener ($L_1$)

$$
P_{\text{comp}}(r \mid p) = \frac{P(r) \cdot P_{\text{prod}}(p \mid r)}{\sum_{r'} P(r') \cdot P_{\text{prod}}(p \mid r')}
$$


#### 5.3 Further break-downs of the mathematical notations in Franke & Jager (2016) and Degen (2023)

#### Literal Listener: Notation Comparison

| Concept                        | Franke & Jäger (2016)                              | Degen (2023)                                     |
|-------------------------------|----------------------------------------------------|--------------------------------------------------|
| Agent                         | $P_{\text{literal}}(r \mid p)$                     | $P_{L_0}(m \mid u)$                              |
| Meaning / Referent            | $r$ = referent                                     | $m$ = meaning                                    |
| Utterance                     | $p$ = property                                     | $u$ = utterance                                  |
| Literal Semantics             | $p$ is true of $r$                                 | $m \in \llbracket u \rrbracket$                 |
| Truth Filter                  | Verbal condition                                   | Indicator: $\delta_{m \in \llbracket u \rrbracket}$ |
| Uniformity                    | Uniform over compatible referents                 | Prior $P(m)$ allows non-uniformity              |
| Normalization                 | Divide by number of compatible referents           | Sum over priors of compatible meanings          |

#### Key Takeaways

- Both formulations implement literal semantics: they restrict attention to meanings that are literally compatible with the utterance.
- Degen’s version allows more **Bayesian flexibility** and incorporates **world knowledge via priors**.
- Franke & Jäger’s approach is useful for **simple reference tasks** with uniform assumptions.


### 5.4 Literal Listener
*(Based on Franke & Jäger, 2016)*

#### Step 1: Understand the Task Setup

| Object   | Color  | Shape   |
|-----------|--------|---------|
| $r_1$     | Green  | Square  |
| $r_2$     | Green  | Cirle  |
| $r_3$     | Blue   | Circle  |

*Possible Utterances (Properties)*: 

$p \in \\\{ "green", "circle", "square", "blue" \\\}$


#### How Does the Literal Listener Interpret an Utterance?

The Literal Listener reasons **purely based on literal semantics**, without considering why the speaker chose a particular utterance.

#### Formula:

$$
P_{\text{literal}}(r \mid p) = 
\begin{cases}
\frac{1}{|\{ r' : p \text{ is true of } r' \}|} & \text{if } p \text{ is true of } r \\\\
0 & \text{otherwise}
\end{cases}
$$

- If the utterance $p$ is true of object $r$, assign **equal probability** among all such objects.
- Otherwise, assign probability $0$.


#### Example 1: Listener Hears “green”

1. Determine which objects that are compatible with the property "green":  
   → $r_1$ (Green Square), $r_2$ (Green Circle)

2. Assign Probabilities:
| Referent | Compatible with "green"? | $P_{\text{literal}}(r \mid p = \text{"green"})$ |
|-----------|--------------------------|----------------------------|
| $r_1$     | Yes                      | 0.5                        |
| $r_2$     | Yes                      | 0.5                        |
| $r_3$     | No                       | 0                          |

> - $\{ r' : p = \text{"green"} \text{ is true of } r' \} = \{ r_1, r_2 \}$  
> - $|\{ \dots \}| = 2$
>
> #### Compute Probabilities:
>
> - $P_{\text{literal}}(r_1 \mid \text{"green"}) = \frac{1}{2} = 0.5$
> - $P_{\text{literal}}(r_2 \mid \text{"green"}) = \frac{1}{2} = 0.5$
> - $P_{\text{literal}}(r_3 \mid \text{"green"}) = 0$


#### Example 2: Listener Hears “square”

1. Determine which objects are compatible with the property "square":  
   → Only $r_1$.

2. Assign Probabilities:
| Referent | Compatible with "square"? | $P_{\text{literal}}(r \mid p = \text{"square"})$ |
|-----------|--------------------------|----------------------------|
| $r_1$     | Yes                       | $1.0$                          |
| $r_2$     | No                      | $0$                        |
| $r_3$     | No                       | $0$                          |

> - $\{ r' : p = \text{"square"} \text{ is true of } r' \} = \{ r_1 \}$  
> - $ |\{ \dots \}| = 1 $
>
> #### Compute Probabilities:
>
> - $P_{\text{literal}}(r_1 \mid \text{"square"}) = \frac{1}{1} = 1.0$
> - $P_{\text{literal}}(r_2 \mid \text{"square"}) = 0$
> - $P_{\text{literal}}(r_3 \mid \text{"square"}) = 0$

#### Example 3: Listener Hears “blue”

1. Determine which objects are compatible with the property "square":  
   → Only $r_1$.

2. Assign Probabilities:
| Referent | Compatible with "square"? | $P_{\text{literal}}(r \mid p = \text{"square"})$ |
|-----------|--------------------------|----------------------------|
| $r_1$     | No                       | $0.0$                          |
| $r_2$     | No                      | $0$                        |
| $r_3$     | Yes                       | $1.0$                          |

> - $\{ r' : p = \text{"blue"} \text{ is true of } r' \} = \{ r_3 \}$  
> - $ |\{ \dots \}| = 1 $
>
> #### Compute Probabilities:
>
> - $P_{\text{literal}}(r_1 \mid \text{"square"}) = 0$
> - $P_{\text{literal}}(r_2 \mid \text{"square"}) = 0$
> - $P_{\text{literal}}(r_3 \mid \text{"square"}) = \frac{1}{1} = 1.0$


### 5.5 Pragmatic Speaker

$$
P_{prod}(p \mid r; \lambda, f) = 
\frac{\exp\left( \lambda \cdot EU_{speaker}(r, p; f) \right)}{\displaystyle \sum_{p'} \exp\left( \lambda \cdot EU_{speaker}(r, p'; f) \right)}
$$

where $EU_{speaker}(r, p; f)$ is **Utility Function**:

$$
EU_{speaker}(r, p; f) = P_{literal}(r \mid p) + f(p)
$$  

- $P_{literal}(r \mid p)$: How likely is it that a literal listener will pick referent $r$ after hearing $p$?  
- $f(p)$: Cost or bias term, penalizing utterances that are long, complex, or dispreferred.


#### **Explanation of Components**

| Symbol             | Explanation                                  |
|--------------------|----------------------------------------------|
| $p$                | Property (utterance).                        |
| $r$                | Referent (target object).                    |
|$P_{prod} (p \mid r; \lambda, f)$     |Probability of Pragmatic Speaker choosing a property/utterance|
| $\lambda$          | Rationality parameter (speaker’s sensitivity to utility differences). |
| $f(p)$              | Cost or bias associated with utterance $p$. |
| $ EU_{speaker}$ | Expected utility of utterance $p$ for referent $r$. |


**_Combine the two_**

$$ P_{prod}(p \mid r; \lambda, f) = 
\frac{\exp\left( \lambda \cdot EU_{speaker}(r, p; f) \right)}{\displaystyle \sum_{p'} \exp\left( \lambda \cdot EU_{speaker}(r, p'; f) \right)} = \frac{\exp\left( \lambda \cdot (P_{literal}(r \mid p) + f(p)) \right)}{\displaystyle \sum_{p'} \exp\left( \lambda \cdot (P_{literal}(r \mid p') + f(p')) \right)}
$$

#### **Worked Example**
Scenario:

| Object   | Color  | Shape   |
|-----------|--------|---------|
| $r_1$     | Green  | Square  |
| $r_2$     | Green  | Circle  |
| $r_3$     | Blue   | Circle  |

  - Target referent $r = r_1$ (Green Square).  
  - Utterance/Property space: "green", "square". (**Note that we limit the utterance choices to be of only "green" and "square"** which are literally true of "Green Square") 

> Note that the set of utterances to choose from matters in final Speaker's probability in choosing which utterance to use
> - $u_1 \in \\\{ "green", "square" \\\}$
> - $u_2 \in \\\{ \text{"green"}, \text{"square"}, \text{"circle"}, \text{"blue"} \\\}$
> 
> #### why the two $u$ sets?
> They lead to different Speaker's probabilities in choosing utterances to refer to a particular referent. 
> **in the $u_2$ option, those semantically incompatible/literally false utterances/properties were also assigned probabilities**.
>
> #### Should False Utterances Be Included?
> #### Option 1: Full Utterance Set (Even Non-True Ones)    
> Assumption:   
> Speakers can, and sometimes do, use suboptimal or false utterances.
> #### Model Characteristics:
> 
> - All utterances in the property space are **included**, regardless of literal truth.
> - Even non-true properties like `"blue"` (for a green object) receive **non-zero probability**, though down-weighted.
> - Matches the **default RSA formulation** as used in:
>   - *Franke & Jäger (2016)*
>   - *Goodman & Frank (2016)*
> #### When to Use:
> 
> - You want to model **noisy, probabilistic human behavior**.
> - You're studying **psycholinguistic behavior**, overinformativeness, or slips.
> - You're interested in **graded inference** and **soft competition**.
> ---
> #### Option 2: Restricted Utterance Set (Only True Properties)
> #### Assumption:
> Speakers are always semantically competent and never use false utterances.
> 
> #### Model Characteristics:
> - The utterance set is **filtered** to include only properties that are literally true of the referent.
> - Softmax normalization is applied **only over true utterances**.
> - Produces **sharper speaker preferences** and downstream listener inference.
> #### When to Use:
> - You're modeling **idealized agents** in formal semantics or decision theory.
> - Your research assumes **strict informativeness**.
> - You're simulating **maximally rational communication**.




**_Speaker production probabilities calculation_**  
*Step 1: Assume:*
  - $\lambda = 1$ (moderate rationality).
  - $f(p) = 0$ (no production cost).  


*Step 2: Compute $P_{literal}(r \mid p)$*

  - Literal Listener for $"green"$:

    - Compatible referents: $r_1$, $r_2$.  
    - $P_{\text{literal}}(r_1 \mid \text{"green"}) = \frac{1}{2} = 0.5$

  - Literal Listener for $"square"$:

    - Only $r_1$ is a square.  
    - $P_{literal}(r_1 \mid {"square"}) = 1.0$


*Step 3: Compute Utility for Each Utterance*

   $EU_{speaker}(r_1, "green"; f) = P_{literal}(r_1 \mid "green") + f("green") = 0.5 + 0 = 0.5$  
   $EU_{speaker}(r_1, "square"; f) = P_{literal}(r_1 \mid "square") + f("square") = 1.0 + 0 = 1.0$

*Step 4: Compute Unnormalized Scores* Using $\exp\left(\lambda \cdot EU_{speaker}(r, p; f)\right) $:

  - $ \exp\left(\lambda \cdot  EU_{speaker}(r_1, "green"; f) \right) = \exp(1 \cdot 0.5) = \exp(0.5) \approx 1.649$  
  - $\exp\left(\lambda \cdot EU_{speaker}(r_1, "square"; f) \right) = \exp(1 \cdot 1.0) = \exp(1) \approx 2.718$

> **What Does $\exp(0.5)$ Mean?**
> - $\exp(x)$ is the **exponential function**, defined as:
>
> $ \exp(x) = e^x $
>
> - Where **$e \approx 2.71828$** is $Euler’s$ number, a fundamental constant in mathematics.
>
> **Why Is This Important in RSA?**
> - The exponential function **transforms utility values into positive scores**.
> - It ensures that higher-utility utterances lead to higher scores in the **softmax calculation** for final probabilities.
> - Without exponentiation, negative utilities could produce invalid (negative) probabilities.
>
> #### **Quick Reference Table**
> | Utility $EU(p, r)$ | $\exp(EU)$   | Interpretation         |
> |--------------------|-------------|------------------------|
> | 0                  | 1.0         | Baseline utility.      |
> | 0.5                | 1.649       | Moderately high utility. |
> | 1.0                | 2.718       | High utility.          |
> | -1.386             | 0.25        | Low utility (as in $\log(0.25)$). |


*Step 5: Normalize to Get Final Probabilities*

$ Total = \exp\left( \lambda \cdot EU_{speaker}(r_1, green'; f) \right) + \exp\left( \lambda \cdot EU_{speaker}(r_1, square'; f) \right) =1.649 + 2.718 = 4.367 $

  - $P_{prod}({"green"} \mid r_1) = \frac{\exp\left( \lambda \cdot EU_{speaker}(r_1, "green"; f) \right)}{\sum_{p'} \exp\left( \lambda \cdot EU_{speaker}(r, p'; f) \right)} =
  \frac{1.649}{4.367} \approx 0.378$  
  - $P_{\text{prod}}(\text{"square"} \mid r_1) = \frac{\exp\left( \lambda \cdot EU_{speaker}(r_1, "square"; f) \right)}{\sum_{p'} \exp\left( \lambda \cdot EU_{speaker}(r, p'; f) \right)} = \frac{2.718}{4.367} \approx 0.622$



#### Final Interpretation

| Utterance    | $P_{\text{prod}}(p \mid r_1)$ |
|---------------|------------------------------|
| "green"       | 0.378 (38%)                  |
| "square"      | 0.622 (62%)                  |

  - These are the Pragmatic Speaker's probabilities in choosing "green" or "square" to refer to $r_1$  (Green Square)
  - The speaker prefers "square" but still sometimes chooses "green".
  - This reflects probabilistic, graded behavior rather than deterministic selection.


#### **Key Insights**

  - **Higher Utility → Higher Probability**  
    But not necessarily 100%, depending on $\lambda$.

  - **Effect of $\lambda$**:
    - If $\lambda = 0$, the speaker would choose "green" and "square" randomly.
    - If $\lambda \to \infty$, the speaker would always choose "square".

  - **Effect of Cost $f(p)$**:
    - If "square" had a higher cost, the speaker might prefer "green" despite its lower informativeness.

---

### 5.6 Pragmatic Listener

In the RSA model, the **pragmatic listener** ($L_1$) updates beliefs about the speaker’s intended referent based on the utterance they receive. This is done using **Bayes' Rule** and the listener’s model of the speaker.

$$
P_{comp}(\text{choose } r \mid \text{receive } p;\ \lambda, f) = \frac{P(r) \cdot P_{prod}(p \mid r;\ \lambda, f)}{\displaystyle \sum_{r'} P(r') \cdot P_{prod}(p \mid r';\ \lambda, f)}
$$

#### Explanation of Components

| Symbol                         | Meaning                                                      |
|--------------------------------|---------------------------------------------------------------|
| $r$                            | A possible referent (object)                                  |
| $p$                            | The utterance (property) received from the speaker            |
| $P(r)$                         | Prior probability of referent $r$                             |
| $P_{prod}(p \mid r;\ \lambda, f)$ | Probability that a speaker with parameters $(\lambda, f)$ would produce $p$ when referring to $r$ |
| $\lambda$                      | Rationality parameter (how optimally the speaker chooses)     |
| $f(p)$                         | Cost or bias associated with producing utterance $p$          |
| $r'$                           | Variable over all referents used to normalize the distribution|


#### Intuition

> The listener **reasons backward**:  
> “If the speaker chose to say $p$, which referent $r$ would make that utterance most likely—assuming they were optimizing utility using $\lambda$ and $f$?”

This is a form of **Bayesian social reasoning**:  
- The listener assumes the speaker is rational (to some degree),
- and uses this model to infer likely referents.


#### Example

***Referents***

| Code  | Description      |
|--------|------------------|
| $r_1$ | Green Square     |
| $r_2$ | Green Circle     |
| $r_3$ | Blue Circle      |

Possible utterances (utterance space): "green", "square", "circle", "blue"  

*Step 1: Assumed Prior*

Uniform prior:  $ P(r_1) = P(r_2) = P(r_3) = \frac{1}{3} $


*Step 2: calculate Pragmatic Speaker's Probability of choosing "green" for each of three referent* 
(using λ = 1, no cost bias $f(p) = 0$):
 
> **1. probability of intending $r_1$ (green square)** for each option in the utterance/property space
> #### Step 1: Literal Listener Probabilities
> 
> - $P_{literal}(r_1 \mid \text{"green"}) = \frac{1}{2} = 0.5$  
> - $P_{literal}(r_1 \mid \text{"square"}) = 1.0$  
> - $P_{literal}(r_1 \mid \text{"circle"}) = 0$
> - $P_{literal}(r_1 \mid \text{"blue"}) = 0$
>
> #### Step 2: Pragmatic Speaker Probabilities
> 
> The formula of Pragmatic Speaker is:
$$ P_{prod}(p \mid r; \lambda, f) =  \frac{\exp\left( \lambda \cdot EU_{speaker}(r, p; f) \right)}{\sum_{p'} \exp\left( \lambda \cdot EU_{speaker}(r, p'; f) \right)} = \frac{\exp\left( \lambda \cdot (P_{literal}(r \mid p) + f(p)) \right)}{\sum_{p'} \exp\left( \lambda \cdot (P_{literal}(r \mid p') + f(p')) \right)}
$$
>
> #### step 2.1: Compute $EU$ Values
> - $EU(r_1, \text{"green"; f}) = P_{literal}(r_1 \mid "green") + f("green") = 0.5 + 0 = 0.5$    
> - $EU(r_1, \text{"square"}; f) = P_{literal}(r_1 \mid "green") + f(p) = 1.0 + 0 = 1.0$  
> - $EU(r_1, \text{"circle"}; f) = P_{literal}(r_1 \mid "green") + f(p) = 0 + 0 = 0$
> - $EU(r_1, \text{"blue"}; f) = P_{literal}(r_1 \mid "blue") + f(p) = 0 + 0 = 0$
>
> #### Step 2.2: Exponentiate and Normalize
> Exponentiate:
> - $\exp\left( \lambda \cdot EU_{speaker}(r_1, "green"; f) \right) = \exp(1 \cdot 0.5) = \exp(0.5)\approx 1.649$  
> - $\exp\left( \lambda \cdot EU_{speaker}(r_1, "square"; f) \right) = \exp(1 \cdot 1.0) = \exp(1)\approx 2.718$  
> - $\exp\left( \lambda \cdot EU_{speaker}(r_1, "circle"; f) \right) = \exp(1 \cdot 0) = \exp(0) = 1.0$
> - $\exp\left( \lambda \cdot EU_{speaker}(r_1, "blue"; f) \right) = \exp(1 \cdot 0) = \exp(0) = 1.0$
> 
> Total sum:  
> $$
> 1.649 + 2.718 + 1.0 + 1.0 = 6.367
> $$
> 
> Final probabilities:
> 
> - $P_{prod}(\text{"green"} \mid r_1) = \frac{1.649}{6.367} \approx 0.2589$  
> - $P_{prod}(\text{"square"} \mid r_1) = \frac{2.718}{6.367} \approx 0.4269$  
> - $P_{prod}(\text{"circle"} \mid r_1) = \frac{1.0}{6.367} \approx 0.1571$
> - $P_{prod}(\text{"blue"} \mid r_1) = \frac{1.0}{6.367} \approx 0.1571$
>
> ---
>
> **2. probability of intending $r_2$ (green circle)** for each option in the utterance/property space
> #### Literal Listener Probabilities
> - $P_{literal}(r_2 \mid "green") = \frac{1}{2} = 0.5$  
> - $P_{literal}(r_2 \mid "square") = 0$  
> - $P_{literal}(r_2 \mid "circle") = \frac{1}{2} = 0.5$
> - $P_{literal}(r_2 \mid "blue") = 0$
> 
> #### Step 2: Pragmatic Speaker Probabilities
> #### step 2.1: Compute $EU$ Values
> - $EU(r_2, \text{"green"; f}) = P_{literal}(r_1 \mid "green") + f("green") = 0.5 + 0 = 0.5$    
> - $EU(r_2, \text{"square"}; f) = P_{literal}(r_1 \mid "green") + f(p) = 0 + 0 = 0$  
> - $EU(r_2, \text{"circle"}; f) = P_{literal}(r_1 \mid "green") + f(p) = 0.5 + 0 = 0.5 $
> - $EU(r_2, \text{"blue"}; f) = P_{literal}(r_1 \mid "blue") + f(p) = 0 + 0 = 0 $
> 
> #### Step 2.2: Exponentiate and Normalize
> Exponentiate:
> - $\exp\left( \lambda \cdot EU_{speaker}(r_2, "green"; f) \right) = \exp(1 \cdot 0.5) = \exp(0.5)\approx 1.649$  
> - $\exp\left( \lambda \cdot EU_{speaker}(r_2, "square"; f) \right) = \exp(1 \cdot 0) = \exp(0) = 1$  
> - $\exp\left( \lambda \cdot EU_{speaker}(r_2, "circle"; f) \right) = \exp(1 \cdot 0.5) = \exp(0.5) \approx 1.649$ 
> - $\exp\left( \lambda \cdot EU_{speaker}(r_2, "blue"; f) \right) = \exp(1 \cdot 0) = \exp(0) = 1$ 
> 
> Total:  
$$
1.649 + 1 + 1.649 + 1 = 5.298
$$
> 
> Final probabilities:
> 
> - $P_{prod}(\text{"green"} \mid r_2) = \frac{1.649}{4.298} \approx 0.3112$  
> - $P_{prod}(\text{"square"} \mid r_2) = \frac{1}{4.298} \approx 0.1888$  
> - $P_{prod}(\text{"circle"} \mid r_2) = \frac{1.649}{4.298} \approx 0.3112$
> - $P_{prod}(\text{"blue"} \mid r_2) = \frac{1}{4.298} \approx 0.1888$
> 
> ---
> **3. probability of intending $r_3$ (blue circle)** for each option in the utterance/property space
> #### Literal Listener Probabilities
> - $P_{literal}(r_2 \mid "green") = 0$  
> - $P_{literal}(r_2 \mid "square") = 0$  
> - $P_{literal}(r_2 \mid "circle") = \frac{1}{2} = 0.5$
> - $P_{literal}(r_2 \mid "blue") = \frac{1}{1} = 1$
> 
> #### Step 2: Pragmatic Speaker Probabilities
> #### step 2.1: Compute $EU$ Values
> - $EU(r_3, \text{"green"; f}) = P_{literal}(r_3 \mid "green") + f("green") = 0 + 0 = 0$    
> - $EU(r_3, \text{"square"}; f) = P_{literal}(r_3 \mid "green") + f(p) = 0 + 0 = 0$  
> - $EU(r_3, \text{"circle"}; f) = P_{literal}(r_3 \mid "green") + f(p) = 0.5 + 0 = 0.5 $
> - $EU(r_3, \text{"blue"}; f) = P_{literal}(r_3 \mid "blue") + f(p) = 1 + 0 = 1 $
> 
> #### Step 2.2: Exponentiate and Normalize
> Exponentiate:
> - $\exp\left( \lambda \cdot EU_{speaker}(r_3, "green"; f) \right) = \exp(1 \cdot 0) = \exp(0) = 1$  
> - $\exp\left( \lambda \cdot EU_{speaker}(r_3, "square"; f) \right) = \exp(1 \cdot 0) = \exp(0) = 1$  
> - $\exp\left( \lambda \cdot EU_{speaker}(r_3, "circle"; f) \right) = \exp(1 \cdot 0.5) = \exp(0.5) \approx 1.649$ 
> - $\exp\left( \lambda \cdot EU_{speaker}(r_3, "blue"; f) \right) = \exp(1 \cdot 1) = \exp(1) \approx 2.718$ 
> 
> Total:  $ 1 + 1 + 1.649 + 2.718 = 6.367 $
> 
> Final probabilities:
> 
> - $P_{prod}(\text{"green"} \mid r_3) = \frac{1}{6.367} \approx 0.1571$  
> - $P_{prod}(\text{"square"} \mid r_3) = \frac{1}{6.367} \approx 0.1571$  
> - $P_{prod}(\text{"circle"} \mid r_3) = \frac{1.64}{6.367} \approx 0.2589$
> - $P_{prod}(\text{"blue"} \mid r_3) = \frac{2.718}{6.367} \approx 0.4269$





































---

### Extra
### Extra #1 Lambda $\lambda$

In the Rational Speech Act (RSA) model, **λ (lambda)** appears in the **Pragmatic Speaker equation**, where it controls how strongly the speaker favors higher-utility utterances.

#### Core Intuition:
> λ determines how **deterministic or probabilistic** the speaker’s utterance choices are.

#### Where Does λ Appear?

In **Franke & Jäger (2016)**, the Pragmatic Speaker is modeled as:

$$
P_{prod}(p \mid r; \lambda, f) = \frac{\exp\left( \lambda \cdot EU(r, p; f) \right)}{\sum_{p'} \exp\left( \lambda \cdot EU(r, p'; f) \right)}
$$

- $p$: utterance (property)
- $r$: intended referent
- $f(p)$: cost or bias of utterance
- $EU(r, p; f)$: utility of utterance $p$ for referent $r$
- **λ**: rationality parameter

#### What Does λ Do?
- λ **scales** the utility before exponentiation.
- It determines **how much more likely** the speaker is to choose high-utility utterances over others.

#### Effects of Different λ Values

| λ Value     | Speaker Behavior                    |
|-------------|--------------------------------------|
| 0           | Completely random (uniform choice)   |
| ~0.5        | Weak preference for better options   |
| 1           | Moderate, probabilistic choice       |
| >5          | Strong preference for best option    |
| → ∞         | Always chooses highest-utility utterance |


#### Mathematical Background
#### Softmax Function

The softmax is a smooth version of the **argmax**:

$$
\text{softmax}_i(x) = \frac{\exp(\lambda x_i)}{\sum_j \exp(\lambda x_j)}
$$

- λ controls the **sharpness** of the preference.
- High λ → output resembles a hard decision (argmax).
- Low λ → output is closer to uniform probability.


#### Connection to Statistical Physics

In the **Boltzmann distribution**:

$$
P_i = \frac{\exp(-E_i / kT)}{\sum_j \exp(-E_j / kT)}
$$

- $T$ is temperature.
- RSA’s λ is analogous to **inverse temperature**:
  
$$
\lambda = \frac{1}{T}
$$

- Low temperature (high λ) → more deterministic.
- High temperature (low λ) → more randomness.

#### Link to Decision Theory

- Softmax choice reflects **bounded rationality**.
- Agents aren’t fully deterministic, but biased toward better options.
- λ represents **decision sharpness** or **confidence**.

#### Numerical Example

Suppose:

- $EU(\text{"square"}) = 1.0$
- $EU(\text{"green"}) = 0.5$

Then:

- With λ = 1:

  $$
  \exp(1 \cdot 1.0) = 2.718,\quad \exp(1 \cdot 0.5) = 1.649
  $$

- Normalize:

  $$
  \text{Total} = 2.718 + 1.649 = 4.367
  $$

  $$
  P(\text{"square"}) = \frac{2.718}{4.367} \approx 0.622,\quad P(\text{"green"}) = \frac{1.649}{4.367} \approx 0.378
  $$

The speaker prefers "square" but still sometimes says "green".


#### Summary Table

| Concept                 | Interpretation                              |
|-------------------------|----------------------------------------------|
| λ (lambda)              | Rationality or sensitivity to utility        |
| Low λ                   | Speaker behaves more randomly                |
| High λ                  | Speaker consistently chooses best utterance |
| λ = 0                   | Speaker chooses uniformly                    |
| λ → ∞                   | Speaker chooses deterministically            |
| Mathematical Function   | Appears inside exponential in softmax        |

#### Final Takeaway

> λ gives the RSA model **flexibility** to represent real human speakers who are sometimes decisive and sometimes probabilistic in their choices. It controls the **softness of rationality** in utterance production.

---

### Extra #2 Softmax Function

#### Why Is the Softmax Function Used in the Pragmatic Speaker Formula?

In the RSA model, the **Pragmatic Speaker** chooses among possible utterances to convey an intended referent.  
The model assumes the speaker is **rational but probabilistic**.

#### The Formula (Franke & Jäger, 2016)

The speaker's production probability is defined as:

$$
P_{prod}(p \mid r; \lambda, f) = \frac{\exp\left( \lambda \cdot EU(r, p; f) \right)}{\sum_{p'} \exp\left( \lambda \cdot EU(r, p'; f) \right)}
$$

- $p$: property/utterance  
- $r$: intended referent  
- $\lambda$: rationality parameter  
- $f(p)$: utterance bias or cost  
- $EU(r, p; f)$: expected utility of utterance $p$ for referent $r$  


#### What Is the Softmax Function Doing Here?

The softmax function:

$$
\text{softmax}_i(x) = \frac{\exp(\lambda x_i)}{\sum_j \exp(\lambda x_j)}
$$

is used to **turn utility scores into probabilities**. This is crucial in RSA because:


#### 1. It Maps Utility to Probability

- Higher utility → higher probability  
- But all utterances still have **some chance** of being chosen  
- This models **graded speaker behavior**

#### 2. It Reflects Real Human Behavior

Humans don’t always choose the "best" utterance. They might:
- Be uncertain
- Prefer shorter or easier words
- Make probabilistic rather than deterministic decisions

Softmax **captures this variation**.


#### 3. It Controls Rationality via λ

| λ Value   | Speaker Behavior                |
|------------|---------------------------------|
| λ = 0      | Completely random               |
| λ = 1      | Matches utility proportionality |
| λ → ∞      | Always chooses best option      |

- λ allows the model to simulate **different levels of speaker precision**
- This is sometimes called **bounded rationality**


#### 4. It Enables Listener Inference

Listeners in RSA models **reverse-engineer speaker choices**.  
Softmax:
- Makes speaker behavior **invertible** using Bayes’ rule
- Lets listeners reason: *“Why would the speaker have said that?”*


#### 5. It’s a Standard Tool in Decision and Learning Models

- Used in machine learning (e.g., neural networks)
- Used in economics (e.g., quantal response models)
- Used in reinforcement learning (for action selection)

Softmax in RSA makes the model mathematically **standard, general, and interpretable**.


#### Intuition

> Softmax lets the speaker be smart—but not rigid.  
> Better utterances are more likely, but nothing is guaranteed.


#### Summary Table

| Feature                   | Why Softmax Helps in RSA                     |
|---------------------------|----------------------------------------------|
| Maps utility → probability| Valid probability distribution               |
| Captures human behavior   | Models graded, non-deterministic choices     |
| Flexible rationality      | λ controls how sharp or flat the distribution is |
| Bayesian inference support| Listener can reason backwards                |
| Standard modeling tool    | Widely used in cognitive science and AI      |


### Extra #3 Lambda Softmax Visualizer

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Softmax Visualization</title>
  <script src="https://cdn.jsdelivr.net/npm/mathjs@11.11.0/lib/browser/math.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/alpinejs@3.x.x/dist/cdn.min.js" defer></script>
  <style>
    body {
      font-family: sans-serif;
      padding: 1rem;
    }
    .bar {
      height: 24px;
      margin: 4px 0;
      background: #e0e0e0;
      position: relative;
    }
    .fill {
      height: 100%;
      background: steelblue;
      color: white;
      text-align: right;
      padding-right: 8px;
      white-space: nowrap;
      overflow: hidden;
      border-radius: 4px;
    }
  </style>
</head>
<body x-data="softmaxViz()">
  <h4>Effect of Lambda (λ) on Speaker Choice</h4>

  <p>Utility of "square": <strong>1.0</strong><br>
     Utility of "green": <strong>0.5</strong></p>

  <label for="lambda">λ (Rationality parameter): <strong x-text="lambda"></strong></label>
  <input id="lambda" type="range" min="0" max="10" step="0.1" x-model.number="lambda">

  <div class="bar">
    <div class="fill" :style="{ width: (pSquare * 100).toFixed(1) + '%' }">
      <span x-text="'square: ' + (pSquare * 100).toFixed(1) + '%' "></span>
    </div>
  </div>
  <div class="bar">
    <div class="fill" :style="{ width: (pGreen * 100).toFixed(1) + '%' }">
      <span x-text="'green: ' + (pGreen * 100).toFixed(1) + '%' "></span>
    </div>
  </div>

  <script>
    function softmaxViz() {
      return {
        lambda: 1,
        uSquare: 1.0,
        uGreen: 0.5,
        get pSquare() {
          const num = Math.exp(this.lambda * this.uSquare);
          const denom = num + Math.exp(this.lambda * this.uGreen);
          return num / denom;
        },
        get pGreen() {
          const num = Math.exp(this.lambda * this.uGreen);
          const denom = Math.exp(this.lambda * this.uSquare) + num;
          return num / denom;
        }
      }
    }
  </script>
</body>
</html>




---
---
### Sources 
Degen (2023), [*The Rational Speech Act Framework*](https://www.annualreviews.org/content/journals/10.1146/annurev-linguistics-031220-010811)

Franke, M., & Jäger, G. (2016). [Probabilistic pragmatics, or why Bayes’ rule is probably important for pragmatics]((https://www.degruyter.com/document/doi/10.1515/zfs-2016-0002/html?lang=en&srsltid=AfmBOorsU5Gn-tQd3xJ7ka_Cl8OKh5eujrjBwscNJHTEkX9JFG2WF9rR)). *Zeitschrift für Sprachwissenschaft*, 35(1), 3 - 44.