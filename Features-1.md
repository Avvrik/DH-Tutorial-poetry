## Features

#### Word frequency
        from collections import Counter
        freq = Counter(tokens)
        frequency = freq.most_common()
        
        #Create a table word - frequency:
        
        with open('Lay_frequency.tsv', 'w') as f:
        f.write('Word\tFrequency\n')
        for word,fr in frequency:
        f.write(word + '\t' +str(fr) + '\n')
#### Bigrams
        n = 2
        bigrams = []
        
        for i in range(len(tokens1)-n+1):
        bigrams.append(tokens1[i:i+n])
        
        ngrams = ['_'.join(tokens1[i:i+n]) for i in range(len(tokens1)-n+1)]
        
        bigram_freq = Counter(ngrams)
        freq_bigram = bigram_freq.most_common(15)
#### Parts of speech (POS tagging)



