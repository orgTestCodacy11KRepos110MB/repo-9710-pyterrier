# Pyterrier

## Terrier Python API

# Installation

### Linux
1. Make sure that JAVA_HOME environment variable is set to your java directory
2. `pip install python-terrier`

### Windows
Pyterrier is not available for Windows because pytrec_eval isn't available for Windows.

### Colab notebooks
```
os.environ["JAVA_HOME"] = "/usr/lib/jvm/java-8-openjdk-amd64"    
!pip install python-terrier
```

# Indexing

### Indexing TREC formatted collections

You can create an index from TREC formatted collection using TRECCollectionIndexer.    
For TXT, PDF, Microsoft Word files, etc files you can use FilesIndexer.    
For Pandas Dataframe you can use DFIndexer.

See examples at:    
https://colab.research.google.com/drive/17WpzhtlMj1U2UJku-RaO2axNsUFhPI6z

# Retrieval and Evaluation

See examples at:
https://colab.research.google.com/drive/1yime_0D21Q-KzFD4IbsRzTvjRbo9vz4I

# Experiment - Perform Retrieval and Evaluation with a single function
We provide an experiment object, which allows to compare multiple retrieval approaches on the same queries & relevance assessments:

```
pt.Experiment(topics, retr_systems, eval_metrics, qrels, perquery=False, dataframe=True)
```

More examples are provided at:
https://colab.research.google.com/drive/15oG7HwyYCBFuborjmfYglea0VLkUjyK-

# Learning to  Rank
First create a FeaturesBatchRetrieve(index, features) object with the desired features and controls.

Call the transform(topics_set) function with the train, validation and test topic sets to get dataframes with the feature scores and use them to train your chosen model.

Use your trained model to predict the score of the test_topics and evaluate the result with Utils.evaluate()

## LTR_pipeline

Create a LTR_pipeline object with arguments:

1. Index reference or path to index on disc
2. Weighting model name
3. Features list
4. Qrels
5. LTR model

Call the fit() method on the created object with the training topics.

Evaluate the results with the Experiment function by using the test topics

```
pt.LTR_pipeline(index, model, features, qrels, LTR)
```

More learning to rank examples are provided at:
https://colab.research.google.com/drive/1KwHoahx_i0vax9fnCZpLP-JmI9jvSoey

