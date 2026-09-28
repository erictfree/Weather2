# Research

> EDITING DIRECTIVE: DEVELOPER AND AGENT EDIT THIS FILE COLLABORATIVELY. THE DEVELOPER MUST REVIEW AND APPROVE ITS CONTENT.

Purpose of this file: Research your context of use, references, weather guidance, technical options, and choices that will guide the specification.

## Instructions for the Developer

Judge sources and recommendations, make the consequential decisions, and keep this file current as the work develops.

To begin, open the project repository in a fresh chat and enter:

`Read ./research.md and help me begin Project 3 research.`

## Instructions for the Agent

Read `AGENTS.md`, `brief.md`, and this file. Ask one focused question at a time. Help investigate and compare options without deciding for the Developer. Verify sources directly and keep this file concise.

## Context of use

I check the app the night before or morning of getting dressed — usually still in bed or at my desk, on phone or laptop. When traveling, I look several days ahead to plan what to pack. Current weather apps make me translate numbers and icons into actual clothing decisions myself; I want something that tells me directly what to put on, using generic/common items I could realistically own or pick up (not a personalized wardrobe I have to set up first).

## User story

Write at least one user story grounded in your context of use:

> As a [type of user], I want to [need or goal], so that [reason or outcome].

Focus on the need rather than prescribing an interface or feature.

1. As a US college student getting ready for the day, I want to see a specific outfit recommendation instead of raw weather numbers, so that I don't have to mentally translate forecast data into clothing decisions every morning.
2. As a college student with a limited wardrobe, I want outfit suggestions that mix and match a small set of common items in different combinations, so that recommendations still feel varied and fresh even though I don't own a lot of clothes.
3. As a student packing for a weekend trip, I want to check outfit recommendations for a future date in a different city, so that I know what to bring before I leave.
4. As a student on a phone with location services, I want the app to use my current location automatically, so that I don't have to type in my city every time.
5. As a student who checks the forecast more than once a day, I want the same outfit recommendation to reappear for a date I've already viewed, so that the suggestion feels consistent rather than random each time I open the app.
6. As a student checking the app while still half-asleep or holding a coffee, I want to get my outfit recommendation with minimal taps using one hand, so that checking the weather doesn't get in the way of getting ready.
7. As a privacy-conscious student, I want to know where the weather data comes from and how my location is used, so that I feel comfortable granting location access.

## References

Collect 5–10 reference images from relevant products and interfaces. Save each image in `reference/`, identify its source, and record a brief observation about what is useful, ineffective, or relevant to this project. Reference images are examples only; do not use them in the app.

## Weather and technical evidence

Record each useful source, what it supports, and important limitations. Research the weather variables, apparel guidance, reminders, accessibility, privacy, artwork, weather providers, and technical options needed for informed decisions.

## Decisions

Record the selected weather provider, forecast range, recommendation categories and rules, screen structure, visual direction, artwork approach (original, AI-generated, or appropriately licensed), deployment method, and one additional feature justified by the research. Briefly explain important trade-offs.

Once the recommendation categories are chosen, estimate the art needed: the character, three outfit variations per category, weather icons, and reminder icons. Use that estimate to choose the artwork approach.

### Backlog (not in current scope)

- Push notifications for umbrella/sunscreen reminders (out of scope for this browser-based app; in-app reminders on the recommendation screen satisfy the brief instead).

## Revisions

Record new evidence or changed decisions and explain why they changed.

## Approval

The Developer reviews the sources and decisions, corrects this file, and explicitly approves it before specification begins.

## Saving the transcript

After the Developer approves the research, ask them to enter `save transcript`. When directed, save the complete conversation as `transcripts/research-YYYY-MM-DD_HHMMSS.md`, label chat messages `Developer` and `Agent`, and confirm the saved path.
