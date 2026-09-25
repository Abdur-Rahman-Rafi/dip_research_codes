# Proposed complete research pipeline

                 LOW-LIGHT IMAGE
                       │
                       ▼
              ┌─────────────────┐
              │ Feature Extractor│
              └────────┬────────┘
                       │
       ┌───────────────┼────────────────┐
       ▼               ▼                ▼
    Texture         Brightness       Entropy
   LBP + GLCM                          │
       │                               │
       └───────────────┬───────────────┘
                       ▼
                 Edge Density
                       │
                       ▼
                 F = [T,B,H,D]
                       │
                       ▼
        ┌──────────────────────────┐
        │ Feature-Guided Predictor │
        │      MLP Network         │
        └────────────┬─────────────┘
                     │
             ┌───────┼────────┐
             ▼       ▼        ▼
          Strength Contrast Denoise
             │       │        │
             └───────┼────────┘
                     ▼
                Zero-DCE++
                     │
                     ▼
             DCE++ Enhanced
                     │
                     ▼
             Adaptive Blending
                     │
                     ▼
             Adaptive Contrast
                     │
                     ▼
             Adaptive Denoising
                     │
                     ▼
              FINAL IMAGE
