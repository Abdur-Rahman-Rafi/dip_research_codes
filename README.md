# Proposed complete research pipeline

                    ┌──────────────────────────────┐
                    │        DATASETS              │
                    └──────────────────────────────┘
                               │
          ┌────────────────────┼────────────────────┐
          │                    │                    │
          ▼                    ▼                    ▼
     LOL-v2                  LOL                 ExDark
     Training              Validation          Real-world
          │                    │                Evaluation
          │                    │                    │
          └──────────────┬─────┴────────────────────┘
                         │
                         ▼
              ┌───────────────────────┐
              │   Image Preprocessing │
              │ Resize / Normalize     │
              │ RGB Conversion         │
              └───────────┬───────────┘
                          │
                          ▼
          ┌────────────────────────────────┐
          │  FEATURE EXTRACTION             │
          │                                │
          │  1. Texture → LBP + GLCM       │
          │  2. Brightness                 │
          │  3. Entropy                   │
          │  4. Edge Density → Canny       │
          └───────────────┬────────────────┘
                          │
                          ▼
                  Feature Vector
                  F = [T,B,H,D]
                          │
                          ▼
          ┌────────────────────────────────┐
          │ Detail-Sensitivity Estimation  │
          │                                │
          │ S = 0.60T + 0.10H + 0.30D     │
          └───────────────┬────────────────┘
                          │
                          ▼
          ┌────────────────────────────────┐
          │ Adaptive Parameter Prediction  │
          │                                │
          │ Enhancement Strength           │
          │ Contrast                       │
          │ Denoising Strength             │
          └───────────────┬────────────────┘
                          │
                          ▼
               ┌────────────────────┐
               │   Zero-DCE++       │
               │  Primary Backbone  │
               └─────────┬──────────┘
                         │
                         ▼
              Zero-DCE++ Enhanced Image
                         │
                         ▼
          ┌────────────────────────────────┐
          │ Adaptive Post-Processing       │
          │                                │
          │  Adaptive Blending             │
          │  Adaptive Contrast             │
          │  Adaptive Denoising            │
          └───────────────┬────────────────┘
                          │
                          ▼
                FINAL ENHANCED IMAGE
                          │
          ┌───────────────┼────────────────┐
          │               │                │
          ▼               ▼                ▼
        LOL-v2           LOL              ExDark
       Training       Validation       Real-world Test
                          │
                          ▼
                SID Generalization
                          │
                          ▼
          ┌───────────────────────────────┐
          │       EVALUATION              │
          │                               │
          │ PSNR                          │
          │ SSIM                          │
          │ NIQE                          │
          │ BRISQUE                       │
          │ Detection mAP                 │
          │ Inference Time                │
          └───────────────────────────────┘
