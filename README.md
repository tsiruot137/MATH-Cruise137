# MATH-Cruise137
This **repository** stores and manages all my mathematics notes during my study in the mathematics major.

Although the repository is named as `MATH-Cruise137`, the `Cruise137` does not have any specific meaning. Please do not take it seriously. This file gives an overall introduction to the repository. In the very beginning, the rule must be followed throughout the writing of this repository:
> **(Append-only)** The repository is append-only.

## 0. Df-Th Workflow
Since the **Axiomatic Set Theory** (the **ZFC** set theory) was set up, math has returned to its original order. Based on the **Axioms** (`Ax`) of the ZFC set theory, we first propose some **Definitions** (`Df`) and then prove some **Theorems** (`Th`). By the workflow of Df-Th-Df-Th- ... so forth, we finally build up the whole mathematical system.

This repository completely follows this **Df-Th** workflow. Clearly the order in which the Dfs and Ths are proposed matters, that is, the **chronologic consistency** below must be always maintained:

> **(Chronologic Consistency)**
>  Any Df or Th must not refer to any Df or Th that is proposed later.

Thus in this repository, each Df or Th is assigned a unique **timestamp** (`t`). Any two timestamps can be compared (`t1 < t2` means `t1` is earlier than `t2`). The order in which the timestamps progress is called the **main-branch order**. 

In the Df-Th workflow, a statement that speaks of some definition (resp. some theorem) is said to has the **Df-validity** (resp. **Th-validity**). In the very beginning there are also statements with **Ax-validity** (that speaks of some axiom). Other statements (that do not speak of any axiom, definition or theorem) have **no validity**, and removing them does not have any effect on the chronologic consistency of the repository.

### 0.1 Format of the Timestamps
The timestamp of each Df or Th is a sequence of integers `{n1.n2.n3. ...}`. Of course for each timestamp `{n1.n2.n3. ...}`, there is some integer `N` such that `nm=0` for all `m > N`. Hence `{n1.n2.n3}` is for `{n1.n2.n3.0.0. ...}`.

The timestamps are compared lexicographically. For example:

+ `{1.1.2} < {2.0.1}`, `{1.3.2} < {1.3.3}`, `{2.3.3.1} < {2.3.3.2}`, `{3.3.4} < {3.4.3}`; 
+ `{4.3.2} < {4.3.2.1}`;
+ `{5.3.2.-1} < {5.3.2}`, `{6.3.2.-2 < {6.3.2.-1}`.


## 1. Hierarchy of the Repository
In the repository, the logic hierarchy is: **course** $\rightarrow$ **chapter** $\rightarrow$ **files**. That is, a file is of the path:
`root_directory\course\chapter\file`.

This hierarchy also tells some of the chronologic consistency. In fact each course (resp. each chapter) is numbered by a unique **course ID** (resp. **chapter ID**), which is an integer. For a Df or Th with timestamp `{n1.n2.n3. ...}`, the course (resp. chapter) ID of the course (resp. chapter) it belongs to is `n1` (resp. `n2`).

### 1.1 Files
Under each `chapter` directory, the files written in LaTeX constitute the major part of the notes for that chapter. These files are divided into different types:

1. **Main** (`M`): Under each chapter there is ONLY ONE main file, named the same as the **chapter name**. 
2. **Insight** (`I`): Insight files are used to record some insights to some topic related to the chapter. No limit on the number of insight files under each chapter.
3. **Problem** (`P`): Problem files are collections of Dfs and Ths about some problems related to the chapter. No limit on the number of problem files under each chapter.

Usually one begins the chapter with the main file, writing down Dfs and Ths in the main-branch order. Each Df or Th takes up some of the space in the main file, and the space is called a **block**. And the non-main files are together called **subordinate files** (or **sub-files** for short). 

#### 1.1.1 Block Insertion
Under a chapter, the main file manages the main-branch order, while the sub-files appear in the main file as the style of **block insertion**. That is, the blocks in an sub- file are inserted into one or more places in the existing main file. The detailed regulations of performing block insertion are as follows (take `I` files as an example of sub-files):

> **(Block Insertion Rule 1: Initialization of Sub-files)** 
> When having some Dfs or Ths about some insights, one can initialize an insight file named `I1.xxx` (if `I1` is already used, then name it `I2.xxx`, and so on). Notice that there is no requirement that the blocks in `I2` must follow after the blocks in `I1`.

The block insertion must make sure that, *when about to assign a timestamp to a block in a file (in the main file or in a sub-file), one can safely ignore other files, and only need to consider assigning a proper timestamp in the current file (keep the global chronologic consistency of course).* This is called the **safety of block insertion**, which is guaranteed by the **birthday-deathday mechanism**.

Before introducing the birthday-deathday mechanism, one may wonder what a possible case that is NOT safe would be like. Imagine in the main file you inserted some blocks between `t1` and `t2`, written in the file `I1`. Then you want to insert another block `t3` between `t1` and `t2`, but this time you need to check that `t3` is not used in `I1` and any other sub-file that has some blocks between `t1` and `t2`!

> **(Block Insertion Rule 2: Birthday-Deathday Blocks)** 
> A **birthday block** (resp. **deathday block**) is a special block that has no content (hence has no validity) but serves as a placeholder for a timestamp. The timestamp of a birthday block (resp. deathday block) is called a **birthday** (resp. **deathday**). At any moment the main-branch grows, the birthday blocks and deathday blocks in a single file are identified in pairs, with each birthday block corresponding to the immediately next deathday block. The space in the file between a birthday block and the paired deathday block is called a **lifespace**, and the range of timestamps $t$ such that $\text{birthday} < t < \text{deathday}$ is called the **lifetime** of the lifespace. Of course the lifespace and the lifetime are always consistent, and any content with validity must be placed in a lifespace (and with a timestamp in the lifetime).

And the following rule illustrates how to use birthday-deathday pairs to guarantee the safety of block insertion:

> **(Block Insertion Rule 3: Birth-Death Alternation)**
> Every time the main file of a chapter is created (say the chapter 2 of some course), a birthday "$\; 2.-\infty \;$" (or, `{2.-999}`, omit the course ID here) and a deathday "$\; 2.+\infty \;$" (or, `{2.999}`) are created (and paired up at this time) in default. This ensures that all blocks with timestamps `{2.x.x. ...}` are in the lifetime of this birthday-deathday pair. Once a sub-file is created and some blocks are about to be inserted, say, between `2.2` and `2.3`, one needs to create a deathday block `{2.2.-999}` and a birthday block `{2.2.999}` in the main file (so that the previous lifetime is divided into two: `{2.-999} -> {2.2.-999}` and `{2.2.999} -> {2.999}`); at the same time, the deathday block `{2.2.-999}` in the main file generates a new birthday block with the same timestamp (`{2.2.-999}`) in the sub-file, and the birthday block `{2.2.999}` in the main file generates a new deathday block with the same timestamp (`{2.2.999}`) in the sub-file. This ensures that any block with timestamp `{2.2.x. ...}` can be safely written in the sub-file.

In short, the Rule 3 states that a new sub-file borrows a period of lifetime from the main file, which is called a **(single) block insertion**. Certainly we should have the later **(multiple) block insertions** as well, following the Rule 4:

> **(Block Insertion Rule 4: Multiple Block Insertions)**
> Each sub-file can borrow multiple periods of lifetime from the main file, as long as each time the lifetime borrowed, in that moment, is exactly in some lifetime of the main file (i.e. the borrowed lifetime is disjoint from the ones previously borrowed).

#### 1.1.2 Course ID, Chapter ID, File ID and Block ID
For a timestamp `{n1.n2.n3. ...}`, the course ID is `n1`, the chapter ID is `n2`. The **file ID**, which indicates which file (the main file or some sub-file) the block lies in, is suffixed to `n2`. The **block ID** is then the part `n3. ...`. In detail, the timestamp is **formatted** as `{course: n1, ID: n2.n3. ...}`. For example, a block with timestamp `{1.2.3.4}` (with course ID 1 and chapter ID 2) and written in the sub-file `I1` is formatted as `{course: 1, ID: 2_I1.3.4}`, where `I1` is the file ID. For the blocks in the main file, their file ID is `M`, which is omitted in the format. Of course, by the birthday-deathday mechanism, the file ID does not affect the timestamp of the block, i.e. if two blocks have the same course ID and chapter ID, we cannot distinguish which one precedes and which one follows by their file IDs.

### 1.2 Naming Convention
Here is the naming convention for the directories and files in the repository:
+ Course directory: `[course ID].[course name]`
+ Chapter directory: `[chapter ID].[chapter name]`
+ Chapter main file: `[chapter name].tex`
+ Chapter problem file: `P[problem number]. [problem name].tex`
+ Chapter insight file: `I[insight number]. [insight name].tex`

PS: the `chapter name` in the chapter file and the corresponding chapter directory keeps the same.

## 2. Writing of the Df-Th Workflow
Each file consists of a series of blocks, and each block has a unique **tag**. According to the Df-Th workflow, if the majority of the statements in a block is of Df-validity, then the block is tagged as `Df`. That is, the tag of a block is artificially assigned to identify what kind of statements the block mainly contains. Hence the tags can be:

+ `Ax`: The block states some axiom;
+ `Df`: The block mainly states some definition;
+ `Th`: The block mainly states some theorem;
  - `Lma`: The block mainly states some **lemma** (a lemma is a kind of theorem that is used to prove other theorems);
  - `Clry`: Some **corollary** (a corollary is a kind of theorem that is proved by some theorems);
  - `Eg`: Some **example** (an example is a kind of theorem that focus on some concrete cases);
  - `Ex`: Some **exercise** (an exercise is a problem by solving which one can obtain some theorems);
+ `Rmk`: Some **remarks**. Remarks are often large paragraphs that provide additional context or explanation for the preceding blocks. 
+ `Birthday` and `Deathday`: ...

### 2.1 More on Tags of Blocks

#### 2.1.1 Ax
An Ax block states some axiom (of the ZFC set theory), where all statements in the block are of Ax-validity. 

#### 2.1.2 Df
A Df block contains mainly some definitions. A definition is a sentence of the form:

> If xxx, then we say yyy.

Or sometimes it may be:

> Let xxx. We say yyy if xxx. 

*A definition is a **if-and-only-if (iff)** statement*, that is, in the above example of definition, we say yyy if and only if xxx is true (although the sentence only states the "if" part).

A Df block may contains some statements of Th-validity besides those of Df-validity, but it can only contains Df or Th validity of statements (and every sentence in the block has validity). For the sentences in a Df block that are of Th-validity, we should mark them with the **Th color** (which is blue in the entire repository). Moreover, a sentence of Th-validity that is not in a Th block should be colored with the **Th color** as well.

#### 2.1.3 Th
A Th block may contain some statements of Df-validity besides those of Th-validity, but it can only contains Df or Th validity of statements (and every sentence in the block has validity). For the sentences in a Th block that are of Df-validity, we should mark them with the **Df color** (which is green in the entire repository). Moreover, a sentence of Df-validity that is not in a Df block should be colored with the **Df color** as well.

A Th block must be equipped with a **proof** (**Pf**), and it is the proof that endows the statements in the block with Th-validity. The proof, however, can be omitted if it is too easy or too hard. Too easy, one can supply the proof anytime and anywhere even without writing it down; too hard, one can omit it and just confirm that the proof, maybe from some classical book or some paper, is valid. The proof of an Ex block is also called an **solution**.

#### 2.1.4 Rmk
A Rmk block can contain any statements (except for those of Ax-validity). In a Rmk block, the statements of Df-validity (resp. Th-validity) should be colored with the **Df color** (resp. **Th color**) of course.

A Rmk block does not have its own timestamp, since it is considered as a remark to its preceding block. 

#### 2.1.5 Birthday and Deathday
As illustrated in 1.1.1, a birthday block (resp. deathday block) contains no content (no sentence) but only a timestamp. 

### 2.2 Cite a Block
To cite a certain block in the writing, the tag and the formatted timestamp of the block must be presented. For example, `Df {course: 3, ID: 4.5}` refers to the Df block with the block ID `5` in the 4th chapter of the 3rd course, and `{course: 3, ID: 4_P2.3.1}` refers to the block with the block ID `3.1` in the `P2` file of the 4th chapter of the 3rd course. For convenience, we can omit the course ID, like `{, ID: 4_P2.3.1}`, if the cited block is in the current course.

To cite a remark block, we can instead refer to the block that the remark block follows (this block has a timestamp). For example, the remark `{, ID: 4_I2.3.1}` refers to the remark block that follows the block with the ID `4_I2.3.1` in the current course.

To cite a proof, just refer to the Th block for which the proof is provided.

## 3. Advanced Topic: Logic Consistency and Chronologic Consistency

All above we say that the **system** (the system **at some time** is all the content at that time of the Ax, Df and Th, along with their timestamps) must be of chronologic consistency. This requires that a theorem must be proved before being used. Things may not be so ideal, however, as one may want to use a theorem that may be out of the scope of the current learning stage (so that the theorem usually lacks a proof based on the previous knowledge), such as we proposed and frequently use the fundamental theorem of algebra in `{course: 1, ID: 1.14}`, but at that moment we lacked a proof for it.

This indicate that the chronologic consistency is too strict to facilitate a reasonable learning process for readers. Thus here we loosen the requirement of chronologic consistency to **logic consistency**, which will allow us to use a theorem temporarily without a proof. **The system is said to be logically consistent if every theorem can be (directly or indirectly) proved based on the axioms (there also must not to be contradiction between the axioms)**

> **(Logic Consistency Rule 1)** Logic consistency is all we need.

At every moment, the system is mathematically a directed graph, where each node is an axiom or a theorem, and a node $T_1$ points to another node $T_2$ iff $T_2$ is DIRECTLY based on (maybe not only based on) $T_1$ according to the proof for $T_2$ given by the system. In the following text about the discussion of logic consistency, we use the notation $T$ for a theorem (of an axiom) in the system. The system of course contains those definitions, but only the axioms and the theorems are essential (since a definition is only a new, shorter abbreviation for a previous, longer statement). 

The system is said to be **closed** if every theorem $T^\prime$ s.t. $T^\prime\to T$ for some $T$ in the system, we have $T^\prime$ also in the system. A chronologically consistent system is always closed, but it is not the case if the system contains some $T$ that based on a $T^\prime$ not involved in the system yet (e.g. the fundamental theorem of algebra, the case we just discussed). Clearly, **the system is logically consistent $\Rightarrow$ the system is closed.** *In the rest of the section 3, we assume that the system is closed.*

> **(Logic Consistency Rule 2)**
> If no contradiction between the axioms, then a system is logically consistent iff it has NO loop. Since the system is man-made, it of course has no self-loop.

When a loop exists in the system, we say it leads to a **cyclic reasoning**. Cyclic reasoning is a synonym of loop.

Now some terms and notations. We denote that $T^\prime\to T$ if $T$ (maybe not only) directly depends on $T^\prime$, and denote that $T^\prime\to\cdots\to T$ if $T$ (maybe indirectly) depends on $T^\prime$. The set $D(T) = \{T^\prime: T^\prime\to \cdots\to T\}$ is called **the set of dependencies** of $T$ (called **the dependencies** of $T$ for short). The set $D_1(T) = \{T^\prime: T^\prime\to T\}$ is called **the first-order dependencies** (or **direct dependencies**) of $T$. The timestamp of $T$ is denoted as $t(T)$, and $t(T^\prime)<t(T)$ express that the timestamp of $T^\prime$ is BEFORE that of $T$.
One can observe that for any $T$, 
1. $D_1(T)\subseteq D(T)$;
2. $D(T) = D_1(T)\cup\left(\bigcup_{T^\prime\in D_1(T)} D(T^\prime)\right)$;

before verifying that:

> **(Logic Consistency Rule 3)**
> + Chronologic consistency $\Leftrightarrow$ $\forall T$, $\forall T^\prime\in D(T)$, $t(T^\prime)<t(T)$
> + Chronologic consistency $\Rightarrow$ logic consistency.

Conversely, logic consistency $\nRightarrow$ chronologic consistency. Then we can verify the following rule, which addresses the problem just discussed:

> **(Logic Consistency Rule 4)**
> The system is logically consistent iff there are no $T$ and $T^\prime$ s.t.
> 1. $T\leftarrow T^\prime$, $t(T)<t(T^\prime)$ but
> 2. $T\to\cdots\to T^\prime$.

That is, we can allow the condition 1 in this rule to happen, as long as we make sure that the condition 2 is false. If we leave the proof of the fundamental theorem of algebra ($T$) to the later complex analysis, say, plan to use $T^\prime$ to verify $T$, then we should (and only need to) develop a proof for $T^\prime$ s.t. $T\notin D(T^\prime)$. When applying this rule, we should figure out every possible such $T^\prime$, that is, we should figure out $D_1(T)$.

When we claim for $T$ that $T\leftarrow T^\prime$ but $t(T)<t(T^\prime)$ at the moment when we wrote the proof of $T$, we should also claim "without cyclic reasoning", as a promise that we could find the proper (proof of) $T^\prime$ that obey this rule 4 of logic consistency.

### 3.1 Copy-back Mechanism

> **(Copy-back Mechanism)**
> We say $T$ is backcopied as $T_c$ if 
> 1. $T_c$ is the same as $T$ in the content (a theorem consists of its timestamp, its **content** and its proof) but
> 2. $t(T_c)<t(T)$.

It is not always the case that a theorem can be backcopied. To follow the logic consistency, 

> **(Copy-back Mechanism Rule 1)**
> $T$ can be backcopied as $T_c$ if we can make a proof for $T_c$ s.t. 
> $$\forall T^\prime\in D(T_c), t(T^\prime)<t(T_c)$$

Hence, the rule 1 of copy-back mechanism is a special case of the rule 4 of logic consistency. Suppose some $T$ depends directly on $T^\prime$ but $t(T)<t(T^\prime)$ (the problem we just discussed occurs), if $T^\prime$ can be backcopied as $T_c^\prime$ s.t. $t(T_c^\prime)<t(T)$, then the condition 2 of the rule 4 of logic consistency, is satisfied, as long as we consider $T_c^\prime\to T$ instead of $T^\prime\to T$.

Copy-back operation is very useful. For example, an insight is often concluded from files of different periods of time, and some valuable conclusions in this insight file can be used in some earlier files. If (the content of) the latest block in the insight file is proposed in the chapter 5, then this insight file must not before the chapter 5. And in this case, if the insight file draw a pretty valuable conclusion only based on the content before the chapter 2, then this conclusion can be copied back to the chapter 2, so that the fruit of the insight can benefit the theory development in the chapter 2.

## 4. Advanced Topic: Definition Shifting

A definition is a new, shorter statement synonymous to a previous, longer statement. The new statement can be a **term** or a **nonation** (or both).

The system is append-only, and thus once a definition is writing down, neither of its timestamp nor its content can be modified. However, this is impractical during the actual writing. Since the common symbols are limited, we may use the same notation for different two meanings; since some term may expresses different meaning in different existing textbooks (such as the preferred term "regular", which is just to express that an object (such as a curve) satisfies a set of common conditions), we may respect the opinions of different textbooks instead of only allowing one meaning of the term (which is very troublesome). The former case is called the **reuse of notations**, and the latter case is called the **change of definitions of terms**. Both cases can lead to the change of a definition's meaning, called the **definition shifting**.

A practical system needs to allows definition shifting. Then we propose in this section our solution, which allows definition shifting, while making sure that the shifting would not cause any ambiguity of text.

### 4.1 Reuse of Notations

We can reuse a notation for different meanings, as long as we take the approach of **"locality"** to avoid confusion. 

> **(Locality Rule 1)**
> If notation "a" is claimed for different meanings, "A" and "B", then you can distinguish the exact meaning by the context in most of the time. If you fail to figure out which of "A" and "B" the notation actually refers to, then the most "local" claim is the correct one (if "a for A" is claimed in the current chapter and "a for B" is claimed in some previous chapter of the current course, then "A" is said to be more "local" than "B"). For a claim of notation, the most "local" claim is the one in the current chapter (no matter in which file of the chapter). And we should make sure that there are no different claims in the same chapter. 

### 4.2 Change of Definitions of Terms

Solve the problem still by the locality:
> **(Locality Rule 2)**
> Suppose we first define a term $d$ to be the situation $A$, at the timestamp $t_A$. After we learn and write down some Df or Th blocks, we find that using $d$ for $A$ is no longer appropriate. Then we can change the meaning of $d$ from $A$ to a new meaning $B$ at the timestamp $t_B$ (where $t_B > t_A$), and there is no ambiguity anywhere in the system, since we can identify $d$ as $A$ in any blocks proposed in $[t_A, t_B)$, and as $B$ in any blocks proposed in $[t_B, \infty)$. If in the future $d$ is changed again to a new meaning $C$ at the timestamp $t_C$, then we identify $d$ as $B$ in any blocks proposed in $[t_B, t_C)$, and as $C$ in any blocks proposed in $[t_C, \infty)$.

In the actual writing, we avoid changing the definition of a term unless it is necessary. Thus the number of such terms is limited compared to the total number of terms (or blocks). To remind the reader of the change of definition, we must specify all of these terms by

> listing them, along the timestamps when they are proposed and changed, in a global file `terms_changed.md` stored in the root directory of the repository. 

When editing the `terms_changed.md` file, we list the terms in the alphabetical order. When reading and using a Df or Th block (or a statement of Df or Th validity), we must be clear about which meaning the term involved refers to, by checking the `terms_changed.md` file.

### 4.3 Definition Generalization

To further limiting the number of terms and notations that are changed in meaning, we ignore a type of implicit change of definition: the **definition generalization**. For example, we defined the limit of a sequence in $\mathbb{R}$ in the chapter 1 of the course 2, and then defined the limit of a sequence in $\mathbb{R}^n$ in the chapter 4 of the course 2. Both definitions are referred to by the same term "limit" (and by the same notation "$\text{lim}$"), but they are indeed different since the former is a special case of the latter. However we would not list it in the `terms_changed.md` file, as we can easily figure out which meaning the term "limit" refers to anywhere during the learning.

## 5. Other Characteristics Friendly to Readers

### 5.1 Exercise Bank
Exercises is a good way to test and consolidate the knowledge. Within the folder of a chapter (resp. a course), there can be one (but not more) file named `exercises.md` to collect some valuable exercise blocks presented in the chapter (resp. in the course). One `exercises.md` file is called the **Exercise Bank** of the corresponding chapter (resp. course). The instructions of exercise banks are as follows:

(1) One chapter or one course can have **at most one** exercise bank, where you extract some valuable exercises from the corresponding chapter or course and put them all in this bank. 

(2) **This bank has no definition or theorem validity**, as it is not allowed to propose any definition or theorem in this bank.

(3) When including some exercise block into the bank, you are required to specify the entire reference of the block (see 7.1). You do not need to copy any content of the exercise after you correctly refer to the block.

(4) It is recommended to specify the **source** of the exercise (from which book, from which webpage or proposed by whom). Feel free on the format of the source as long as you can relocate the exercise in future.

(5) It is also recommended to make a rating to an exercise. This **rate** to an exercise is a complex number which reflects roughly its importance and difficulty, with the real component for "difficulty" and the imaginary component for "importance". It should be noted that the rating of one exercise can be changed over time. Now is the **rating rule**. 
> Begin at score 0, each time I want to try on the exercise I will update the rate. If I can solve it, then add $i$ to the rating; if I cannot answer it or I finally give a wrong solution, then add $1+i$ to the rating. Each trial on solving an exercise, it is recommended to be familiar with the corresponding content beforehand and to limit the time.

So the rating $r$ of an exercise is a complex number, where a larger $\text{Re}(r)$ means a higher difficulty and a larger $\text{Im}(r)$ means a higher importance. The square of the absolute value $|r|^2$ is the **overall score** of the exercise.

(6) Exercises and examples: the two types of blocks — exercises (Ex) and examples (Eg) — differ little actually. Assign either an Ex block or an Eg block to record a given instance. Since then, **the influential Eg blocks (essential, introductive to the understanding of knowledge) should be included in the exercise bank.** 

### 5.2 Pre-exercise and Post-exercise
Exercises needs reflection and summerization. If a proof or a solution is complete in your own work, it is worthwhile to record the **train of thought** called the **pre-exercise**. After solving the exercise — especially when you must refer to some other materials to solve it — it is suggested to write down some **experiences** called the **post-exercise**.

> **Pre & Post Exercise pattern**: 
> optional pre-exercise part + concise formal solution + optional post-exercise part.

In note files, you are strongly recommended to follow the **pre & post exercise pattern**; while in insight files it does not matter since there we often take a more flexible writing style.

In insight files, it is not necessary to follow the pre-exercise and post-exercise pattern.

### 5.3 Restatement of Definitions and Theorems
Sometimes there is no time to formulate a decent insight file for the newly learned content (or I am just not capable for that extent of comprehension). In this case, it is encouraged to temporarily write down the knowledge in the note file, and then supplement the insight file whenever possible. 

In the insight file at that time, some, or most, of the definitions and theorems may have been proposed in the note file. Then we can just restate them wherever in need in the insight file, for the convenience and the coherence of the writing.

This time of restatement can be assigned with new blocks (including new block IDs) in the insight file. But these blocks do not yield validity, instead, they are just copies of the original blocks in the previously written note file. **Thus we should mark these blocks with a non-validity sign** "nv". And now that these new blocks are not to hold validity, especially for theorem blocks, they can be proposed without a rigorous proof.

### 5.4 Personal Notations
Sometimes some personal notations are used in place of the standard notations (in the math literature) for the sake of convenience. In this case the personal notations should be claimed as "personal" in the block proposing the notation.

### 5.5 Hint step
It is widely acknowledged by math learners that a proof easy to check is usually written in a reverse order of the thinking chain, and thus is usually hard to think of. To balance the checkability and the thinkability, we can still write the proof easy to check, but ``reverse the order'' at some critical steps, that is, give some hints. 

An example of hint step can be seen in the writing of equality. For some equality $a = b$, it is often the case that given $b$ we can notice $b=a$, but given $a$ we may fail to notice $a=b$. In this case we had better to hint $b$ (possibly mark $b$ in another color). For a continued equality $a = b = c = d$ we may want to prove $a = d$. But if $b=c$ is hinted we mean that we first notice $b=c$, and then notice $c=d$ and $b=a$. Such trick can be seen in the proof of the theorem `{course: 5, ID: 2_P2.4.3.2.3 }`, and this way we can exhibit our chain of thought. 
