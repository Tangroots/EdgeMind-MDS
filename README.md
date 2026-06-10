# EdgeMind-MDS
Multimodal Surveillance Dataset for Edge Behavior & Camera State Joint Reasoning

---

## Table of Contents
- [Introduction](#introduction)
- [Dataset Access](#dataset-access)
- [Dataset Overview](#dataset-overview)
  - [Data Modalities](#data-modalities)
  - [Label Categories](#label-categories)
  - [Preprocessing Pipeline](#preprocessing-pipeline)
- [Usage](#usage)
- [Experimental Protocol](#experimental-protocol)
- [Data Release Statement](#data-release-statement)

---

## Introduction
EdgeMind-MDS is a real-world multimodal surveillance dataset constructed for the paper **EdgeMind: Joint Human Behavior and Camera State Reasoning with Multimodal LLM at Edge**, published in *IEEE Transactions on Mobile Computing*.

This dataset consists of **synchronized video frames and vibration sensor signals**, designed for two core tasks: human behavior analysis and camera state diagnosis. Data is collected in typical edge surveillance scenarios including hallways, colonnades and entrance lobbies. We also conducted experiments to explore the influence of different sensor installation structures. We evaluated the model's performance under the original floor tile setup (O) and three alternative supporting structures: concrete wall (C), hollow metal pole (M), and wooden structure (W).

## Dataset Access
Some data files are stored in the **`dataset/`** folder of this repository:
- `dataset/sensers_npz/`: Contains vibration sensor signals in `.npz` format.
- `dataset/videos_npy/`: Contains preprocessed video frame sequences in `.npy` format.

## Dataset Overview
### Data Modalities
- Synchronized video stream
- Vibration time-series signals (filtered, normalized and processed via STFT)

### Label Categories
#### 1. Human Behavior
- NPP: No person present
- NW: Normal walking
- SS: Standing still
- VSM: Variable-speed motion
- PC: Path change
- J: Jumping

#### 2. Camera State
- NO: Normal operation
- MO: Malicious occlusion
- EO: Environmental occlusion
- MS: Malicious shaking
- ED: Environmental disturbance

### Preprocessing Pipeline
1. **Video**: Resize frames to uniform resolution and extract frame sequences via equidistant downsampling.
2. **Vibration Signal**: Apply band-pass filtering to eliminate noise, perform normalization and Short-Time Fourier Transform (STFT), followed by frequency band aggregation and temporal pooling.
3. **Alignment**: Synchronize video and vibration data strictly by timestamps.

## Usage
This dataset is applicable for:
- Edge intelligent surveillance algorithm development
- Multimodal large language model (MLLM) cross-modal fusion and instruction reasoning
- Multi-task learning for joint behavior analysis and device status diagnosis
- Robust perception evaluation under low-light and visual interference conditions

## Experimental Protocol
- Data split: Training set, validation set and test set are divided with fixed ratios (see documents for details).
- Evaluation Metrics: Macro-F1, Exact Match Ratio (EMR), Hamming Loss (HL), BLEU, ROUGE.
- Baselines: Compatible with mainstream models including X3D-M, I3D, SlowFast, Qwen2-VL, CogVLM2-Video, etc.

## Data Release Statement
To balance reproducibility and privacy protection, we will provide partial data on GitHub, together with a detailed statistical summary, category definitions, preprocessing configuration, and experimental protocol. We also plan to release a more complete version after privacy-preserving vectorization and anonymization are completed.
