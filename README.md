# 🍰 Layered Representations from a Single Image

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![PyTorch](https://img.shields.io/badge/PyTorch-Deep%20Learning-ee4c2c.svg)

This project provides an automated pipeline to decompose a single RGB image into a stack of interpretable, re-composable RGBA layers. By combining state-of-the-art foundation models for segmentation, depth estimation, and generative inpainting, it transforms flat images into a 3D-aware scene structure.

These extracted layers are highly useful for advanced image editing, 2.5D parallax animations, scene relighting, and downstream computer vision tasks.

### ✨ Key Features
* **Semantic Grouping:** Automatically discovers and extracts crisp object masks (people, furniture, animals) using **Segment Anything (SAM)**.
* **Relative Depth Ordering:** Generates high-resolution global depth maps using **Depth Anything V2** to sort layers accurately from background to foreground (near $\rightarrow$ far).
* **Generative Background Inpainting:** Subtracts foreground objects and hallucinates the missing background pixels using models like **LaMa**, ensuring layers can move independently without leaving visual "holes".
* **Intrinsic Decomposition (Experimental):** Separates base layer colors (albedo) from lighting and shading maps for realistic scene relighting.

### 🚀 The Pipeline
1. **Input:** A single 2D bitmap image.
2. **Process:** `RGB` $\rightarrow$ `Global Depth Map + SAM Masks` $\rightarrow$ `Z-Index Sorting` $\rightarrow$ `Layer Inpainting`.
3. **Output:** A directory of ordered, transparent RGBA `.png` files ready for compositing or animation.
