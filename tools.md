---
layout: default
title: Tools & Code
description: Links to helpful tools and our code for the extraction and analysis process.
---

Links to tools and our code for the extraction and analysis process. 

## **Extraction Process**
* * *

### **Utterance Alignments**
* * *

### CMU Wilderness 
*CMU Wilderness* releases pre-computed utterance alignments for the chapter-level audio and text on [bible.is](https://bible.is). The original audio and text cannot be directly re-distributed, so Wilderness provides scripts to download the audio and text from source and apply the indices for utterance segmentation they have estimated. 
However, in many cases the links on bible.is have changed since the original Wilderness paper; we are working to resolve and update the scripts where possible. 

[[GitHub repository]](https://github.com/festvox/datasets-CMU_Wilderness#create-alignments-for-a-language)
[[paper]](https://ieeexplore.ieee.org/document/8683536)


### **Grapheme-to-Phoneme (G2P) Resources**
* * *

### Epitran
**Epitran** is a precision G2P model which uses a combination of hand-written rules and postprocessing for inadequate orthographies. Epitran supports both IPA and X-SAMPA. 
For the languages in our corpus for which Epitran has [high-quality support](https://github.com/dmort27/epitran#language-support) for the orthography present on bible.is, we use Epitran as our highest-quality G2P resource. 

We encourage contributions to Epitran to e.g. extend its language or orthography coverage. 
If you are comfortable with GitHub, you may submit a pull-request, or if not, please contact David Mortensen directly at <mailto:dmortens@cs.cmu.edu> with mappings/rules and he will incorporate them. 

[[GitHup repository]](https://github.com/dmort27/epitran) 
[[paper]](https://www.aclweb.org/anthology/L18-1429/)


### Wiktionary Annotations
Wiktionary contains word-level pronunciation annotations in IPA at both the phonemic and phonetic level, with more annotations available at the phonemic level.
We used the **WikiPron** package to retrieve pronunciations for languages with coverage on Wiktionary, and use the phonemic annotations for our phoneme alignments which we map to X-SAMPA. 
We additionally use WikiPron-mined data from the [SIGMORPHON 2020 task](https://sigmorphon.github.io/sharedtasks/2020/task1/) to tune our G2P models.

[[GitHub repository]](https://github.com/kylebgorman/wikipron) 
[[paper]](https://www.aclweb.org/anthology/2020.lrec-1.521/) 

Previous work has used additional tools for Wiktionary such as [wikt2pron](https://github.com/abuccts/wikt2pron), which supports both IPA and X-SAMPA. 


### Phonetisaurus
**Phonetisaurus** contains implementations of multiple G2P models. We use their WFST implementation to train G2P models using Wiktionary pronunciation annotations to supplement word tokens in our vocabulary for which there are no Wiktionary pronunciations. 

[[GitHub repository]](https://github.com/AdolfVonKleist/Phonetisaurus) 
[[paper]](https://www.aclweb.org/anthology/W16-3702.pdf) 


### Unitran
**Unitran** is a mapping that takes individual graphemes and maps them to 1-several phonemes in X-SAMPA, regardless of language and context.
We discuss clear caveats of this approach in detail in our paper. Nonetheless, this provides initial G2P to generate first-pass alignments, to hopefully facilitate analysis.

We used the Unitran version in [Festvox](https://github.com/festvox/festvox/blob/master/src/grapheme/make_cg_grapheme) following the [Wilderness procedure](https://github.com/festvox/datasets-CMU_Wilderness); we plan to push python scripts of this Unitran version to our [GitHub repository](https://github.com/VoxClamantisProject/extraction-process) for greater accessibility. 

Note that Alan W Black's Unitran has diverged slightly from the version of Unitran in [NLTK/ScriptTranscriber](https://github.com/nltk/nltk_contrib/tree/master/nltk_contrib/scripttranscriber); he added or edited many common graphemes in the Wilderness dataset without Unitran mappings or for which the expansions were incorrect. 

[[paper]](https://www.aclweb.org/anthology/P07-1015/)


### **Phoneme Alignments**
* * *

### Kaldi
We train multilingual ASR models for phoneme alignment in [**kaldi**](https://github.com/kaldi-asr/kaldi), given lexicons created with G2P using methods above.
Training data and model specifics are described in the ASRU 2019 paper below. 
We link to an older version of the Wilderness recipe in ESPnet below; we will push our kaldi recipe soon. 

[[GitHub repository]](https://github.com/espnet/espnet/tree/master/egs/cmu_wilderness)
[[paper]](./assets/pdfs/Zero_Shot_ronunciation_Lexicons_For_Cross_Language_Acoustic_Model_Transfer-ASRU_2019.pdf)


### Wilderness Festvox synthesis
The CMU Wilderness paper trains language-specific acoustic models for phoneme alignments via speech synthesis using [**Festvox**](https://github.com/festvox/festvox), which we recreate here following their recipes.

[[GitHub repository]](https://github.com/festvox/datasets-CMU_Wilderness#creating-phone-level-alignments-for-all-utterances) 
[[paper]](https://ieeexplore.ieee.org/document/8683536)


### **Phonetic Measures**
* * *

### Our Code
Our Praat and R scripts to extract vowels and sibilants, given phoneme alignments, are available on GitHub.

[[GitHub repository]](https://github.com/VoxClamantisProject/extraction-process)


## **Analysis**
* * *

### Our Code
Our R scripts to perform analysis on vowel and sibilant phonetic measures are available on GitHub. 

[[GitHub repository]](https://github.com/VoxClamantisProject/analysis)


* * *

[[back]](./)