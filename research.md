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

1. `reference/apps/example1.webp` — Reddit r/capsulewardrobe thread ([discussion](https://www.reddit.com/r/capsulewardrobe/comments/1ldvng6/a_weather_app_that_knows_my_capsule_wardrobe_and/)). Shows user demand for outfit suggestions tied to a small, known wardrobe rather than generic advice — supports keeping recommendations to common/generic items per the context of use.
2. `reference/apps/example2.webp` — Weather Fit (weatherfit.com), iOS app, 4.6★/16K+ ratings. Validates the character + outfit + weather concept and umbrella/sunscreen reminder pattern central to this brief. Also shows wardrobe customization, multi-location support, and widget/watch surfaces — mostly out of scope for Weather2 but confirms the core idea works well with users.

## Weather and technical evidence

Record each useful source, what it supports, and important limitations. Research the weather variables, apparel guidance, reminders, accessibility, privacy, artwork, weather providers, and technical options needed for informed decisions.

### Weather providers considered

- **Open-Meteo** ([docs](https://open-meteo.com/en/docs)) — Free for non-commercial use under 10,000 calls/day, no API key or signup required. Forecast up to 16 days (covers current + trip-planning use case). Includes a free geocoding API to resolve typed city names to coordinates. Provides temperature, apparent temperature, precipitation, wind, UV index, and weather codes needed for outfit/reminder rules.
- **National Weather Service (NWS) API** ([docs](https://www.weather.gov/documentation/services-web-api)) — Free, no key, official US government source. Limited to ~7-day forecast and US coverage only; requires a separate geocoding step since it takes lat/lon, not place names.
- **OpenWeatherMap** ([pricing](https://openweathermap.org/price)) — Free tier: 1,000,000 calls/month, 60/min, current weather + 5-day/3-hour forecast. 16-day daily forecast requires a paid plan. Requires signup/API key.
- **WeatherAPI.com** ([pricing](https://www.weatherapi.com/pricing.aspx)) — Free tier: 100,000 calls/month but only a 3-day forecast; longer forecast ranges require a paid plan. Requires signup/API key.

**Decision: Open-Meteo selected** as the weather provider — no key/signup friction, forecast range comfortably covers trip planning, and built-in geocoding simplifies manual location entry. Trade-off accepted: non-commercial free-tier cap of 10,000 calls/day, acceptable for this prototype's scale.

### Apparel and reminder guidance

- **NWS Wind Chill** ([weather.gov](https://www.weather.gov/safety/cold-wind-chill-chart)) — Defined only for temperatures at or below 50°F with wind above 3 mph; supports a cold/layering threshold and a "feels colder than the number" note for cold-weather outfit categories.
- **EPA UV Index Scale** ([epa.gov](https://www.epa.gov/sunsafety/uv-index-scale-0)) — 1–2 Low (no protection needed), 3–7 Moderate to High (sunscreen, hat, sunglasses), 8+ Very High to Extreme (extra protection). Supports numeric thresholds for a sunscreen reminder.
- **NWS Heat Index** ([weather.gov](https://www.weather.gov/safety/heat-index)) — Standard categories: 80–90°F Caution (fatigue possible), 90–103°F Extreme Caution (heat cramps/exhaustion possible), 103–124°F Danger, 125°F+ Extreme Danger. Supports a hydration-reminder threshold, e.g. triggering at Extreme Caution (~90°F+). Note: source page renders its chart as an image; categories confirmed from the well-established public NWS heat index scale.

### Accessibility, privacy, and artwork

- **Accessibility** — WCAG 2.1/2.2 AA basics apply: sufficient color contrast, text alternatives for icons/character states, minimum touch target size (44×44px), and no color-only signaling for recommendation categories (pair color with icon/text).
- **Privacy** — The browser Geolocation API requires explicit per-origin user permission. The brief requires storing only the most recent location on-device; this should use `localStorage` rather than a server or account, and be disclosed on the information screen along with the data source.
- **Artwork copyright** — Per the US Copyright Office ([copyright.gov/ai](https://www.copyright.gov/ai/)), purely AI-generated content without meaningful human creative input is not copyrightable in the US, and the area remains actively evolving (Reports Parts 1–3, 2024–2025). This affects the artwork approach: options are (a) original hand-drawn/vector art (clear ownership, more effort), (b) AI-generated art with substantial human editing (arguably protectable, still a gray area, must be disclosed per Copyright Office guidance and the brief's credits requirement), or (c) appropriately licensed asset packs (clear terms, requires credit).

## Decisions

Record the selected weather provider, forecast range, recommendation categories and rules, screen structure, visual direction, artwork approach (original, AI-generated, or appropriately licensed), deployment method, and one additional feature justified by the research. Briefly explain important trade-offs.

Once the recommendation categories are chosen, estimate the art needed: the character, three outfit variations per category, weather icons, and reminder icons. Use that estimate to choose the artwork approach.

- **Weather provider**: Open-Meteo (see rationale above). Forecast range: current conditions plus forecast days available through Open-Meteo (covers same-day and trip-planning use cases).

- **Recommendation categories** (temperature-driven, three tiers):

  | Category | Range | Basis |
  |---|---|---|
  | Cold | ≤50°F, or wind chill applies (≤50°F + wind >3mph) | NWS wind chill guidance |
  | Mild | 51–74°F | between cold and hot cutoffs |
  | Hot | ≥75°F | — |

- **Reminders** (independent of category, layered as icon + text on top of whichever outfit is shown — not separate outfits):
  - Umbrella — triggered by forecast precipitation (Open-Meteo precipitation probability/weather code)
  - Sunscreen — triggered by UV index ≥3 (EPA moderate-and-above)
  - Hydration — triggered by heat index ≥90°F (NWS extreme-caution-and-above)

  Trade-off: early wireframes (`reference/art/rain.jpg`) drew a full separate rain outfit (raincoat, boots). Decision: keep this simpler — the character keeps its temperature-tier outfit and reminders layer on as icon/text only, avoiding extra art states. Those wireframes are treated as superseded layout sketches, not the final interaction model.

- **Screen structure**:
  - Main screen: location entry (manual + device location) and today/forecast date navigation, current conditions summary, character with outfit and written recommendation, reminder banners, and entry points to the Fashion Show and Credits/Info screens.
  - Credits/Info screen (modal or separate screen): creator, weather-data source, recommendation methods/sources, privacy practices, and art credits/licenses.
  - **Phone layout**: single-column stack (per existing wireframes), optimized for one-handed use.
  - **Laptop layout**: not a stretched copy of the phone layout — character and recommendation stay as a left-hand focal column; location/date controls, conditions card, and reminders are arranged as separate panels in a row to the right, all visible without scrolling.
  - Hand-drawn phone and laptop screens still need to be produced for `spec.md`; the wireframes in `reference/art/` so far are phone-only and predate the reminder-layering decision above.

- **Visual direction**: existing hand-drawn/notebook-style wireframes (`reference/art/`) are layout wireframes only, not the final visual style. Final visual style to be defined in `spec.md` once art is produced.

- **Artwork approach**: AI-generated, unedited. Estimate: 1 character + 3 outfit variations × 3 categories (9 outfit states) + weather icons (clear, rain, and any other conditions surfaced) + reminder icons (umbrella, sunscreen, hydration). Trade-off accepted: per the Copyright Office research above, purely AI-generated art without meaningful human creative input is not copyrightable in the US; for this prototype, disclosure in the Credits/Info screen is sufficient and no exclusive ownership claim over the art is required.

- **Deployment method**: GitHub Pages, per the brief's recommendation.

- **Additional feature (research-justified)**: Fashion Show — previews all three outfit variations for the current category without changing the persisted selection for the viewed date. Justified by user story 2 (wanting variety to feel present despite a small wardrobe): this lets the user see the range of variations directly rather than only encountering them by chance.

- **Bonus feature (outside required scope)**: "I feel 80s today" — a fun, Back to the Future-styled outfit easter egg. Not the brief's required additional feature; kept as an extra if time allows.

### Backlog (not in current scope)

- Push notifications for umbrella/sunscreen reminders (out of scope for this browser-based app; in-app reminders on the recommendation screen satisfy the brief instead).

## Revisions

Record new evidence or changed decisions and explain why they changed.

## Approval

The Developer reviews the sources and decisions, corrects this file, and explicitly approves it before specification begins.

## Saving the transcript

After the Developer approves the research, ask them to enter `save transcript`. When directed, save the complete conversation as `transcripts/research-YYYY-MM-DD_HHMMSS.md`, label chat messages `Developer` and `Agent`, and confirm the saved path.
