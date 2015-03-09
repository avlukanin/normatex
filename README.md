# Normatex - Russian text normalization

This is a set of Finite-State Transducers (FSTs) for normalization of Russian texts for speech synthesis, machine translation and other natural language processing tasks.

The FSTs are developed in [Unitex](http://www-igm.univ-mlv.fr/~unitex/), a corpus processor.

To normalize a Russian text:

1. Copy your text (e.g. `example.txt`) to `Corpus` folder, open it in Unitex and preprocess it with following resources:
  * apply `Graphs/Preprocessing/Sentence/SentenceUniver.grf` in MERGE mode
  * apply `Graphs/Preprocessing/Replace/replace.grf` in REPLACE mode
2. Apply lexical resources:
  * [the full version of the Russian computational morphological dictionary developed at CIS, Munich](http://www-igm.univ-mlv.fr/~unitex/index.php?page=5&html=bibliography.html#russian): `CISLEXru.bin`, `CISLEXru_disamb-.bin` and `CISLEXru_EN.bin`
  * `Dela/univer.bin`
  * `Dela/univer_disamb-.bin`
3. Create a cascade (`Text\Apply CasSys Cascade...` menu, `New`) to sequentially apply the following FSTs to your text in REPLACE mode (menu `Text/Locate pattern`):
  * `Graphs/numbers.fst2`
  * `Graphs/abbr/abbr_w.fst2`
  * `Graphs/abbr/acronyms_w.fst2`
  * `Graphs/Postprocessing/replace.fst2`
4. Launch the cascade of FSTs.
5. The normalized text is in `Corpus/example_csc/example_4_0.snt`.
