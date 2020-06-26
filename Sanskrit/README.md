# Models on Sanskrit

- [SanBERTa](#SanBERTa:-RoBERTa-trained-on-Sanskrit)

## SanBERTa: RoBERTa trained on Sanskrit

Configuration

| Parameter | Value |
|---|---|
| `num_attention_heads` | 12 |
| `num_hidden_layers` | 6 |
| `hidden_size` | 768 |
| `vocab_size` | 29407 |

## Example of usage

For Embeddings

```python

tokenizer = AutoTokenizer.from_pretrained("surajp/SanBERTa")
model = RobertaModel.from_pretrained("surajp/SanBERTa")

op = tokenizer.encode("इयं भाषा न केवलं भारतस्य अपि तु विश्वस्य प्राचीनतमा भाषा इति मन्यते।", return_tensors="pt")
ps = model(op)
ps[0].shape

```

```python
'''
Output:
--------
torch.Size([1, 47, 768])

```
