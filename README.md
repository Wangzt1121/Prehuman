# Prehuman
CUDA_VISIBLE_DEVICES=0,1,2,3,4,5,6,7 accelerate launch --config_file examples/flux/model_training/full/accelerate_config.yaml examples/flux/model_training/train.py \
  --dataset_base_path ./Prehumans/ \
  --dataset_metadata_path ./prompt.json \
  --data_file_keys "image,kontext_images" \
  --max_pixels 1048576 \
  --dataset_repeat 1 \
  --learning_rate 1e-5 \
  --num_epochs 3 \
  --remove_prefix_in_ckpt "pipe.dit." \
  --save_steps 700 \
  --output_path "./checkpoint/train/full" \
  --trainable_models "dit" \
  --extra_inputs "kontext_images" \
  --resume_from_checkpoint /nvmedata/workspace2/users/wzt/DiffSynth-Studio/checkpoint/train/step-700.safetensors \
  --use_gradient_checkpointing \
  --use_gradient_checkpointing_offload \
  --model_paths " [\"/nvmedata/workspace2/users/wzt/pretrained/FLUX.1-Kontext-dev/flux1-kontext-dev.safetensors\",
  \"/nvmedata/workspace2/users/wzt/pretrained/FLUX.1-dev/text_encoder/model.safetensors\",
  \"/nvmedata/workspace2/users/wzt/pretrained/FLUX.1-dev/text_encoder_2/model.safetensors\",
  \"/nvmedata/workspace2/users/wzt/pretrained/FLUX.1-dev/ae.safetensors\"]"
