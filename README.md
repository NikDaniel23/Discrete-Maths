# 🧮 Discrete Mathematics: Chapter 1 Logic

## 📑 Table of Contents

0. [Chapter Overview](#-0-chapter-overview)
1. [Propositions](#-1-propositions)
2. [Logical Operators (Connectives)](#-2-logical-operators-connectives)
3. [Compound Propositions](#-3-compound-propositions)
4. [Tautologies, Contradictions and Contingencies](#-4-tautologies-contradictions-and-contingencies)
5. [Logic Laws](#-5-logic-laws)
6. [Rules of Inference](#-6-rules-of-inference)
7. [Negation in Logic](#-7-negation-in-logic)
8. [Practice Questions](#-8-practice-questions)
9. [Cheat Sheet and Exam Checklist](#-9-cheat-sheet-and-exam-checklist)
10. [Slide Index and Study Tracker](#-10-slide-index-and-study-tracker)

**Symbols used:** `∧` AND · `∨` OR · `→` implies · `↔` if and only if · `¬` or `~` NOT · `⊕` XOR · `≡` or `⇔` logically equivalent · `∴` therefore · `T` true · `F` false

---

## 🧭 0. Chapter Overview

📺 **Slides 1–5**

### Learning outcomes (slide 2)

By the end of this chapter you should be able to:

| # | Outcome | Where in these notes |
|:-:|---|---|
| 1 | Identify a proposition | [Section 1](#-1-propositions) |
| 2 | Tell the names of the logical connectives | [Section 2](#-2-logical-operators-connectives) |
| 3 | Construct a truth table | [Sections 2 and 3](#-3-compound-propositions) |
| 4 | Combine propositions using the logical connectives | [Section 3](#-3-compound-propositions) |
| 5 | Show that a proposition is a tautology, contradiction or equivalent | [Section 4](#-4-tautologies-contradictions-and-contingencies) |
| 6 | Identify laws of logic | [Section 5](#-5-logic-laws) |
| 7 | Learn the 4 rules of inference | [Section 6](#-6-rules-of-inference) |

### What is logic? (slide 3)

- Logic is the **study of reasoning**. It focuses on whether an argument is correct or not.
- It is widely used in **philosophy, mathematics and computer science**.
- It is a **tool for telling the true from the false**.
- It is often called the **"calculus of computer science"** because it is fundamental to designing algorithms, programming languages and software systems.

### Where logic is used (slide 4)

| Area | How logic shows up |
|---|---|
| **Database systems** | Querying and managing data. A `WHERE age > 18 AND city = 'KL'` condition is a compound proposition. |
| **Artificial intelligence** | Reasoning and decision-making (rules such as "if the sensor reads X, then do Y"). |
| **Programming languages** | Control flow and operations: `if`, `while`, `and`, `or`, `not`. |
| **Cryptography** | XOR, the same `⊕` operator used in my cryptography notes. |
| **Circuit design** | Logic gates (AND, OR, NOT, XOR) are the connectives built in hardware. |

### Key components of logic (slide 5)

The chapter is built from four parts, and each later section follows this order:

1. **Propositions** (what we reason about)
2. **Logical connectives** (how we combine propositions)
3. **Logic laws** (how we simplify statements)
4. **Logical inferences / rules of inference** (how we draw valid conclusions)

### 🐍 A tool for checking your own answers

T and F behave like Python's `True` and `False`, so you can check any truth table in seconds:

```python
from itertools import product

# change the expression inside to test any statement
for p, q in product([True, False], repeat=2):
    print(p, q, (not p) or q)        # this tests  ¬p ∨ q
```

Use `and`, `or`, `not`, and `(not p) or q` for `p → q`. The rows come out in the same order as the slides: TT, TF, FT, FF.

---

## 💡 1. Propositions

📺 **Slides 6–14**

> A **proposition** is a **declarative statement** that is **either true or false, but not both**. In other words, it has a **well-defined truth value**.

- Also known as **sentential logic** and **statement logic**.
- **Logic** is a system based on propositions, whose truth value is either true or false.
- Propositions are usually named with letters: `p`, `q`, `r`, `s`.

### Statement vs proposition

| Word | Meaning |
|---|---|
| **Statement** | A declarative sentence (it states something). |
| **Proposition** | A statement that has a **definite** truth value, true or false. |

Every proposition is a statement, but **not every statement is a proposition**. A statement can fail to be a proposition when its truth value depends on a variable that has not been given a value.

### The lecturer's six examples (slides 7–12)

| Slide | Sentence | Statement? | Proposition? | Truth value | Why |
|:-:|---|:-:|:-:|:-:|---|
| 7 | Currency of Malaysia is Ringgit. | Yes | **Yes** | **True** | Definite and correct. |
| 8 | 3 + 4 = 8 | Yes | **Yes** | **False** | False, but it still has a definite truth value. |
| 9 | "y > 5" | Yes | **No** | Cannot determine | Depends on `y`, and `y` is not specified. |
| 10 | x + y > 10 | Yes | **No** | No truth value | Depends on `x` and `y`, which are not specified. |
| 11 | What day is today? | **No** | **No** | No truth value | It is a question, not a declaration. |
| 12 | x < y if and only if y > x. | Yes | **Yes** | **True** | True **whatever** `x` and `y` are, so its truth value does not depend on specific values. |

### 🧠 Understanding it

Ask one question: **"Can I sensibly say 'that is true' or 'that is false'?"**

- **Yes, and there is a definite answer** → proposition (even if it is false, like `3 + 4 = 8`).
- **It depends on an unknown value** (`y > 5`) → not a proposition yet. Give `y` a value (say `y = 9`) and it becomes one.
- **It is a question, command or suggestion** → not a proposition, because it does not claim anything.
- **Slide 12 is the tricky one.** It contains `x` and `y`, but the statement is true for *every* choice of them, so it still has a single truth value.

| Sentence | Proposition? | Reason |
|---|:-:|---|
| Kuala Lumpur is the capital of Malaysia | ✅ | True |
| 2 + 2 = 5 | ✅ | False, but definite |
| What time is it? | ❌ | Question |
| Close the door! | ❌ | Command |
| x + 2 = 5 | ❌ | Depends on `x` |
| This sentence is false | ❌ | Paradox: it cannot be given a truth value |

### ✏️ Exercise (slide 13) and truth values (slide 14)

Which of these are propositions?

1. The sun is shining.
2. n is a prime number.
3. Bring me a glass of water.
4. Let's go to the restaurant.
5. Come to class!!
6. The sum of two prime numbers are even.

<details>
<summary>Answers</summary>

| # | Proposition? | Explanation |
|:-:|:-:|---|
| 1 | ✅ **Yes** | We can check whether the sun is shining or not. It is true or false depending on the situation (if it is shining → TRUE, if not → FALSE). |
| 2 | ❌ **No** | `n` is unspecified, so there is no definite truth value. |
| 3 | ❌ **No** | A command. |
| 4 | ❌ **No** | A suggestion or invitation. |
| 5 | ❌ **No** | A command. |
| 6 | ✅ **Yes, and it is false** | Counterexample: 2 + 3 = 5 is odd. (3 + 5 = 8 is even, but one counterexample is enough to make "the sum is always even" false.) |

Slide 14 shows the working for items 1, 2 and 6. Items 3 to 5 follow the same test: commands and suggestions have no truth value.

</details>

---

## 🔧 2. Logical Operators (Connectives)

📺 **Slides 15–22**

Propositions are written with letters such as `p`, `q`, `r`, `s`, and combined using **6 logical operators**. **Truth tables** show how each operator combines propositions into compound propositions.

| # | Operator | Name | Symbol | Type |
|:-:|---|---|:-:|---|
| i | NOT | Negation | `¬` or `~` | Unary (one input) |
| ii | AND | Conjunction | `∧` | Binary (two inputs) |
| iii | OR | Disjunction | `∨` | Binary |
| iv | XOR | Exclusive or | `⊕` | Binary |
| v | if – then | Implication | `→` | Binary |
| vi | if and only if | Biconditional | `↔` | Binary |

**Tip:** treat T as 1 and F as 0.

| Operator | Behaves like |
|---|---|
| `p ∧ q` | the **smaller** of the two (or `p × q`) |
| `p ∨ q` | the **larger** of the two |
| `¬p` | `1 − p` |
| `p ⊕ q` | addition without carry (`1 + 1 = 0`), the same XOR as in my cryptography notes |

### ❌ Negation (NOT): `¬p` or `~p` (slide 16)

A **unary** operator (works on one proposition). It flips the truth value.

- `P` = I am a Malaysian.
- `¬P` = I am not a Malaysian.

| P | ¬P |
|:-:|:-:|
| T | F |
| F | T |

### ➕ Conjunction (AND): `p ∧ q` (slide 17)

A **binary** operator. True only when **both** are true. One failure ruins the whole thing.

- `P` = I will have salad for lunch
- `Q` = I will have fried mee for dinner
- `P ∧ Q` = I will have salad for lunch **and** fried mee for dinner

| P | Q | P ∧ Q |
|:-:|:-:|:-:|
| T | T | **T** |
| T | F | F |
| F | T | F |
| F | F | F |

If I have the salad but skip the fried mee, the promise "salad **and** fried mee" is broken, so it is false.

### 🔀 Disjunction (OR): `p ∨ q` (slide 18)

True if **at least one** is true. It only fails when **both** are false.

- `P` = ladybugs are purple
- `Q` = ladybugs are green
- `P ∨ Q` = ladybugs are purple **or** ladybugs are green

| P | Q | P ∨ Q |
|:-:|:-:|:-:|
| T | T | **T** |
| T | F | **T** |
| F | T | **T** |
| F | F | F |

> 📌 Logic's OR is **inclusive**: "both true" counts as true. In everyday English, "tea or coffee?" usually means one only. That meaning is **XOR**.

### ⚡ Exclusive Or (XOR): `p ⊕ q` (slide 19)

The exclusive or ensures that **only one of them can be true at a time, but not both**. Think "they are different".

- `P` = the light is on
- `Q` = the fan is on
- `P ⊕ Q` = either the light is on or the fan is on (but not both)

| P | Q | P ⊕ Q |
|:-:|:-:|:-:|
| T | T | F |
| T | F | **T** |
| F | T | **T** |
| F | F | F |

Equivalent forms: `p ⊕ q ≡ (p ∨ q) ∧ ¬(p ∧ q) ≡ ¬(p ↔ q)`

> 🔗 Compare OR and XOR: they differ only in the **first row** (both true). OR gives T, XOR gives F.

### ➡️ Implication (if – then): `p → q` (slide 20)

`p` is the **hypothesis** (the "if" part, also called the antecedent). `q` is the **conclusion** (the "then" part, also called the consequent).

- `P` = you study hard
- `Q` = you will get a good grade
- `P → Q` = if you study hard, then you will get a good grade

| P | Q | P → Q |
|:-:|:-:|:-:|
| T | T | **T** |
| T | F | **F** |
| F | T | **T** |
| F | F | **T** |

> 📌 `p → q` is false in **exactly one case**: `p` is true but `q` is false.

**Why is F → anything true?** Think of `p → q` as a **promise**. It is only broken when you study hard (`p` true) and still do not get a good grade (`q` false). If you did not study hard, the promise was never tested, so it cannot be broken. This is called **vacuously true**.

| Studied hard? | Good grade? | Promise broken? | `P → Q` |
|:-:|:-:|---|:-:|
| Yes | Yes | No | **T** |
| Yes | No | **Yes** | **F** |
| No | Yes | Not tested | **T** |
| No | No | Not tested | **T** |

**Many ways to say `p → q`:**

- if p, then q
- p implies q
- q if p
- p **only if** q
- p is **sufficient** for q
- q is **necessary** for p

**Useful rewrite:** `p → q ≡ ¬p ∨ q` ("either `p` fails, or `q` holds").

**Related statements (a common exam trap)**

| Name | Form | Equivalent to `p → q`? |
|---|---|:-:|
| Converse | `q → p` | ❌ No |
| Inverse | `¬p → ¬q` | ❌ No |
| **Contrapositive** | `¬q → ¬p` | ✅ **Yes** |

For `P → Q` = *"If you study hard, you will get a good grade"*:

- Converse: If you get a good grade, then you studied hard.
- Inverse: If you did not study hard, then you will not get a good grade.
- Contrapositive: If you did not get a good grade, then you did not study hard.

The contrapositive is the basis of **Modus Tollens** (section 6).

### 🔁 Biconditional (if and only if): `p ↔ q` (slide 21)

- `P` = you can take the flight
- `Q` = you buy a ticket
- `P ↔ Q` = you can take the flight **if and only if** you buy a ticket

| P | Q | P ↔ Q |
|:-:|:-:|:-:|
| T | T | **T** |
| T | F | F |
| F | T | F |
| F | F | **T** |

**Rule to remember (from the slide):**

- **Same** truth values (T,T or F,F) → **T**
- **Different** truth values (T,F or F,T) → **F**

It is a **two-way promise**: `p ↔ q ≡ (p → q) ∧ (q → p)`. It is also the exact opposite of XOR: `p ↔ q ≡ ¬(p ⊕ q)`.

### 🔢 Order of operations

From highest to lowest: **`¬`, then `∧`, then `∨`, then `→`, then `↔`**. Conventions can vary between lecturers, so **use brackets** when unsure. For example, `¬p ∧ q` means `(¬p) ∧ q`, not `¬(p ∧ q)`.

### ✏️ Slide 22: which is the correct truth table for `¬p ∨ q`?

Four tables are offered (rows are TT, TF, FT, FF, in that order):

| p | q | 1 | 2 | 3 | 4 |
|:-:|:-:|:-:|:-:|:-:|:-:|
| T | T | T | T | T | F |
| T | F | T | T | F | T |
| F | T | T | F | T | T |
| F | F | F | T | T | T |

Hint from the slide: **look at the values of p and q that make `¬p ∨ q` false.**

<details>
<summary>Answer: table 3</summary>

An OR is false only when **both** parts are false. So `¬p ∨ q` is false when `¬p` is false **and** `q` is false:

- `¬p` is false when `p = T`.
- `q` is false when `q = F`.

So the only false row is **p = T, q = F** (the second row). That is table **3**: `T, F, T, T`.

Full working:

| p | q | ¬p | ¬p ∨ q |
|:-:|:-:|:-:|:-:|
| T | T | F | **T** |
| T | F | F | **F** |
| F | T | T | **T** |
| F | F | T | **T** |

Notice this column is the same as `p → q`. That is the rewrite `p → q ≡ ¬p ∨ q`.

</details>

---

## 🧩 3. Compound Propositions

📺 **Slides 23–25**

One or more propositions can be combined to form a single **compound proposition**.

**Example (slide 23)**

- `m`: Roses are red
- `n`: Roses are blue
- `m ∧ n`: Roses are red **and** blue

### 🛠️ How to build a truth table

1. Count the variables `n`. You need **2ⁿ rows** (2 variables = 4 rows, 3 variables = 8 rows).
2. List the rows in a fixed order, starting with all T and ending with all F (`TT, TF, FT, FF`).
3. Add a column for each **negation and inner bracket first**, then work outwards.
4. The **last column** is the answer. Do not skip the in-between columns.

For 3 variables the row order is `TTT, TTF, TFT, TFF, FTT, FTF, FFT, FFF`.

### ✏️ Slide 24, Question 1

*Show that the statement forms `¬(p ∧ q)` and `¬p ∧ ¬q` are **not** logically equivalent.*

> Note on the slide: two statements are logically equivalent only if **both columns have exactly the same truth values**.

<details>
<summary>Answer</summary>

| p | q | p ∧ q | ¬(p ∧ q) | ¬p | ¬q | ¬p ∧ ¬q |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| T | T | T | F | F | F | F |
| T | F | F | **T** | F | T | **F** |
| F | T | F | **T** | T | F | **F** |
| F | F | F | T | T | T | T |

The `¬(p ∧ q)` column is `F, T, T, T` and the `¬p ∧ ¬q` column is `F, F, F, T`. They **differ in rows 2 and 3**, so they are **not logically equivalent**.

The correct De Morgan's law is `¬(p ∧ q) ≡ ¬p ∨ ¬q`. The `∧` becomes `∨` when `¬` goes inside the brackets.

</details>

### ✏️ Slide 24, Question 2

*Construct the truth table for `(p ∨ q) ∧ ¬(p ∧ q)`.*

<details>
<summary>Answer</summary>

| p | q | (1) p ∨ q | p ∧ q | (2) ¬(p ∧ q) | (1) ∧ (2) |
|:-:|:-:|:-:|:-:|:-:|:-:|
| T | T | T | T | F | **F** |
| T | F | T | F | T | **T** |
| F | T | T | F | T | **T** |
| F | F | F | F | T | **F** |

The result column (`F, T, T, F`) is identical to **XOR**, so `(p ∨ q) ∧ ¬(p ∧ q) ≡ p ⊕ q`. In words: "at least one is true, **but not both**".

</details>

### ✏️ Slide 24, Question 3

*Write the following sentences symbolically, letting `h` = "It is hot" and `s` = "It is sunny".*

a) It is not hot and it is sunny.
b) It is either hot or sunny.

<details>
<summary>Answer</summary>

a) **`¬h ∧ s`**
b) **`h ∨ s`**

"Either … or" is treated as the ordinary (inclusive) OR here. If the question had said "either hot or sunny, **but not both**", it would be `h ⊕ s`.

</details>

### ✏️ Slide 25: translating sentences into symbols

Given `P` = It is raining and `Q` = the grass is wet, write these using logical connectives:

i. It is raining, and the grass is wet.
ii. If it is raining then the grass is wet.
iii. The grass is wet if and only if it is raining.
iv. It is not raining or the grass is not wet.

<details>
<summary>Answer</summary>

| | Sentence | Symbols |
|:-:|---|:-:|
| i | It is raining, **and** the grass is wet | **`P ∧ Q`** |
| ii | **If** it is raining **then** the grass is wet | **`P → Q`** |
| iii | The grass is wet **if and only if** it is raining | **`Q ↔ P`** (same as `P ↔ Q`) |
| iv | It is **not** raining **or** the grass is **not** wet | **`¬P ∨ ¬Q`** |

Statement iv is the same as `¬(P ∧ Q)` by De Morgan's law, or `P → ¬Q`.

</details>

### 🗣️ Translating English into logic: a cheat table

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

---

## 🎯 4. Tautologies, Contradictions and Contingencies

📺 **Slides 26–31**

| Type | Definition | Result column |
|---|---|---|
| **Tautology** | A logical statement that is **always true**. No matter what values you assign to the variables, the outcome is always true. | **All T** |
| **Contradiction** | A logical statement that is **always false**. No matter what values you assign to the variables, the outcome is always false. | **All F** |
| **Contingency** | **Neither** always true nor always false. It can be true in some cases and false in others. | **A mixture of T and F** |

> 🎓 **"Remember this for your exam" (slide 31):** Tautology: all or always **T**. Contradiction: all or always **F**. Contingency: a **mixture** of T and F.

### Slide 27: Tautology (always true): `p ∨ ¬p`

Let `p`: Today is Friday. The statement is *"Today is Friday, or today is not Friday."* It is always true, regardless of whether today is Friday. So it is a **tautology**.

| p | ¬p | p ∨ ¬p |
|:-:|:-:|:-:|
| T | F | **T** |
| F | T | **T** |

### Slide 28: Contradiction (always false): `p ∧ ¬p`

Let `p`: Today is Friday. The statement is *"Today is Friday, **and** today is not Friday."* It is always false because today cannot be Friday and not Friday at the same time. So it is a **contradiction**.

| p | ¬p | p ∧ ¬p |
|:-:|:-:|:-:|
| T | F | **F** |
| F | T | **F** |

### Slide 29: Contingency (sometimes true, sometimes false): `p ∧ q`

Let `p`: Today is Friday, `q`: It is raining. The statement is *"Today is Friday, and it is raining."* It can be true or false depending on the truth values of `p` and `q`. So it is a **contingency**: true in one case and false in the others.

| p | q | p ∧ q |
|:-:|:-:|:-:|
| T | T | **T** |
| T | F | **F** |
| F | T | **F** |
| F | F | **F** |

### Slide 30: Another contingency, this time with OR: `p ∨ q`

Let `p`: Today is Friday, `q`: It is raining. Statement: *"Today is Friday, or it is raining."*

| p | q | p ∨ q |
|:-:|:-:|:-:|
| T | T | **T** |
| T | F | **T** |
| F | T | **T** |
| F | F | **F** |

- The statement is true if **at least one** of `p` or `q` is true.
- The statement is false **only when both** `p` and `q` are false.
- **Conclusion:** `p ∨ q` is a contingency because the final column contains **both T and F**.

### 🛠️ How to classify any statement

**Method 1: truth table.** Build the table and look at the **last column only**: all T = tautology, all F = contradiction, mixed = contingency.

**Method 2: quick reasoning.** For an implication `A → B`, try to make it false (A true and B false). If that is impossible, it is a tautology.

**Worked examples**

| Statement | Type | Reason |
|---|---|---|
| `p ∨ ¬p` | Tautology | One of `p` or `¬p` is always true |
| `p ∧ ¬p` | Contradiction | `p` and `¬p` can never both be true |
| `p ∧ q` | Contingency | True only when both are true |
| `(p ∧ q) → p` | Tautology | To be false we would need `p ∧ q` true and `p` false, which is impossible |
| `p → (q → p)` | Tautology | If `p` is true then `q → p` is true. If `p` is false then `p → …` is true |
| `(p → q) ∧ p ∧ ¬q` | Contradiction | `p` and `p → q` force `q` true, but `¬q` says false |
| `(p ∨ q) → (p ∧ q)` | Contingency | TT gives T, TF gives F, FT gives F, FF gives T |

### Useful facts

- `¬(tautology)` is a contradiction, and `¬(contradiction)` is a tautology.
- **Two statements are logically equivalent (`A ≡ B`) exactly when their truth-table columns are identical**, which is the same as saying `A ↔ B` is a **tautology**. This is how every law in section 5 is proven.
- *"It will rain or it will not rain"* (`p ∨ ¬p`) is a tautology. It is always true but tells you nothing about the weather.

---

## 📐 5. Logic Laws

📺 **Slides 32–35**

Logic laws are used to **reduce complex formulas or statements into a simpler form**. They are crucial in mathematics, computer science and philosophy for analysing and solving logical problems.

### The Laws of Logic (slide 33)

On the slide, **`t`** stands for a **tautology** (a statement that is always TRUE) and **`c`** stands for a **contradiction** (a statement that is always FALSE).

| # | Law | Equivalence |
|:-:|---|---|
| 1 | **Law of Double Negation** | `¬¬p ⇔ p` |
| 2 | **De Morgan's Laws** | `¬(p ∨ q) ⇔ ¬p ∧ ¬q` · `¬(p ∧ q) ⇔ ¬p ∨ ¬q` |
| 3 | **Commutative Laws** | `p ∨ q ⇔ q ∨ p` · `p ∧ q ⇔ q ∧ p` |
| 4 | **Associative Laws** | `(p ∧ q) ∧ r ⇔ p ∧ (q ∧ r)` · `(p ∨ q) ∨ r ⇔ p ∨ (q ∨ r)` |
| 5 | **Idempotent Laws** | `p ∨ p ⇔ p` · `p ∧ p ⇔ p` |
| 6 | **Identity Laws** | `p ∨ c ⇔ p` · `p ∧ t ⇔ p` |
| 7 | **Absorption Laws** | `p ∨ (p ∧ q) ⇔ p` · `p ∧ (p ∨ q) ⇔ p` |
| 8 | **Negation Laws** | `p ∨ ¬p ⇔ t` · `p ∧ ¬p ⇔ c` |
| 9 | **Distributive Laws** | `p ∧ (q ∨ r) ⇔ (p ∧ q) ∨ (p ∧ r)` · `p ∨ (q ∧ r) ⇔ (p ∨ q) ∧ (p ∨ r)` |

Some books write `T` and `F` instead of `t` and `c`. They mean the same: `p ∨ F ≡ p` and `p ∧ T ≡ p`.

### 🧠 Making the laws stick

Group them by what they do instead of memorising nine separate laws:

| Group | Laws | The idea |
|---|---|---|
| Simple ones | Double negation, Idempotent, Identity | Two `¬` cancel, repeating does nothing, and `T`/`F` act like 1 and 0 |
| Rearranging | Commutative, Associative | Order and brackets do not matter when you only use one type of operator |
| Mixing | Distributive, Absorption | How `∧` and `∨` interact |
| Flipping | De Morgan's, Negation | Handling `¬`, and the "always true or false" results |

- **De Morgan in plain words:** *"Break the line, change the sign."* To push a `¬` inside brackets, swap `∧` and `∨` and negate each part. *"It is not true that I am rich and famous"* = *"I am not rich **or** I am not famous"*.
- **Negation laws:** `p ∨ ¬p` is always true (at least one of them must hold), and `p ∧ ¬p` is always false (both cannot hold).
- **Distributive:** it works **both ways**. `∧` distributes over `∨`, and `∨` distributes over `∧`. (Ordinary arithmetic only has one: `×` over `+`.)
- **Absorption:** `p ∨ (p ∧ q) ⇔ p` because if `p` is true the whole thing is true, and if `p` is false then `p ∧ q` is also false. The `q` never matters.

### ✏️ Slide 34: simplify `¬(¬p ∧ q) ∧ (p ∨ q)`

**Solution from the lecture, with each step explained:**

| Step | Statement | Law used | What happened |
|:-:|---|---|---|
| 0 | `¬(¬p ∧ q) ∧ (p ∨ q)` | (start) | |
| 1 | `(¬(¬p) ∨ ¬q) ∧ (p ∨ q)` | **De Morgan's laws** | `¬` pushed inside, `∧` became `∨` |
| 2 | `(p ∨ ¬q) ∧ (p ∨ q)` | **Double negation law** | `¬(¬p)` became `p` |
| 3 | `p ∨ (¬q ∧ q)` | **Distributive law** | `p ∨` factored out of both brackets |
| 4 | `p ∨ (q ∧ ¬q)` | **Commutative law** | swapped `¬q ∧ q` into `q ∧ ¬q` |
| 5 | `p ∨ c`  (i.e. `p ∨ F`) | **Negation law** | `q ∧ ¬q` is a contradiction `c` (false) |
| 6 | `p` | **Identity law** | `p ∨ F = p` |

**Notes from the slide**

- AND: `q ∧ ¬q = F`, because both cannot be true.
- OR: `q ∨ ¬q = T`, because at least one must be true.
- `p ∨ F = p` and `p ∧ T = p`.

**Final answer: `p`**

### Slide 35: why the identity laws work

The result is always the same as `p`.

| p | F | p ∨ F |
|:-:|:-:|:-:|
| T | F | **T** |
| F | F | **F** |

| p | T | p ∧ T |
|:-:|:-:|:-:|
| T | T | **T** |
| F | T | **F** |

So **`p ∨ F = p`** (OR with False changes nothing) and **`p ∧ T = p`** (AND with True changes nothing). Compare the `p` column with the last column: they match in every row.

### 🛠️ Strategy for simplifying anything

1. **Remove `→` and `↔`** first, using `p → q ≡ ¬p ∨ q`.
2. **Push `¬` inwards** using De Morgan and double negation.
3. **Tidy up** with distributive, negation (`p ∨ ¬p ≡ t`), identity, absorption.
4. **Write the law used** next to each step. Exams usually require it.

### More worked examples

**Example 1:** simplify `(p ∧ q) ∨ (p ∧ ¬q)`

| Step | Result | Law used |
|:-:|---|---|
| 1 | `p ∧ (q ∨ ¬q)` | Distributive (factor out `p`) |
| 2 | `p ∧ t` | Negation |
| 3 | `p` | Identity |

**Example 2:** simplify `p ∧ (p → q)`

| Step | Result | Law used |
|:-:|---|---|
| 1 | `p ∧ (¬p ∨ q)` | Implication (`p → q ≡ ¬p ∨ q`) |
| 2 | `(p ∧ ¬p) ∨ (p ∧ q)` | Distributive |
| 3 | `c ∨ (p ∧ q)` | Negation |
| 4 | `p ∧ q` | Identity |

This is why Modus Ponens works: if `p` and `p → q` are both true, then `q` is true.

**Example 3:** simplify `¬(p ∨ q) ∨ p`

| Step | Result | Law used |
|:-:|---|---|
| 1 | `(¬p ∧ ¬q) ∨ p` | De Morgan |
| 2 | `(¬p ∨ p) ∧ (¬q ∨ p)` | Distributive |
| 3 | `t ∧ (¬q ∨ p)` | Negation |
| 4 | `p ∨ ¬q` | Identity |

**Example 4:** show `(p → q) ∧ (p → r) ≡ p → (q ∧ r)`

| Step | Result | Law used |
|:-:|---|---|
| 1 | `(¬p ∨ q) ∧ (¬p ∨ r)` | Implication (both) |
| 2 | `¬p ∨ (q ∧ r)` | Distributive (factor out `¬p`) |
| 3 | `p → (q ∧ r)` | Implication (reverse) |

> ✅ **Checking your answer:** plug in values or build a truth table. If the last columns of the original and simplified forms match, you are right.

### 📎 Laws that are not on the slide but are handy

| Law | Equivalence |
|---|---|
| **Domination** | `p ∨ t ≡ t` · `p ∧ c ≡ c` |
| **Implication** | `p → q ≡ ¬p ∨ q` |
| **Contrapositive** | `p → q ≡ ¬q → ¬p` |
| **Biconditional** | `p ↔ q ≡ (p → q) ∧ (q → p)` |

The implication and biconditional rules reappear on the "5 most important rules" slide in section 7.

---

## 🧠 6. Rules of Inference

📺 **Slides 36–40**

Rules of inference let us derive a **valid conclusion** from given statements (premises).

- **Premises** are the facts we are given. The **conclusion** follows from them (`∴` means "therefore").
- An argument is **valid** if, whenever all the premises are true, the conclusion **must** be true.

The lecture covers **4 rules**:

| # | Rule | Form | Reads as |
|:-:|---|---|---|
| 1 | **Modus Ponens** (affirming the antecedent) | `p → q`, `p` ∴ `q` | If p is true then q is true. p is true, so q is true. |
| 2 | **Modus Tollens** (denying the consequent) | `p → q`, `¬q` ∴ `¬p` | If p is true then q is true. q is not true, so p is not true. |
| 3 | **Elimination** (disjunctive syllogism) | `p ∨ q`, `¬p` ∴ `q` | Either p or q is true. p is not true, so q is true. |
| 4 | **Transitivity** | `p → q`, `q → r` ∴ `p → r` | A chain of if-thens joins up. |

### Rule 1: Modus Ponens (slide 36)

```
p → q
p
∴ q
```

*If the password is correct, then login is permitted.*
*The password is correct.*
*∴ Login is permitted.*

Memory trick: *ponens* = you **affirm** `p` (the first part) to get `q`.

### Rule 2: Modus Tollens (slide 36)

```
p → q
¬q
∴ ¬p
```

*If the password is correct, then login is permitted.*
*Login is not permitted.*
*∴ The password is incorrect.*

Memory trick: *tollens* = you **deny** `q` (the second part) to get `¬p`. It is the contrapositive in action: `p → q` is the same as `¬q → ¬p`.

### Rule 3: Elimination, also called Disjunctive Syllogism (slide 36)

```
p ∨ q
¬p
∴ q
```

*Either Amin is in the library or he is in the cafe.*
*Amin is not in the library.*
*So he must be in the cafe.*

It also works the other way round: `p ∨ q`, `¬q` ∴ `p`. You **eliminate** the false side and the other must be true. (The handwritten note on the slide shows this: "or ¬q ∴ p".)

### Rule 4: Transitivity (slide 36)

```
p → q
q → r
∴ p → r
```

There are **3 statements: p, q and r**.

*If tomorrow is not a holiday then I have to go to work.* (`p → q`)
*If I have to go to work then I have to take the train.* (`q → r`)
***∴ If tomorrow is not a holiday then I have to take the train.*** (`p → r`)

The middle statement `q` appears in both premises and drops out, like a chain linking `p` to `r`.

### 🔍 How to spot which rule applies

| If you see… | Use… |
|---|---|
| An **if-then** and the **first part** (`p`) is stated as true | **Modus Ponens** |
| An **if-then** and the **second part** (`q`) is stated as false (not true) | **Modus Tollens** |
| An **or** and one side is stated as **false** | **Elimination** |
| **Two if-thens** where the "then" of one is the "if" of the other | **Transitivity** |

### ✏️ Slide 37: recognising Modus Ponens and Modus Tollens

Fill in the blank line in each argument, and name the rule.

a) If it is snowing, then I will study discrete math.
   It is snowing.
   ∴ ……………………… (modus ponens)

b) If the sum of the digits of 371,487 is divisible by 3, then 371,487 is divisible by 3.
   ……………………………
   ∴ 371,487 is divisible by 3. (Modus Ponens)

c) ……………………………
   870,232 is not divisible by 3.
   ∴ 870,232 is not divisible by 6. (modus tollens)

<details>
<summary>Answers</summary>

**a)** ∴ **I will study discrete math.** (Modus Ponens: `p → q`, `p` ∴ `q`)

**b)** **The sum of the digits of 371,487 is divisible by 3.** (the missing `p`). Check: 3+7+1+4+8+7 = 30, which is divisible by 3. (Modus Ponens)

**c)** **If 870,232 is divisible by 6, then 870,232 is divisible by 3.** (the missing `p → q`). Check: 8+7+0+2+3+2 = 22, which is not divisible by 3. So 870,232 is not divisible by 3 (`¬q`), therefore it is not divisible by 6 (`¬p`). (Modus Tollens)

These three missing lines are exactly the three statements in my lecture notes (*"I will study discrete math"*, *"the sum of the digits of 371487 is divisible by 3"*, and *"if 870232 is divisible by 6, then 870232 is divisible by 3"*).

</details>

### ✏️ Slide 38: identify the rule of inference

a) If Anisah's father is Ahmad then Anisah could be my sister.
   **Anisah is not my sister, therefore her father is not Ahmad.

b) If you get an 'A' for this subject then I will buy you ice cream.
   **You scored 'A' for this subject. Therefore I will buy you ice cream.

c) x − 3 = 0 or x + 2 = 0.
   ** x + 2 ≠ 0
   ∴ x − 3 = 0

d) If you invest in the stock market, then you will get rich.
   If you get rich, then you will be happy.
   **If you invest in the stock market, then you will be happy.

The answer choices in my notes were: **a) Tollens, b) Ponens ("Pollen" in my notes was a typo for Ponens), c) Elimination, d) Transitivity.** These match the four questions above in order.

<details>
<summary>Answers</summary>

| | Shape | Rule |
|:-:|---|---|
| **a)** | `p → q`, `¬q` ∴ `¬p` | **Modus Tollens** (deny the "then" part) |
| **b)** | `p → q`, `p` ∴ `q` | **Modus Ponens** (affirm the "if" part) |
| **c)** | `p ∨ q`, `¬q` ∴ `p` (with `p`: x − 3 = 0 and `q`: x + 2 = 0) | **Elimination** (disjunctive syllogism) |
| **d)** | `p → q`, `q → r` ∴ `p → r` | **Transitivity** |

Step by step for a):

- `p`: Anisah's father is Ahmad. `q`: Anisah could be my sister.
- Premises: `p → q` and `¬q` ("Anisah is not my sister").
- Conclusion: `¬p` ("her father is not Ahmad").

</details>

### Slide 39: where inference rules are used

These rules are foundational in logical reasoning and are widely used in **mathematics, philosophy and computer science**. In computer science, **modus ponens, modus tollens, disjunctive syllogism and transitivity** are frequently applied in **algorithms, formal verification and logic programming**.

### Slide 40: Modus Ponens in programming

```python
age = 20
if age >= 18:
    print("Eligible to vote")
```

- `p`: the person is 18 or older (`age >= 18`)
- `q`: they are eligible to vote
- Rule: `p → q` (if the age is 18 or older, then eligible to vote)
- Fact: the age is 20, so `p` is true
- ∴ `q` is true, so the person is eligible to vote

Every `if` statement in code is a Modus Ponens: the condition is `p`, and the body that runs is `q`.

### ⚠️ Two invalid look-alikes (fallacies)

These **sound right** but are **not valid**. Exams like to test them.

| Fallacy | Form | Why it fails |
|---|---|---|
| **Affirming the consequent** | `p → q`, `q` ∴ `p` | If it rains, the ground is wet. The ground is wet. ∴ It rained? ❌ A sprinkler could have done it. |
| **Denying the antecedent** | `p → q`, `¬p` ∴ `¬q` | If it rains, the ground is wet. It did not rain. ∴ The ground is dry? ❌ Same sprinkler. |

Compare with the valid ones: Modus Ponens **affirms the antecedent** (the first part, `p`), and Modus Tollens **denies the consequent** (the second part, `q`). Only those two directions are valid.

### 🛠️ How to answer an inference question

1. **Give each simple statement a letter** (`p`, `q`, `r`).
2. **Write every premise in symbols.**
3. **Combine premises one step at a time.** Number each step and write the rule used.
4. **Stop** when you reach the conclusion.

**Worked example A:** Premises: (1) `p → q`, (2) `q → r`, (3) `¬r`. Conclusion: `¬p`.

| Step | Statement | Reason |
|:-:|---|---|
| 1 | `p → q` | Premise |
| 2 | `q → r` | Premise |
| 3 | `p → r` | Transitivity (1, 2) |
| 4 | `¬r` | Premise |
| 5 | `¬p` | Modus Tollens (3, 4) |

**Worked example B:** Premises: (1) `p ∨ q`, (2) `¬p`, (3) `q → r`. Conclusion: `r`.

| Step | Statement | Reason |
|:-:|---|---|
| 1 | `p ∨ q` | Premise |
| 2 | `¬p` | Premise |
| 3 | `q` | Elimination (1, 2) |
| 4 | `q → r` | Premise |
| 5 | `r` | Modus Ponens (3, 4) |

**Worked example C (in words):** *"If I study, I pass. If I pass, my parents buy me a phone. I did not get a phone. Therefore I did not study."* Same shape as example A: Transitivity, then Modus Tollens.

<details>
<summary>📎 Extra rules not in the lecture (only if you meet them elsewhere)</summary>

| Rule | Form |
|---|---|
| **Addition** | `p` ∴ `p ∨ q` |
| **Simplification** | `p ∧ q` ∴ `p` |
| **Conjunction** | `p`, `q` ∴ `p ∧ q` |
| **Resolution** | `p ∨ q`, `¬p ∨ r` ∴ `q ∨ r` |

Transitivity is also called **Hypothetical Syllogism** in many textbooks. The lecture uses the name **Transitivity**.

</details>

---

## 🚫 7. Negation in Logic

📺 **Slides 41–47**

**Negation** is a fundamental operation in logic, used to express the **opposite (or denial)** of a statement. The symbol for negation is **`~` or `¬`**, and it is applied to propositions or statements.

### Slide 42: simple and compound statements

**1. Negation of a simple statement.** For a simple statement `p`:

- The negation of `p` is `~p`, which reads as "not p".
- If `p` is true, then `~p` is false, and vice versa.

Example: Statement `p`: "It is raining." Negation `~p`: "It is not raining."

**2. Negation of compound statements.** When negating compound logical statements, we apply specific rules based on the **structure** of the statement.

**a. Negation of a conjunction (AND, `∧`)**

For `p ∧ q` (both `p` and `q` are true), the negation is:

> **`~(p ∧ q) ≡ ~p ∨ ~q`**

This means "not p" **or** "not q" (at least one of them is false).

Example:

- Statement: "I am studying **and** it is raining."
- Negation: "I am not studying **or** it is not raining."

### Slide 43: disjunction and conditional

**b. Negation of a disjunction (OR, `∨`)**

For `p ∨ q` (either `p` or `q` is true), the negation is:

> **`~(p ∨ q) ≡ ~p ∧ ~q`**

This means "not p" **and** "not q" (both are false).

Example:

- Statement: "I will eat pizza **or** I will eat pasta."
- Negation: "I will not eat pizza **and** I will not eat pasta."

**c. Negation of a conditional statement (IF-THEN, `p → q`)**

For `p → q` (if p, then q), the negation is:

> **`~(p → q) ≡ p ∧ ~q`**

This means "p is true **and** q is false."

Example:

- Statement: "If it rains, then I will stay home."
- Negation: "It rains, **and** I do not stay home."

### Slide 44: biconditional

**d. Negation of a biconditional statement (IF AND ONLY IF, `p ↔ q`)**

For `p ↔ q` (p if and only if q), the negation is:

> **`~(p ↔ q) ≡ (p ∧ ~q) ∨ (~p ∧ q)`**

This means either "p is true and q is false" or "p is false and q is true." **They must differ.**

Example:

- Statement: "I will attend the meeting if and only if my friends attend."
- Negation: "I attend the meeting and my friends do not attend, **or** I do not attend the meeting and my friends attend the meeting."

### Slide 45: summary table of negation rules

| Original statement | Negation |
|---|---|
| `p` | `¬p` |
| `p ∧ q` | `¬p ∨ ¬q` |
| `p ∨ q` | `¬p ∧ ¬q` |
| `p → q` | `p ∧ ¬q` |
| `p ↔ q` | `(p ∧ ¬q) ∨ (¬p ∧ q)` |

### Slide 46: "The 5 most important rules"

| # | Rule | Formula |
|:-:|---|---|
| 1 | NOT (negation) | `¬(¬p) = p` |
| 2 | Implication | `p → q ≡ ¬p ∨ q` |
| 3 | Negation of implication | `¬(p → q) ≡ p ∧ ¬q` |
| 4 | De Morgan's AND rule | `¬(p ∧ q) ≡ ¬p ∨ ¬q` |
| 5 | De Morgan's OR rule | `¬(p ∨ q) ≡ ¬p ∧ ¬q` |

### Slide 47: "If and only if" rules

| Rule | Formula |
|---|---|
| If and only if | `p ↔ q ≡ (p → q) ∧ (q → p)` |
| Negation of if and only if | `¬(p ↔ q) ≡ (p ∧ ¬q) ∨ (¬p ∧ q)` |

### 🧠 Understanding it

**The one-line rule:** to negate, **flip the operator and negate the parts**: `∧` ↔ `∨`, and for `→` the answer becomes an AND.

| To negate… | Do this |
|---|---|
| `p ∧ q` | `∧` becomes `∨`, negate both parts |
| `p ∨ q` | `∨` becomes `∧`, negate both parts |
| `p → q` | **Keep** `p`, **AND** it with `¬q` |
| `p ↔ q` | The two sides **differ** (this is XOR) |

**Why do these work?** Think of when the original statement is **false**:

- `p ∧ q` is false when **at least one** is false → `¬p ∨ ¬q`.
- `p ∨ q` is false only when **both** are false → `¬p ∧ ¬q`.
- `p → q` is false only when `p` is true and `q` is false (the broken promise) → `p ∧ ¬q`.
- `p ↔ q` is false when `p` and `q` have **different** values → `(p ∧ ¬q) ∨ (¬p ∧ q)`, which is `p ⊕ q`.

**Proof that `¬(p → q) ≡ p ∧ ¬q`** (using laws from section 5):

| Step | Result | Law used |
|:-:|---|---|
| 1 | `¬(¬p ∨ q)` | Implication |
| 2 | `¬¬p ∧ ¬q` | De Morgan |
| 3 | `p ∧ ¬q` | Double negation |

### 🛠️ How to negate an English sentence

1. Name each simple statement (`p`, `q`, …).
2. Write the sentence in symbols.
3. Put `¬( … )` around the whole thing.
4. Apply the matching rule from the table.
5. Translate back to English and tidy up any double negatives.

### ⚠️ Common mistakes

| Wrong | Why it is wrong | Right |
|---|---|---|
| `¬(p ∧ q) = ¬p ∧ ¬q` | This is exactly slide 24 question 1: the tables differ in rows 2 and 3 | `¬p ∨ ¬q` |
| "If it rains then I will **not** stay home" as the negation of "If it rains then I will stay home" | An if-then is not negated by another if-then | "It rains **and** I do not stay home" |
| Forgetting to flip `∧`/`∨` | De Morgan always swaps them | Break the line, change the sign |

---

## 📝 8. Practice Questions

Try each one first, then open the answer. Questions marked 📺 come straight from the slides.

**Q1.** 📺 *(slide 13)* Which of these is **not** a proposition? (a) "Come to class!!" (b) "7 is prime." (c) "x > 10." (d) "3 + 4 = 8."

<details>
<summary>Answer</summary>

**(a) and (c)** are not propositions. (a) is a command and (c) depends on `x`. (b) is a true proposition and (d) is a false proposition. A proposition can be false.

</details>

**Q2.** Is "If 2 + 2 = 5, then the moon is made of cheese" true or false?

<details>
<summary>Answer</summary>

**True.** Both parts are false (F → F), and F → F is true. The promise was never tested.

</details>

**Q3.** Write the converse, inverse and contrapositive of: *"If I am in KL, then I am in Malaysia."*

<details>
<summary>Answer</summary>

- **Converse:** If I am in Malaysia, then I am in KL.
- **Inverse:** If I am not in KL, then I am not in Malaysia.
- **Contrapositive:** If I am not in Malaysia, then I am not in KL. ✅ (the only one equivalent to the original)

</details>

**Q4.** 📺 *(slide 22)* Which truth table is correct for `¬p ∨ q`?

<details>
<summary>Answer</summary>

Table **3** (`T, F, T, T`). It is false only when `p = T` and `q = F`.

</details>

**Q5.** Show with a truth table that `¬p ∨ q ≡ p → q`.

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

**Q6.** Build the truth table for `(p ∨ q) → r`.

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

**Q7.** 📺 *(slide 25 style)* Given `P` = It is raining, `Q` = the grass is wet, write: (a) "If it is raining then the grass is wet." (b) "It is not raining or the grass is not wet." (c) "The grass is wet if and only if it is raining."

<details>
<summary>Answer</summary>

(a) `P → Q`  (b) `¬P ∨ ¬Q`  (c) `Q ↔ P`

</details>

**Q8.** Translate to symbols: (a) "I will fail unless I study." (b) "You can enter only if you have a ticket." (c) "Neither the lights nor the fan is on."

<details>
<summary>Answer</summary>

- (a) `s`: I study, `f`: I fail. **`¬s → f`** (equivalent to `s ∨ f`)
- (b) `e`: you enter, `t`: you have a ticket. **`e → t`**
- (c) `l`: lights on, `f`: fan on. **`¬l ∧ ¬f`**

</details>

**Q9.** Classify as tautology, contradiction or contingency: (a) `(p ∧ q) → p` (b) `p ∧ ¬p` (c) `p → q` (d) `p ∨ ¬p`

<details>
<summary>Answer</summary>

- (a) **Tautology.** It is impossible for `p ∧ q` to be true and `p` false.
- (b) **Contradiction.** `p` cannot be both true and false.
- (c) **Contingency.** False when `p` is T and `q` is F, true otherwise.
- (d) **Tautology.** One of them must be true.

</details>

**Q10.** 📺 *(slide 34 style)* Simplify `p ∨ (¬p ∧ q)`.

<details>
<summary>Answer</summary>

| Step | Result | Law used |
|:-:|---|---|
| 1 | `(p ∨ ¬p) ∧ (p ∨ q)` | Distributive |
| 2 | `t ∧ (p ∨ q)` | Negation |
| 3 | `p ∨ q` | Identity |

</details>

**Q11.** Simplify `¬(¬p ∧ q)`.

<details>
<summary>Answer</summary>

| Step | Result | Law used |
|:-:|---|---|
| 1 | `¬¬p ∨ ¬q` | De Morgan |
| 2 | `p ∨ ¬q` | Double negation |

</details>

**Q12.** 📺 *(slides 36–38 style)* Name the rule, or say it is invalid:
(a) If I study, I pass. I did not pass. ∴ I did not study.
(b) It is at home or at the mamak. It is not at home. ∴ It is at the mamak.
(c) If I study, I pass. I passed. ∴ I studied.
(d) If it is Friday, there is a class. It is Friday. ∴ There is a class.
(e) If I am late, I miss the bus. If I miss the bus, I walk. ∴ If I am late, I walk.

<details>
<summary>Answer</summary>

- (a) **Modus Tollens** ✅
- (b) **Elimination** (disjunctive syllogism) ✅
- (c) **Invalid**, because it is affirming the consequent. I might have passed without studying. ❌
- (d) **Modus Ponens** ✅
- (e) **Transitivity** ✅

</details>

**Q13.** Premises: (1) `p ∨ q`, (2) `¬p`, (3) `q → r`. Conclude `r`.

<details>
<summary>Answer</summary>

| Step | Statement | Reason |
|:-:|---|---|
| 1 | `p ∨ q` | Premise |
| 2 | `¬p` | Premise |
| 3 | `q` | Elimination (1, 2) |
| 4 | `q → r` | Premise |
| 5 | `r` | Modus Ponens (3, 4) |

</details>

**Q14.** Premises: (1) `p → q`, (2) `r → ¬q`, (3) `p`. Conclude `¬r`.

<details>
<summary>Answer</summary>

| Step | Statement | Reason |
|:-:|---|---|
| 1 | `p` | Premise |
| 2 | `p → q` | Premise |
| 3 | `q` | Modus Ponens (1, 2) |
| 4 | `¬¬q` | Double negation (3) |
| 5 | `r → ¬q` | Premise |
| 6 | `¬r` | Modus Tollens (5, 4): the "then" part `¬q` is denied by `¬¬q` |

</details>

**Q15.** 📺 *(slides 42–44 style)* Write the negation of each: (a) "I will eat rice and drink tea." (b) "The server is down or the network is slow." (c) "If you score 80, then you get a scholarship." (d) "You can log in if and only if your password is correct."

<details>
<summary>Answer</summary>

- (a) I will **not** eat rice **or** I will **not** drink tea. (`¬p ∨ ¬q`)
- (b) The server is **not** down **and** the network is **not** slow. (`¬p ∧ ¬q`)
- (c) You score 80 **and** you do **not** get a scholarship. (`p ∧ ¬q`)
- (d) (You can log in **and** your password is **not** correct) **or** (you can**not** log in **and** your password **is** correct). (`(p ∧ ¬q) ∨ (¬p ∧ q)`)

</details>

**Q16.** Simplify the negation: (a) `¬(¬p ∨ q)` (b) `¬(p ∧ ¬q)`

<details>
<summary>Answer</summary>

- (a) `¬(¬p ∨ q) ≡ ¬¬p ∧ ¬q ≡ p ∧ ¬q` (De Morgan, then double negation). This is also `¬(p → q)`.
- (b) `¬(p ∧ ¬q) ≡ ¬p ∨ ¬¬q ≡ ¬p ∨ q` (De Morgan, then double negation). This is also `p → q`.

</details>

---

## 📋 9. Cheat Sheet and Exam Checklist

### The connectives

| Connective | Symbol | True when… |
|---|:-:|---|
| NOT | `¬p` | `p` is false |
| AND | `p ∧ q` | **both** true |
| OR | `p ∨ q` | **at least one** true |
| XOR | `p ⊕ q` | they are **different** |
| Implies | `p → q` | anything except `T → F` |
| Iff | `p ↔ q` | they are the **same** |

### Truth table results to remember

| p | q | p ∧ q | p ∨ q | p ⊕ q | p → q | p ↔ q |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| T | T | T | T | F | T | T |
| T | F | F | T | T | F | F |
| F | T | F | T | T | T | F |
| F | F | F | F | F | T | T |

### Key equivalences

- `¬¬p ≡ p`
- `p → q ≡ ¬p ∨ q ≡ ¬q → ¬p`. The converse and inverse are **not** equivalent.
- `¬(p ∧ q) ≡ ¬p ∨ ¬q` and `¬(p ∨ q) ≡ ¬p ∧ ¬q` (De Morgan).
- `¬(p → q) ≡ p ∧ ¬q`
- `p ↔ q ≡ (p → q) ∧ (q → p) ≡ ¬(p ⊕ q)`
- `¬(p ↔ q) ≡ (p ∧ ¬q) ∨ (¬p ∧ q)`
- "p only if q" = `p → q`. "p if q" = `q → p`.

### Classification and equivalence

- **Tautology** = all T · **Contradiction** = all F · **Contingency** = a mixture of T and F.
- `A ≡ B` exactly when their columns are identical (`A ↔ B` is a tautology).

### The 4 rules of inference

| Rule | Form |
|---|---|
| Modus Ponens | `p → q`, `p` ∴ `q` |
| Modus Tollens | `p → q`, `¬q` ∴ `¬p` |
| Elimination | `p ∨ q`, `¬p` ∴ `q` |
| Transitivity | `p → q`, `q → r` ∴ `p → r` |

Invalid: `p → q`, `q` ∴ `p` (affirming the consequent) and `p → q`, `¬p` ∴ `¬q` (denying the antecedent).

### Exam checklist

- ☐ Truth tables: right number of rows (2ⁿ), a column for each sub-part, rows in order.
- ☐ Equivalence: compare **whole columns**, and a single different row proves "not equivalent".
- ☐ Simplifying: write the law next to each step.
- ☐ Inference: number the steps and write the rule used.
- ☐ Translating: check "only if", "unless" and "neither/nor" twice.
- ☐ Negating: break the line, change the sign, and remember `¬(p → q) = p ∧ ¬q`.

---

<p align="center">⭐ Notes in progress. More to come as I keep learning. ⭐</p>
