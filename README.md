# Directory structure
> "./NeMo" 

is the downloaded repository from https://github.com/NVIDIA/NeMo.
It contains the scripts for preparing data, training and evaluating Thutmose Tagger ("./NeMo/examples/nlp/text_normalization_as_tagging/)

> "./GTN_ini" 

should contain the initial version of Google Text Normalization dataset which contains 100 files. Thutmose Tagger is trained and evaluated on this dataset. Please download from "https://www.kaggle.com/datasets/richardwilliamsproat/text-normalization-for-english-russian-and-polish" and unzip it if you want to do training.

> "./test_data"

is the test data extracted from GTN_ini using the data preparation script from Thutmose Tagger. 

"test.input" is the default test set input and "test.labeled" is the label for the input. 

"test1000.input" is the hard test set input and "test1000.labeled" is the corresponding label.

To customize evaluation data as well as training data, you may need to modify "./NeMo/examples/nlp/text_normalization_as_tagging/prepare_dataset_en.sh" and associated Python scripts. Note that Google Text Normalization Dataset is huge. Processing such dataset will take a long time. You may add tqdm() in relevant codes to check progress. 

# Installation
1. First create a conda virtual environment by running 
```
conda env create -n <env_name> python=3.10
conda activate <env_name>
conda install -c anaconda cython
```
2. cd into ./NeMo folder then run
```
sh reinstall.sh
```
3. If you need to prepare your own data for training, you need run
```
sh ./NeMo/examples/nlp/text_normalization_as_tagging/install_requirements.sh
```

Finally, specify parameters in "./NeMo/examples/nlp/text_normalization_as_tagging/run_infer.sh" and run it if you want to do inference. 
If you are running on a device with multiple GPUs, go to line 110 at "./NeMo/nemo/core/connectors/save_restore_connector.py" to change GPU.