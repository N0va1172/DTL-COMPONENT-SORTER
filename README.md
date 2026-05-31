# ElectroCom v2.0 — Vercel Deployment

A mobile-friendly web app with two features:
1. **Component Detection** — Upload a photo, detect electronic components via Roboflow AI, view datasheets
2. **Resistor Scanner** — Use your phone camera to read resistor colour bands in real-time

## Deploy to Vercel

### Option A: Vercel CLI
```bash
npm install -g vercel
cd electrocom-vercel
vercel deploy --prod
```

### Option B: GitHub + Vercel Dashboard
1. Push this folder to a GitHub repo
2. Go to vercel.com → New Project → Import your repo
3. No build settings needed (static + serverless)
4. Click Deploy

## How to use

### Component Detection
1. Open the deployed URL on your phone
2. Enter your **Roboflow API key** (get one free at roboflow.com)
3. Upload a photo of your electronic components
4. Tap **Detect Components**
5. Tap **Open Datasheet** on any detected component

### Resistor Scanner
1. Switch to **Resistor Scanner** tab
2. Tap **Start Camera** (allow camera access)
3. Hold resistor horizontally in the green target box
4. Tap **Snap & Read** to capture and decode
5. OR tap **Upload Photo** to use an existing image

## Project Structure
```
electrocom-vercel/
├── api/
│   └── detect.js          # Serverless: Roboflow proxy
├── public/
│   ├── index.html         # Full frontend (single-file)
│   └── datasheets/        # 29 PDF datasheets
│       ├── arduino-uno.pdf
│       ├── esp32.pdf
│       └── ...
├── package.json
└── vercel.json            # Routing config
```

## Notes
- No backend server needed — runs 100% on Vercel edge
- Resistor colour detection runs entirely in the browser (no API calls)
- Datasheets are served as static files
- API key is stored in session memory only (never sent to our servers)
