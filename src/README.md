# Studio 2025 — Module Structure

Future modularization target. Currently all code is in `index.html`.

## Directory Map

```
src/
  utils/       — DOM helpers (G), SVG primitives (E, Rc, Ln, Tx, Ci, Pg)
  engines/     — DimensionEngine, SimplificationEngine, AutoLayoutEngine,
                 BuildLogic, ComponentEngine, TemplateEngine, SectionEngine,
                 AnnotationEngine, DetailEngine
  views/       — drawFront, drawSide, drawTop, drawIso, drawSection
  ui/          — Sidebar, keyboard shortcuts, zoom, drag-snap, display modes
  export/      — SVG, PNG, PDF, DXF, S25, CSV exporters
  three/       — Three.js engine, model loader, capture, controls
styles/        — Extracted CSS (main, components, modals, print)
```

## Extraction Order

1. `src/utils/svg.js` + `src/utils/dom.js` (no deps)
2. `src/engines/*` (depend on utils + constants)
3. `src/views/*` (depend on engines)
4. `src/ui/*` (depend on state + render)
5. `src/export/*` (depend on state + render)
6. `src/three/*` (already semi-isolated)
