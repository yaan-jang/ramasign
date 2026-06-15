# RamaSign ver 1.0

# Generative Protein Design via Diffusion on Ramachandran Maps

This repository implements a **generative protein design framework** using a **Transformer-based diffusion model** operating directly over **Ramachandran maps** (φ–ψ backbone torsion angle space). The model learns to generate realistic proteins by modeling the intrinsic geometry of protein structures in a compact, biologically meaningful representation.


## Overview

This approach enables:

- Generation of physically plausible proteins
- Learning of structural priors from protein datasets
- Efficient sampling in low-dimensional torsion space
- Conditional protein design (sequence/structure/evolutionary constraints)
- Exploration of novel folds


## Key Idea

We reformulate protein generation as diffusion over Ramachandran basins:

- **State space:** sequences of (φ, ψ) angles per residue  
- **Forward process:** gradual corruption with wrapped/angular noise  
- **Reverse process:** Transformer-based denoising model  
- **Output:** reconstructed protein sequences from denoised basins  

Unlike Cartesian diffusion models, this approach directly models the **biologically meaningful conformational space**.


## Model Architecture

### Transformer-based Denoiser
- Sequence-level attention over residues
- Captures long-range structural dependencies
- Supports conditioning (sequence, motifs, evolution, constraints)

### Diffusion Process
- Forward noising in Ramachandran space using wrapped Gaussian noise
- Reverse process learned via neural denoiser
- Operates on sin/cos embeddings to ensure periodicity


## Features

- Diffusion modeling in Ramachandran space
- Transformer-based diffusion architecture
- Conditional generation support
- PyTorch implementation


## Installation

```bash
git clone https://github.com/yaan-jang/ramasign.git
cd ramasign

pip install -r requirements.txt
```

## Usage
```
python generation.py \
  --config configs/config_generate_demo.yaml \
  --seed 42 
```

## Applications

- De novo protein backbone design  
- Structural biology hypothesis generation  
- Protein fold space exploration  
- Conditional protein generation  
- Pretraining representations for downstream folding models  


## Technical Details

- Diffusion is performed directly in **Ramachandran space**  
- Uses sinusoidal embeddings for stability  
- Transformer captures long-range residue interactions  
- Sampling can incorporate conditional guidance  


## License

This project is licensed under the Apache License (version 2.0).
