<H3>NAME: Junaid Sardar S</H3>
<H3>REGISTER NO. 212224100028</H3>
<H3>EX. NO.6</H3>
<H3>DATE: 9/11/25</H3>
<H1 ALIGN =CENTER>Implementation of Semantic ANalysis</H1>

## Aim: 
to perform Parts of speech identification and Synonym using Natural Language Processing (NLP) techniques.  

## Algorithm:
Step 1: Import the nltk library.<br>
Step 2: Download the 'punkt', 'wordnet', and 'averaged_perceptron_tagger' resources.<br>
Step 3:Accept user input for the text.<br>
Step 4:Tokenize the input text into words using the word_tokenize function.<br>
Step 5:Iterate through each word in the tokenized text.<br>
•	Perform part-of-speech tagging on the tokenized words using nltk.pos_tag.<br>
•	Print each word along with its corresponding part-of-speech tag.<br>
•	For each verb , iterate through its synsets (sets of synonyms) using wordnet.synsets(word).<br>
•	Extract synonyms and antonyms using lemma.name() and lemma.antonyms()[0].name() respectively.<br>
•	Print the unique sets of synonyms and antonyms.

## Program:
```
import nltk
from nltk.tokenize import word_tokenize
from nltk.corpus import wordnet
import pandas as pd

# Download required NLTK resources
nltk.download('punkt')
nltk.download('punkt_tab')
nltk.download('wordnet')
nltk.download('omw-1.4')
nltk.download('averaged_perceptron_tagger_eng')

# Input sentence
sentence = "I am very interested in Applied AI"

# Tokenize sentence
words = word_tokenize(sentence)

# Create lists for DataFrame
word_list = []
synonym_list = []
antonym_list = []

for word in words:
    synonyms = set()
    antonyms = set()
    for syn in wordnet.synsets(word):
        for lemma in syn.lemmas():
            synonyms.add(lemma.name())
            if lemma.antonyms():
                antonyms.add(lemma.antonyms()[0].name())
    
    if synonyms or antonyms:  # Include only meaningful words
        word_list.append(word)
        synonym_list.append(', '.join(list(synonyms)[:5]))  # Limit to 5 for readability
        antonym_list.append(', '.join(list(antonyms)[:5]))

# Display results as a table
df = pd.DataFrame({
    'Word': word_list,
    'Synonyms (Top 5)': synonym_list,
    'Antonyms (Top 5)': antonym_list
})

print("Sentence:", sentence)
print("\nWord-wise Synonyms and Antonyms:\n")
display(df)
```
## Output
![alt text](image.png)

## Result:
Thus ,the program to perform the Parts of Speech identification and Synonymis executed sucessfully.
