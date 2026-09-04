# ArchView

## What it does

ArchView generates IT architecture diagrams and model views in a node-image style, primarily at the enterprise solution architecture (ESA) level, the space between enterprise architecture and solution design. Ask for an architecture diagram, a solution architecture view, an enterprise architecture model, or something like "visualize this system's architecture," and AI will map your solution onto a set of ESA elements (services, data stores, gateways, roles, and so on), generate a self-contained HTML view with zoom, PNG/PDF export, and a properties panel.

It's built for large or complex solutions that need a clear, maintainable view, not for detailed-design or code-level diagrams (class diagrams, sequence diagrams), and not for quick informal sketches.

## ArchView Skill Download

- [archview.zip download](https://archview.github.io/skill/download/archview.zip)

## Installing ArchView

#### Quick Start with the Claude app or claude.ai

In the Claude app or claude.ai (browser or desktop)

1. Go to **Settings**, then open **Skills** (this may also appear as "Customize > Skills" depending on your plan).
2. Make sure **Code execution** (Settings > Capabilities > Code execution and file creation) is turned on. Skills won't appear without it.
3. Click **Upload skill** (Skills > Add) and select `archview.zip`.

That's it. From then on, just ask Claude for an architecture diagram or view in any conversation, and it will use ArchView automatically when relevant.

*Team/Enterprise:* an organization owner can instead provision ArchView for everyone under **Organization settings > Skills**.

### Other Installation Options

- see [skill-install.md](docs/skill-install.md)

## How to Use ArchView

> For a quick architecture view, simply submit your request, and AI will generate a well-structured diagram for you.

If your solution is highly complex or you need a more refined result, you can take a multi-step approach. Here is a brief guide:

1. Gather what you have: ArchView works from whatever you already have, none of this is required, but the more context you give, the better the first draft

2. *Ask for the view: Just describe what you want in plain language. For example: "Create an architecture view for this system: [paste description or attach a diagram]"*

3. Say how much guidance you want (optional)

4. Tell AI your scope, if it matters

5. *Review the output*

6. Ask for changes, if any

7. Build out the full model, if you need one

> You can have different detail-level views. For example, a lean-mode view with fewer elements, a succinct outline view, a view with detailed architectural analysis, or a full set of model views.

For a bit more detailed step-by-step instruction, see this [link ](docs/step-by-step-instructions.md).

## Samples

- [archview output HTML page](samples/archview-oms-functional.html)

- [archview report pdf](samples/archview-sample-report.pdf)

- [archview saved PNG image](samples/archview-sample-saved.png)

## Layout Limitation and Customization

Because of the auto-layout, elements in the output view may not appear in the expected order or position. However, you can customize the layout by moving groups or nodes to their desired positions, improving the layering order and overall visual presentation.
Archview is primarily designed to provide architectural clarity rather than visual appeal. However, the layout and visual style will be further refined and enhanced in future releases.

## Feedback welcome

This is an early version of ArchView, and it's still evolving. Your feedback is welcome.
