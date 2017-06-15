# Baseline Sentiment Analysis Tool


## Overview

This baseline system performs relevance classification, sentiment analysis, aspect categorization and opinion target extraction from a document. It was designed for the GermEval 2017 Shared Task on Aspect Based Sentiment Analysis (https://sites.google.com/view/germeval2017-absa/)

You can download the compiled project from:
https://ltnas1.informatik.uni-hamburg.de:8081/owncloud/index.php/s/0dht3oSyBhTZDzL

## Machine Learning

The baseline system contains two classifiers. A SVM  is used for relevance classification, sentiment analysis and aspect categorization. For opinion target identification, it uses a CRF classifier.

### Features

The SVM uses the following features:
* term frequency
* German sentiment lexica [1]

The CRF classifier uses these features:
* the token (without standardization/lemmatization/lowercasing)
* the POS tag

Both features are unigram features on the current token, no preceding/following tokens are taken into account.


## Training and Testing

The download package and the project come with pre-trained models.
To train the models, use the following command:

```
java -cp ABSA-Baseline-0.0.1-SNAPSHOT.jar uhh_lt.GermEval2017.baseline.TrainAllClassifiers path/to/train.xml
 path/to/train.xml
```

If you want to train from the TSV file, you can do so as well. Note, that in this case, no model for Aspect Target Identification is being trained.
```
java -cp ABSA-Baseline-0.0.1-SNAPSHOT.jar uhh_lt.GermEval2017.baseline.TrainAllClassifiers path/to/train.tsv
```

You can test the models by executing:
```
java -cp ABSA-Baseline-0.0.1-SNAPSHOT.jar uhh_lt.GermEval2017.baseline.Classify ../dev.xml
```
or
``
java -cp ABSA-Baseline-0.0.1-SNAPSHOT.jar uhh_lt.GermEval2017.baseline.Classify ../dev.tsv
```

This will produce a file with "_classified" added to its name. This file contains the predictions.



## Access to the classification results

You can use the system to get a prediction that can be used in an ensemble system.
A quick way to do this is to add the following repository to your projects POM file:

```
	<repositories>
		<repository>
		    <id>jitpack.io</id>
		    <url>https://jitpack.io</url>
		</repository>
	</repositories>
```

Now, you can add the project's dependency:


## Quickstart



## Licence
This software is published under the Apache Software Licence 2.0


## References

[1] Waltinger, U. (2010): Sentiment Analysis Reloaded: A Comparative Study On Sentiment Polarity Identification Combining Machine Learning And Subjectivity Features, In: Proceedings of the 6th International Conference on Web Information Systems and Technologies (WEBIST '10), Valencia, Spain.
