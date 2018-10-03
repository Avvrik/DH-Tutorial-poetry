## Предобработка текстов (Preprocessing)

#### Загрузить файлы
      with open('file-name-here', 'r', encoding = 'utf-8') as f:
        string = f.read()
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
     from nltk.stem import WordNetLemmatizer
     lemmas = [lemmatizer.lemmatize(t) for t in tokens]
      
      
      
