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
| 8 | CS Wiki CS4780 | Information about CS4780| https://cornellcswiki.gitlab.io/classes/CS4780.html|
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

**Chunk size:** 1200 characters

**Overlap:** 200 characters

**Reasoning:**
My documents include official course descriptions, Reddit posts, professor reviews, and CS Wiki pages. Many of these sources are short or medium-length, so a 1200 character chunk size should have related information together without making chunks too large. The 200 character overlap helps prevent important context from being split across chunk boundaries, especially when a course description, workload comment, or prerequisite explanation spans multiple paragraphs.

---

## Retrieval Approach

<!-- Which embedding model are you using (e.g., all-MiniLM-L6-v2 via sentence-transformers)?
     How many chunks will you retrieve per query (top-k)?
     If you were deploying this for real users and cost wasn't a constraint, what tradeoffs
     would you weigh in choosing a different embedding model — context length, multilingual
     support, accuracy on domain-specific text, latency? -->

**Embedding model:** Miini-M-L6-v2

**Top-k:** 5

**Production tradeoff reflection:**
For this project, all-MiniLM-L6-v2 is a good choice because it is lightweight, fast, and accurate enough for retrieving short course descriptions and student comments. If this system were deployed for real users and cost was not a constraint, I would consider a stronger embedding model with better accuracy and longer context length. Multilingual support is less important for this specific project because most of the sources are in English.

---

## Evaluation Plan

<!-- List your 5 test questions with their expected correct answers.
     Questions should be specific enough that you can judge whether the system's response
     is right or wrong. "What are good dining halls?" is too vague.
     "What do students say about wait times at [dining hall name] during lunch?" is testable. -->

| # | Question | Expected answer |
|---|----------|-----------------|
| 1 | What is CS 1110 mainly designed to teach? | The answer should identify CS 1110 as an introductory programming course and mention that it introduces students to programming/computing fundamentals, commonly using Python.|
| 2 | What course is commonly described as Cornell’s object-oriented programming and data structures course?| The answer should identify CS 2110 as the object-oriented programming and data structures course, with CS 2112 possibly mentioned as an honors or more advanced alternative.|
| 3 | What programming language or programming style is strongly associated with CS 3110?| The answer should mention that CS 3110 is strongly associated with functional programming and OCaml.|
| 4 | If a student asks about official CS major requirements, which sources should the system prioritize?| The answer should prioritize the official Cornell CS BA and BS requirement pages over Reddit, RateMyProfessors, or unofficial student guides.|
| 5 | If a student asks about workload or difficulty, what type of source should the system use?| The answer should use unofficial/student-experience sources such as Cornell CS Wiki, Reddit course discussions, and RateMyProfessors, while making clear that these are subjective opinions rather than official requirements.|

---

## Anticipated Challenges

<!-- What could go wrong? Name at least two specific risks with reasoning.
     Consider: noisy or inconsistent documents, missing source attribution, off-topic
     retrieval, chunks that split key information across boundaries. -->

1. Reddit and RateMyProfessors can provide useful student experiences, but they may also include outdated, biased, or contradictory opinions. The system should avoid presenting one student’s opinion as a universal fact.

2.Course information may change by semester. Official course offerings, professors, prerequisites, and requirements can be different between semesters such as FA26 and SP26. The system should cite the source it used and avoid assuming that a course is offered every semester.

---

## Architecture

<!-- Draw a diagram of your pipeline showing the five stages:
     Document Ingestion → Chunking → Embedding + Vector Store → Retrieval → Generation
     Label each stage with the tool or library you're using.
     You can use ASCII art, a Mermaid diagram, or embed a sketch as an image.
     You'll use this diagram as context when prompting AI tools to implement each stage. -->

A [Document Ingestion: Load Cornell pages, CS Wiki, Reddit, and RateMyProfessors data, requests + BeautifulSoup] 
--> 
B[Chunking: Split documents into 1200-character chunks, 200-character overlap]B --> 
C[Embedding and Vector Store: all-MiniLM-L6-v2 embeddings, Stored in ChromaDB] --> 
D[Retrieval: Similarity search, Return top 5 relevant chunks]
--> 
E[Generation: LLM creates response, Includes source citations]

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
I will use Claude to help implement document ingestion and chunking. I will give it my Documents and Chunking Strategy sections and ask it to write functions that load webpage text, clean the text, attach source metadata, and split the text into 1200-character chunks with 200-character overlap. I will verify the output by checking that each chunk includes text, source title, URL, and course-related metadata when available.

**Milestone 4 — Embedding and retrieval:**
I will use Claude to help implement embedding and retrieval. I will give it my Retrieval Approach section and ask it to use sentence-transformers with all-MiniLM-L6-v2 and store vectors in ChromaDB. I expect it to produce code that embeds chunks, saves them in the vector store, and retrieves the top 5 most relevant chunks for a query. I will verify the output by testing course-specific questions like “What is CS 3110 known for?” and checking whether the retrieved chunks actually mention CS 3110.

**Milestone 5 — Generation and interface:**
I will use Claude to help build the final answer-generation step. I will give it my Evaluation Plan and Architecture sections and ask it to write code that takes retrieved chunks and generates an answer with source citations. I will verify the output by running my five evaluation questions and checking whether the answers match the expected answers and cite relevant sources.