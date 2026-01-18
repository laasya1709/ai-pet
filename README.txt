AI Pet That Learns My Voice (Chromebook-friendly)

WHAT THIS IS
- A simple web app that listens to a Teachable Machine (Audio) model and shows a pet action.
- Includes 4 pet images: Sit, Stand, Jump, Sleep.
- Includes button fallback if the classroom is noisy.

FOLDER STRUCTURE
ai-pet/
  index.html
  pet-sit.png
  pet-stand.png
  pet-jump.png
  pet-sleep.png
  model/
    model.json
    metadata.json
    weights.bin

STEP 1 — TRAIN YOUR VOICE MODEL (Teachable Machine)
1) Go to Teachable Machine -> Audio Project
2) Create EXACTLY 3 classes (recommended):
   - Sit
   - Jump
   - Sleep
3) Record 25–40 samples per class using the SAME headset mic.
4) Train the model.

STEP 2 — EXPORT MODEL (TensorFlow.js)
1) Export Model -> TensorFlow.js
2) Download the model
3) Copy these 3 files into the /model folder next to index.html:
   - model.json
   - metadata.json
   - weights.bin

STEP 3 — RUN IT (IMPORTANT)
Do NOT double-click index.html and run from file://
That commonly causes "Model not found".

You MUST run it from a web server.

EASIEST OPTIONS
A) GitHub Pages / Netlify (recommended for Chromebook)
- Upload the folder contents
- Open the https URL

B) Local server (if available)
- If you have Python: run "python -m http.server 8000" inside the folder
- Open http://localhost:8000

TROUBLESHOOTING: "MODEL NOT FOUND"
If you see the error, check these:
1) Are the files exactly named (case-sensitive)?
   model/model.json
   model/metadata.json
   model/weights.bin

2) Are you running from a server (https:// or http://), NOT file:// ?

3) Open browser DevTools -> Console/Network:
   - If model.json/weights.bin shows 404, your path is wrong.
   - If it shows blocked by CORS, you're on file://

4) If your class names are not Sit/Jump/Sleep:
   - The UI still works, but the app maps labels by keyword.
   - Best practice: name classes exactly Sit, Jump, Sleep.

DEMO TIPS (TO WIN)
- Use headset mic.
- Keep only 3 voice commands.
- If the room gets noisy, use the buttons.
