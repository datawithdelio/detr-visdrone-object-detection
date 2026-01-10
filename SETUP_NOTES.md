# SkelAI + COCO Setup Notes

## Goal
Prepare VisDrone dataset for DETR by:
1) generating SkelAI skeleton images for each split
2) converting VisDrone annotations to COCO JSON
3) creating COCO folder structure expected by README

## SkelAI preprocessing (creates images_skel/)
Commands:
- python tools/skelai_preprocess.py --input VisDrone2019-DET-train/images --output VisDrone2019-DET-train/images_skel
- python tools/skelai_preprocess.py --input VisDrone2019-DET-val/images   --output VisDrone2019-DET-val/images_skel
- python tools/skelai_preprocess.py --input VisDrone2019-DET-test-dev/images --output VisDrone2019-DET-test-dev/images_skel

Verification (counts must match):
- train: 6471 == 6471
- val:   548  == 548
- test:  1610 == 1610

## Convert VisDrone annotations -> COCO JSON
Command:
- python tools/visdrone_to_coco.py

Outputs:
- coco/annotations/instances_train2017.json
- coco/annotations/instances_val2017.json

## COCO folder structure (expected by README)
- coco/train2017/  (image files)
- coco/val2017/    (image files)
- coco/annotations/instances_train2017.json
- coco/annotations/instances_val2017.json

## How images are linked (symlinks)
We symlinked original images into COCO folders:
- ln -s VisDrone2019-DET-train/images/* coco/train2017/
- ln -s VisDrone2019-DET-val/images/*   coco/val2017/

To use SkelAI images instead later:
- ln -s VisDrone2019-DET-train/images_skel/* coco/train2017/
- ln -s VisDrone2019-DET-val/images_skel/*   coco/val2017/
