# SpanPSP
The pretrained models will be released soon.

## Environment
* Python 3.7 or higher.
* Pytorch 1.6.0, or any compatible version.
* NLTK 3.2, torch-struct 0.4, transformers 4.3.0, or compatible.
* pytokenizations 0.7.2 or compatible.

## Repository structure
```
SpanPSP
├──bert-base-chinese
|   ├──config.json
|   ├──pytorch_model.bin
|   └──vocab.txt
├──data
|   ├──train
|   |   ├──raw_data
|   |   |   ├──raw_train.txt
|   |   |   ├──raw_validate.txt
|   |   |   └──raw_test.txt
|   |   └──tree_data
|   |       ├──tree_train.txt
|   |       ├──tree_validate.txt
|   |       └──tree_test.txt
|   └──inference
|       ├──raw_data
|       |   └──raw_data.txt
|       ├──tree_data
|           └──tree_data.txt
├──models
|   ├──pretrained_model
|   |   └──pretrained_SpanPSP.pt
|   └──yours
├──src
|   ├──benepar
|       ├── ...
|   ├──count_fscore.py
|   ├──evaluate.py
|   ├──export.py
|   ├──inference_seq2tree.py
|   ├──learning_rate.py
|   ├──main.py
|   ├──seq_with_label.py
|   ├──train_seq2tree.py
|   ├──transliterate.py
|   ├──treebank.py
├──README.md
```


## Training and test with your dataset (soon)
### Data preprocessing
First prepare your own dataset into the following format, and put it in the right place as shown in the repository structure.
> 猴子#2用#1尾巴#2荡秋千#3。
```
$ python src/train_seq2tree.py
```
### Training
Train your model using:
```
$ python src/main.py  train  --train-path [your_training_data_path]  --dev-path [your_dev_data_path]  --model-path-base [your_saving_model_path] 
```
### Test
Test your model using:
```
$ python src/main.py  test  --model-path [your_trained_model_path]  --test-path [your_test_data_path]
```
## Using the pre-trained model to automatically label the prosody structure of text data (soon)
### Data preprocessing
First prepare your own dataset into the following format, and put it in the right place as shown in the repository structure.
> 猴子用尾巴荡秋千。
```
$ python src/inference_seq2tree.py
```
### Automatic labeling
```
$ python src/main.py  auto_labels  --model-path [your_pretrained_model_path]  --test-path [your_test_data_path]  --output-path [your_output_data_path]
```
