# Preprocessed SemEval-2010 Benchmark dataset

* **update 2025/02/09** the dataset is available on huggingface: [https://huggingface.co/datasets/taln-ls2n/semeval-2010-pre](https://huggingface.co/datasets/taln-ls2n/semeval-2010-pre)

If you use this dataset, please cite:

  - **How Document Pre-processing affects Keyphrase Extraction Performance.**
    Florian Boudin, Hugo Mougard and Damien Cram.
    *COLING 2016 Workshop on Noisy User-generated Text (WNUT).* 

The dataset is split into three directories:

  * `references`: reference keyphrases for evaluation
  * `test`: test set
  * `train`: training set

For both test and training sets, documents are further split into four 
preprocessing levels:

  * `lvl-1`: each input file is processed using the Stanford CoreNLP suite 
    v3.6.0. We use the default parameters and perform tokenization, sentence 
    splitting and Part-Of-Speech (POS) tagging. Files are in XML format.

  * `lvl-2`: for each file, we manually retrieved the original PDF file from 
    the ACM Digital Library. We then extract the enriched textual content of 
    the PDF files using an Optical Character Recognition (OCR) system and 
    perform document logical structure detection using ParsCit v110505. We use
    the detected logical structure to remove author-assigned keyphrases and 
    select only relevant elements : title, headers, abstract, introduction, 
    related work, body text and conclusion. We finally apply a systematic 
    dehyphenation at line breaks and run the Stanford CoreNLP suite.

  * `lvl-3`: we further abridge the input text from level 2 preprocessed 
    documents to the following~: title, headers, abstract, introduction, 
    related work, background and conclusion.

  * `lvl-4`: we abridge the input text from level 3 preprocessed documents using
    an unsupervised sumamrization technique. We keep the title and abstract
    and select the most content bearing sentences from the remaining contents.

We provide the URL links to retreive the original PDF documents (links.txt).

Reference keyphrases provided by the SemEval-2010 organizers were converted into
json format for ease of use:
	
  * `[test|train].[author|reader|combined].[stem].json`: author, reader or
    combined (stemmed or not) reference keyphrases for test or train splits.
