# language-models

# परिवर्तक - Transformers
A repository for my experiments with Language models with different languages. Currently, I am focusing on Indian Languages, especially on Sanskrit, Hindi and Gujarati.

## Sanskrit
 
### RoBERTa trained on Sanskrit (SanBERTa)

Configuration

| Parameter | Value |
|---|---|
| `num_attention_heads` | 12 |
| `num_hidden_layers` | 6 |
| `hidden_size` | 768 |
| `vocab_size` | 29407 |

### Example of usage:

For Embeddings

```

tokenizer = AutoTokenizer.from_pretrained("surajp/SanBERTa")
model = RobertaModel.from_pretrained("surajp/SanBERTa")

op = tokenizer.encode("इयं भाषा न केवलं भारतस्य अपि तु विश्वस्य प्राचीनतमा भाषा इति मन्यते।", return_tensors="pt")
ps = model(op)
ps[0].shape

```
```
'''
Output:
--------
torch.Size([1, 47, 768])

```
