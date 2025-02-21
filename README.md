# Main

This script takes the user question, embeds it, searches in the index map, and provides a list of protocols.  
An index map and a JSON file with the map for the index are required. (The `indexGenerator` script generates the index and the JSON.)

## Requirements

### DeepSeek
- [DeepSeek Model](https://ollama.com/library/deepseek-r1:14b)
- Install `ollama` in the scipion enviroment (scipionProtocolRecomender) and pull the model:
  ```bash
  conda activate scipionProtocolRecomender
  conda install condaforge::ollama
  ollama serve
  ollama pull deepseek-r1:14b
  ollama list
  ```
  models located at .ollama/models/blob

  model = "deepseek-r1:14b"
  model = "deepseek-r1:32b"
  model = "deepseek-r1:671b"

### Embedding
  HuggingFaceEmbeddings
  ```bash
  pip install langchain_huggingface
  curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
  source $HOME/.cargo/env
  pip install -qU langchain-huggingface
  ```
  model_name="sentence-transformers/all-mpnet-base-v2"
  

### Indexing
  faiss-cpu
  numpy
  


#  indexGenerator

A Scipion enviroment has to be created. The script can install all the plugins of Scipion, takes all the protocol, embedd all of them and save it in an index map (numpy array) and a json file with the plugin-protocol-index references.
Maybe you need to update the compilers in the conda scipion env: 
```bash
  scipion3 run conda install -c conda-forge libstdcxx-ng
```

## Preparation
An Scipion enviroment with Scipion installed:
```bash
  python3 -m scipioninstaller -conda -n scipionProtocolRecomender -noAsk scipionProtocolRecomender
```
1. In terminal, activate the enviroment
2. Edit the parameters to prepare the enviroment:
   - SCIPION_ENVIROMENT_NAME
   - PATH_SCIPION_INSTALLED
   - SITE_PACKAGES
   - If INSTALL_PLUGINS is True will install all the plugins
3. Goes to the path the Scipion is installed
4. Activate ollama
```bash
    ollama serve
```
5. Launch the script with:
6. 
```bash
    python3 indexGenerator.py
```


## Requirements
- os
- pathlib
- requests
- subprocess
- json
- numpy
- ollama (see main section to how to install)
  - model 43GB:
    model = "deepseek-r1:70b"
  - model 404GB
    model = "deepseek-r1:671b"
  
