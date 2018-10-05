## Предобработка текстов (Preprocessing)

#### Загрузить файлы
      with open('file-name-here', 'r', encoding = 'utf-8') as f:
        string = f.read()
#### Убрать пунктуацию
      import re 
      children_clean = re.sub("[.,\"?!:;()\[\]{}\-–—]", "", children)
      lay_clean = re.sub("[.,\"?!:;()\[\]{}\-–—]", "", lay)
      prof_clean = re.sub("[.,\"?!:;()\[\]{}\-–—]", "", prof)
#### Токенизация
      Вручную:
            tokens = string.lower().split()
      NLTK:
            1. Download and install nltk:
            https://www.nltk.org/install.html  
            
            2. import nltk
            from nltk.tokenize import word_tokenize
                       
            3. tokens = nltk.word_tokenize(string)
#### Лемматизация

     def lemmatizer(poem):
          tokens = word_tokenize(poem)
          tokens_tags = nltk.pos_tag(tokens)
          matching_tags = {'NN':'n', 'VB':'v', 'JJ':'a', 'RB':'r'}

          lemmatizer = WordNetLemmatizer()
          tokens_lemma = []
          for (token, tag) in tokens_tags:

              if not(token[0].isalpha()):
                  continue
              token = token.lower()
              if tag[:2] in matching_tags:
                  token = lemmatizer.lemmatize(token, pos=matching_tags[tag[:2]])
                  tokens_lemma.append(token)

          return ' '.join(tokens_lemma)
    
#### Стоп-слова
      from nltk.corpus import stopwords
      stop_words = set(stopwords.words('english'))
      stop_words.update(['.', ',', '"', "'", '?', '!', ':', ';', '(', ')', '[', ']', '{', '}'])
      good_words = [word for word in tokens if word not in stop_words]
#### Маленькие слова
 tinies = ['a', 'ah', 'am', 'an',
 'as',
 'at',
 'be',
 'do',
 'go',
 'ha',
 'he',
 'hi',
 'i',
 'in',
 'is',
 'it',
 'me',
 'my',
 'no',
 'of',
 'oh',
 'ok',
 'or',
 'so',
 'to']
      
      
