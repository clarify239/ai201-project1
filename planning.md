# Project 1 Planning: The Unofficial Guide

> Write this document before you write any pipeline code.
> Your spec and architecture diagram are what you'll use to direct AI tools (Claude, Copilot, etc.) to generate your implementation — the more specific they are, the more useful the generated code will be.
> Update the Retrieval Approach and Chunking Strategy sections if you change your approach during implementation.
> Update this file before starting any stretch features.

---

## Domain

<!-- What domain did you choose? Why is this knowledge valuable and hard to find through official channels? -->
> My domain is a guide to CS courses at Cornell University. Official course descriptions list topics and prerequisites, but they often do not include student experiences such as workload, grading style, etc. This knowledge is valuable because students use it to make realistic schedules, and it is scattered across many sources. 

---

## Documents

<!-- List your specific sources: URLs, subreddit names, forum threads, or file descriptions.
     Aim for at least 10 sources that together cover different subtopics or perspectives within your domain. -->

| # | Source | Description | URL or location |
|---|--------|-------------|-----------------|
| 1 | RateMyProfessor | Includes professor reviews and look for professors who teach courses that start with CS or INFO| https://www.ratemyprofessors.com/|
| 2 | Cornell Course Catalog FA26| Includes all CS classes for Fall 2026| https://classes.cornell.edu/search/roster/FA26?q=&subjects%5B%5D=CS&days-type=any&distrReqs-type=any&explStudies-type=any&pi= |
| 3 | Cornell CS Wiki| Already contains some compiled information about CS classes at Cornell | https://cornellcswiki.gitlab.io/#cs-classes |
| 4 | Reddit | Scour the r/Cornell subreddit for information about Computer Science (CS) classes| https://www.reddit.com/r/Cornell/search/?q=CS&cId=4da5b906-9269-458a-bc38-f1d392c7b817&iId=efa91c2a-6a69-484f-b1b3-b331dbb949ce|
| 5 | CS Wiki CS1110| Information about CS1110|https://cornellcswiki.gitlab.io/classes/CS1110.html |
| 6 | CS Wiki CS2110| Information about CS2110| https://cornellcswiki.gitlab.io/classes/CS2110.html|
| 7 |CS Wiki CS3110 | Information about CS3110 |https://cornellcswiki.gitlab.io/classes/CS3110.html |
| 8 | CS Wiki CS4780 | Information about CS3780| https://cornellcswiki.gitlab.io/classes/CS4780.html|
| 9 | Cornell Course Catalog SP26 | Includes all CS courses for Spring 26| https://classes.cornell.edu/search/roster/SP26?q=&subjects%5B%5D=CS&days-type=any&distrReqs-type=any&explStudies-type=any&pi= |
| 10 |Reddit User Class Ranking | Includes a Reddit users ranking for the CS classes they've taken at Cornell | https://www.reddit.com/r/Cornell/comments/1cwhzr2/also_ranking_every_course_ive_ever_taken_at/|
| 11 | Cornell Class Catalog | Courses offered at Cornell| https://courses.cornell.edu/courses/cs/ | 
| 12 | Cornell CS BA | Degree requirements to get a BA in CS at Cornell | https://www.cs.cornell.edu/bachelor-arts-computer-science |
| 13 | Cornell CS BS | Degree requirements to get a BS in CS at Cornell | https://bowers.cornell.edu/bachelor-science-computer-science | 
---

## Chunking Strategy

<!-- How will you split documents into chunks?
     State your chunk size (in tokens or characters), overlap size, and explain why those
     numbers fit the structure of your documents.
     A review-heavy corpus warrants different chunking than a long FAQ. -->

**Chunk size:**

**Overlap:**

**Reasoning:**

---

## Retrieval Approach

<!-- Which embedding model are you using (e.g., all-MiniLM-L6-v2 via sentence-transformers)?
     How many chunks will you retrieve per query (top-k)?
     If you were deploying this for real users and cost wasn't a constraint, what tradeoffs
     would you weigh in choosing a different embedding model — context length, multilingual
     support, accuracy on domain-specific text, latency? -->

**Embedding model:**

**Top-k:**

**Production tradeoff reflection:**

---

## Evaluation Plan

<!-- List your 5 test questions with their expected correct answers.
     Questions should be specific enough that you can judge whether the system's response
     is right or wrong. "What are good dining halls?" is too vague.
     "What do students say about wait times at [dining hall name] during lunch?" is testable. -->

| # | Question | Expected answer |
|---|----------|-----------------|
| 1 | | |
| 2 | | |
| 3 | | |
| 4 | | |
| 5 | | |

---

## Anticipated Challenges

<!-- What could go wrong? Name at least two specific risks with reasoning.
     Consider: noisy or inconsistent documents, missing source attribution, off-topic
     retrieval, chunks that split key information across boundaries. -->

1.

2.

---

## Architecture

<!-- Draw a diagram of your pipeline showing the five stages:
     Document Ingestion → Chunking → Embedding + Vector Store → Retrieval → Generation
     Label each stage with the tool or library you're using.
     You can use ASCII art, a Mermaid diagram, or embed a sketch as an image.
     You'll use this diagram as context when prompting AI tools to implement each stage. -->

---

## AI Tool Plan

<!-- For each part of the pipeline below, describe:
     - Which AI tool you plan to use (Claude, Copilot, ChatGPT, etc.)
     - What you'll give it as input (which sections of this planning.md, which requirements)
     - What you expect it to produce
     - How you'll verify the output matches your spec

     "I'll use AI to help me code" is not a plan.
     "I'll give Claude my Chunking Strategy section and ask it to implement chunk_text()
     with my specified chunk size and overlap" is a plan. -->

**Milestone 3 — Ingestion and chunking:**

**Milestone 4 — Embedding and retrieval:**

**Milestone 5 — Generation and interface:**
