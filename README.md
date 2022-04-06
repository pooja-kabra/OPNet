# Instructions
To run train the network or run inference, you first need to download the [LA-CATER dataset](https://chechiklab.biu.ac.il/~avivshamsian/OP/OP_HTML.html#DatasetLinks) and extract the folders into `data/train_data`, `data/val_data`, and `data/test_data` directories.

## Training
The Transformer models can be trained by running:
```sh
# Transformer+LSTM
$ python main.py --model_type transformer_lstm --model_config configs/transformer_lstm_model_config.json --training_config configs/training_config.json
# Transformer+Transformer
$ python main.py --model_type double_transformer --model_config configs/double_transformer_model_config.json --training_config configs/training_config.json
```

## Inference
Inference can be done by running:
```sh
# Transformer+LSTM
$ python main.py --model_type transformer_lstm --model_config configs/transformer_lstm_model_config.json --results_dir ./results --inference_config configs/inference_config.json
# Transformer+Transformer
$ python main.py --model_type double_transformer --model_config configs/double_transformer_model_config.json --results_dir ./results --inference_config configs/inference_config.json
```

## Analysis
The results of inference can be parsed and analyzed to get IoU and mAP metrics.
```sh
$ python main.py analysis --predictions_dir ./results --labels_dir test_data/labels --containment_annotations test_data/containment_and_occlusions/containment_annotations.txt --containment_only_static_annotations test_data/containment_and_occlusions/containment_only_static_annotations.txt --containment_with_movements_annotations test_data/containment_and_occlusions/containment_with_move_annotations.txt --visibility_ratio_gt_0 test_data/containment_and_occlusions/visibility_rate_gt_0.txt --visibility_ratio_gt_30 test_data/containment_and_occlusions/visibility_rate_gt_30.txt --iou_thresholds 0.5,0.9 --output_file results.csv
```

# Previous works
This project was based on the dataset and task defined in "Learning Object Permanence from Video."
```
@inproceedings{shamsian2020learning,
  title={Learning object permanence from video},
  author={Shamsian, Aviv and Kleinfeld, Ofri and Globerson, Amir and Chechik, Gal},
  booktitle={European Conference on Computer Vision},
  pages={35--50},
  year={2020},
  organization={Springer}
}
```
