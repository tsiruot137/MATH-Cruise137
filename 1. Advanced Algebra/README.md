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
The Df-Th workflow basically consists of definitions and theorems. A definition or a theorem is written as a building block that takes up a region of a file, with a formatted **timestamp** representing the logic time when the definition or the theorem is proposed.
## 4. Customized Orgnanization in Different Files
Although the three genres of files share the same basic composition, they are actually organized in their corresponding variants of the Df-Th workflow. 
### 4.1 Notes
Notes files are the major part of the repository, which records the entire process of math theory's development. Notes files act as the source of the problems files and insights files. The notes-variant of the definition-theorem workflow consists of the following building blocks:
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

The differenciation of "lemma", "property" and "corollary" is actually involved after some time of learning. In the very beginning when I was unconscious about this, I just simply set two importance levels for theorems.

### 4.2 Problems
Problems files record the mathematical problems I have done research on. Actually, I would just record some small problems since a formal professional math problem is of course recorded with a paper. 

No problems recorded yet. To be done.

### 4.3 Insights
Insights files record the insights I have summarized. Similar to the notes-invariant, the insights-variant of the definition-theorem workflow consists of the following building blocks:
  + **Definition**
  + **Theorem**
  + **Remark**

In the insights files, the order in which I propose the definitions and theorems is not only chronological, but also logical, fluent, and reasonable for the readers to understand. In other words, the insights files focus more on the ideas, connections, motivations and applications, rather than the details of the proofs. 

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
A course is divided into chapters, as it is impractical to put all chapters in one file. Each chapter of content is written in a **single** `.tex` file (note file, problem file, or insight file).

## 7. Formatted Timestamp
The physical structures of different hierarchy levels must be coded in a unified timestamp format:
+ Course: the course ID is an integer within `[0, 99]` (as I do not expect to learn more than 100 courses in my life)
+ Chapter: the **chapter ID** is a lexical pair of two integers. For example, the chapter ID `3_2` refers to the **2nd article** (a problem file or an insight file) when learning the 3rd chapter of the course. When learning a chapter, the note file is always placed before the problem file and the insight file, and the note. Hence the note file is always the 0th article, i.e. here assigned with the chapter ID `3_0` (`3` for short). **Here every digit of the chapter ID can only be a non-negative integer.**
+ Block: every block except the remark blocks is assigned with a **block ID**. A block ID is a lexical tuple of integers, comprised of the chapter ID and the **block ID within the chapter**. For example, the block ID `3_2.4` is the block `4` in the chapter `3_2`, `3_2.4.5` is the block `4.5` in the chapter `3_2`, `3.6.1` is the block `6.1` in the chapter `3` (namely, the chapter `3_0`). **The block ID within the chapter is a lexical tuple of integers, representing the main-branch order:** 
  + `3.2` is before `3.3`, `3.3.1` is before `3.3.2` and `3.3.4` is before `3.4.3`.
  + `3.2` is before `3.2.1`, as `3.2` is actually `3.2.0` (exactly, it is `3.2.0.0.0. ...`). A block ID within the chapter is a lexical sequence infinite of integers, where those digits after the last presented digit are all zeros.
  + Each digit in the ID can be any integer, even negative. For example, `3.2.-1` is before `3.2` and `3.2.-2` is before `3.2.-1`.

### 7.1 Reference to the Timestamp
To refer to a certain block in the writing, the **entire ID** of the block must be presented. The entire ID is the lexical tuple concatenating the course ID and the block ID, in the format `{course: [course ID], ID: [block ID]}`. For example, `{course: 3, ID: 4.5}` refers to the block with the block ID `4.5` in the 3rd course, and `{course: 3, ID: 4_2.3.1}` refers to the block with the block ID `4_2.3.1` in the 3rd course. Sometimes for convenience, we can omit the course ID, like `{, ID: 4_2.3.1}`, if the referred block is in the current course. 

To refer to a remark block, we can use the entire ID of the block that the remark block follows (this block has an ID). For example, the remark `{, ID: 4_2.3.1}` refers to the remark block that follows the block with the ID `4_2.3.1` in the current course.

To refer to a proof, just use the entire ID of the proved theorem. 

## 8 Flexible Writing and Other Details
### 8.1 Hard Proofs
The proof for each non-trivial theorem is necessary. However there are always some theorems whose proof exceeds the scope of the current learning. In this case, without cyclic reasoning, we can just leave the proof to the future blocks, or just mark it as "todo" to wait for the future completion.

### 8.2 Definition Generalization
The learning of math is from concrete to abstract, thus sometimes a proposed definition is a special case of a more general definition (the latter may not be always noted by me). Hence, it is natural and practical to propose the specific definition first, and add the general one in the future, with the consistency guaranteed (for example, we can first propose the Df of the limit of sequence in $\mathbb{R}$, and add the definition of limit of sequence in $\mathbb{R^n}$, as long as the latter reduces to the former if $n=1$).

### 8.3 Reuse of Notations
The notations human uses are limited, and the math expressions are expected to be precise and concise. Hence we can reuse the notations for different meanings, as long as we take the approach of **"locality"** to avoid confusion. 

> If notation "a" is claimed for concepts "A" and "B", then you can distinguish the exact meaning by the context in most of the time. If you fail to figure out which of "A" and "B" the notation actually refers to, then the most "local" claim is the correct one (if "a for A" is claimed in the current chapter and "a for B" is claimed in some previous chapter of the current course, then "A" is said to be more "local" than "B").
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

### 8.5 Validity Marks
When inserting a definition or a theorem in a remark block, I use the corresponding color to mark the validity of the text.

## 9. Last Modified: 2024-7-5