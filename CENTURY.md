# Century

In this file I document changes we make to our fork of Meta's Segment Anything Model.

## Setup

I've switched over to `uv` for control of the packages and environment for this project. Here are the commands I used to get it set up:

    uv venv
    source .venv/bin/activate
    uv pip install --editable .
    uv init
    uv add opencv-python pycocotools matplotlib onnxruntime onnx torch torchvision
    uv add --dev ipython

The above only needed to be done once to set it up, now you can just install all the dependencies using:

    uv sync

## Model

I've downloaded the largest model here:

    checkpoints/sam_vit_h_4b8939.pth

The model can be loaded in python as follows:

    from segment_anything import sam_model_registry, SamAutomaticMaskGenerator
    import cv2
    sam = sam_model_registry["vit_h"](checkpoint="checkpoints/sam_vit_h_4b8939.pth")
    _ = sam.to(device="cuda")
    mask_generator = SamAutomaticMaskGenerator(sam)
    image_fn = "test_discs.png"
    image = cv2.imread(image_fn)
    image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
    masks = mask_generator.generate(image)
    len(masks)
    # 43
    ", ".join(masks[0].keys())
    # 'segmentation, area, bbox, predicted_iou, point_coords, stability_score, crop_box'







