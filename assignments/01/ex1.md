## for tiny model
INFO: Epoch 011: valid_loss 5.25 | num_tokens 15.5 | batch_size 500 | valid_perplexity 191
INFO: Epoch 012: loss 3.74 | lr 0.0003 | num_tokens 14.55 | batch_size 1 | grad_norm 54.67 | clip 1
INFO: Epoch 012: valid_loss 5.24 | num_tokens 15.5 | batch_size 500 | valid_perplexity 188
INFO: Epoch 013: loss 3.642 | lr 0.0003 | num_tokens 14.55 | batch_size 1 | grad_norm 56.44 | clip 1
INFO: Epoch 013: valid_loss 5.2 | num_tokens 15.5 | batch_size 500 | valid_perplexity 181
INFO: Epoch 014: loss 3.55 | lr 0.0003 | num_tokens 14.55 | batch_size 1 | grad_norm 57.28 | clip 1
INFO: Epoch 014: valid_loss 5.2 | num_tokens 15.5 | batch_size 500 | valid_perplexity 182
INFO: Epoch 015: loss 3.441 | lr 0.0003 | num_tokens 14.55 | batch_size 1 | grad_norm 58.99 | clip 1
INFO: Epoch 015: valid_loss 5.24 | num_tokens 15.5 | batch_size 500 | valid_perplexity 189
INFO: Epoch 016: loss 3.366 | lr 0.0003 | num_tokens 14.55 | batch_size 1 | grad_norm 60.54 | clip 1
INFO: Epoch 016: valid_loss 5.21 | num_tokens 15.5 | batch_size 500 | valid_perplexity 184
INFO: No validation set improvements observed for 3 epochs. Early stop!

f cat assignments/01/baseline/infopankki_translations.p.txt | sacrebleu data/en-sv/infopankki/preprocessed/test.en
{
 "name": "BLEU",
 "score": 3.4,
 "signature": "nrefs:1|case:mixed|eff:no|tok:13a|smooth:exp|version:2.4.3",
 "verbose_score": "14.5/4.4/2.0/1.0 (BP = 1.000 ratio = 1.147 hyp_len = 8338 ref_len = 7270)",
 "nrefs": "1",
 "case": "mixed",
 "eff": "no",
 "tok": "13a",
 "smooth": "exp",
 "version": "2.4.3"
}
 cat assignments/01/baseline/bible_translations_tiny.p.txt | sacrebleu data/en-sv/bible_uedin/raw/test.en
{
 "name": "BLEU",
 "score": 0.0,
 "signature": "nrefs:1|case:mixed|eff:no|tok:13a|smooth:exp|version:2.4.3",
 "verbose_score": "7.7/0.8/0.0/0.0 (BP = 0.134 ratio = 0.333 hyp_len = 4860 ref_len = 14614)",
 "nrefs": "1",
 "case": "mixed",
 "eff": "no",
 "tok": "13a",
 "smooth": "exp",
 "version": "2.4.3"
}

## Norml model
INFO: Epoch 059: loss 2.155 | lr 0.0003 | num_tokens 14.86 | batch_size 1 | grad_norm 64.37 | clip 0.9875 
INFO: Epoch 059: valid_loss 2.67 | num_tokens 15.5 | batch_size 500 | valid_perplexity 14.4
INFO: Epoch 060: loss 2.144 | lr 0.0003 | num_tokens 14.86 | batch_size 1 | grad_norm 64.35 | clip 0.988                                                                                                                         
INFO: Epoch 060: valid_loss 2.68 | num_tokens 15.5 | batch_size 500 | valid_perplexity 14.6
INFO: Epoch 061: loss 2.136 | lr 0.0003 | num_tokens 14.86 | batch_size 1 | grad_norm 64.4 | clip 0.987                                                                                                                          
INFO: Epoch 061: valid_loss 2.68 | num_tokens 15.5 | batch_size 500 | valid_perplexity 14.5
INFO: Epoch 062: loss 2.135 | lr 0.0003 | num_tokens 14.86 | batch_size 1 | grad_norm 64.5 | clip 0.9871                                                                                                                         
INFO: Epoch 062: valid_loss 2.67 | num_tokens 15.5 | batch_size 500 | valid_perplexity 14.4
INFO: No validation set improvements observed for 3 epochs. Early stop!
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

| Domain       | BLEU Score | 1-gram Precision | 2-gram Precision | 3-gram Precision | 4-gram Precision |
|--------------|------------|------------------|------------------|------------------|------------------|
| In-domain    | 13.5       | 32.9%            | 16.3%            | 9.8%             | 6.3%             |
| Out-of-domain| 0.6        | 17.5%            | 2.1%             | 0.2%             | 0.0%             |


The BLEU score on the in-domain test set will be relatively high considering the model
was trained on very little data. Take a look at the raw data sets. Which characteristics of
the in-domain data could be responsible for a high BLEU score?
In both the training and the validation set, the sentences are relatively short, which is beneficial for the BLEU, additionlly both contain a considerable amount of if sentences, whos structure the model probably learned to predict. 


• Compare the model’s performance on the in-domain test set vs. the out-of-domain test
set. Why is the out-of-domain test set so much harder to translate? Support your answer
with examples from the test set.

The bible text contains quite a lot unseen token, especieally the biblical names, which I guess are hard to predict for the model. Further more the english bible translation has very specific idiosyncrasies, both in the lexical and in the syntactical area. I can not judge to which extend they are present in the swedish version. 

• Choose a language other than English that you know well. Find 3 words that may be
translated differently into English depending on the context and provide examples. How
do your examples fit into the discussion of in-domain vs. out-of-domain? Can you think
of a possible way to ensure a specific translation for a word is used by an NMT model

Neigung: can mean several things without further context: tendency, inclination, slope, disposition.
laufen: is a very generic verb in german; can have several translations: walk, run, (does are probably similarly interchangable in english as in german) but there are also more domain specific transaltions like: being in progress (Die Aufnahme läuft; the recoring is in progress), work (Der Moror läuft mit voller Kapazität; The motor works at full capacity),  go (Alles läuft nach Plan: Everything goes according to plan) and probably more. 
Hausbank: can either mean a bench beloning to a house, or the bank (money institution) of ones trust,  which could be translate for example as local bank, or main bank. 
A model trained on data of one domain, will probably learn a to narrow representation of the above mentiont wors, and therefore translate them wrongly in an out-of domain setting. For example a model trained on data related to motor sports might learn to translate laufen as work, which does not make sense in most other out-of-domain transaltion tasks. 

To ensure specific translations one could try several strategies: 
Train the model on enough and a variaty of data form differnet domains, such that it learns context dependend translations.
Train a model for the specific use case, meaning if legal documents should be translate with the model, train it on text from this domain.
Manipulate the models logit value, in such a way that domain related words get higher probabilities to be generate or the not domain related get low probs. 
Provide the model with a dictoinaire predefining certain translations. 



