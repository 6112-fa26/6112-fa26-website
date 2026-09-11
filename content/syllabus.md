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

The main component of this course is a project where you will build a language implementation almost entirely from scratch. The first two phases (which cover parsing, lexing, and interpretation) of the project will be done individually, and the rest of the project will be done in groups of two.
Details about the project can be found on the [project overview][project] page. Specific instructions for each phase of the project will be released later in the class.

## Class

See [Class Meetings](@/schedule.md#class-meetings) for class times and locations.

_Lectures_ will cover the fundamental concepts and structures of dynamic programming languages. _Recitations_ will focus more on the project and tutorial content. (Please *disregard* the listing of "lectures" versus "recitations" on Hydrant/course registrar.)

 __Please check the [course calendar][calendar] regularly.__ Lecture dates are not all finalized at the start of the semester. Some lectures may be canceled or moved depending on the class's comfort and progress on the projects.

There will be weeks that have few or no lectures, especially as we draw closer to project deadlines. This year, we are projecting roughly 8 weeks of lectures in total. We will also announce urgent changes on [Piazza][piazza].

#### Missed Classes

If you have taken [6.110](https://6110-sp25.github.io), you may be familiar with the re-lecture videos which are video recordings of lecture content. 6.112 will not have any re-lectures for this offering. Lecture slides and recitation materials will still be available on this website; however, you are personally responsible for catching up on any missed content on your own.

## Office Hours
See the [office-hours schedule][office-hours] for more information.

## Quizzes
Two quizzes will be held during class time. Please check the [course calendar][calendar] for the dates. More information about quizzes, including practice material, will be released closer to the quiz dates.

## Grading

Your grade is based upon three components: the project (65%), two quizzes (30%, 15% each), and class participation (5%). 

| Component                          | Weight |
| ---------------------------------- | ------ |
| Project phases 1 and 2 (combined)   | 5%     |
| Project phase 3 (memory management) | 10%    |
| Project phase 4 (virtual machine)   | 20%    |
| Project phase 5 (derby)             | 30%    |
| Quizzes (15% each)                 | 30%    |
| Class participation                | 5%     |

## Late Policy

We will accept late final submissions for any reason up to 72 hours after the deadline. 10% will be deducted for a submission that's up to 24 hours late, 20% will be deducted for a submission that's up to 48 hours late, and 30% will be deducted for a submission that's up to 72 hours late. 

If you have additional extenuating circumstances, we can grant additional extensions (without penalty) as long as we get a note from [Student Support Services (S<sup>3</sup>)][s3].

## Collaboration Policy

While you may discuss the high-level approaches to the project with anybody, you must develop your code within your team (or by yourself for [phase 1][phase_1] and [phase 2][phase_2] of the project). In particular:
- You _are allowed_ to use reference material available online, as well as resources and existing libraries, as long as you cite them in your project reports, and they don't trivialize the project. (Please use your best judgment here, and ask the course staff if you are unsure.) If you decide to use larger code snippets, please also explain how you adapted and used them in your project report.
- You _are allowed_ to use LLM-generated code. Make sure to read [the AI policy](#ai-policy) below.
- You _may not_ share any code with other teams.
- You _may not_ post your project code on publicly accessible websites or file spaces, including public GitHub repositories.

## AI Policy

You are allowed to use AI in an unrestricted way, except for in-person evaluations.

More specifically, you are allowed to use LLM - generated code in your project, and use it to brainstorm ideas. However, you will need to maintain a firm graps of your codebase and an in depth understanding of the semantics of the language to perform well in the class.  

[004]: https://student.mit.edu/catalog/m6a.html#6.1910
[031]: https://student.mit.edu/catalog/m6a.html#6.1020
[catalog]: https://student.mit.edu/catalog/m6a.html#6.1120
[github]: https://github.com/6112-fa26/
[piazza]: https://piazza.com/mit/fall2026/61120/home
[gradescope]: https://www.gradescope.com/courses/1378085
[s3]: https://studentlife.mit.edu/s3
[phase_1]: @/project/phase_1.md
[phase_2]: @/project/phase_2.md
[textbooks]: @/resources.md#recommended-textbooks
[inspiration]: @/resources.md#other-sources-of-inspiration
[references]: @/resources.md#references
[calendar]: @/schedule.md#calendar
[office-hours]: @/schedule.md#office-hours
[project]: @/project/_index.md#introduction
