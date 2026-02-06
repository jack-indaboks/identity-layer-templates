# Personal Identity Layer Template (PILT)

## *Development has moved back to the [PILT](https://github.com/jack-indaboks/PILT) repository.*

Use this repository as the starter Personal Identity Layer. Identity Layers are Markdown bundles that define the AI’s persona, guardrails, and default context. This layer stands on its own and can also be combined with a Team Identity Layer to form a blended Identity.

> Looking for the Team Identity Layer template? Switch to the `Team` branch and read its README for guidance tailored to teams.

## Structure

| Range | Category | Purpose |
|-------|----------|---------|
| 00 | `00_CORE_{ILname}.md` | Central system prompt containing the non-negotiable instructions, values, and operating intent for this personal layer. |
| 01 | `01_INDEX_{ILname}.md` | Routing guide that tells the agent when to load each identity file and what prerequisites apply. |
| 02 | `02_TASKS_{ILname}.md` | Personal workflows or shortcuts the agent runs verbatim when their triggers fire. |
| 03 | `03_SOURCES_{ILname}.md` | Registry of preferred sources plus the allowed and disallowed lists that govern research. |
| 04 | `04_PERSONAS_{ILname}.md` | Catalog of alternate personas plus activation guidance for sanctioned voice shifts. |
| 05-08 | Reserved | Future core template slots shared across personal identity layers. |
| 09 | `09_MEMORY.md` | Optional durable memory log the agent creates only when the deployment allows file writes. |
| 10 | `10_USER_{ILname}.md` | In-depth profile of the primary user for tailoring voice, tone, and priorities. |
| 11 | `11_PEOPLE_{ILname}.md` | Profiles for additional contacts the personal agent should recognize and support. |
| 12 | `12_ORGANIZATION_{ILname}.md` | Organizations and initiatives that shape the user’s work. |
| 13 | `13_ENVIRONMENT_{ILname}.md` | Devices, software, automation, and other environmental constraints. |
| 14 | `14_PROJECTS_{ILname}.md` | Portfolio of active initiatives with status, dependencies, and handoff notes. |
| 15-18 | Reserved | Future shared template slots. |
| 19 | `19_GLOSSARY_{ILname}.md` | Canonical definitions for personal terminology and shorthand. |
| 20-99 | Custom extensions | Additional identity files you create to extend the personal layer. |

## How to Customize and Use Your Personal Identity Layer

1. Fork or clone this repository and rename it for your personal assistant (for example `Jarvis`). Do not use the Template button unless you want a team layer instead.
2. Replace `{ILname}` across filenames and file contents.
3. Populate `00_CORE_{ILname}.md`:
    - **Identity** — The team persona’s mission, tone, and expertise.
    - **Governance** — Guardrails, sourcing policies, and escalation paths the team expects the assistant to enforce.
    - **Preferences** — Reusable formats, cadence notes, and stylistic defaults; mark anything that must remain mandatory during collaboration.
    - **Identity Layer Protocol** — template-maintained section that keeps the identity stack functional; only edit when evolving this template.
4. Tailor every document to match how you work. Each heading or field is only a prompt, so reshape or delete anything that doesn’t serve you, and decide which identity files to use. Remove any unused placeholders from the identity files.
5. In `03_SOURCES_{ILname}.md`, provide either an Allowed list or a Disallowed list before you start researching; omit the unused section to avoid ambiguity.
6. Slots 20–99 are available for you to add any additional files as you see fit. For compatibility, avoid adding or renaming files in the 00–19 range.
7. Name every file in the 20–99 range using `NN_{ILname}_FileName.md`; hyphens are allowed inside `FileName` as needed. Consider reserving each band’s `N0` slot, such as 20 or 30 or 40, for the overview or template that governs that category.
8. Whenever you add, rename, retire, or relocate an identity file, whether in the core slots (00-19) or custom extensions (20-99), update `01_INDEX_{ILname}.md` so the AI can route correctly, and keep cross-references in other files aligned.
9. Keep the layer’s canonical source in version control (e.g., a git repository) and tag releases or branches so composite identities and future you can pull updates confidently.
10. Track upstream template changes by adding this repository as an upstream remote, then cherry-pick individual commits or merge `upstream/personal` depending on how tightly you want to curate updates.

## For Operators and End Users

1. Paste `00_CORE_{ILname}.md` into the system prompt (or equivalent); if you are running a blended stack, paste it immediately after the team’s core file. If using a platform that does not support file uploads, copy only the `Identity` section and any other relevant sections, up to the platform limit.
2. Upload or stage the supporting identity files:
	- Simple file-upload interfaces (for example, ChatGPT or Anthropic Workbench): attach every remaining identity file. Treat those uploaded copies as read-only and make changes in this source repository before re-uploading.
	- Directory-based workflows (for example, GitHub Copilot repositories): place the personal bundle inside `.github/2_{ILname}/` and any paired team layer inside `.github/1_{TILname}/`; keep Markdown links intact because the agent relies on them to reach the rest of the identity stack.
3. When durable and/or portable memory is needed, ensure the deployment environment allows the AI to create `09_MEMORY.md`; the agent will generate and update the file when permitted.
