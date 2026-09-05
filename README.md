# BriefFlow — brief to pipeline

A prototype for HexCoded, built around the two things Jivesh's email named directly: **node-based workflows in Creative Studio** and **agentic chats for content creation**. BriefFlow is the seam between them.

## The idea

Creative professionals don't think in nodes. A client brief sounds like *"15s reel for our sneaker launch, moody, three shots, brand orange."* Today, turning that into a pipeline means either typing it into a chat box and hoping the output matches, or building the graph by hand on a blank canvas.

BriefFlow takes the plain-English brief, sends it to an agent, and gets back a real pipeline: brief → shots → animate → grade → sound → export, laid out as editable nodes — each with its own prompt and parameters — before anything renders. You can rewrite any single step ("Rewrite this step"), or talk to the whole pipeline ("add a slow-motion shot", "make it warmer") and the agent restructures the graph. Export the result as JSON.

**Where this sits next to HexCoded:** Magnific pushes single-image quality, ImagineArt and OpenArt cover broad generation and templates, LTX Studio takes a script to a shot-by-shot film. None of them take an unstructured client ask and lay it out as a pipeline a node canvas can already run. That's the gap this fills, and it's built to sit directly on top of Creative Studio's node model rather than replace it.

## What's real vs. placeholder

- **Real:** the planning agent. Every "Lay out the pipeline," "Update," and "Rewrite this step" action is a live call to Claude that reasons about the brief and returns a structured pipeline.
- **Placeholder:** the node previews are gradient swatches, not actual renders — there's no image/video generation wired in. Swapping those for HexCoded's own generation nodes is the obvious next step, and the graph structure (types, params, edges) is already shaped for that handoff.

## Running it

It's a single self-contained HTML file — no build step, no dependencies.

**Fastest — just open it:**
Double-click `briefflow.html`, or drag it into a browser tab. It works immediately with no setup.

**Deploy it somewhere with a URL** (any of these take under a minute since it's one static file):
- **Vercel:** `npx vercel deploy` from the folder, or drag the file into vercel.com/new
- **Netlify:** drag-and-drop the file at app.netlify.com/drop
- **GitHub Pages:** push it to a repo, enable Pages on the branch
- **Replit:** create a static HTML repl, paste the file in, hit Run

## API key

The app calls `https://api.anthropic.com/v1/messages` directly from the browser. When run inside a Claude.ai artifact preview it works with no key. Deployed anywhere else, click the ⚙ icon in the sidebar and paste an Anthropic API key — it's kept in memory for that browser tab only, never written to storage or sent anywhere but Anthropic's API.

## Files

- `briefflow.html` — the whole app
- `README.md` — this file
