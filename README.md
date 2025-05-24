# MATH-Cruise137
This repository stores all my cumulative mathematical knowledge, including **notes** from the courses learning, some interesting **problems** I have encountered, and some summaries or **insights** I concluded from my learning.

As though repository is named as `MATH-Cruise137`, the `Cruise137` does not have any specific meaning. Please do not take it seriously. Here I will give an overall introduction to this repository.

## 1. Courses-Based Organization
This repository is in general organized by the courses I have learned. Every time I learn a new course, a directory for the notes, problems, and insights from that course will be added to the repository. Actually the contents (of the notes, problems, and insights) of a certain course are not necessarily all related to the course, and they can be any mathematical knowledge I have learned during that period of time.

## 2. Basic Composition of the Content
Every course directory contains three genres of files: `notes`, `problems`, and `insights`, which are all written in LaTeX. These three genres of files share the same composition, which is the commonly-used **"Definition-Theorem"** workflow in mathematics. This workflow is described below (as though every math learner would be familiar with it).
> **Definition-Theorem workflow ("Df-Th" workflow for short)**: Math theory is developed in chronological order. Mathamaticians start with some basic definitions, then they prove some theorems based on these definitions or on theorems previously proved. For the progress of math theory, there must be always new definitions proposed so that new theorems offering more insights to the world can be discovered. **In this workflow, every definition or theorem must based on the previous definitions or theorems. Every definition or theorem must be verified to be valid, and each newly proposed definition or theorem must not conflict with any previous ones.** Thus in the very beginning of math theory, mathematicians must initialize a set of **logic** or rules that must be followed throughout the development of the theory, and some cornerstones (called **axioms**) to support all the theory.
>

## 3. Writing of the Df-Th Workflow
The four genres of files share the same composition based on the Df-Th workflow. The Df-Th workflow basically consists of definitions and theorems. A definition or a theorem is written as a **building block** that takes up a region of a file, with a formatted **timestamp** representing the logic time when the definition or the theorem is proposed.

In each LaTeX file, a variant of Df-Th workflow is adopted instead. The variant of Df-Th workflow consists of the following building blocks:
  + **Axiom**: Only present in those files in the very beginning.
  + **Definition**
  + **Theorem**: A theorem must be also followed by a proof. Theorems are also of different importance, since some theorems dipict the core of the some theory, while others are just some scaffolds. Thus besides the important theorems (assigned with a **Theorem** block), there are also the following blocks. Of course, all these above are just essentially theorems, they are all belongs to the "Th" part of the Df-Th workflow, and are said to have the **validity of theorem**.
    + **Lemma**
    + **Property**
    + **Corollary**
    + **Example**
    + **Exercise**
  + **Remark**: A remark block is a further illustration of a definition or a theorem. Each definition block or theorem block can be followed by at most one remark block.

Actually, the develepment of math theory is a huge project, which is filled with massive trivial definitions and theorems. **Hence, to assign a block for each definition and theorem is not practical, and what mathematicians do is to insert the trivial definitions and theorems into the remark blocks.** Each theorem, theoriotically, must be proved, but for those evident, we had better to omit that.

The differenciation of "lemma", "property", "corollary" and so on is actually involved after some time of learning. In the very beginning when I was unconscious about this, I just simply set two importance levels for theorems.
## 4. Customized Writing in Different Files

### 4.1 Notes
Notes files record the notes I have taken during the courses learning. A notes file is more like a dictionary, which just take everything into consideration.  

### 4.2 Problems
Problems files record the mathematical problems I have done research on. Actually, I would just record some small problems since a formal professional math problem is of course recorded with a paper. 

No problems recorded yet. To be done.

### 4.3 Insights
Insights files record the insights I have summarized. In the insights files, the order in which I propose the definitions and theorems is not only chronological, but also logical, fluent, and reasonable for the readers to understand. In other words, the insights files focus more on the ideas, connections, motivations and applications, rather than the details of the proofs. 

In the insights files, a remark block is often rather long, as it must act as a connecting link between the preceding and the following blocks. 

## 5. Chronological Consistency
All the notes, problems, and insights files in the entire repository share the same chronological order, which called **my main-branch**. In this branch, every block must not be in conflict with any previous blocks. For those blocks that contains multiple definitions or theorems, (such as a long remark block), the internal "Df" and "Th" must also keep the consistency.

## 6. Hierarchy of the Repository
In the repository directory, the logical hierarchy is: 
`field -> course -> chapter`.

and the physical hierarchy (namely, the actual directory structure) is:
`home/course/chapter/file`.

### 6.1 Field
As the courses learned increase, I would be navigating between different fields in math. Hence in the future, the courses will be organized in the corresponding fields. On that day, the courses-based organization of the repository will not change, but a new file named `fields.md` will be added in the repository directory and maintained. 

### 6.2 Chapter
A course is divided into chapters, as it is impractical to put all chapters in one file. Each chapter of content is written in some `.tex` files (note files, problem files or insight files).

### 6.3 File
In the early design of this repository, I planned to record all the contents of one chapter in a single file. But with the increasing need of insights, it is better to separate them into the four genres of files.

## 7. Formatted Timestamp
The physical structures of different hierarchy levels must be coded in a unified timestamp format:
+ Course: the **course ID** is an integer within `[0, 99]` (as I do not expect to learn more than 100 courses in my life)
+ Chapter: the **chapter ID** is a non-negative integer.
+ File: the **file ID** is a non-negative integer prefixed with the genre of the file (`I` for insight, `P` for problem, and none for note). For example, the file ID `I3` refers to the **3rd insight file** of this chapter. 
+ Block: every block except the remark blocks is assigned with a **block ID**. A block ID is a lexical tuple of integers prefixed with the chapter ID and the file ID. For example, the block ID `3_I2.4` is the block `4` in the file `I2` of the chapter `3`, `3_P2.4.5` is the block `4.5` in the file `P2` of the chapter `3`, `3.6.1` is the block `6.1` in the note file of chapter `3`. **The block ID within the chapter**, is the remaining part of the block ID after removing the prefix. For example, for the block ID `3_P2.4.5`, the block ID within the chapter is `4.5`.  The block ID is a lexical tuple of integers, representing the main-branch order:
  + `3.2` is before `3.3`, `3.3.1` is before `3.3.2` and `3.3.4` is before `3.4.3`.
  + `3.2` is before `3.2.1`, as `3.2` is actually `3.2.0` (exactly, it is `3.2.0.0.0. ...`). A block ID within the chapter is a lexical sequence infinite of integers, where those digits after the last presented digit are all zeros.
  + Each digit in the ID can be any integer, even negative. For example, `3.2.-1` is before `3.2` and `3.2.-2` is before `3.2.-1`.
  + As for the blocks in different genres of files, the first digit of the block ID is claimed to be equal. For example, in the 3rd chapter, the prefixes `3`, `3_I1`, `3_P2`, `3_P3` or others are equal. This design is just as claimed above that I just distribute the chapters into the four genres of files.

### 7.1 Reference to the Timestamp
To refer to a certain block in the writing, the **entire ID** of the block must be presented. The entire ID is the lexical tuple concatenating the course ID and the block ID, in the format `{course: [course ID], ID: [block ID]}`. For example, `{course: 3, ID: 4.5}` refers to the block with the block ID `4.5` in the 3rd course, and `{course: 3, ID: 4_P2.3.1}` refers to the block with the block ID `4_P2.3.1` in the 3rd course. Sometimes for convenience, we can omit the course ID, like `{, ID: 4_P2.3.1}`, if the referred block is in the current course. 

To refer to a remark block, we can use the entire ID of the block that the remark block follows (this block has an ID). For example, the remark `{, ID: 4_I2.3.1}` refers to the remark block that follows the block with the ID `4_I2.3.1` in the current course.

To refer to a proof, just use the entire ID of the proved theorem. 

## 8 Flexible Writing and Other Details
### 8.1 Hard Proofs
The proof for each non-trivial theorem is necessary. However there are always some theorems whose proof exceeds the scope of the current learning. In this case, without cyclic reasoning, we can just leave the proof to the future blocks, or just mark it as "todo" to wait for the future completion.

### 8.2 Change of Definitions of Terms
Clearly a definition assigns a term to a certain situation. But it is also often the case that we change our understanding to one concept, but still want to keep the original term. In this case, the definition of the term is changed, which was considered illegal in our early design. Then here is our solution:

> Suppose we first define a term $d$ to be the situation $A$, at the timestamp $t_A$. After we learn and write down some Df or Th blocks, we find that using $d$ for $A$ is no longer appropriate. Then we can change the meaning of $d$ from $A$ to a new meaning $B$ at the timestamp $t_B$ (where $t_B > t_A$), and the consistency of the system is still kept, by identifying $d$ as $A$ in any blocks proposed in $[t_A, t_B)$, and as $B$ in any blocks proposed in $[t_B, \infty)$. If in the future $d$ is changed again to a new meaning $C$ at the timestamp $t_C$, then we identify $d$ as $B$ in any blocks proposed in $[t_B, t_C)$, and as $C$ in any blocks proposed in $[t_C, \infty)$.

In the actual writing, we avoid changing the definition of a term at most of the time unless it is necessary. Thus the number of such terms is limited compared to the total number of terms (or blocks). To remind the reader of the change of definition, we must specify all of these terms by

> listing them, along the timestamps when they are proposed and changed, in a global file `terms_changed.md` stored in the root directory of the repository. 

When editing the `terms_changed.md` file, we list the terms in the alphabetical order. When reading and using a Df or Th block (or a statement of Df or Th validity), we must be clear about which meaning the term involved refers to, by checking the `terms_changed.md` file.

To further limiting the number of terms that are changed, we ignore a type of implicit change of definition: the **definition generalization**. For example, we defined the limit of a sequence in $\mathbb{R}$ in the chapter 1 of the course 2, and then defined the limit of a sequence in $\mathbb{R}^n$ in the chapter 4 of the course 2. Both definitions are referred to by the same term "limit", but they are indeed different since the former is a special case of the latter. However we would not list it in the `terms_changed.md` file, as we can easily figure out which meaning the term "limit" refers to anywhere during the learning.

### 8.3 Shorthands for Blocks
+ **Axiom** -> **Ax**
+ **Definition** -> **Df**
+ **Theorem** -> **Th**
  + **Lemma** -> **Lma**
  + **Property** -> **Prpty**
  + **Corollary** -> **Clry**
  + **Example** -> **Eg**
  + **Exercise** -> **Ex**
+ **Remark** -> **Rmk**

In the writing, I use two colors to distinguish the blocks of definitions validity and theorems validity. And each block is marked with its type (an axiom or a definition or others) and its timestamp.

When refer to a block, it is better to also specify the shorthand.

### 8.4 Reuse of Notations
The notations human uses are limited, and the math expressions are expected to be precise and concise. Hence we can reuse the notations for different meanings, as long as we take the approach of **"locality"** to avoid confusion. 

> If notation "a" is claimed for concepts "A" and "B", then you can distinguish the exact meaning by the context in most of the time. If you fail to figure out which of "A" and "B" the notation actually refers to, then the most "local" claim is the correct one (if "a for A" is claimed in the current chapter and "a for B" is claimed in some previous chapter of the current course, then "A" is said to be more "local" than "B"). For a claim of notation, the most "local" claim is the one in the current chapter (no matter in which file of the chapter) and there are no different claim in the same chapter.
>

### 8.5 Naming Convention
Here is the naming convention for the directories and files in the repository:
+ Course directory: `[course ID].[course name]`
+ Chapter directory: `[chapter ID].[chapter name]`
+ Chapter note file: `[chapter name].tex`
+ Chapter problem file: `P[problem number]. [problem name].tex`
+ Chapter insight file: `I[insight number]. [insight name].tex`

PS: the `chapter name` in the chapter file and the corresponding chapter directory keeps the same.
### 8.6 Validity Marks
When inserting a definition or a theorem in a remark block, I use the corresponding color to mark the validity of the text.

### 8.7 Block Copy-Back Mechanism
Sometimes a block is proposed in a file, but you would use this block (e.g. illustrate based on this block of theorem) later in some earlier files, without cyclic reference. Theoretically, all blocks in a file share the same prefix of the block ID, and thus a block in an earlier file is before any block in a later file, which means you cannot simply do this.

To solve this problem, we propose the **Block Copy-Back Mechanism**. In an earlier file, when you need to use a block proposed in a later file, you can just copy the block to some appropriate place (maybe an even earlier file) so that this duplicated block can be referred to, **as long as you have checked that this block can be supported by the content before the copy destination (i.e. check that no cyclic reference is made).**

Note that this copy-back machanism is not an manual operation, which means that you do not need to really copy the block's code to the earlier file. You just need to first claim the block in the earlier file (with the timestamp, shorthand and other information you want to show) and then refer to the original block in this claim (with the entire block ID of the original block). 

> **About Cyclic Reference**: 
> It is necessary to check the cyclic reference when apply the copy-back operation. If the original block is based on something after the copy-back destination, then this is a cyclic reference. However, this restriction can be further loosened. If the original block can be verified as able to be proposed only based on the content before the copy-back destination, even if the original block is literally based on something after the copy-back destination, then there is actually no cyclic reference and the copy-back operation is still valid. 

Copy-back operation is very useful. For example, an insight is often concluded from files of different periods of time, and some valuable conclusions in this insight file can be used in some earlier files. If the latest referred block in the insight file is proposed in the chapter 5, then this insight file must not before the chapter 5. And in this case, if the insight file draw a pretty valuable conclusion only based on the content before the chapter 2, then this conclusion can be copy-back to the chapter 2 without cyclic reference, so that the fruit of the insight can benefit the theory development in the chapter 2.

### 8.8 Fixed Sentence Patterns
A definition is just to pack some propositions. For example, the definition of vector space packs several operational properties including the commutativity, associativity, distributivity, and so on. A theorem is to link some propositions, which links the premises to the conclusion. In writing a definition or a theorem, the following sentence patterns are often used:
+ **Definition**: **`[Suppose / Let / ... ] (1). Then (2) [is called / is said to be / is defined as / ... ] (3) if (4).`** Here the stuff within `[]` are necessary but with multiple options. In this pattern, `(1)` and `(4)` are the premises for the terminology "`(2)` to be `(3)`". **Note that a definition is always a "if and only if" statement, which means that we say `(2)` to be `(3)` exactly when both `(1)` and `(4)` are satisfied.**
+ **Theorem**: **`[Suppose / Let / ... ] (1). (If (2),) then (3).`** Here `(1)` and `(2)` are the premises, and `(3)` is the conclusion. The `If (2),` part is optional since `(2)` is just a part of the whole premises.

Above we have seen the sentence pattern of definition and theorem, where the whole premise is divided into multiple parts (e.g. some part lead by "Suppose" and some part lead by "if" and so on). One purpose for doing this is to alleviate the impact of the **definition shifting**. 

A definition delimits the exact range of cases where we say the definition terminology (as above, the terminology "`(2)` to be `(3)`"), and normally, a definition cannot shifts the cases which its terminology refers to. However, this shifting can happen when we persuit the flexibility of writing. For example, the methodology "definition generalization" mentioned above is a kind of shifting, where a generalized definition shifts the cases to a wider range.

A shifted definition may has an impact on other definitions and theorems based on it. The shifted definition may appear in the premises or conclusions of other definitions or theorems. Hence, distributed the premises into multiple parts can alleviate the impact of the shifting. 

### 8.9 Exercise Bank
Exercises is a good way to test and consolidate the knowledge. Within the folder of a chapter (resp. a course), there can be one (but not more) file named `exercises.md` to collect some valuable exercise blocks presented in the chapter (resp. in the course). One `exercises.md` file is called the **Exercise Bank** of the corresponding chapter (resp. course). The instructions of exercise banks are as follows:

(1) One chapter or one course can have **at most one** exercise bank, where you extract some valuable exercises from the corresponding chapter or course and put them all in this bank. 

(2) **This bank has no definition or theorem validity**, as it is not allowed to propose any definition or theorem in this bank.

(3) When including some exercise block into the bank, you are required to specify the entire reference of the block (see 7.1). You do not need to copy any content of the exercise after you correctly refer to the block.

(4) It is recommended to specify the **source** of the exercise (from which book, from which webpage or proposed by whom). Feel free on the format of the source as long as you can relocate the exercise in future.

(5) It is also recommended to make a rating to an exercise. This **rate** to an exercise is a complex number which reflects roughly its importance and difficulty, with the real component for "difficulty" and the imaginary component for "importance". It should be noted that the rating of one exercise can be changed over time. Now is the **rating rule**. 
> Begin at score 0, each time I want to try on the exercise I will update the rate. If I can solve it, then add $i$ to the rating; if I cannot answer it or I finally give a wrong solution, then add $1+i$ to the rating. Each trial on solving an exercise, it is recommended to be familiar with the corresponding content beforehand and to limit the time.

So the rating $r$ of an exercise is a complex number, where a larger $\text{Re}(r)$ means a higher difficulty and a larger $\text{Im}(r)$ means a higher importance. The square of the absolute value $|r|^2$ is the **overall score** of the exercise.

(6) Exercises and examples: the two types of blocks — exercises (Ex) and examples (Eg) — differ little actually. Assign either an Ex block or an Eg block to record a given instance. Since then, **the influential Eg blocks (essential, introductive to the understanding of knowledge) should be included in the exercise bank.** 

### 8.10 Pre-exercise and Post-exercise
Exercises needs reflection and summerization. If a proof or a solution is complete in your own work, it is worthwhile to record the **train of thought** called the **pre-exercise**. After solving the exercise — especially when you must refer to some other materials to solve it — it is suggested to write down some **experiences** called the **post-exercise**.

> **Pre & Post Exercise pattern**: 
> optional pre-exercise part + concise formal solution + optional post-exercise part.

In note files, you are strongly recommended to follow the **pre & post exercise pattern**; while in insight files it does not matter since there we often take a more flexible writing style.

In insight files, it is not necessary to follow the pre-exercise and post-exercise pattern.

### 8.11 Restatement of Definitions and Theorems
Sometimes there is no time to formulate a decent insight file for the newly learned content (or I am just not capable for that extent of comprehension). In this case, it is encouraged to temporarily write down the knowledge in the note file, and then supplement the insight file whenever possible. 

In the insight file at that time, some, or most, of the definitions and theorems may have been proposed in the note file. Then we can just restate them wherever in need in the insight file, for the convenience and the coherence of the writing.

This time of restatement can be assigned with new blocks (including new block IDs) in the insight file. But these blocks do not yield validity, instead, they are just copies of the original blocks in the previously written note file. **Thus we should mark these blocks with a non-validity sign** "nv". And now that these new blocks are not to hold validity, especially for theorem blocks, they can be proposed without a rigorous proof.

### 8.12 Maintain the Consistency during Block-Insertion
It is often the case that you turn back to insert a new block in a previously written file. For example, in some moment, you may want to supplement a new theorem `Th` for the moment to use, and you open an appropriate note file `N` and find the appropriate place, say, between the adjacent blocks `{, ID: 1.3.1}` and `{, ID: 1.4}`. And, you assign the ID `1.3.2` to `Th` and insert it at the empty lines in the file `N` between the two blocks.

Since within `N` all blocks are in the main-branch order, this process seems OK. However, you must be cautious if there are some other files in the same chapter. For example, if there is an insight file `I` in the same chapter, and the ID `{, ID: 1_I.3.2}` has been used, then things go wrong as you would overlook the file `I`.

To solve this problem, we make the following regulation:
> 1. Every time new a chapter folder, the corresponding note file `N` must be first initialized, and the other genres of files (if you have) follow second.
> 2. In general you edit a file in the ``append-only'' mode — append in the main-branch order. If in some moment you are not **appending**, but writing a block with (either Df or Th) validity elsewhere in the file, you are just doing **insertion**. Besides, **every time you write a block with validity in some other file besides** `N`, **you are also doing insertion.** Insertion must follow the regulations below.
> 3. **Insertion by newing a non-note file (which is about to hold validity) `I`**: write a **reminder block** at the desired position — say, between the adjacent blocks `{, ID: 1.3.1}` and `{, ID: 1.4}` — to indicate that some blocks with validity are inserted here.
> 4. **Insertion by write a block with validity in `I`**: suppose the reminder block of `I` is **exactly between** the blocks with IDs `id1` and `id2` (`id1` is before `id2`) in this moment, **keep the written block's timestamp after `id1`, before `id2` and in the right order within `I`**. 
> 5. **Insertion by write a block with validity in `N`**: if in that moment, one or both of the adjacent positions of the written block are some reminder blocks, say, the next (resp. the last) position is, then keep the timestamp of the written block **before the first block (resp. after the last block) with validity in the file referred by the reminder block**.

### 8.13 Personal Notations
Sometimes some personal notations are used in place of the standard notations (in the math literature) for the sake of convenience. In this case the personal notations should be claimed as "personal" in the block proposing the notation.

### 8.14 Hint step
It is widely acknowledged by math learners that a proof easy to check is usually written in a reverse order of the thinking chain, and thus is usually hard to think of. To balance the checkability and the thinkability, we can still write the proof easy to check, but ``reverse the order'' at some critical steps, that is, give some hints. 

An example of hint step can be seen in the writing of equality. For some equality $a = b$, it is often the case that given $b$ we can notice $b=a$, but given $a$ we may fail to notice $a=b$. In this case we had better to hint $b$ (possibly mark $b$ in another color). For a continued equality $a = b = c = d$ we may want to prove $a = d$. But if $b=c$ is hinted we mean that we first notice $b=c$, and then notice $c=d$ and $b=a$. Such trick can be seen in the proof of the theorem `{course: 5, ID: 2_P2.4.3.2.3 }`, and this way we can exhibit our chain of thought. 