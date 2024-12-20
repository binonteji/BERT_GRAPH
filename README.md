

## Installation

    $ pip install -r requirements.txt

## Train BERTwalk

You can run `--help` option to view optional args:

    $ python3 train_bert_walk.py --help

```
usage: train_bert_walk.py [-h] [--batch_size BATCH_SIZE] [--emsize EMSIZE] [--nhid NHID] [--nlayers NLAYERS] [--nhead NHEAD] [--dropout DROPOUT]
                          [--learning_rate LEARNING_RATE] [--epochs EPOCHS] [--K K] [--alpha ALPHA] [--mask_rate MASK_RATE] [--p P] [--q Q]
                          [--walk_length WALK_LENGTH] [--num_walks NUM_WALKS] [--input_graphs INPUT_GRAGHS]

Train the BERT_GRAPH model on MLM task.

optional arguments:
  -h, --help            show this help message and exit
  --batch_size BATCH_SIZE
                        Size of batch.
  --emsize EMSIZE       Dim of embbeding.
  --nhid NHID           Num of hidden dim.
  --nlayers NLAYERS     Num of transformer layers.
  --nhead NHEAD         Num of attention heads in transformer.
  --dropout DROPOUT     dropout.
  --learning_rate LEARNING_RATE
                        Learning rate.
  --epochs EPOCHS       Num of training epochs.
  --K K                 Num of propagation iterations.
  --alpha ALPHA         Reset factor RWR.
  --mask_rate MASK_RATE
                        masking rate MLM.
  --p P                 Return hyperparameter. Default is 1.
  --q Q                 Inout hyperparameter. Default is 1.
  --walk_length WALK_LENGTH
                        Length of random walk.
  --num_walks NUM_WALKS
                        Num of walks from each node.
  --input_graphs        Networks files to be integrated.
```

Example, training for yeast:
```
    python train_bert_walk.py --walk_length 10 --organism FIRSTMM_DB --epochs 40 --input_graphs inputs/FIRSTMM_DB/FIRSTMM_DB_0.txt inputs/FIRSTMM_DB/FIRSTMM_DB_1.txt inputs/FIRSTMM_DB/FIRSTMM_DB_2.txt inputs/FIRSTMM_DB/FIRSTMM_DB_3.txt inputs/FIRSTMM_DB/FIRSTMM_DB_4.txt inputs/FIRSTMM_DB/FIRSTMM_DB_5.txt inputs/FIRSTMM_DB/FIRSTMM_DB_6.txt inputs/FIRSTMM_DB/FIRSTMM_DB_7.txt inputs/FIRSTMM_DB/FIRSTMM_DB_8.txt
```
## Extract Embedding from Trained 

Models are located under `artifacts/`.

    $ python3 extract_embedding_from_trained.py --model_name <trained model name>

## Train Sequence Classifier

The model uses a pre-traind BERT GRAPH model, and fine tune it on sequence level classification task.

    $ python3 train_classifier.py --help

```
usage: train_classifier.py [-h] [--model_name MODEL_NAME] [--data_path DATA_PATH]

Tune the trainded  model on classification task.

optional arguments:
  -h, --help            show this help message and exit
  --model_name MODEL_NAME
                        Trained model name.
  --data_path DATA_PATH
                        Data file.
```
