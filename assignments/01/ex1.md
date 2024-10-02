## Exercise 1 
### Bleu Score Table

| Domain       | BLEU Score | 1-gram Precision | 2-gram Precision | 3-gram Precision | 4-gram Precision |
|--------------|------------|------------------|------------------|------------------|------------------|
| In-domain    | 13.5       | 32.9%            | 16.3%            | 9.8%             | 6.3%             |
| Out-of-domain| 0.6        | 17.5%            | 2.1%             | 0.2%             | 0.0%             |

## Questions 
### Bleu Score in-domain
The BLEU score on the in-domain test set will be relatively high considering the model
was trained on very little data. Take a look at the raw data sets. Which characteristics of
the in-domain data could be responsible for a high BLEU score?

The sentences are relatively short, which is beneficial for achieving higher BLEU scores. 
Additionally, the in-domain dataset is fairly consistent in its sentence structures, primarily comprising main clauses 
with "you" or nouns as subjects. When sentence structures are more complex, 
they are mostly conditional sentences ("if" clauses). Furthermore, the beginning of one sentence is often repeated in 
the following sentence, leading to similar sentence patterns throughout the data. All these factors, 
combined with a more or less consistent vocabulary in both the test and training data, m
ake it easier for the model to predict in-domain translations without generalizing well to other sources of text.

### Bleu Score in-domain vs. out-of-domain
Compare the model’s performance on the in-domain test set vs. the out-of-domain test
set. Why is the out-of-domain test set so much harder to translate? Support your answer
with examples from the test set.

The Bible text contains a large number of unseen tokens, especially biblical names, 
which are likely difficult for the model to predict. Furthermore, the English Bible translation has 
very specific idiosyncrasies, both lexically and syntactically. I am unsure to what extent these are present in the Swedish version.


### Context dependent translations
Choose a language other than English that you know well. Find 3 words that may be
translated differently into English depending on the context and provide examples. How
do your examples fit into the discussion of in-domain vs. out-of-domain? Can you think
of a possible way to ensure a specific translation for a word is used by an NMT model


**Neigung**: Depending on the context, this word can mean "tendency," "inclination," "slope," or "disposition."

**Laufen**: A very generic verb in German, which can be translated as "walk" or "run." It also has domain-specific translations, such as "being in progress" (e.g., "Die Aufnahme läuft" = "The recording is in progress"), "work" (e.g., "Der Motor läuft mit voller Kapazität" = "The motor works at full capacity"), and "go" (e.g., "Alles läuft nach Plan" = "Everything goes according to plan").

**Hausbank**: This can either mean a bench belonging to a house or a trusted financial institution, which could be translated as "local bank" or "main bank."

A model trained on data from a single domain will likely learn too narrow a representation of these words, leading to incorrect translations in an out-of-domain setting. For instance, a model trained on data related to motorsports might learn to translate "laufen" as "work," which would not make sense in most other contexts.

To ensure specific translations, several strategies could be employed:

Train the model on a large and diverse dataset from multiple domains so that it learns context-dependent translations.
Train the model for a specific use case, such as translating legal documents, by using domain-specific text.
Manipulate the model’s logit values so that domain-relevant words have higher probabilities of being generated, while non-relevant terms have lower probabilities.
Provide the model with a dictionary that predefines certain translations.
When working with larger models like Chatgpt further strategies could promting the model to translate specific source words to specific target words. 

## Training output 
INFO: Epoch 059: loss 2.155 | lr 0.0003 | num_tokens 14.86 | batch_size 1 | grad_norm 64.37 | clip 0.9875 

INFO: Epoch 059: valid_loss 2.67 | num_tokens 15.5 | batch_size 500 | valid_perplexity 14.4

INFO: Epoch 060: loss 2.144 | lr 0.0003 | num_tokens 14.86 | batch_size 1 | grad_norm 64.35 | clip 0.988      

INFO: Epoch 060: valid_loss 2.68 | num_tokens 15.5 | batch_size 500 | valid_perplexity 14.6

INFO: Epoch 061: loss 2.136 | lr 0.0003 | num_tokens 14.86 | batch_size 1 | grad_norm 64.4 | clip 0.987         

INFO: Epoch 061: valid_loss 2.68 | num_tokens 15.5 | batch_size 500 | valid_perplexity 14.5

INFO: Epoch 062: loss 2.135 | lr 0.0003 | num_tokens 14.86 | batch_size 1 | grad_norm 64.5 | clip 0.9871         

INFO: Epoch 062: valid_loss 2.67 | num_tokens 15.5 | batch_size 500 | valid_perplexity 14.4

INFO: No validation set improvements observed for 3 epochs. Early stop!

## Sacrebleu  raw  Output 
assignments/01/baseline/infopankki_translations.p.txt \
| sacrebleu data/en-sv/infopankki/raw/test.en
{
 "name": "BLEU",
 "score": 13.5,
 "signature": "nrefs:1|case:mixed|eff:no|tok:13a|smooth:exp|version:2.4.3",
 "verbose_score": "32.9/16.3/9.8/6.3 (BP = 1.000 ratio = 1.548 hyp_len = 10766 ref_len = 6957)",
 "nrefs": "1",
 "case": "mixed",
 "eff": "no",
 "tok": "13a",
 "smooth": "exp",
 "version": "2.4.3"
}
{
 "name": "BLEU",
 "score": 0.6,
 "signature": "nrefs:1|case:mixed|eff:no|tok:13a|smooth:exp|version:2.4.3",
 "verbose_score": "17.5/2.1/0.2/0.0 (BP = 1.000 ratio = 1.340 hyp_len = 19578 ref_len = 14614)",
 "nrefs": "1",
 "case": "mixed",
 "eff": "no",
 "tok": "13a",
 "smooth": "exp",
 "version": "2.4.3"
}
