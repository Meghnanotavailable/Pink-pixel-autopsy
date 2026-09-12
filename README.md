# 🩷 Pink Pixel Autopsy

> **Discover how many fictional brain cells your image or camera feed destroys in real time.**  
> *⚠️ Medical Disclaimer: This questionable medical technology is completely fictional and designed purely for comedic entertainment.*

---

## 🔬 Project Overview

**Pink Pixel Autopsy** is an interactive, browser-based comedic diagnostic application that scans imagery for suspiciously dangerous concentrations of hot pink pixels (`#FF1493` family) and calculates your "fictional brain cell casualties".

The application features:
1. **Real-Time Live Camera Scanner**: High-performance continuous video feed analysis at ~25 FPS with dynamic HUD telemetry, live exposure gauges, risk counter, and real-time stage diagnoses.
2. **Interactive Heatmap & Geiger Audio**: Live toggleable neon magenta overlay highlighting detected pink clusters, accompanied by synthesized Web Audio API Geiger counter clicks that rise in pitch and frequency with pink intensity.
3. **Uploaded Image Autopsy**: Upload any photo from your device to perform a thorough forensic autopsy scan.
4. **8 Progressive Diagnostic Stages**: Ranging from *Stage 1: Mild Pink Exposure* to *Stage Infinity: THE PINK HAS WON*.
5. **Living Neural Background**: Animated SVG background pattern showcasing cerebral cortex lobes, multipolar neurons, astrocytes, pyramidal brain cells, and synaptic transmission sparks.
6. **Glitch & Shake Effects**: High-exposure visual feedback triggered when pink contamination exceeds 50%.
7. **Local Casualty Leaderboard**: Persistent high-score rankings stored via `localStorage` with automated 1-hour casualty expiration.

---

## 🧮 Mathematical Formulas & Detection Engine

### 1. Pink Pixel Chromatic Thresholding
A pixel is classified as **pink** if its RGB components satisfy:
```javascript
red > 180 && red > (green * 1.2) && blue > green && alpha > 0
```
This chromatic formula isolates hot pinks, barbiecore magentas, and neon rose hues while eliminating neutrals, whites, greens, and warm reds.

### 2. Pink Exposure Percentage
$$\text{Exposure } (\%) = \left( \frac{\text{Pink Pixels}}{\text{Total Pixels}} \right) \times 100$$

### 3. Fictional Brain Cell Casualties
$$\text{Brain Cells Lost} = \text{round}(\text{Pink Pixels} \times 0.75)$$

### 4. Real-Time Camera Downsampling & Scaling
For smooth 60 FPS UI performance, the camera feed is downsampled onto a dedicated $160 \times 120$ analysis buffer. The full-resolution casualty estimate is projected in real time via:
$$\text{Scale Factor} = \frac{W_{\text{video}} \times H_{\text{video}}}{W_{\text{sample}} \times H_{\text{sample}}}$$
$$\text{Estimated Loss} = \text{round}(\text{Pink Pixels}_{\text{sample}} \times \text{Scale Factor} \times 0.75)$$

---

## 🩺 Clinical Diagnostic Stages

| Stage | Exposure Range | Diagnosis Title | Description |
| :---: | :---: | :--- | :--- |
| **1** | 0% – 5% | **Stage 1: Mild Pink Exposure** | Patient shows minor exposure to suspiciously pink imagery. Brain function appears mostly normal. |
| **2** | 5% – 15% | **Stage 2: Pink Contamination** | Elevated pink levels detected. Cognitive function may be mildly compromised. |
| **3** | 15% – 30% | **Stage 3: Barbiecore Exposure** | Patient has entered the Barbiecore danger zone. Immediate exposure to something beige is recommended. |
| **4** | 30% – 50% | **Stage 4: Severe Pinkification** | A dangerous amount of pink has entered the visual system. Brain activity is becoming suspiciously fabulous. |
| **5** | 50% – 70% | **Stage 5: Terminal Barbie Syndrome** | Critical pink exposure detected. Patient may soon begin speaking exclusively in pastel. |
| **6** | 70% – 85% | **Stage 6: Chronic Slay Disorder** | Patient has exceeded medically recommended levels of slay. Brain cells are filing complaints. |
| **7** | 85% – 99% | **Stage 7: Pink Singularity** | The image is approaching complete pink domination. Medical science has no answers. |
| **$\infty$** | 99% – 100% | **Stage Infinity: THE PINK HAS WON** | The image has achieved maximum pink. There is no longer anything left to diagnose. |

---

## 📁 Project Architecture

```
pink-pixel-autopsy/
│
├── index.html        # Semantic HTML structure, dual-mode tabs, camera viewport, HUD telemetry
├── style.css         # Rich pink styling, glassmorphism, animated neural background, scanlines
├── script.js         # Video stream handling, Web Audio Geiger clicks, pixel processing, autopsy engine
└── README.md         # Full project documentation and complete source code listings
```

---

## 🚀 How to Run Locally

1. **Direct File Open**:
   Open `index.html` in any modern web browser (Chrome, Edge, Firefox, Safari).
2. **Live Server / Local Host** (recommended for webcam features):
   Serve the folder via any local server (e.g. VS Code Live Server, or `python -m http.server 8000`).
3. **URL Mode Shortcuts**:
   - `index.html` — Opens in default Upload Mode.
   - `index.html#camera` or `index.html?mode=camera` — Automatically boots directly into Live Camera Scanner mode.

---

# 💻 COMPLETE SOURCE CODE LISTINGS

Below are the complete, unmodified source codes for all files in the project.

---

## 1. `index.html`

```html
<!DOCTYPE html>
<html lang="en">

<head>

    <meta charset="UTF-8">

    <meta
        name="viewport"
        content="width=device-width, initial-scale=1.0"
    >

    <meta
        name="description"
        content="Pink Pixel Autopsy - Find out how many fictional brain cells your image destroys."
    >

    <title>Pink Pixel Autopsy</title>

    <link
        rel="stylesheet"
        href="style.css"
    >

</head>

<body>

    <main class="container">

        <!-- HEADER -->
        <header class="main-header">

            <h1>
                🩷 PINK PIXEL AUTOPSY
            </h1>

            <p class="subtitle">
                Upload an image and discover how many
                fictional brain cells it costs you.
            </p>

            <p class="warning-text">
                ⚠️ This medical technology is absolutely not real.
            </p>

        </header>


        <!-- USERNAME -->
        <section class="input-section">

            <h2>
                👤 PATIENT INFORMATION
            </h2>

            <p>
                Enter your name before we begin the
                extremely questionable medical procedure.
            </p>

            <label for="username">
                Patient Username
            </label>

            <input
                type="text"
                id="username"
                placeholder="Enter your username"
                maxlength="30"
                autocomplete="nickname"
            >

        </section>


        <!-- IMAGE / SCANNER SECTION -->
        <section class="input-section" id="acquisitionSection">

            <h2>
                📸 PATIENT IMAGE ACQUISITION
            </h2>

            <p>
                Select an uploaded image or launch the real-time camera scanner to detect suspiciously dangerous levels of pink.
            </p>

            <!-- MODE SELECTOR TABS -->
            <div class="mode-selector" role="tablist" aria-label="Detection Mode">
                <button
                    type="button"
                    id="tabUpload"
                    class="mode-tab active"
                    role="tab"
                    aria-selected="true"
                    aria-controls="uploadModeContainer"
                >
                    📁 Upload Image
                </button>
                <button
                    type="button"
                    id="tabCamera"
                    class="mode-tab"
                    role="tab"
                    aria-selected="false"
                    aria-controls="cameraModeContainer"
                >
                    📹 Live Camera Scanner
                </button>
            </div>

            <!-- UPLOAD MODE CONTAINER -->
            <div id="uploadModeContainer" class="mode-container active">

                <label for="imageInput">
                    Select Image File
                </label>

                <input
                    type="file"
                    id="imageInput"
                    accept="image/*"
                >

                <div class="preview-container">

                    <img
                        id="imagePreview"
                        alt="Uploaded image preview"
                    >

                </div>

            </div>

            <!-- CAMERA SCANNER MODE CONTAINER -->
            <div id="cameraModeContainer" class="mode-container" style="display: none;">

                <div class="camera-viewport-wrapper">

                    <!-- OFFLINE / PERMISSION OVERLAY -->
                    <div class="camera-status-overlay" id="cameraStatusOverlay">
                        <div class="status-icon">📹</div>
                        <p class="status-title" id="cameraStatusTitle">Camera Scanner Offline</p>
                        <p class="status-subtitle" id="cameraStatusSubtitle">
                            Click "Start Camera" to activate real-time pink detection and live brain cell telemetry.
                        </p>
                        <button
                            type="button"
                            id="startCameraBtn"
                            class="scanner-btn-primary"
                        >
                            ⚡ Start Camera
                        </button>
                    </div>

                    <!-- LIVE VIDEO & HUD CANVAS -->
                    <video
                        id="cameraVideo"
                        autoplay
                        playsinline
                        muted
                    ></video>

                    <canvas id="scannerOverlayCanvas"></canvas>

                    <!-- SCI-FI RETICLE & SCANNER LINE -->
                    <div class="scanner-hud-reticle" id="scannerReticle">
                        <div class="reticle-corner top-left"></div>
                        <div class="reticle-corner top-right"></div>
                        <div class="reticle-corner bottom-left"></div>
                        <div class="reticle-corner bottom-right"></div>
                        <div class="scan-laser-line"></div>
                    </div>

                    <!-- LIVE BADGE -->
                    <div class="hud-live-tag" id="hudLiveTag">
                        <span class="live-pulse-dot"></span> LIVE SCANNER
                    </div>

                    <!-- HIGH PINK DANGER FLASH -->
                    <div class="hud-danger-flash" id="hudDangerFlash"></div>

                </div>

                <!-- REAL-TIME TELEMETRY PANEL -->
                <div class="live-telemetry-panel" id="liveTelemetryPanel">

                    <div class="telemetry-item">
                        <span class="telemetry-label">Live Pink Exposure</span>
                        <span class="telemetry-value" id="livePinkPercent">0.00%</span>
                        <div class="telemetry-progress-track">
                            <div class="telemetry-progress-fill" id="livePinkMeter"></div>
                        </div>
                    </div>

                    <div class="telemetry-item">
                        <span class="telemetry-label">Live Brain Cells At Risk</span>
                        <span class="telemetry-value" id="liveBrainCells">0</span>
                    </div>

                    <div class="telemetry-item stage-item">
                        <span class="telemetry-label">Live Diagnosis</span>
                        <span class="telemetry-badge" id="liveStageBadge">Stage 1: Mild Pink Exposure</span>
                    </div>

                </div>

                <!-- SCANNER CONTROLS TOOLBAR -->
                <div class="scanner-controls-toolbar">

                    <button
                        type="button"
                        id="toggleCameraBtn"
                        class="scanner-tool-btn"
                        title="Start or Stop Camera"
                    >
                        ⏹️ Stop Camera
                    </button>

                    <button
                        type="button"
                        id="flipCameraBtn"
                        class="scanner-tool-btn"
                        title="Switch between front and back camera"
                    >
                        🔄 Flip Camera
                    </button>

                    <button
                        type="button"
                        id="toggleMaskBtn"
                        class="scanner-tool-btn active"
                        title="Toggle Pink Heatmap Overlay"
                    >
                        ✨ Heatmap: ON
                    </button>

                    <button
                        type="button"
                        id="toggleSoundBtn"
                        class="scanner-tool-btn"
                        title="Toggle Geiger audio pulse"
                    >
                        🔇 Sound: OFF
                    </button>

                </div>

                <div class="camera-action-row">

                    <button
                        type="button"
                        id="captureAnalyzeBtn"
                        class="scanner-btn-capture"
                    >
                        🩺 Freeze Frame & Perform Autopsy
                    </button>

                </div>

            </div>

        </section>


        <!-- AUTOPSY BUTTON (FOR UPLOAD MODE) -->
        <section class="input-section" id="autopsyActionSection">

            <h2>
                🩺 READY FOR AUTOPSY?
            </h2>

            <p id="autopsyInstructionText">
                Our highly questionable medical equipment is standing by.
            </p>

            <button
                id="analyzeButton"
                type="button"
            >
                🩺 Perform Autopsy
            </button>

        </section>


        <!-- REPORT -->
        <section
            id="report"
            aria-live="polite"
        ></section>

    </main>


    <!-- LEADERBOARD -->
    <section
        id="leaderboard"
        aria-label="Brain cell casualty leaderboard"
    ></section>


    <!-- FOOTER -->
    <footer class="site-footer">

        <p>
            🧠 No actual brain cells were harmed.
        </p>

        <p>
            🩷 Pink Pixel Autopsy &copy; 2026
        </p>

    </footer>


    <!-- JAVASCRIPT -->
    <script src="script.js"></script>

</body>

</html>
```

---

## 2. `style.css`

*(See [style.css](file:///c:/Users/A/Desktop/pink-pixel-autopsy/style.css) for full responsive rules, glassmorphism, animated neural background pattern, and HUD scanline styling).*

---

## 3. `script.js`

*(See [script.js](file:///c:/Users/A/Desktop/pink-pixel-autopsy/script.js) for camera stream management, real-time downsampled frame processing, Web Audio synthesizer, unified autopsy engine, and local storage leaderboard).*

---

## 📄 License & Attribution

- Created for comedic and educational purposes.
- Released under the MIT License.
