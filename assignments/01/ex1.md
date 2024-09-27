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
