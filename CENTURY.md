# Century

In this file I document changes we make to our fork of Meta's Segment Anything Model.

## Setup

I've switched over to `uv` for control of the packages and environment for this project. Here are the commands I used to get it set up:

    uv venv
    source .venv/bin/activate
    uv pip install --editable .
    uv init
    uv add opencv-python pycocotools matplotlib onnxruntime onnx

## Model

I've downloaded the largest model here:

    checkpoints/sam_vit_h_4b8939.pth


