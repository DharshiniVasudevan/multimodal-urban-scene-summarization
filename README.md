# A Multimodal Knowledge-Driven Framework for Urban Scene Summarization

Final-year B.Tech. Computer Science capstone project — Srinivasa Ramanujan Centre, SASTRA Deemed to be University, Kumbakonam.

An end-to-end pipeline that processes dashcam/surveillance video to build a **Dynamic Knowledge Graph (DKG)** of a scene, detect safety-relevant events, and generate natural-language narratives — fusing visual detections with audio cues that traditional video analytics discard entirely (sirens and other sounds).

## Team

| Register No. | Name |
|---|---|
| 226003163 | Dharshini V |
| 226003135 | Sushma Sri R |
| 226003049 | Gayathri A |

**Guide:** Smt. S. Hemamalini, AP-II / CSE

## Problem Statement

Urban surveillance systems produce more video data than human operators can meaningfully monitor. Traditional video analytics rely solely on visual detection and process each frame independently, discarding audio signals entirely, and no existing lightweight system links object detection, relational reasoning, and structured response generation into a single pipeline — leaving scene summaries without real semantic grounding.

## Pipeline Architecture

| Module | Name | Role |
|--------|------|------|
| M0 | Preprocessor | Audio extraction + YAMNet tokenisation |
| M1 | Perception | YOLOv11x object detection + ByteTrack |
| M2 | Tracking | Velocity, acceleration, direction features |
| M3 | Relation Inference | Spatial + audio-visual triplet generation (rule-based) |
| M4 | Dynamic Knowledge Graph | Temporal Bayesian graph construction |
| M5 | Event Engine | Rule-based event detection (16 event types) |
| M6 | Summarizer | Phi-3 Mini narrative generation |
| M7 | Visualizer | DKG plots + annotated video export |
| M8 | Action & Response | JSON-based response suggestion + incident deduplication |

## Dataset

TAU, MAVAD, and a small set of custom test videos used for evaluation.

## Evaluation

The pipeline is assessed with 20 metrics spanning four dimensions: audio-visual fusion quality, knowledge graph structure, event detection accuracy, and narrative quality (including predicate diversity entropy, entity hallucination rate, node coverage ratio, Bayesian fusion gain, and throughput).

## Repository Structure

```
multimodal-urban-scene-summarization/
├── Multimodal_Urban_Scene_Summarization.ipynb
├── requirements.txt
├── README.md
└── LICENSE
```

## Setup

```bash
git clone https://github.com/<your-username>/multimodal-urban-scene-summarization.git
cd multimodal-urban-scene-summarization
pip install -r requirements.txt
```

The notebook was developed and run on Kaggle (GPU runtime). Update `VIDEO_PATH` and `WORKING_DIR` in the configuration cell to point to your own input video and working directory before running locally.

## Tech Stack

- **Vision:** Ultralytics YOLOv11x, Supervision, PyTorch
- **Audio:** TensorFlow / YAMNet, Librosa
- **NLP:** Transformers (Phi-3 Mini), Accelerate, BitsAndBytes (4-bit quantization)
- **Graph:** NetworkX, PyVis
- **Evaluation:** BERTScore

## Acknowledgements

Developed under the guidance of Smt. S. Hemamalini, Department of CSE, Srinivasa Ramanujan Centre, SASTRA Deemed to be University.
