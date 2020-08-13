<h1> NLP_V2 </h2>

<pre>

This repository contains all important stuff I have learned , implemented  and I find useful for nlp. I want to make this repo. as a go to place to find 
all the nlp stuff when I need hence this repo will always be a work in progress as learning never stops.

The structure of this repo:

There are basically five main folders.

1. <b>Visualization</b> : This folder is ment to contain all the stuff which is required to visualize text data. As text data is different from     tabular data we cannot use the same visualization methods to get insights of out data. Aside from visualization this also includes extracting meta-features like word_len,number of tokens ect. Which may or may not be useful but gives us insights about the data.  
t 

<!-- images -->


2. <b>Preprocessing</b> : From the name one might guess this folder contains different preprocessing steps. This also includes preprocessing steps needed to increase the word coverage when using pre-trained enbeddings. Things like replacing digits greater than 9 with #'s, handling contractiong etc. 
I am also working on a more general notebook which contains all the preprocessing steps regardless the dataset being used.




<code>


    for key in tqdm(vocab.keys()):

        word = key

        embedding_vector = embeddings_index.get(word)
        #checking if word is present.
        if embedding_vector is not None:
#             embedding_matrix[word_dict[key]] = embedding_vector
            known_words += 1
            continue

        #check if lower case of the word is present.
        word = key.lower()
        embedding_vector = embeddings_index.get(word)
        if embedding_vector is not None:
#             embedding_matrix[word_dict[key]] = embedding_vector
            known_words += 1
            continue

        #cheking if the upper case of the word is present.
        word = key.upper()
        embedding_vector = embeddings_index.get(word)
        if embedding_vector is not None:
#             embedding_matrix[word_dict[key]] = embedding_vector
            known_words += 1
            continue

        #checking if capital word is present.
        word = key.capitalize()
        embedding_vector = embeddings_index.get(word)
        if embedding_vector is not None:
#             embedding_matrix[word_dict[key]] = embedding_vector
            known_words += 1
            continue

        '''
        Three steppers are  used 

        ps -> PorterStemmer 
        ls -> lancaster 
        sb->snowball stemmer 

        need to check on this as well

        
        '''    

        word = ps.stem(key)
        embedding_vector = embeddings_index.get(word)
        if embedding_vector is not None:
#             embedding_matrix[word_dict[key]] = embedding_vector
            stem.append(word)
            known_words += 1
            continue


        word = lc.stem(key)
        embedding_vector = embeddings_index.get(word)
        if embedding_vector is not None:
#             embedding_matrix[word_dict[key]] = embedding_vector
            stem.append(word)
            known_words += 1
            continue


        word = sb.stem(key)
        embedding_vector = embeddings_index.get(word)
        if embedding_vector is not None:
#             embedding_matrix[word_dict[key]] = embedding_vector
            stem.append(word)
            known_words += 1
            
            continue

        '''
        Using Lemmatization
        
        '''    

        word = wnl.lemmatize(key,'v')
        embedding_vector = embeddings_index.get(word)
        if embedding_vector is not None:
#             embedding_matrix[word_dict[key]] = embedding_vector
            lemma.append(key)
            known_words += 1
            continue

        ''''
        Checking for spellling mistakes 
        
        '''    
        if len(key) > 1:
            word = correction(key)
            embedding_vector = embeddings_index.get(word)
            if embedding_vector is not None:
#                 embedding_matrix[word_dict[key]] = embedding_vector
                correct.append(word)
                known_words += 1
                continue

                
</code>
3. <b>Embedding</b> : This folder includes the meta-embeddings. In this we try to combine more than one embeddings eg concatenating word2vec and glove embedings.The different methods covered here are meta-embedding by 
1. Taking the average 
2. Concatenation
3. DME
4. PME

This folder also includes research papers on different Embedding Methods.

4.<b>Problems</b>: This folder is made of 2 seperate folder BinaryProbelms, Multi-Label Problems 

BinaryProbelms: Includes notebooks for handling sementic analysis problems. It also includes differnt model architectures used to solve the probelm


Multi-Label : In this notebook I have solved two problems 
1. stackoverflow tag prediction : Where the input is the question and title and the model needs to predict tags.
2. Toxicity Classification problem : Where each comment can belong in any one or more of the 6 classes.

In this section I have made use of ml model like logistic regression with OneVsRestClassifier as thses models can hangle multi-label data. The reason for doing this is that my final year project was based on a similar mult-label problem where in I had to develope a model which could be deployed on a server as a result both the compute power and memory needed for re-training the model is limited hence the use of ml models instead of resource intensive LSTMs,also the size of the dataset was small as this was a piolit project the company who had give us the project.

5. <b>Attention</b>: Attention has become an very important part of NLP.The reason why most of the advancements in the field (ImageNet moment). The purpose of this folder is to house all the different attentions architectures. The attention mechanisms included in the folder are 

1. Simple Attention : 
2. Self Attention 
3. Attention with context (I like this one.)
4. Additive Attention 
5. Scaled Dot Product Attentoon
6. MultiHeadAttention.
There are reasearch papers which help in understanding why this mechanisms work.


A new notebook comparing the different attention's is in porcess.


</pre>
