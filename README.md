## Hebrew Coreference Data

Public dataset and resources for Hebrew coreference resolution. This repository provides gold-standard CoNLL-U data and accompanying inputs used by neural and LLM-based systems.

### Dataset Overview

- **Total Documents**: 351 (301 train, 26 dev, 24 test)
- **Total Sentences**: 6,151
- **Total Tokens**: 159,975

### Mention Statistics

- **Total Mentions (no singleton)**: 19,483
- **Total Mentions (with singleton)**: 45,689
- **Singleton Mentions**: 26,206 (57.4%)

#### Distribution across splits:
- **Train**: 16,907 mentions
- **Dev**: 1,181 mentions  
- **Test**: 1,395 mentions

### Agreement Scores

- **Coreference Agreement**: CoNLL Score: 0.811, Mention Score: 0.850

### Data layout

```
data/
├── conllu/                    # Gold CoNLL-U splits
│   ├── no_singleton/          # train/dev/test without singletons
│   └── with_singleton/        # train/dev/test with singletons
├── neural_input/              # Inputs for neural models
│   ├── wl/                    # WL format (train/dev/test + head variants)
│   └── lingmess/              # LingMess format (train/dev/test; SOTA tokenized)
└── llm_input/                 # Inputs and outputs used with LLM pipelines
    ├── mentions_by_llm_from_raw/
    ├── mentions_by_model_danit_parse/
    ├── mentions_by_model_gold_parse/
    ├── raw_documents/
    ├── tokenized_documents/
    └── tokenized_documents_danit_tokenization/
```

### Repository Structure

```
hebrew_coreference_data/
├── data/                      # Main data directory
│   ├── conllu/               # Gold standard CoNLL-U annotations
│   ├── neural_input/         # Neural model inputs
│   └── llm_input/            # LLM pipeline data
├── guidelines/                # Annotation guidelines
├── agreement_calculation/     # Agreement calculation tools
└── annotation/                # Original annotation data
    ├── final_coref/          # Final consolidated annotations
    ├── coref_pairwise/       # Pairwise agreement annotations
    └── mention_annotation/   # Individual annotator data
```

Notes
- The content of `data/conllu/` is sourced from the project's gold data ("conllu_gold") and is organized into `with_singleton` and `no_singleton` variants per split.
- `neural_input/wl` and `neural_input/lingmess` mirror the common Hebrew splits used in prior work.
- `llm_input` contains raw and tokenized documents as well as model- and LLM-derived mentions.

### Guidelines
The English guidelines for the annotation scheme are available at `guidelines/Hebrew_Coreference_Guidelines_English.pdf`.

### Citation
If you use this repository, please cite it and acknowledge the Hebrew coreference annotation effort.
@inproceedings{greenfeld-tsarfaty-2026-beyond,
    title = "Beyond Word Boundaries: A {H}ebrew Coreference Benchmark and an Evaluation Protocol for Morphologically Complex Text",
    author = "Greenfeld, Refael Shaked  and
      Tsarfaty, Reut",
    editor = "Liakata, Maria  and
      Moreira, Viviane P.  and
      Zhang, Jiajun  and
      Jurgens, David",
    booktitle = "Proceedings of the 64th Annual Meeting of the {A}ssociation for {C}omputational {L}inguistics (Volume 1: Long Papers)",
    month = jul,
    year = "2026",
    address = "San Diego, California, United States",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2026.acl-long.488/",
    doi = "10.18653/v1/2026.acl-long.488",
    pages = "10669--10683",
    ISBN = "979-8-89176-390-6",
    abstract = "Coreference Resolution (CR) is a fundamental NLP task critical for long-form tasks as information extraction, summarization, and many business applications. However, CR methods originally designed for English struggle with Morphologically Rich Languages (MRLs), where mention boundaries do not necessarily align with word boundaries, and a single token may consist of multiple anaphors. CR modeling and evaluation protocols standardly assume that, as in English, words and mentions mostly align. However, this assumption breaks down in MRLs, particularly in the context of LLMs' raw-text processing and end-to-end tasks. To assess and address this challenge, we introduce KibutzR, the first comprehensive CR dataset for Modern Hebrew, an MRL rich with complex words and pronominal clitics. We deliver an annotated dataset that identifies mentions at word, sub-word and multi-word levels, and propose an evaluation protocol that directly addresses word/morpheme boundary discrepancies. Our experiments show that contemporary LLMs perform significantly worse on Hebrew than on English, and that performance degrades on raw unsegmented text. Crucially, we show an inverse performance-trend in Hebrew relative to English, where smaller encoders perform far better than contemporary decoder models, leaving ample space for investigation and improvement. We deliver a new benchmark for Hebrew coreference resolution and a segmentation-aware evaluation protocol to inform future work on other MRLs."
}


### Contact
Please open an issue for questions or clarifications.
