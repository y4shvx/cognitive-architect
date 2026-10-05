# Cognitive Architect

A single-page, choice-driven narrative experience. You play an "Architect" — a near-future psychological counselor who enters the subconscious mind of a catatonic patient and navigates eight symbolic stages built from literary and Jungian motifs. Every choice shifts two underlying traits (logic vs. empathy, individual vs. collective), and the ending you reach is determined by where you land.

## Play it

Open `cognitive-architect.html` directly in any modern browser — desktop or mobile. There's nothing to install or build; it's a single self-contained HTML file.

If you're running it locally, a quick way to serve it (recommended over double-clicking the file, so the custom fonts load correctly) is:

```bash
python3 -m http.server 8000
```

then visit `http://localhost:8000/cognitive-architect.html`.

## How it works

- **No build step, no dependencies.** HTML, CSS, and vanilla JavaScript in one file.
- **Branching narrative**: each of the 8 stages presents a moral dilemma; your choice nudges two score axes and determines which of 5 ending archetypes you reach.
- **Responsive layout**: single-column on mobile, a two-panel layout with a live stats sidebar on screens ≥ 992px wide.
- **Lightweight analytics (optional)**: on completion, the result is optionally logged to a Google Form for anonymous aggregate tracking. See *Telemetry* below if you fork this and want to disable or repoint it.

## Telemetry

The script submits each playthrough's final scores and choice path to a Google Form endpoint (see the `TELEMETRY` object near the top of the `<script>` block). If you fork or redistribute this:

- Replace `TELEMETRY.formUrl` and the `entry.*` field IDs with your own Google Form, or
- Delete the `dispatchDataTelemetry()` call at the end of `triggerProfileAnalysis()` to disable tracking entirely.

## Customizing

All narrative content lives in the `Database` object in the `<script>` block — each stage has a prompt, two choices, their outcome text, and their effect on the two score axes. Add, remove, or rewrite stages there; the UI and progress tracker adapt automatically as long as each stage's `target` points to a valid next key.

## License

Add your preferred license here (e.g. MIT) before publishing, if you want others to be able to reuse or modify this freely.
