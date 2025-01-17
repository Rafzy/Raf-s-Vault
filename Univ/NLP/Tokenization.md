#nlp 

**Tokenization** is the process of breaking down a piece of text into smaller units called tokens. These tokens can be words, phrases, symbols, or other meaningful elements. Tokenization is a fundamental step in text preprocessing for many NLP tasks, as it simplifies the analysis by converting the text into manageable pieces.

##### Types of Tokenization

1. **Word Tokenization:**
    - Splitting a sentence into individual words.
    - Example: "Natural Language Processing" becomes \["Natural", "Language", "Processing"].

1. **Sentence Tokenization:**
    - Splitting a paragraph into individual sentences.
    - Example: "NLP is fun. It involves text analysis." becomes \["NLP is fun.", "It involves text analysis."].

1. **Subword Tokenization:**
    - Splitting words into smaller subword units, often used in languages with complex morphology or in byte pair encoding (BPE).
    - Example: "unhappiness" might become \["un", "happiness"] or \["un", "hap", "pi", "ness"].