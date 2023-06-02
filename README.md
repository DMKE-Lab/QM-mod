# QM-mod
# Quadruple Mention Text-Enhanced Temporal Knowledge Graph Reasoning

## Usage
### Training the TKG reasoning model
Before using QM-mod you need to train a TKG reasoning model. You can use any knowledge graph embedding framework for training. 
We used the PyTorch version of [OpenKE](https://github.com/thunlp/OpenKE/tree/OpenKE-PyTorch).  

To use a previously trained TKG reasoning model with QM-mod you need to export the entity, relation and timestamps matrices as 
*numpy arrays* using pickle:
 - For TTransE and TA-TransE/TA-DistMult the matrices are called 'entities.p',  'relations.p' and 'timestamp.p'

Furthermore you need to provide one files: 'Now-2022', which contain a mention text mapping of quadruple corresponding index (id) in the embedding files.

The trained 200D ComplEx embeddings can be obtained from(https://github.com/haseebs/haseebs.github.io/raw/master/assets/embeddings.zip).

#### Instructions for OpenKE
Follow the instructions to install OpenKE. Under [openke_scripts](openke_scripts/) you can find exemplary training scripts (make sure you update the paths to the dataset in OpenKE format). As the API of OpenKE frequently changes, scripts work with the 
[following version of OpenKE](https://github.com/thunlp/OpenKE/tree/0a55399b3e800bc779582c4784cac96f00230fd8).

### Training the QM-mod
Word embeddings are required for training the extension. You may obtain the wikipedia2vec word embeddings from [here](https://wikipedia2vec.github.io/wikipedia2vec/pretrained/). 
An example config file to reproduce the results is provided as config.ini in the root folder.

For training:
python owe/run_QM_mod.py -t -c <PATH_TO_DATASET> -d  <PATH_TO_CONFIG_AND_OUTPUT_DIR> --<KGC_MODEL_NAME> <PATH_TO_KGC_EMBEDDINGS>


