# Real-Time Speed Tracking

Minimal, notebook-first workflow for measuring the speed of moving objects from a recorded video or a live webcam stream — all inside Google Colab.

[Open the TLDraw Planning Board ›](https://www.tldraw.com/f/T6oHe2VW4S5P4fRhE0Aqv?d=v-8987.-3939.16148.7670.-3ammlZr97oO5MAsfNS3P)

---

## ✨ Highlights
- Run entirely in Google Colab (no local setup)
- Custom Graph for Pixel Coordinate Calculation
- Works with uploaded video files or live webcam (Colab JS capture)
- Calibrated real-world speed estimation (px → meters)
- Frame-by-frame object tracking with smoothing
- Overlay: trajectory, instantaneous + average speed
- Modular cells you can remix
- Custom Color Assignment


---

## 📂 Notebook Structure 

| Section | Purpose |
|---------|---------|
| Setup & Imports | Install + import libraries |
| Config | Tunable params (FPS override, smoothing, detection model) |
| Media Input | Upload video / activate webcam |
| Calibration | Convert pixels → meters |
| Detection | Locate object(s) per frame |
| Tracking | Persist identity + position history |
| Speed Computation | Distance / time with smoothing |
| Visualization | Overlay bounding boxes, path, speed text |
| Export | Save processed MP4 + metrics CSV |

---

## 🧠 How It Works

1. Read frame (video or webcam)
2. Detect object (centroid or bounding box)
3. Track motion: store sequential positions
4. Compute frame delta distance in pixels
5. Convert to meters using:  
   meters = pixels * (meters_per_pixel)
6. Speed (m/s) = delta_meters / delta_time  
   Then optionally: km/h = m/s * 3.6
7. Apply smoothing (moving average or exponential)
8. Draw overlays + write out frame

---

## ⚙️ Configuration Knobs

| Parameter | Description | Example |
|-----------|-------------|---------|
| `PIXEL_BASELINE` | Pixel length of known distance | 420 |
| `REAL_DISTANCE_M` | Real distance in meters | 5.0 |
| `SMOOTH_WINDOW` | Moving average window (frames) | 5 |
| `MIN_CONF` | Detection confidence threshold | 0.4 |
| `OUTPUT_FPS` | Override if metadata wrong | 30 |

Meters-per-pixel = REAL_DISTANCE_M / PIXEL_BASELINE

---

## 🧪 Detection Options

- Simple: Color threshold / contour (fast, controlled scenes)
- Intermediate: Background subtraction (static camera)
- Robust: Pretrained model (e.g. YOLO) for general objects

Swap the detection cell to upgrade accuracy without rewriting the rest.


---

## 📈 Tips for Better Accuracy

- Use high-FPS source (≥30fps)
- Avoid motion blur (good lighting)
- Keep camera stable (mounted)
- Calibrate using longest measurable distance
- Prefer perpendicular camera angle to motion plane

---

## 🔄 Roadmap (Feel Free to Extend)

- [x] Multi-object tracking
- [x] Perspective (homography) correction
- [ ] Auto baseline detection (lane markers etc.)
- [ ] Confidence bands on speed
- [ ] Edge device adaptation


---

## 🙏 Acknowledgements

- Roboflow community for video + geometry tools
- Colab for frictionless experimentation
- YOLO / Ultralytics / Supervision / OpenCV


---

## 🗣️ Support

Questions? Open an Issue with:
- Example frame
- Video FPS
- Calibration details
- Detection method used

---

Built for clarity, remixability, and learning. Enjoy measuring motion.
