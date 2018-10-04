## Build a classifier with sklearn and KFold
#### Разделить тексты на 2 выборки: train и test
        from sklearn.model_selection import KFold
        kf = KFold(n_splits=3, shuffle = True)
        kf.get_n_splits(all_texts)
#### Импортировать необходимые библиотеки
        from sklearn.metrics import recall_score
        from sklearn.metrics import classification_report
        from sklearn.naive_bayes import MultinomialNB
        from collections import Counter
#### Построить классификатор и распечатать данные о его работе
        report = []

        for train_index, test_index in kf.split(all_texts):
            all_texts_train, all_texts_test = all_texts[train_index], all_texts[test_index]
            all_labels_train, all_labels_test = all_labels[train_index], all_labels[test_index]
            vect = TfidfVectorizer(min_df=10, max_df=0.5, stop_words = 'english')
            tfidf_train = vect.fit_transform(all_texts_train)
            tfidf_test = vect.transform(all_texts_test)
            classifier = MultinomialNB()
            classifier.fit(tfidf_train, all_labels_train)
            predicted_labels = classifier.predict(tfidf_test)
            classif_report = classification_report(all_labels_test, predicted_labels)
            report.append(classif_report)

        print(report)
        print()
  #### Проверить классификатор
          poem = "string"
          tfidf_test = vect.transform([poem])
          predicted_labels = classifier.predict(tfidf_test)
          predicted_labels
