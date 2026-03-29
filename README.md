# IGGCN

Code & data accompanying the paper "[Classification of Epileptic Seizures in EEG Data based on Iterative Gated Graph Convolution Network]"(https://doi.org/10.3389/fncom.2024.1454529)

Authors: Yue Hu, Jian Liu, Rencheng Sun, Yongqiang Yu, and Yi Sui.

## Overview
The automatic and precise classification of epilepsy types using electroencephalogram (EEG) data is critical for diagnosis. However, traditional Graph Convolutional Neural Networks (GCN) often rely on static, predefined
graph topologies and struggle to capture long-temporal dependencies in EEG signals.

To address these challenges, we propose an Iterative Gated Graph Convolutional Network (IGGCN). Our model iteratively optimizes the EEG
graph structure using a multi-head attention mechanism, introduces Gated Graph Neural Networks (GGNN) to capture long-term sequence dependencies, and employs Focal Loss to alleviate data imbalance. The model achieves
an average F1 score of 91.5% and an average Recall of 91.8% on the TUSZ dataset.

## Details of IGGCN
<img width="1055" height="700" alt="image" src="https://github.com/user-attachments/assets/6ea7043d-6d13-4cf0-9b7d-85f8795c656d" />
Figure 1 shows the overall framework of our proposed Iterative Gated Graph Convolutional Network (IGGCN).

The model consists of four key components:

- **Multi-Head Graph Attention**: Iteratively optimizes the EEG graph structure using multi-head attention, adapting to dynamic brain connectivity patterns.
- **GGNN Module**: Captures long-term temporal dependencies in EEG signals via gated graph neural networks.
- **Graph Regularization**: Applies smoothness, degree, and sparsity losses to ensure biologically plausible graph structures.
- **Prediction Head**: Uses a linear layer to classify seizure types, with Focal Loss to address data imbalance in the TUSZ dataset.

## Dataset
The model is evaluated on the Temple University Hospital EEG Seizure Corpus (TUSZ). The original seizure types are reclassified into four main categories for this task:
* CFSZ: Combined Focal Non-Specific Seizure
* GNSZ: Generalized Non-Specific Seizure
* ABSZ: Absence Seizure
* CTSZ: Combined Tonic Seizures
<img width="516" height="412" alt="image" src="https://github.com/user-attachments/assets/bd910c96-7040-435f-852f-72937efd9b6d" />



## Get started

### Prerequisites
This code is written in python 3. You will need to install a few python packages in order to run the code.
We recommend you to use `virtualenv` to manage your python packages and environments.
Please take the following steps to create a python virtual environment.

* If you have not installed `virtualenv`, install it with ```pip install virtualenv```.
* Create a virtual environment with ```virtualenv venv```.
* Activate the virtual environment with `source venv/bin/activate`.
* Install the package requirements with `pip install -r requirements.txt`.


### Data preprocess
* Cd into the `Preprocess` folder
* Start preprocessing the raw data by running the following notebook

    ```
         prepare_data_for_tusz.ipynb
    ```

* The processed data will be stored in the `data` folder

### Run the IGGCN models

* Cd into the `src` folder
* Run the IDGL model and report the performance

    ```
         python main.py -config config/tusz_eeg/4_class/ggnn.yml
    ```
<img width="1057" height="852" alt="image" src="https://github.com/user-attachments/assets/9b38c074-ddbb-4282-8271-4a8b857dbff1" />



* Notes:
    - Output Data: You can find the output data in the `out` folder specified in the config file.
    - Dataset Download: You can download the TUSZ dataset from [here](https://isip.piconepress.com/projects/tuh_eeg/)

## Citation
If you use our code or find our research helpful, please cite our paper:

```bibtex
@article{hu2024classification,
  title={Classification of epileptic seizures in EEG data based on iterative gated graph convolutional network},
  author={Hu, Yue and Liu, Jian and Sun, Rencheng and Yu, Yongqiang and Sui, Yi},
  journal={Frontiers in Computational Neuroscience},
  volume={18},
  pages={1454529},
  year={2024},
  publisher={Frontiers Media SA},
  doi={10.3389/fncom.2024.1454529}
}
  
