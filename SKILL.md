---
name: guided-research
description: "Deep research on any topic using a fixed process: first gather inputs through a guided dialogue with the user, then conduct the research, then produce a Markdown report. Use for competitive analysis, audience and pain-point research, market, niche, or technology research, and content-topic research. Trigger on requests such as: ‘research this,’ ‘conduct research,’ ‘analyze the competitors/market/audience,’ ‘collect user pain points,’ ‘study this topic,’ or ‘prepare a report on…’; trigger words include: research, deep research, study, and report. This skill is universal for research tasks whose outcome is a report or recommendations. DO NOT use it for a one-off fact-check that can be answered in 1–2 sentences or for writing code."
---

# Guided Research

## Objective

Conduct in-depth research on the user's topic and deliver a Markdown report. The topic can be anything: competitors, an audience and its pain points, a market, a niche, a technology, or a content topic.

Follow the process below strictly. The key principle is that 80% of research quality is determined by the quality of the inputs, and users rarely know how to provide those inputs on their own. Therefore, DO NOT begin researching immediately. First guide the user through steps 1–5 to gather inputs: objective, context, structure, style, and sources. Only then conduct the research in step 6 and write the report in step 7. During steps 1–5, lead the dialogue by asking questions with answer options through `ask_user`; do not wait for the user to formulate everything independently.

The result is ALWAYS a `.md` report saved in the current project's `reports/` directory. Create the directory if it does not exist. Use a clear filename in the language of the request, for example `reports/competitor_research_video_tracker.md`. After saving it, show or provide the file to the user.

## Process

Hard limit on user interruptions: 3–4 across the entire workflow (objective → context on one screen → structure + style + sources on one screen → report). More interruptions are frustrating; fewer will make the report too generic. Ask every multiple-choice question through `ask_user`.

## Step 1. Objective — formulate it TOGETHER with the user

This is the most important step.

1. Ask for the research objective. A topic such as “research the competitors” is NOT an objective; it is the subject. Reframe it using this formula: “I want to [action/decision] so that [outcome]; to do that, I need to understand [what must be learned].”
2. Based on what the user wrote, offer 2–3 candidate formulations through `ask_user`. The user selects one or edits it.
3. Record the objective in ONE sentence. It will become the first screen of the report and the inclusion filter: anything that does not serve the objective does not belong in the report.

Example: a poor objective is “research the coffee-shop market”; a good objective is “I am deciding whether to open a coffee shop in neighborhood X, and I need to understand demand, competitors, and unoccupied price segments.”

## Step 2. Context — generate questions based on the objective

Generate 4–6 questions BASED ON the confirmed objective; do not use a fixed list. Generation rules:

- Every question must change the report's content. If an answer would not affect anything, do not ask the question.
- Cover the dimensions relevant to the type of objective: object/subject, audience, geography/language, constraints, facts already known to the user, and “how this is currently solved.”
- Where possible, provide 2–4 selectable answer options through `ask_user`.

Ask all questions in ONE `ask_user` call, with at most two rounds. Do not interrogate the user repeatedly. Do not ask again for information the user already provided in the first message.

## Step 3. Report structure + demo excerpt

1. Show a report outline tailored to the objective. Sections must depend on the objective rather than being fixed. Use a pyramid structure by default: conclusions first, then evidence.
2. Write ONE demo excerpt: 2–3 lines from a representative block, such as part of a comparison table, one finding with a source, or one conclusion with its rationale. Ask, “Is this format okay?” This is a low-cost validation BEFORE spending time on research; do not skip it.

## Step 4. Style — offer options; do not ask an open-ended question

Use `ask_user` to offer these choices: “pyramid structure + tables + diagrams” (default), “brief 1–2 page summary,” or “maximally detailed long-form report.”

## Step 5. Sources — ask what to emphasize

Use `ask_user` to offer these choices: “voices of real people (forums, Reddit, X, review sites, chats),” “official data, statistics, and studies,” “what the market participants publish themselves (websites, ads, content),” or “all of the above.” The choice changes the search patterns, so apply it in step 6. Combine steps 3–5 on one screen.

## Step 6. Research

Run a deep-research loop with 10+ search steps. After each round, provide a brief Thinking + Summary: what you found, what is missing, and what comes next. Adapt search patterns to the selected source emphasis and the relevant language/geography. For “voices of real people,” search forums, Reddit, and review sites in the market's language. For official data, search statistics and reports. For “market participants themselves,” search their websites, ads, and content.

Hard rules:

- Quotes must be verbatim and include a source.
- Find participants' weaknesses in negative reviews.
- Investigate “how people currently solve the problem without ready-made solutions.”
- Invent NOTHING. If data is unavailable, say so explicitly.

## Step 7. Report → `.md` in `reports/`

Assemble the report using the structure approved in step 3 and the selected style. The first screen must contain the objective in one sentence. Complete the checklist, then save the file in `reports/` and provide it to the user.

Checklist before saving:

- The report answers the confirmed objective from step 1; verify this literally.
- Every conclusion and recommendation answers the question, “How was this derived?”
- Every number and quote has a source; quotes are not distorted.
- The pyramid structure is preserved, with tables and, where appropriate, diagrams.
- The structure is the one the user approved in step 3.

## Hardcoded requirements (do not violate)

- The objective formula from step 1, expressed in one sentence.
- The question-generation rules from step 2.
- The demo-excerpt rule: mandatory before research begins.
- The quality checklist from step 7: required before every save.
- “Quotes must be verbatim,” “invent nothing,” and “the result is always a `.md` file in `reports/`.”

Generate everything else from scratch for each task.
