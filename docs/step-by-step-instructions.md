# How to Use ArchView

A step-by-step guide for getting a good architecture view out of ArchView once it's installed. 

## Step 1: Gather what you have

ArchView works from whatever you already have, none of this is required, but the more context you give, the better the first draft:

- An existing diagram (a screenshot, a Mermaid / PlantUML file, a whiteboard photo, a draw.io export)
- A written description of the solution (components, how they talk to each other, key requirements)
- Just a rough idea and a request to have AI propose a structure using leading practices

## Step 2: Ask for the view

Just describe what you want in plain language. For example:

- "Create an architecture view for this system: [paste description or attach a diagram]"
- "Draw a solution architecture view for an order management platform with a mobile app, an API layer, and a database"
- "Help me design an enterprise architecture view for our data platform, I don't have a draft yet"

You don't need to mention "ArchView" by name or know any ESA terminology. AI will recognize the request and take it from there.

## Step 3: Say how much guidance you want (optional)

If you already have a strong opinion on the architecture, say so ("use my structure, just clean it up"). If you want AI to lead with typical patterns, say that instead ("what would a leading practice look like here?"). If you don't say either way, AI will default to a collaborative pass, using your input where you've given it and filling gaps with common patterns, and will flag any assumptions it made.

## Step 4: Tell AI your scope, if it matters

A few things worth mentioning up front if they apply:

- **Scope**: one quick view to clarify a single piece, a full walkthrough of an end-to-end scenario, or a holistic model of the whole enterprise solution. If you don't say, AI will infer this from your request.
- **Audience**: is this for engineers, business stakeholders, or architects? AI adjusts which elements it uses and how much detail it includes.

## Step 5: Review the output

AI will generate a single, self-contained HTML file. Open it to:

- **Zoom** in and out (mouse wheel works too)
- **Toggle** between the diagram and its properties/description panel
- **Save as image** (PNG) or **save as PDF report** (diagram plus the write-up)
- **Export as JSON or XML**, useful for keeping a record, continuing later, or opening in a compatible diagram editor

Open the file directly in a browser tab. Downloads may not work if it's opened inside an embedded preview panel in an AI app.

## Step 6: Ask for changes

Treat the first output as a draft. You can ask for things like:

- "Split this into two views, it's too crowded"
- "Add a governance and monitoring group"
- "Simplify this, my team doesn't need this much detail"
- "Show more of the data flow between the catalog and the warehouse"

AI will revise and regenerate rather than starting over, so you can keep iterating until it's right.

## Step 7: Build out the full model, if you need one

A single view rarely tells the whole story for a large solution. If you're modeling something substantial, consider asking for companion views, for example a business capability view, an operational / deployment view, or a metrics view, so the full picture is covered. AI will tell you if it thinks another view would help complete the model.

## A few tips

- **Simple requests get simple views.** If you just say "show me the roles, systems, and boundaries," AI will keep it lean rather than pulling in the full element set.
- **Vendor-specific diagrams aren't the goal.** ArchView won't render vendor product icons (e.g., a literal AWS or Azure services diagram); it renders the underlying architecture in ESA's vendor-neutral element set instead.
- **Detailed design isn't in scope.** For class diagrams, sequence diagrams, or code-level views, ArchView will say so and suggest a different tool is a better fit.

## Feedback welcome

If a view doesn't come out the way you expected, or a request gets misread, that's useful to know. Let us know what happened and what you were hoping for; it helps shape where ArchView goes next.