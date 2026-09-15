+++
title = "Syllabus"
weight = 10
template = "page.html"
+++
**Prereq:** [6.1020<sub>\[6.031\]</sub>][031] or [6.1910<sub>\[6.004\]</sub>][004]<br>
**Units:** 4-4-4<br>
**Class times and locations:** See [Class Meetings](@/schedule.md#class-meetings).

Studies the design and implementation of modern, dynamic programming languages. Topics include fundamental approaches for parsing, semantics and interpretation, virtual machines, garbage collection, just-in-time machine code generation, and optimization. Includes a semester-long, group project that delivers a virtual machine that spans all of these topics.

---

## Staff

#### Lecturers
[Michael Carbin](https://people.csail.mit.edu/mcarbin/) (<mcarbin@mit.edu>)

#### Teaching Assistant
Ege Kabasakaloglu (<egekabas@mit.edu>)

## Communication

- We will distribute assignments here and make all announcements via [Piazza][piazza]. Important announcements will also be made via email.
  - Office hours details will be announced on [Piazza][piazza].
  - Since lecture dates are not all finalized at the start of the semester, please check the [course calendar][calendar] regularly.
- For all general questions and/or concerns, please post publicly on [Piazza][piazza]. If the matter is private, please post privately on [Piazza][piazza].
- Surveys need to be completed via [Gradescope][gradescope].

**Gradescope enrollment code:** `ZPRXNZ`

## Recommended Texts

6.112 has no officially required textbook.

We can point you to [recommended textbooks][textbooks], [technical papers and useful blogs][inspiration], and [compiler reference guides][references].

## Project

The main component of this course is a project where you will build a language implementation almost entirely from scratch. Phases 1–3 (lexing and parsing, interpretation, and memory management) will be done individually. Phases 4–5 (the virtual machine and performance optimization) will be done in groups of two.
Details about the project can be found on the [project overview][project] page. Specific instructions for each phase of the project will be released later in the class.

### In-Person Evaluations

Phases 1–4 will each include a graded in-person evaluation in the form of a quiz held during regular class hours. Each quiz will cover material related to its corresponding project phase. Phase 5 will not have an in-person evaluation.

Please check the [course calendar][calendar] for the dates. More information, including practice material, will be released closer to each evaluation.

## Class

See [Class Meetings](@/schedule.md#class-meetings) for class times and locations.

_Lectures_ will cover the fundamental concepts and structures of dynamic programming languages. _Recitations_ will focus more on the project and tutorial content. (Please *disregard* the listing of "lectures" versus "recitations" on Hydrant/course registrar.)

 __Please check the [course calendar][calendar] regularly.__ Lecture dates are not all finalized at the start of the semester. Some lectures may be canceled or moved depending on the class's comfort and progress on the projects.

There will be weeks that have few or no lectures, especially as we draw closer to project deadlines. This year, we are projecting roughly 8 weeks of lectures in total. We will also announce urgent changes on [Piazza][piazza].

#### Missed Classes

If you have taken [6.110](https://6110-sp25.github.io), you may be familiar with the re-lecture videos which are video recordings of lecture content. 6.112 will not have any re-lectures for this offering. Lecture slides and recitation materials will still be available on this website; however, you are personally responsible for catching up on any missed content on your own.

## Office Hours
See the [office-hours schedule][office-hours] for more information.

## Grading

Your course grade is based on the five project phases, which total 100%. Class participation provides up to **5 additional percentage points of extra credit**.

| Component                          | Weight |
| ---------------------------------- | ------ |
| Project phase 1 (lexing and parsing) | 10%   |
| Project phase 2 (interpretation)    | 15%    |
| Project phase 3 (memory management) | 10%    |
| Project phase 4 (virtual machine)   | 35%    |
| Project phase 5 (derby)             | 30%    |
| Class participation (extra credit) | +5%    |

The grade for each phase will be determined by the submitted project code and, where applicable, the in-person evaluation.

## Late Policy

We will accept late final submissions for any reason up to 72 hours after the deadline. 10% will be deducted for a submission that's up to 24 hours late, 20% will be deducted for a submission that's up to 48 hours late, and 30% will be deducted for a submission that's up to 72 hours late. 

If you have additional extenuating circumstances, we can grant additional extensions (without penalty) as long as we get a note from [Student Support Services (S<sup>3</sup>)][s3].

## Collaboration Policy

While you may discuss the high-level approaches to the project with anybody, you must develop your code individually for phases 1-3, and only with your assigned partner for phases 4–5. In particular:
- You _are allowed_ to use reference material available online, as well as resources and existing libraries, as long as you cite them in your repository’s README and they don't trivialize the project. (Please use your best judgment here, and ask the course staff if you are unsure.) If you decide to use larger code snippets, please also explain how you adapted and used them.
- You _are allowed_ to use LLM-generated code. Make sure to read [the AI policy](#ai-policy) below.
- You _may not_ share any code with other teams.
- You _may not_ post your project code on publicly accessible websites or file spaces, including public GitHub repositories.

## AI Policy

You are allowed to use AI in an unrestricted way, except for in-person evaluations.

More specifically, you are allowed to use LLM-generated code in your project and use LLMs to brainstorm ideas. However, you will need to maintain a firm grasp of your codebase and an in-depth understanding of the semantics of the language to perform well in the class.

[004]: https://student.mit.edu/catalog/m6a.html#6.1910
[031]: https://student.mit.edu/catalog/m6a.html#6.1020
[catalog]: https://student.mit.edu/catalog/m6a.html#6.1120
[github]: https://github.com/6112-fa26/
[piazza]: https://piazza.com/mit/fall2026/61120/home
[gradescope]: https://www.gradescope.com/courses/1378085
[s3]: https://studentlife.mit.edu/s3
[textbooks]: @/resources.md#recommended-textbooks
[inspiration]: @/resources.md#other-sources-of-inspiration
[references]: @/resources.md#references
[calendar]: @/schedule.md#calendar
[office-hours]: @/schedule.md#office-hours
[project]: @/project/_index.md#introduction
