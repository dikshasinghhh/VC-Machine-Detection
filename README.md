# VC Video Object Detection Pipeline

 Advanced framewise object detection pipeline for **industrial inspection videos**, leveraging **YOLOv8s and YOLOv5s** fine-tuned on custom CVAT annotations with automated preprocessing and clean dataset management for scalable training and inference.

---

## Project Overview

This project builds a **video object detection pipeline** for **industrial part placement inspection** using a **single annotated video (~2390 frames)** labeled frame-by-frame on **CVAT**. The pipeline detects:

- `base plate`
- `inner plate`
- `multi lobe plate-1`
- `multi lobe plate-2`
- `multi lobe plate-3`
- `springs`
- `outer plate`

using **YOLOv8s and YOLOv5s** for experimentation, achieving high-speed inference and accurate detection for production-level inspection pipelines.

---

## 📂 **Dataset**

- **Source**: Annotated on CVAT, exported in YOLO format.
- **Frames**: ~2390, frame-by-frame annotated.
- **Classes**: 8 industrial parts.
- **Preprocessing**: Only labeled frames are extracted from the video using OpenCV.

## **Environment**
- Python: 3.10+ <br>
- PyTorch: 2.2+ <br>
- ultralytics: latest (pip install ultralytics --upgrade) <br>
- GPU: Trained on Kaggle T4 GPU environment <br>

<h2> Workflow</h2>

<p><strong>1️⃣ Preprocessing</strong><br>
Extract labeled frames using OpenCV scripts.<br>
Organize dataset into YOLO <code>images/train</code>, <code>images/val</code>, <code>labels/train</code>, <code>labels/val</code>.
</p>

<p><strong>2️⃣ Training</strong><br>
Fine-tune <code>yolov8s.pt</code> using <code>ultralytics</code> on Kaggle GPU with:<br>
<code>epochs=100</code>, <code>batch=8</code>, <code>imgsz=640</code><br>
Advanced augmentations: RandAugment, Mosaic, Mixup, Perspective, HSV, Flip, Scale.
</p>
