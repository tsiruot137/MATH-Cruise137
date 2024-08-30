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

### 4.4 Insights
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
  + As for the blocks in different genres of files, the first digit of the block ID is claimed to be equal. For example, in the 3rd chapter, the prefixes `3`, `3_I1`, `3_P2`, `3_P3`, `3_E4`, `3_E5` or others are equal. This design is just as claimed above that I just distribute the chapters into the four genres of files.

### 7.1 Reference to the Timestamp
To refer to a certain block in the writing, the **entire ID** of the block must be presented. The entire ID is the lexical tuple concatenating the course ID and the block ID, in the format `{course: [course ID], ID: [block ID]}`. For example, `{course: 3, ID: 4.5}` refers to the block with the block ID `4.5` in the 3rd course, and `{course: 3, ID: 4_P2.3.1}` refers to the block with the block ID `4_P2.3.1` in the 3rd course. Sometimes for convenience, we can omit the course ID, like `{, ID: 4_P2.3.1}`, if the referred block is in the current course. 

To refer to a remark block, we can use the entire ID of the block that the remark block follows (this block has an ID). For example, the remark `{, ID: 4_I2.3.1}` refers to the remark block that follows the block with the ID `4_I2.3.1` in the current course.

To refer to a proof, just use the entire ID of the proved theorem. 

## 8 Flexible Writing and Other Details
### 8.1 Hard Proofs
The proof for each non-trivial theorem is necessary. However there are always some theorems whose proof exceeds the scope of the current learning. In this case, without cyclic reasoning, we can just leave the proof to the future blocks, or just mark it as "todo" to wait for the future completion.

### 8.2 Definition Generalization
The learning of math is from concrete to abstract, thus sometimes a proposed definition is a special case of a more general definition (the latter may not be always noted by me). Hence, it is natural and practical to propose the specific definition first, and add the general one in the future, with the consistency guaranteed (for example, we can first propose the Df of the limit of sequence in $\mathbb{R}$, and add the definition of limit of sequence in $\mathbb{R^n}$, as long as the latter reduces to the former if $n=1$ and no other definitions and theorems is influenced).

### 8.3 Reuse of Notations
The notations human uses are limited, and the math expressions are expected to be precise and concise. Hence we can reuse the notations for different meanings, as long as we take the approach of **"locality"** to avoid confusion. 

> If notation "a" is claimed for concepts "A" and "B", then you can distinguish the exact meaning by the context in most of the time. If you fail to figure out which of "A" and "B" the notation actually refers to, then the most "local" claim is the correct one (if "a for A" is claimed in the current chapter and "a for B" is claimed in some previous chapter of the current course, then "A" is said to be more "local" than "B"). For a claim of notation, the most "local" claim is the one in the current chapter (no matter in which file of the chapter) and there are no different claim in the same chapter.
>

### 8.4 Shorthands for Blocks
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

(2) This bank has no definition or theorem validity, as it is not allowed to propose any definition or theorem in this bank.

(3) When including some exercise block into the bank, you are required to specify the entire reference of the block (see 7.1). You do not need to copy any content of the exercise after you correctly refer to the block.

(4) It is recommended to specify the **source** of the exercise (from which book, from which webpage or proposed by whom). Feel free on the format of the source as long as you can relocate the exercise in future.

(5) It is also recommended to make a rating to an exercise. This **rate** to an exercise is a complex number which reflects roughly its importance and difficulty, with the real component for "difficulty" and the imaginary component for "importance". It should be noted that the rating of one exercise can be changed over time. Now is the **rating rule**. 
> Begin at score 0, each time I want to try on the exercise I will update the rate. If I can solve it, then add $i$ to the rating; if I cannot answer it or I finally give a wrong solution, then add $1+i$ to the rating. Each trial on solving an exercise, it is recommended to be familiar with the corresponding content beforehand and to limit the time.

So the rating $r$ of an exercise is a complex number, where a larger $\text{Re}(r)$ means a higher difficulty and a larger $\text{Im}(r)$ means a higher importance. The square of the absolute value $|r|^2$ is the **overall score** of the exercise.

### 8.10 Pre-exercise and Post-exercise
Exercises needs reflection and summerization. If a proof or a solution is complete in your own work, it is worthwhile to record the **train of thought** called the **pre-exercise**. After solving the exercise — especially when you must refer to some other materials to solve it — it is suggested to write down some **experiences** called the **post-exercise**.

> **Pre & Post Exercise pattern**: 
> optional pre-exercise part + concise formal solution + optional post-exercise part.

In note files, you are strongly recommended to follow the *pre & post exercise pattern*; while in insight files it does not matter since there we often take a more flexible writing style.

In insight files, it is not necessary to follow the pre-exercise and post-exercise pattern.