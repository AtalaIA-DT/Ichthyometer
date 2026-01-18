## **Angler-Friendly AI Pipeline for Recreational Fisheries**
**Code + Species Classification Dataset**

This repository contains the **full pipeline code** and the **species classification dataset** used in the paper:  
**“An Angler-Friendly AI Pipeline for Self-Reporting and Automatic Catch Analysis in Recreational Fisheries.”**

### **What it does**
It turns angler-submitted **smartphone catch photos** into **standardized, analysis-ready records** (species composition, individual lengths) via a modular workflow:

1. **Fish detection** — *Grounding DINO* (text-prompted with **“fish”**)  
2. **Instance segmentation** — *SAM2* (pixel-accurate masks)  
3. **Species classification** — *CLIP + lightweight visual adapter* (few-shot, data-efficient)  
4. **Length estimation (optional)** — **AprilTag ichthyometer** → homography-based **pixel-to-cm** calibration + midline fitting

### **Dataset (classification)**
The released dataset targets a **mixed-species recreational fishery (western Mediterranean)** and is designed for **few-shot learning**:
- **38 species**
- Fixed splits per species (e.g., **12 train / 4 val / 8 test** images when available)
- Fish provided as **single-instance crops** derived from segmentation (standardized background/padding)

### **Reported performance (paper)**
Validated under realistic field conditions (variable lighting, clutter, occlusions, mixed catches):
- **Detection + segmentation:** **F1 ≈ 0.93**
- **Species classification:** **0.85 accuracy** across **38 species** with **few-shot training**
- **Length estimation:** **MAE ≈ 1.25 cm** (when the AprilTag board is present)

### **Use cases**
- **Reproduce the paper results**
- **Train/extend the classifier** to new species or regions with minimal extra labeling
- **Deploy the pipeline** as a backend service integrated with catch-reporting apps and monitoring workflows
