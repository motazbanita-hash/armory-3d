# ARMORY 3D — EXPLORE. INSPECT. DISCOVER.

FPS-style equipment selection and 3D inspection. React + Vite + Three.js + React Three Fiber + Drei + Zustand + GSAP.

## Run

```bash
npm install
npm run dev        # http://localhost:5173
npm run build      # production build in dist/
```

## Put it online as a website (open it from your phone)

This is a static website (`npm run build` → `dist/`). Pick one:

- **Netlify (no install on your computer):** put the project in a GitHub repo → Netlify → *Add new site* → *Import from Git*. `netlify.toml` already sets the build command and `dist` folder. You get a public URL.
- **Netlify Drop:** run `npm install && npm run build` once, then drag the `dist` folder onto app.netlify.com/drop.
- **Vercel:** import the GitHub repo; `vercel.json` is included.
- **Replit:** import the zip, press Run, open the preview URL on your phone (prompt in `docs/PROMPTS.md`).
- **Same Wi-Fi only:** `npm run dev`, then open the printed `Network:` address on your phone.

## What is in the catalog

Only the three supplied quadcopters (`public/images/quadcopter-0{1,2,3}.jpg`, used unchanged as thumbnails and reference images).
Manufacturer, model, flight time, range, weight etc. are **not provided** and display "Not provided" — nothing is invented.
The 3D models are **visual proxies** built from Three.js primitives, labelled as such in the UI; they are not dimensionally accurate.

## Structure

```
src/
  data/            products.js · categories.js · components.js · models/*  (all data, no UI)
  store/           useArmoryStore.js  (Zustand — single source of truth)
  systems/         Raycasting · ExplodeEngine · LayerManager · CameraManager · OrbitControls
  components/      Navigation · ProductSelector · ProductViewer · ProductInformation
                   ComponentExplorer · LayerPanel · ControlToolbar · Comparison · Layout · Overlays · ui
  hooks/ utils/ styles/
```

Data flow: UI → store → systems/3D. The 3D runtime reads the store with `getState()` inside the frame loop, so slider drags and hovers never re-render React.

## Extending

**Add a product** — add an entry to `PRODUCTS` in `src/data/products.js` (set `category`, `components`, `image`, `model.id`), then add a model spec in `src/data/models/` and register it in `models/index.js`. Selector, search, comparison, info panel and component list pick it up automatically.

**Fill in a real spec** — `specs: { 'Flight time': '25 min' }` on the product. Unset fields stay "Not provided".

**Change an exploded layout** — edit the `explode` vector (and optional `delay` for staging) on each part in `src/data/models/*.js`.

**Use a real GLB** — put the file in `public/models/quadcopter-01/` and set `model.glb: '/models/quadcopter-01/model.glb'`. Name meshes `<groupId>__name` (e.g. `propellers__front_left`) so raycasting, layers and explode work per component. If the file is missing or fails to load, the proxy model is used automatically.

**Add a new category's products** — set `category: 'weapons'` (etc.) on the product. The six categories already exist in `src/data/categories.js`; empty ones show an "offline" state.

## Controls

Desktop: drag rotate · wheel zoom · right-drag pan · click a part. Touch: one finger rotate · pinch zoom · two-finger pan · tap a part · swipe the title to change product.
Keys: `← →` product · `1-3` select · `I` mode · `E` explode · `L` layers · `V` views · `O` isolate · `Space` auto-rotate · `R` reset · `C` compare · `F` fullscreen · `/` or `Ctrl K` search · `Esc` back.
