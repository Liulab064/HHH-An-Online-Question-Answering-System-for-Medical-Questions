The selected pre-train model is `uncased_L-12_H-768_A-12`

The running platform is Colab and you can run it on other Linux system.

The total number of data = `10000`

The number distribution of `Train: dev: test = 6:2:2`

First experiment result eval_accuracy: `0.7702703`

Second experiment result eval_accuracy: `0.7612613`

Third experiment result eval_accuracy: `0.7742743`

Average eval_accuracy by three times experiments: `0.76860196666`

Range of change: `(-0.00734066666, +0.00567233334)`

Here is the code of running the `run_classifier.py` with detail training parameters which includes training and evaluation.
```
python run_classifier.py \
  --task_name=quora \
  --do_train=True \
  --do_eval=True \
  --do_predict=True \
  --data_dir=../Data/Model_train_dev_test_dataset/BERT_train_dev_test_dataset/ \
  --vocab_file=gs://cloud-tpu-checkpoints/bert/uncased_L-12_H-768_A-12/vocab.txt \
  --bert_config_file=gs://cloud-tpu-checkpoints/bert/uncased_L-12_H-768_A-12/bert_config.json \
  --init_checkpoint=gs://cloud-tpu-checkpoints/bert/uncased_L-12_H-768_A-12/bert_model.ckpt \
  --max_seq_length=128 \
  --train_batch_size=32 \
  --learning_rate=5e-5 \
  --num_train_epochs=2.0 \
  --output_dir=output 
```

Training script is referred from [Sentence (and sentence-pair) classification tasks](https://github.com/google-research/bert#sentence-and-sentence-pair-classification-tasks)

Test script is referred from [Prediction from classifier](https://github.com/google-research/bert#prediction-from-classifier)
