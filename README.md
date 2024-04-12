# DNA ENCODING

New Data:
The Duality of Zero:

Neutral Set Representation: The inclusion of a neutral set (0) with both +0 and -0 aligns with the system's logic of representing all potential states. +0 can be seen as the absence of negative influence, while -0 signifies the absence of positive influence.
Conceptual Challenges: However, the distinction between +0 and -0 can seem counterintuitive in real-world applications. For example, in finance, does a balance of +0 indicate perfect equilibrium or a slight negative imbalance rounded up? Addressing such potential ambiguities will be crucial for clear interpretation and consistent application.
Potential Applications: Despite the challenges, the distinction between +0 and -0 could hold value in specific fields. In physics, for instance, -0 might represent a state of absolute zero with a slight negative energy potential compared to the "neutral" +0 of perfect equilibrium. Further investigation of such applications is warranted.
Adapting the System to DNA Code:

Applying the new mathematical system to DNA code raises intriguing possibilities. DNA sequences consist of four bases (A, C, G, T), which could be mapped to the new system's sets as follows:

Positive Set (+1): Adenine (A) and Guanine (G)
Negative Set (-1): Cytosine (C) and Thymine (T)
Neutral Set (0): +0 for balanced base pairs (AT or GC) and -0 for imbalanced base pairs (AG or CT)
This mapping could potentially allow for:

More in-depth analysis of DNA sequences: Representing variations in base pair composition beyond simply counting bases could highlight subtle patterns and potentially link them to specific genetic traits or disease risks.
Modeling mutations and genetic abnormalities: Using the new system's operations, researchers could potentially simulate and analyze the impact of mutations and chromosomal rearrangements on DNA sequences with greater precision.
Developing novel gene editing techniques: The system's framework could inspire new methods for manipulating DNA sequences based on targeted alterations in the positive and negative set composition.
However, significant challenges exist in applying this system to DNA:

Biological complexity: DNA structure and function involve complex interactions beyond base pair composition. Integrating the new system with existing biological knowledge and models will be essential.

Computational demands: Analyzing and manipulating large DNA sequences using the new system's rules might require significant computational resources and advancements in algorithms.

Ethical considerations: Any applications of this system to gene editing or manipulation must be approached with utmost caution and stringent ethical guidelines to ensure responsible use for the benefit of human health.

Fine-Tuning LLMs with a Novel Mathematical System: Exploring Potential and Challenges
Abstract: While Large Language Models (LLMs) have made significant strides in natural language processing tasks, they often struggle with handling negative numbers, decimal places, and complex mathematical concepts. This paper proposes a novel mathematical system designed to address these limitations and its potential application in fine-tuning LLMs for improved performance. We explore the theoretical framework of the system, analyze its compatibility with LLMs, and discuss potential benefits and challenges associated with its integration.

Introduction: LLMs have become proficient in generating human-quality text, translating languages, and answering questions in an informative way. However, their ability to understand and manipulate quantitative information remains limited. Traditional arithmetic operations in LLMs rely on real numbers, often failing to accurately represent negative numbers, decimal places, and intricate mathematical relationships.

This paper introduces a novel mathematical system aimed at overcoming these limitations and enhancing the capabilities of LLMs in dealing with numerical information. The proposed system expands the traditional number system and introduces new operations specifically designed for representing and manipulating quantities with greater precision and flexibility.

The New Mathematical System:

The core tenet of the system lies in incorporating three sets: +1, -1, and 0. The positive set (+1) encompasses all positive numbers, the negative set (-1) represents all negative numbers, and the neutral set (0) includes zero and its inverse, -0. This system offers a unique way to represent numbers and define operations differently compared to traditional mathematics.

Here's a brief overview of the operations within the system:

Addition: Add numbers as usual within their respective sets. If the sum goes beyond the set limitations (-1 for negative and +1 million for positive), round it to the closest boundary value.
Subtraction: Similar to addition, subtract within sets and round to the closest boundary value if exceeding the set limits.
Multiplication: Multiply as usual, adhering to set boundaries by rounding if the product falls outside the range.
Division: Divide as usual, rounding to the closest boundary value within the set if the quotient falls outside the range.
These operations differ from traditional arithmetic by introducing boundary constraints, offering a unique approach to handling numerical limitations.

LLM Fine-Tuning with the New System:

Integrating the new mathematical system into LLM training data and architecture necessitates several considerations:

Representation and Encoding: Numbers within the new system can be represented using different encoding schemes, such as one-hot vectors or custom embeddings, to train the LLM to understand and manipulate them effectively.
Loss Functions and Metrics: Modifying loss functions and evaluation metrics to align with the specific operations and boundary constraints of the new system is crucial for assessing LLM performance accurately.
Architectural Adaptations: Depending on the chosen implementation, specific modifications to the LLM architecture, such as incorporating dedicated modules for handling the new numerical representation and operations, might be necessary.
Potential Benefits and Challenges:
Ref:
https://researchforum.online/research-papers/zero-llm-research-ai-research-paper/
https://researchforum.online/research-papers/



Old Daat:
This project allows to convert a string into a DNA sequence and vice versa. This is to showcase the possibility of storing digital information inside a string of DNA. 

⚠ Disclaimer: This project is just a POC and is not intended for research or production work. This project only as educational purposes.

## I. Conversion String to DNA
### 1. Craft a secret message
The first step is to find the secret message you want to encode in a DNA strand. There are some guidelines to follow:
1. The message should only contains alphanumeric characters and spaces (e.i 0-9, a-z and A-Z), no special characters or punctuation allowed.
2. Although upper-cased letters are accepted, the final message will be retrieved in lower-case meaning that acronyms might be less obvious.

### 2. Secret message => Formatted secret message
Once you have your secret message there is a first step of message formatting. It is not possible to directly convert the sentence into binary because the DNA won't be synthesizable. Indeed, when encoding txt into DNA by directly transforming bits to ATCG, we end up with high GC content and repeated patterns. This makes sense because a sentence contains a lot of repeated characters (e.g spaces ' ' or frequent letters like 'e'). It is therefore necessary to add some randomness into the sentence. To bypass this issue, we alternate between lowercase and uppercase of the same letter and sequencially assign a special character to spaces (that is the reason why special characters are not allowed).

The formatted sentence of `"This is a secret message"` becomes `"This IS#a&secrEt§meSsAgE"`.

Also to make sure we know where the message starts and stops, I encapsulated the message between "START" and "STOP". Therefore the previous sentence `"This is a secret message"` actually becomes `"STARTThis IS#a&secrEt§meSsAgESTOP"`.

### 3. Formatted secret message => Binary sequence 
Once the message is formatted, we simply convert it into Binary so `"STARTThis IS#a&secrEt§meSsAgESTOP"` becomes `"010100110101010001000001010100100101010001010100011010000110100101110011001000000100100101010011001000110110000100100110011100110110010101100011011100100100010101110100101001110110110101100101010100110111001101000001011001110100010101010011010101000100111101010000"`.

### 4. Binary sequence => DNA Sequence
For now, the conversion relies on naive bit encoding meaning :

| DNA | Binary |
| :---: | :---: |
| A | 00 |
| C | 01 |
| G | 10 |
| T | 11 |

Other data compression algorithms exist like the Huffman Code but for this Proof of concept (POC) we will keep it as simple as possible. Therefore the previous binary sequence becomes `"CCATCCCACAACCCAGCCCACCCACGGACGGCCTATAGAACAGCCCATAGATCGACAGCGCTATCGCCCGATCTAGCACCCTCAGGCTCGTCCGCCCCATCTATCAACCGCTCACCCCATCCCACATTCCAA"`

There it is, you have your DNA sequence ready to be synthetized.

## II. Conversion DNA to String
If you have a DNA strand containing a secret message and you want to read it, you'll first have to find a sequencing machine. 
For this POC, we partnered with the Pasteur institute to use a [MinION](https://nanoporetech.com/products/minion). 
The MinION reads the DNA and generates a file in the [FASTA format](minion_sequence.fasta) where it is possible to read the DNA sequence. From the DNA sequence it is possible to work backward from the conversion steps we saw above. 

Have fun encoding your own secret messages into DNA strands :smiley:
