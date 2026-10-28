# 🧮 Discrete Mathematics: Propositional Logic

My notes on propositional logic: propositions, logical connectives, logic laws and rules of inference.

## 📑 Table of Contents

1. [Propositions](#-1-propositions)
2. [Logical Operators (Connectives)](#-2-logical-operators-connectives)
3. [Compound Propositions](#-3-compound-propositions)
4. [Tautologies, Contradictions and Contingencies](#-4-tautologies-contradictions-and-contingencies)
5. [Logic Laws](#-5-logic-laws)
6. [Rules of Inference](#-6-rules-of-inference)
7. [Practice Questions](#-7-practice-questions)
8. [Quick Cheat Sheet](#-8-quick-cheat-sheet)
9. [Study Tracker](#-study-tracker)

**Symbols used:** `∧` AND · `∨` OR · `→` implies · `↔` if and only if · `¬` / `~` NOT · `⊕` XOR · `≡` logically equivalent · `∴` therefore

---

## 💡 1. Propositions

> A **proposition** is a declarative statement that is **either true or false, but not both**. It has a well-defined truth value.

- Also called **sentential logic** or **statement logic**.
- **Logic** is a system based on propositions whose truth value is either true or false.

**Example:** *"The currency of Malaysia is Ringgit."*
- Is it a statement? ✅ Yes
- Is it a proposition? ✅ Yes (it is true)

Propositions are usually named with lowercase letters: `p`, `q`, `r`, `s`.

### How to tell if something is a proposition

Ask: *can I sensibly say "that is true" or "that is false"?*

| Sentence | Proposition? | Why |
|---|:-:|---|
| Kuala Lumpur is the capital of Malaysia | ✅ | True |
| 2 + 2 = 5 | ✅ | False, but it still has a truth value |
| What time is it? | ❌ | A question |
| Close the door! | ❌ | A command |
| x + 2 = 5 | ❌ | Depends on `x`, so no truth value yet |
| This sentence is false | ❌ | Paradox, can't be assigned true or false |

> 📌 A proposition **can be false**. It just needs a definite truth value.

---

## 🔧 2. Logical Operators (Connectives)

| # | Operator | Name | Symbol |
|:-:|---|---|:-:|
| i | NOT | Negation | `¬` or `~` |
| ii | AND | Conjunction | `∧` |
| iii | OR | Disjunction | `∨` |
| iv | XOR | Exclusive or | `⊕` |
| v | if – then | Implication | `→` |
| vi | if and only if | Biconditional | `↔` |

**Tip:** treat T as 1 and F as 0.

| Operator | Behaves like |
|---|---|
| `p ∧ q` | the **smaller** of the two (or `p × q`) |
| `p ∨ q` | the **larger** of the two |
| `¬p` | `1 − p` |
| `p ⊕ q` | addition without carry (`1 + 1 = 0`), same XOR as in my cryptography notes |

### ❌ Negation (NOT): `¬p`

Flips the truth value.

- `p`: I'm a Malaysian
- `¬p`: I'm not a Malaysian

| p | ¬p |
|:-:|:-:|
| T | F |
| F | T |

### ➕ Conjunction (AND): `p ∧ q`

True only when **both** are true. One failure ruins the whole thing.

- `p`: I will have salad for lunch
- `q`: I will have fried mee for dinner
- `p ∧ q`: I will have salad for lunch **and** fried mee for dinner

| p | q | p ∧ q |
|:-:|:-:|:-:|
| T | T | **T** |
| T | F | F |
| F | T | F |
| F | F | F |

### 🔀 Disjunction (OR): `p ∨ q`

Pick either one. True if **at least one** is true. It only fails when **both** are false.

| p | q | p ∨ q |
|:-:|:-:|:-:|
| T | T | **T** |
| T | F | **T** |
| F | T | **T** |
| F | F | F |

> 📌 Logic's OR is **inclusive**, so "both true" counts as true. In everyday English, "tea or coffee?" often means one only. That meaning is **XOR**.

### ⚡ Exclusive Or (XOR): `p ⊕ q`

Ensures only **one** of them is true at a time, but **not both**. Think "they are different".

| p | q | p ⊕ q |
|:-:|:-:|:-:|
| T | T | F |
| T | F | **T** |
| F | T | **T** |
| F | F | F |

Equivalent forms: `p ⊕ q ≡ (p ∨ q) ∧ ¬(p ∧ q) ≡ ¬(p ↔ q)`

### ➡️ Implication (if – then): `p → q`

`p` is the **hypothesis** (the "if" part), `q` is the **conclusion** (the "then" part).

**Exercise**
- `p`: You eat a lot
- `q`: You will be full
- `p → q`: If you eat a lot, then you will be full

| p | q | p → q |
|:-:|:-:|:-:|
| T | T | **T** |
| T | F | **F** |
| F | T | **T** |
| F | F | **T** |

> 📌 `p → q` is false in exactly one case: `p` is true but `q` is false.

**Why is F → anything true?** Think of `p → q` as a **promise**. It is only broken when you eat a lot (`p` true) and are still not full (`q` false). If you didn't eat a lot, the promise was never tested, so it can't be broken. This is called **vacuously true**.

| You ate a lot? | You're full? | Promise broken? | `p → q` |
|:-:|:-:|---|:-:|
| Yes | Yes | No | **T** |
| Yes | No | **Yes** | **F** |
| No | Yes | Not tested | **T** |
| No | No | Not tested | **T** |

**Real example:** *"If 870232 is divisible by 6, then it is divisible by 3."* The digit sum of 870232 is 8+7+0+2+3+2 = 22, so it is not divisible by 3, and so not by 6 either. That is the F → F row, and the statement is still **true**.

**Useful rewrite:** `p → q ≡ ¬p ∨ q` ("either `p` fails, or `q` holds").

**Related statements (common exam trap)**

| Name | Form | Equivalent to `p → q`? |
|---|---|:-:|
| Converse | `q → p` | ❌ No |
| Inverse | `¬p → ¬q` | ❌ No |
| **Contrapositive** | `¬q → ¬p` | ✅ **Yes** |

For `p → q` = *"If you eat a lot, you will be full"*:
- Converse: If you are full, then you ate a lot.
- Inverse: If you didn't eat a lot, you won't be full.
- Contrapositive: If you are not full, then you didn't eat a lot.

**Negation of an implication:** `¬(p → q) ≡ p ∧ ¬q` (the only way to break the promise).

### 🔁 Biconditional (if and only if): `p ↔ q`

True when `p` and `q` have the **same** truth value.

| p | q | p ↔ q |
|:-:|:-:|:-:|
| T | T | **T** |
| T | F | F |
| F | T | F |
| F | F | **T** |

It is a **two-way promise**: `p ↔ q ≡ (p → q) ∧ (q → p)`. It is also the opposite of XOR: `p ↔ q ≡ ¬(p ⊕ q)`.

Example: *"You pass if and only if you score at least 50."*

### 🔢 Order of operations

From highest to lowest: **`¬`, then `∧`, then `∨`, then `→`, then `↔`**. Conventions can vary, so **use brackets** when unsure. For example, `¬p ∧ q` means `(¬p) ∧ q`, not `¬(p ∧ q)`.

---

## 🧩 3. Compound Propositions

One or more propositions can be combined into a single **compound proposition**.

**Example**
- `m`: Roses are red
- `n`: Roses are blue
- `m ∧ n`: Roses are red **and** blue

### 🛠️ How to build a truth table

1. Count the variables `n`. You need **2ⁿ rows** (2 variables = 4 rows, 3 variables = 8 rows).
2. List the rows in a fixed order, starting with all T and ending with all F (`TT, TF, FT, FF`).
3. Add a column for each **negation and inner bracket first**, then work outwards.
4. The **last column** is the answer. Don't skip the in-between columns.

### Truth table: `¬(p ∧ q)`

| p | q | p ∧ q | ¬(p ∧ q) |
|:-:|:-:|:-:|:-:|
| T | T | T | F |
| T | F | F | T |
| F | T | F | T |
| F | F | F | T |

### Truth table: `¬p ∧ ¬q`

| p | q | ¬p | ¬q | ¬p ∧ ¬q |
|:-:|:-:|:-:|:-:|:-:|
| T | T | F | F | F |
| T | F | F | T | F |
| F | T | T | F | F |
| F | F | T | T | **T** |

This is true only when both are false, which is the same as `¬(p ∨ q)` (De Morgan's law, section 5).

### ✏️ Question 2: `(p ∨ q) ∧ ¬(p ∧ q)`

| p | q | (1) p ∨ q | p ∧ q | (2) ¬(p ∧ q) | (1) ∧ (2) |
|:-:|:-:|:-:|:-:|:-:|:-:|
| T | T | T | T | F | **F** |
| T | F | T | F | T | **T** |
| F | T | T | F | T | **T** |
| F | F | F | F | T | **F** |

> 💡 The result column is identical to **XOR**, so `(p ∨ q) ∧ ¬(p ∧ q) ≡ p ⊕ q`.

### Example with 3 variables: `(p ∧ q) → r`

| p | q | r | p ∧ q | (p ∧ q) → r |
|:-:|:-:|:-:|:-:|:-:|
| T | T | T | T | T |
| T | T | F | T | **F** |
| T | F | T | F | T |
| T | F | F | F | T |
| F | T | T | F | T |
| F | T | F | F | T |
| F | F | T | F | T |
| F | F | F | F | T |

It is false only when `p` and `q` are true and `r` is false (the one way to break the promise).

### 🗣️ Translating English into logic

| English | Logic |
|---|---|
| p and q / p but q | `p ∧ q` |
| p or q | `p ∨ q` |
| not p | `¬p` |
| if p then q / p implies q | `p → q` |
| p only if q | `p → q` |
| p if q | `q → p` |
| p if and only if q | `p ↔ q` |
| p is sufficient for q | `p → q` |
| p is necessary for q | `q → p` |
| p unless q | `¬q → p` (same as `p ∨ q`) |
| neither p nor q | `¬p ∧ ¬q` |
| either p or q, but not both | `p ⊕ q` |

**Steps**
1. Pick a letter for each simple statement.
2. Spot the connecting words (and, or, not, if, only if, unless).
3. Write the formula, using brackets to show grouping.

**Example:** *"If it rains and I don't have an umbrella, I will get wet."*
- `p`: it rains, `q`: I have an umbrella, `r`: I get wet
- Formula: `(p ∧ ¬q) → r`

**Example:** *"I will go out only if it does not rain."*
- `p`: I go out, `q`: it rains
- Formula: `p → ¬q`

> ⚠️ **"only if" is the tricky one.** "p only if q" means `p → q` (not `q → p`). If `p` happens, then `q` must be true.

---

## 🎯 4. Tautologies, Contradictions and Contingencies

| Type | Definition | Result column |
|---|---|---|
| **Tautology** | Always **true**, whatever values the variables take. | All T |
| **Contradiction** | Always **false**, whatever values the variables take. | All F |
| **Contingency** | Neither always true nor always false. It is true in some cases and false in others. | Mix of T and F |

**Standard examples**

| Expression | Type | Why |
|---|---|---|
| `p ∨ ¬p` | Tautology | One of `p` or `¬p` is always true |
| `p ∧ ¬p` | Contradiction | `p` and `¬p` can never both be true |
| `p ∧ q` | Contingency | True only when both are true |

### 🛠️ How to classify a statement

**Method 1: truth table.** Build the table and look at the **last column** only: all T = tautology, all F = contradiction, mixed = contingency.

**Method 2: quick reasoning.** For an implication `A → B`, try to make it false (A true, B false). If that is impossible, it is a tautology.

**Worked examples**

| Statement | Type | Reason |
|---|---|---|
| `(p ∧ q) → p` | Tautology | To be false we'd need `p ∧ q` true and `p` false, which is impossible |
| `p → (q → p)` | Tautology | If `p` is true then `q → p` is true. If `p` is false then `p → …` is true |
| `(p → q) ∧ p ∧ ¬q` | Contradiction | `p` and `p → q` force `q` true, but `¬q` says false |
| `(p ∨ q) → (p ∧ q)` | Contingency | TT gives T, TF gives F, FT gives F, FF gives T |

### Useful facts

- `¬(tautology)` is a contradiction, and `¬(contradiction)` is a tautology.
- **Two statements are logically equivalent (`A ≡ B`) exactly when `A ↔ B` is a tautology.** This is how every law in section 5 is proven.
- *"It will rain or it will not rain"* (`p ∨ ¬p`) is a tautology. It is always true but tells you nothing about the weather.

---

## 📐 5. Logic Laws

Logic laws are used to **reduce complex formulas into simpler forms**. They are crucial in mathematics, computer science and philosophy for analysing and solving logical problems.

> ⚠️ **Need to revise this section.** The table below is the standard list, so cross-check it against the lecture slides.

| Law | Equivalence |
|---|---|
| **Identity** | `p ∧ T ≡ p` · `p ∨ F ≡ p` |
| **Domination** | `p ∨ T ≡ T` · `p ∧ F ≡ F` |
| **Idempotent** | `p ∨ p ≡ p` · `p ∧ p ≡ p` |
| **Double negation** | `¬(¬p) ≡ p` |
| **Commutative** | `p ∨ q ≡ q ∨ p` · `p ∧ q ≡ q ∧ p` |
| **Associative** | `(p ∨ q) ∨ r ≡ p ∨ (q ∨ r)` · `(p ∧ q) ∧ r ≡ p ∧ (q ∧ r)` |
| **Distributive** | `p ∨ (q ∧ r) ≡ (p ∨ q) ∧ (p ∨ r)` · `p ∧ (q ∨ r) ≡ (p ∧ q) ∨ (p ∧ r)` |
| **De Morgan's** | `¬(p ∧ q) ≡ ¬p ∨ ¬q` · `¬(p ∨ q) ≡ ¬p ∧ ¬q` |
| **Absorption** | `p ∨ (p ∧ q) ≡ p` · `p ∧ (p ∨ q) ≡ p` |
| **Negation** | `p ∨ ¬p ≡ T` · `p ∧ ¬p ≡ F` |
| **Implication** | `p → q ≡ ¬p ∨ q` |
| **Contrapositive** | `p → q ≡ ¬q → ¬p` |
| **Biconditional** | `p ↔ q ≡ (p → q) ∧ (q → p)` |

### 🧠 Remembering the laws

| Group | Laws | The idea |
|---|---|---|
| Simple ones | Identity, Domination, Idempotent, Double negation | T and F act like 1 and 0, and repeating does nothing |
| Rearranging | Commutative, Associative | Order and brackets don't matter for a single type of operator |
| Mixing | Distributive, Absorption | How `∧` and `∨` interact |
| Flipping | De Morgan's, Negation, Implication | Handling `¬` and `→` |

**De Morgan in plain words:** *"Break the line, change the sign."* To push a `¬` inside brackets, swap `∧` and `∨` and negate each part.

*"It is not true that I am rich and famous"* = *"I am not rich **or** I am not famous"*.

### 🛠️ Strategy for simplifying anything

1. **Remove `→` and `↔`** first, using `p → q ≡ ¬p ∨ q`.
2. **Push `¬` inwards** using De Morgan and double negation.
3. **Tidy up** with distributive, negation (`p ∨ ¬p ≡ T`), identity, domination, absorption.
4. **Write the law used** next to each step. Exams usually require it.

**Worked example 1:** simplify `(p ∧ q) ∨ (p ∧ ¬q)`

| Step | Result | Law used |
|---|---|---|
| 1 | `p ∧ (q ∨ ¬q)` | Distributive (factor out `p`) |
| 2 | `p ∧ T` | Negation |
| 3 | `p` | Identity |

**Worked example 2:** simplify `p ∧ (p → q)`

| Step | Result | Law used |
|---|---|---|
| 1 | `p ∧ (¬p ∨ q)` | Implication |
| 2 | `(p ∧ ¬p) ∨ (p ∧ q)` | Distributive |
| 3 | `F ∨ (p ∧ q)` | Negation |
| 4 | `p ∧ q` | Identity |

This is why Modus Ponens works: if `p` and `p → q` are both true, `q` must be true.

**Worked example 3:** simplify `¬(p ∨ q) ∨ p`

| Step | Result | Law used |
|---|---|---|
| 1 | `(¬p ∧ ¬q) ∨ p` | De Morgan |
| 2 | `(¬p ∨ p) ∧ (¬q ∨ p)` | Distributive |
| 3 | `T ∧ (¬q ∨ p)` | Negation |
| 4 | `p ∨ ¬q` | Identity |

**Worked example 4:** show `¬(p → q) ≡ p ∧ ¬q`

| Step | Result | Law used |
|---|---|---|
| 1 | `¬(¬p ∨ q)` | Implication |
| 2 | `¬¬p ∧ ¬q` | De Morgan |
| 3 | `p ∧ ¬q` | Double negation |

**Worked example 5:** show `(p → q) ∧ (p → r) ≡ p → (q ∧ r)`

| Step | Result | Law used |
|---|---|---|
| 1 | `(¬p ∨ q) ∧ (¬p ∨ r)` | Implication (both) |
| 2 | `¬p ∨ (q ∧ r)` | Distributive (factor out `¬p`) |
| 3 | `p → (q ∧ r)` | Implication (reverse) |

> ✅ **Checking your answer:** plug in values or build a truth table. If the last columns of the original and simplified forms match, you are right.

---

## 🧠 6. Rules of Inference

Rules of inference let us derive a valid conclusion from given premises.

- **Premises** are the facts we are given. The **conclusion** follows from them (`∴` means "therefore").
- An argument is **valid** if, *whenever all the premises are true, the conclusion must be true*.

| Rule | Form | Everyday example |
|---|---|---|
| **Modus Ponens** | `p`, `p → q` ∴ `q` | If it rains, the ground is wet. It rains. ∴ The ground is wet. |
| **Modus Tollens** | `¬q`, `p → q` ∴ `¬p` | If it rains, the ground is wet. The ground is not wet. ∴ It did not rain. |
| **Hypothetical Syllogism** (Transitivity) | `p → q`, `q → r` ∴ `p → r` | If I study, I pass. If I pass, I graduate. ∴ If I study, I graduate. |
| **Disjunctive Syllogism** (Elimination) | `p ∨ q`, `¬p` ∴ `q` | It's nasi lemak or roti canai. It's not nasi lemak. ∴ Roti canai. |
| **Addition** | `p` ∴ `p ∨ q` | I'm in Malaysia. ∴ I'm in Malaysia or on Mars. |
| **Simplification** | `p ∧ q` ∴ `p` | I'm tired and hungry. ∴ I'm tired. |
| **Conjunction** | `p`, `q` ∴ `p ∧ q` | I'm tired. I'm hungry. ∴ I'm tired and hungry. |
| **Resolution** | `p ∨ q`, `¬p ∨ r` ∴ `q ∨ r` | |

**Memory trick:** *ponens* = you **affirm** `p` to get `q`. *Tollens* = you **deny** `q` to get `¬p`.

### 🔍 How to spot which rule applies

| If you see... | Use... |
|---|---|
| An `if-then` and the **first part** (`p`) is true | Modus Ponens |
| An `if-then` and the **second part** (`q`) is false | Modus Tollens |
| Two `if-then`s that **chain** (`q` appears in both) | Hypothetical Syllogism |
| An `or` and one side is **false** | Disjunctive Syllogism (Elimination) |
| An `and` you want to split | Simplification |
| Two separate facts you want to join with `and` | Conjunction |
| One fact, and you want to add `∨ anything` | Addition |

### ⚠️ Two invalid arguments (fallacies)

| Fallacy | Form | Why it fails |
|---|---|---|
| **Affirming the conclusion** | `q`, `p → q` ∴ `p` | If it rains, the ground is wet. The ground is wet. ∴ It rained? ❌ A sprinkler could have done it |
| **Denying the hypothesis** | `¬p`, `p → q` ∴ `¬q` | If it rains, the ground is wet. It didn't rain. ∴ The ground is dry? ❌ Same sprinkler |

### 🛠️ How to answer an inference question

1. **Give each simple statement a letter** (`p`, `q`, `r`).
2. **Write every premise in symbols.**
3. **Combine premises one step at a time.** Number each step and write the rule used.
4. **Stop** when you reach the conclusion.

**Worked example A:** Premises: (1) `p → q`, (2) `q → r`, (3) `¬r`. Conclusion: `¬p`.

| Step | Statement | Reason |
|---|---|---|
| 1 | `p → q` | Premise |
| 2 | `q → r` | Premise |
| 3 | `p → r` | Hypothetical Syllogism (1, 2) |
| 4 | `¬r` | Premise |
| 5 | `¬p` | Modus Tollens (3, 4) |

**Worked example B:** Premises: (1) `(p ∧ q) → r`, (2) `p`, (3) `q`. Conclusion: `r`.

| Step | Statement | Reason |
|---|---|---|
| 1 | `p` | Premise |
| 2 | `q` | Premise |
| 3 | `p ∧ q` | Conjunction (1, 2) |
| 4 | `(p ∧ q) → r` | Premise |
| 5 | `r` | Modus Ponens (3, 4) |

**Worked example C (in words):**
*"If I study, I pass. If I pass, my parents buy me a phone. I did not get a phone. Therefore I did not study."*
Same shape as example A: Hypothetical Syllogism, then Modus Tollens.

**Worked examples using the numbers from the practice question:**
- *"If the sum of the digits of a number is divisible by 3, then the number is divisible by 3. The sum of the digits of 371487 is 30, which is divisible by 3. ∴ 371487 is divisible by 3."* → **Modus Ponens**
- *"If 870232 is divisible by 6, then it is divisible by 3. 870232 is not divisible by 3. ∴ 870232 is not divisible by 6."* → **Modus Tollens**
- *"I will study discrete math. ∴ I will study discrete math or I will go to the gym."* → **Addition**

### ✏️ Practice question (from lecture)

1. I will study discrete math
2. The sum of the digits of 371487 is divisible by 3
3. If 870232 is divisible by 6, then 870232 is divisible by 3

Which rule applies?

- a) Tollens
- b) Pollen *(probably "Ponens")*
- c) Elimination
- d) Transitivity

**How to approach it:** look at the shape of each statement. Statement 3 is an `if-then`, so pair it with a statement about its first part (Ponens) or the negation of its second part (Tollens). Check the lecture slide for exactly how each statement is meant to be used.

---

## 📝 7. Practice Questions

Try each one first, then open the answer.

**Q1.** Which of these is a proposition? (a) "Close the window." (b) "7 is prime." (c) "x > 10."

<details>
<summary>Answer</summary>

Only **(b)**. (a) is a command and (c) depends on `x`. "7 is prime" is true, so it has a truth value.

</details>

**Q2.** Is "If 2 + 2 = 5, then the moon is made of cheese" true or false?

<details>
<summary>Answer</summary>

**True.** Both parts are false (F → F), and F → F is true.

</details>

**Q3.** Write the converse, inverse and contrapositive of: *"If I am in KL, then I am in Malaysia."*

<details>
<summary>Answer</summary>

- **Converse:** If I am in Malaysia, then I am in KL.
- **Inverse:** If I am not in KL, then I am not in Malaysia.
- **Contrapositive:** If I am not in Malaysia, then I am not in KL. ✅ (the only one equivalent to the original)

</details>

**Q4.** Show with a truth table that `¬p ∨ q ≡ p → q`.

<details>
<summary>Answer</summary>

| p | q | ¬p | ¬p ∨ q | p → q |
|:-:|:-:|:-:|:-:|:-:|
| T | T | F | T | T |
| T | F | F | F | F |
| F | T | T | T | T |
| F | F | T | T | T |

The last two columns match in every row, so they are equivalent.

</details>

**Q5.** Build the truth table for `(p ∨ q) → r`.

<details>
<summary>Answer</summary>

| p | q | r | p ∨ q | (p ∨ q) → r |
|:-:|:-:|:-:|:-:|:-:|
| T | T | T | T | T |
| T | T | F | T | **F** |
| T | F | T | T | T |
| T | F | F | T | **F** |
| F | T | T | T | T |
| F | T | F | T | **F** |
| F | F | T | F | T |
| F | F | F | F | T |

It is a contingency (a mix of T and F).

</details>

**Q6.** Translate to symbols: (a) "I will fail unless I study." (b) "You can enter only if you have a ticket." (c) "Neither the lights nor the fan is on."

<details>
<summary>Answer</summary>

- (a) `s`: I study, `f`: I fail. **`¬s → f`** (equivalent to `s ∨ f`)
- (b) `e`: you enter, `t`: you have a ticket. **`e → t`**
- (c) `l`: lights on, `f`: fan on. **`¬l ∧ ¬f`**

</details>

**Q7.** Classify as tautology, contradiction or contingency: (a) `(p ∧ q) → p` (b) `p ∧ ¬p` (c) `p → q`

<details>
<summary>Answer</summary>

- (a) **Tautology.** It's impossible for `p ∧ q` to be true and `p` false.
- (b) **Contradiction.** `p` can't be both true and false.
- (c) **Contingency.** False when `p` is T and `q` is F, true otherwise.

</details>

**Q8.** Simplify `p ∨ (¬p ∧ q)`.

<details>
<summary>Answer</summary>

| Step | Result | Law used |
|---|---|---|
| 1 | `(p ∨ ¬p) ∧ (p ∨ q)` | Distributive |
| 2 | `T ∧ (p ∨ q)` | Negation |
| 3 | `p ∨ q` | Identity |

</details>

**Q9.** Simplify `¬(¬p ∧ q)`.

<details>
<summary>Answer</summary>

| Step | Result | Law used |
|---|---|---|
| 1 | `¬¬p ∨ ¬q` | De Morgan |
| 2 | `p ∨ ¬q` | Double negation |

</details>

**Q10.** Name the rule, or say it is invalid:
(a) If I study, I pass. I did not pass. ∴ I did not study.
(b) It's at home or at the mamak. It's not at home. ∴ It's at the mamak.
(c) If I study, I pass. I passed. ∴ I studied.
(d) If it is Friday, there is a class. It is Friday. ∴ There is a class.

<details>
<summary>Answer</summary>

- (a) **Modus Tollens** ✅
- (b) **Disjunctive Syllogism** (Elimination) ✅
- (c) **Invalid**, because it is affirming the conclusion. I might have passed without studying. ❌
- (d) **Modus Ponens** ✅

</details>

**Q11.** Premises: (1) `p ∨ q`, (2) `¬p`, (3) `q → r`. Conclude `r`.

<details>
<summary>Answer</summary>

| Step | Statement | Reason |
|---|---|---|
| 1 | `p ∨ q` | Premise |
| 2 | `¬p` | Premise |
| 3 | `q` | Disjunctive Syllogism (1, 2) |
| 4 | `q → r` | Premise |
| 5 | `r` | Modus Ponens (3, 4) |

</details>

**Q12.** Premises: (1) `p → q`, (2) `r → ¬q`, (3) `p`. Conclude `¬r`.

<details>
<summary>Answer</summary>

| Step | Statement | Reason |
|---|---|---|
| 1 | `p` | Premise |
| 2 | `p → q` | Premise |
| 3 | `q` | Modus Ponens (1, 2) |
| 4 | `r → ¬q` | Premise |
| 5 | `q → ¬r` | Contrapositive of 4 (`¬¬q → ¬r`, then double negation) |
| 6 | `¬r` | Modus Ponens (3, 5) |

Alternatively, step 5 can be Modus Tollens on `r → ¬q` with `q` (since `¬(¬q)` is `q`), giving `¬r` directly.

</details>

---

## 📋 8. Quick Cheat Sheet

| Connective | Symbol | True when... |
|---|:-:|---|
| NOT | `¬p` | `p` is false |
| AND | `p ∧ q` | **both** true |
| OR | `p ∨ q` | **at least one** true |
| XOR | `p ⊕ q` | they are **different** |
| Implies | `p → q` | anything except `T → F` |
| Iff | `p ↔ q` | they are the **same** |

**Remember:**
- `p → q ≡ ¬p ∨ q ≡ ¬q → ¬p`. The converse and inverse are **not** equivalent.
- `¬(p → q) ≡ p ∧ ¬q`
- `¬(p ∧ q) ≡ ¬p ∨ ¬q` and `¬(p ∨ q) ≡ ¬p ∧ ¬q` (De Morgan).
- `p ↔ q ≡ (p → q) ∧ (q → p) ≡ ¬(p ⊕ q)`.
- "p only if q" = `p → q`. "p if q" = `q → p`.
- Tautology = all T, contradiction = all F, contingency = mixed.
- `A ≡ B` exactly when `A ↔ B` is a tautology.
- Valid inference = true premises force a true conclusion.
- Beware the two fallacies: affirming the conclusion and denying the hypothesis.

**Exam checklist**
- ☐ Truth tables: right number of rows (2ⁿ), columns for each sub-part, rows in order.
- ☐ Simplifying: write the law next to each step.
- ☐ Inference: number the steps and write the rule used.
- ☐ Translating: check "only if", "unless" and "neither/nor" twice.

---

## ✅ Study Tracker

| Topic | Status |
|---|---|
| Propositions & connectives | 📍 Stopped at slide 20 |
| Tautologies & contradictions | 📍 Stopped at slide 25 |
| Logic laws | ⚠️ Weak area, needs revision |
| Rules of inference | 📍 Stopped at slide 40 |

**📅 Upcoming**
- 📝 Test in **week 3**
- 🏫 Replacement class: **Friday night, 30 Oct**

---

<p align="center">⭐ Notes in progress. More to come as I keep learning. ⭐</p>
