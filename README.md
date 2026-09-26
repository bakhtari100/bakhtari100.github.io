# Coffee Portfolio

A personal portfolio site with a twist: as you scroll through it, a cup of iced coffee gets made in real time on the left side of the page. Each section corresponds to a step in the drink, so by the time you reach the contact section, the coffee is fully assembled.

**Live site:** https://bakhtari100.github.io

## How it's built

Single self-contained `index.html` file. No build step, no framework, no dependencies. Plain HTML, CSS, and vanilla JavaScript.

- The cup is inline SVG, with each ingredient (beans, ice, milk, espresso, straw, condensation) as its own group that fades or fills in based on which section is in view.
- A scroll listener tracks which section is closest to the center of the screen and updates a `data-stage` attribute on the page, which CSS selectors key off of to animate the cup.
- Two photos are referenced as plain image files (`me.jpg`, `me-2.jpg`) sitting next to `index.html`, so nothing but static files is needed to host it.

## Sections

| Section | Coffee step |
|---|---|
| Welcome | Set out the glass |
| About me | Add the beans |
| Education | Grind |
| Work experience | Pull the shot |
| Skills | Ice and milk |
| Projects | Pour the shot over |
| Volunteer | Give it a stir |
| Connect | Straw in, serve |

## Hosting

Deployed with GitHub Pages, served straight from the `main` branch. No build pipeline, since it's already a finished static file.

## Built with Claude

I built this with Claude (Anthropic), going back and forth on the concept, the copy, the animation logic, and the layout until it matched what I wanted. I made the calls on content, structure, and design direction; Claude wrote and revised the code.

If you want to build something similar for yourself, here's the prompt I'd hand to Claude to get started. Swap in your own theme and details.

### Prompt to build your own

```
I want to build a single-page personal portfolio website where a visual
metaphor "completes" as the visitor scrolls through it. Here's the concept:

[Describe your metaphor, e.g. "As you learn more about me, we build a
cup of coffee" or "As you scroll, a plant grows" or "As you scroll, a
rocket gets assembled and launches."]

Sections and what each one should represent in the metaphor:
- Welcome: [step 1]
- About me: [step 2]
- Education: [step 3]
- Work experience: [step 4]
- Skills: [step 5]
- Projects: [step 6]
- Volunteer / other: [step 7]
- Connect / contact: [final step, fully complete]

Requirements:
- Single self-contained HTML file: inline CSS and JS, no external
  dependencies besides a Google Font if needed.
- The visual (the thing being "built") should be an SVG that stays
  fixed on one side of the screen (or top, on mobile) while the
  content scrolls on the other side.
- Track scroll position directly (not with IntersectionObserver
  thresholds alone, which can lag or flicker) so the animation stays
  in sync with the scroll, with no visible delay when scrolling fast.
- Include a sidebar or progress rail showing all the steps, with the
  current one highlighted, and make each step clickable to jump to
  that section.
- Responsive: works on both desktop (side-by-side layout) and mobile
  (stacked layout, small version of the visual pinned at the top).
- Support both light and dark mode based on the visitor's system
  setting.
- Leave clearly marked placeholders for two personal photos I can
  drop in later, sized appropriately for a header shot and a closing
  shot.
- Reduced motion: respect prefers-reduced-motion and skip animations
  for people who have that setting on.

For content, here's my background: [paste your resume, LinkedIn
summary, or bullet points about your education, work experience,
skills, projects, and volunteer work].

Build it section by section, and ask me before assuming details I
haven't given you.
```

That last line matters. Claude will make reasonable choices to keep moving, but flagging what it assumed lets you correct course before it's baked into ten more edits.
