# Prompts for developing ARMORY 3D with other tools

The full, editable kit (ChatGPT, Replit, Hugging Face, Perplexity, Higgsfield) is the shared document
"ARMORY 3D — Multi-Tool Development Prompt Kit". The two prompts you need first are kept here.

## Shared brief (paste first in every tool)

```text
PROJECT: ARMORY 3D — an FPS-style equipment selection and 3D inspection website.
DELIVERABLE TYPE: a responsive WEBSITE that runs in the browser (static Vite build opened by URL on desktop
and phone). NOT a native or mobile app: no React Native, Expo, Capacitor, Electron, APK or app-store packaging.
STACK: React 18, Vite 5, Three.js 0.169, @react-three/fiber 8, @react-three/drei 9, Zustand 4, GSAP 3, lucide-react.
ARCHITECTURE: src/data (data only) · src/store (one Zustand store) · src/systems (Raycasting, ExplodeEngine,
LayerManager, CameraManager, OrbitControls) · src/components · src/hooks · src/utils · src/styles.
DATA RULES: exactly three products. The three supplied photos in public/images are official and must never be
replaced or edited. Never invent manufacturers, model numbers, specs or performance claims; unknown = "Not provided".
The 3D models are visual proxies and are labelled as not dimensionally accurate.
```

## Replit

```text
Run the ARMORY 3D project as a WEBSITE (not an app).
1. Install dependencies and start the Vite dev server on 0.0.0.0 so the Replit preview works.
2. Fix every install, build and runtime error with the smallest possible change and report each fix.
3. Verify in the preview: loading screen, category UAV SYSTEMS active, 3 products switch viewer + info + parts,
   part click highlight, explode slider, layers, camera presets, reset, compare, search, favorites, fullscreen,
   and the mobile layout at 390 px wide. Report pass/fail for each.
4. Run `npm run build`, then deploy as a static website serving the `dist` folder and give me the public URL.
Do not redesign, add features, change product data or images.
```
