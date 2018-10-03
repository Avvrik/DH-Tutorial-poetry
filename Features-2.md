## Features
#### Tf-idf
* (Term frequency – inverse document frequency) - мера, используемая для оценки важности слова в тексте ("документе"), являющегося частью коллекции документов или корпуса. Вес слова пропорционален частоте употребления этого слова в документе и обратно пропорционален частоте употребления слова во всех документах коллекции.

      from sklearn.feature_extraction.text import TfidfVectorizer, CountVectorizer
      count = CountVectorizer(min_df=4, max_df=0.9, stop_words = 'english')
      tf = count.fit_transform(string).toarray()
      tf.shape
      
      vect = TfidfVectorizer(min_df=5, max_df=0.8, stop_words = 'english')
      tfidf = vect.fit_transform(poems).toarray()
      tfidf.shape
      
      vect.stop_words_
      vect.vocabulary_
      
      words = vect.get_feature_names()
      
      row = tfidf[0]
      row.shape
      
      import numpy as np
      
      sort_indeces = np.argsort(row) 
      
      top_indeces = list(sort_indeces)[-20:]
      
      top_words = []
      for ind in top_indeces:
          top_words.append(words[ind])
      
      for row in tfidf:
      print()
      sort_indeces = np.argsort(row)
      top_indeces = list(sort_indeces)[-20:]
      top_words = []
      for ind in top_indeces:
          top_words.append(words[ind])
      print(top_words)

#### Topic modeling

      from sklearn.decomposition import LatentDirichletAllocation 
      lda = LatentDirichletAllocation(n_components=5)
      lda.fit(tf)
      topic_words = lda.components_
      topic_words.shape
      count_words = count.get_feature_names()
      for topic_ind, topic in enumerate(topic_words):
        print('topic', topic_ind)
        top_indeces = list(topic.argsort())[-12:]
        lda_top_words = []
        for ind in top_indeces:
            lda_top_words.append(count_words[ind])
        print(', '.join(lda_top_words))
        
        from sklearn.decomposition import NMF
        nmf = NMF(n_components=5)
        nmf.fit(tf)
        nmf_topic_word = nmf.components_
        nmf_topic_word.shape
        for topic_ind, topic in enumerate(nmf_topic_word):
          print('topic', topic_ind)
          top_indeces = list(topic.argsort())[-10:]
          top_words = []
          for ind in top_indeces:
              top_words.append(count_words[ind])
          print(', '.join(top_words))
