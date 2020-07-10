# RoBERTa-hindi-guj-san

HuggingFace Model Hub link: [RoBERTa-hindi-guj-san](https://huggingface.co/surajp/RoBERTa-hindi-guj-san)

## Model description

Multillingual RoBERTa like model trained on Wikipedia articles of Hindi, Sanskrit, Gujarati languages. The tokenizer was trained on combined text. 
However, Hindi text was used to pre-train the model and then it was fine-tuned on Sanskrit and Gujarati Text combined hoping that pre-training with Hindi 
will help the model learn similar languages.

## Intended uses & limitations

#### How to use

```python
# Example usage
from transformers import AutoTokenizer, AutoModelWithLMHead, pipeline

tokenizer = AutoTokenizer.from_pretrained("surajp/RoBERTa-hindi-guj-san")
model = AutoModelWithLMHead.from_pretrained("surajp/RoBERTa-hindi-guj-san")

fill_mask = pipeline(
    "fill-mask",
    model=model,
    tokenizer=tokenizer
)

# Sanskrit: इयं भाषा न केवलं भारतस्य अपि तु विश्वस्य प्राचीनतमा भाषा इति मन्यते।
# Hindi:  अगर आप अब अभ्यास नहीं करते हो तो आप अपने परीक्षा में मूर्खतापूर्ण गलतियाँ करोगे।
# Gujarati: ગુજરાતમાં ૧૯મી માર્ચ સુધી કોઈ સકારાત્મક (પોઝીટીવ) રીપોર્ટ આવ્યો <mask> હતો.
fill_mask("ગુજરાતમાં ૧૯મી માર્ચ સુધી કોઈ સકારાત્મક (પોઝીટીવ) રીપોર્ટ આવ્યો <mask> હતો.")

'''
Output:
--------
[
{'score': 0.07849744707345963, 'sequence': '<s> ગુજરાતમાં ૧૯મી માર્ચ સુધી કોઈ સકારાત્મક (પોઝીટીવ) રીપોર્ટ આવ્યો જ હતો.</s>', 'token': 390},
{'score': 0.06273336708545685, 'sequence': '<s> ગુજરાતમાં ૧૯મી માર્ચ સુધી કોઈ સકારાત્મક (પોઝીટીવ) રીપોર્ટ આવ્યો ન હતો.</s>', 'token': 478},
{'score': 0.05160355195403099, 'sequence': '<s> ગુજરાતમાં ૧૯મી માર્ચ સુધી કોઈ સકારાત્મક (પોઝીટીવ) રીપોર્ટ આવ્યો થઇ હતો.</s>', 'token': 2075},
{'score': 0.04751499369740486, 'sequence': '<s> ગુજરાતમાં ૧૯મી માર્ચ સુધી કોઈ સકારાત્મક (પોઝીટીવ) રીપોર્ટ આવ્યો એક હતો.</s>', 'token': 600},
{'score': 0.03788900747895241, 'sequence': '<s> ગુજરાતમાં ૧૯મી માર્ચ સુધી કોઈ સકારાત્મક (પોઝીટીવ) રીપોર્ટ આવ્યો પણ હતો.</s>', 'token': 840}
]

```

## Eval results

perplexity = 2.920005983224673
