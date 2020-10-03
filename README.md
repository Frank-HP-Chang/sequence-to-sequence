# sequence-to-sequence

Sequence to sequence tutorial implemented with `PyTorch`.

## Install

```sh
# Clone the project.
git clone https://github.com/ProFatXuanAll/sequence-to-sequence.git

# Install dependencies.
pipenv install
```

## Train Tokenizer

### Train Source Text Tokenizer

```sh
python run_train_tknzr.py character --exp_name 'src_tknzr' --dset_name 'arithmetic.src' --min_count 1 --n_vocab 50 --is_cased
```

### Train Target Text Tokenizer

```sh
python run_train_tknzr.py character --exp_name 'tgt_tknzr' --dset_name 'arithmetic.tgt' --min_count 1 --n_vocab 50 --is_cased
```

## Train Model

```sh
python run_train_model.py RNN \
  --batch_size 32 \
  --ckpt_step 1000 \
  --dec_d_emb 100 \
  --dec_d_hid 300 \
  --dec_dropout 0.1 \
  --dec_n_layer 2 \
  --dec_tknzr_exp 'tgt_tknzr' \
  --dset_name 'arithmetic' \
  --enc_d_emb 100 \
  --enc_d_hid 300 \
  --enc_dropout 0.1 \
  --enc_n_layer 2 \
  --enc_tknzr_exp 'src_tknzr' \
  --epoch 10 \
  --exp_name 'test' \
  --is_bidir \
  --log_step 500 \
  --lr 1e-4 \
  --seed 42
```
