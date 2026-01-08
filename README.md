## DETR Training (COCO-format)

Dataset is not included (too large).
Place dataset at: ./coco/

Expected:
coco/train2017/
coco/val2017/
coco/annotations/instances_train2017.json
coco/annotations/instances_val2017.json

Train:
python3 detr_tutorial/detr/main.py \
  --dataset_file coco \
  --coco_path coco \
  --num_classes 11 \
  --output_dir runs/detr_run \
  --epochs 50 \
  --lr 1e-4 \
  --lr_backbone 1e-5 \
  --batch_size 2 \
  --num_workers 2
