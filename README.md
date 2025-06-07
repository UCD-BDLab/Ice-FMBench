# Ice-FMBench: A Foundation Model Benchmark for Sea Ice Type Segmentation
Ice-FMBench is a benchmark for evaluating the transferability of foundation models for sea ice type segmentation using SAR imagery. It supports a variety of remote sensing foundation models and fine-tuning strategies.
## Data Description

**AI4Arctic Sea Ice Challenge Dataset**: 
   We use the raw version of this dataset, which was produced for the AutoICE competition initiated by the European Space Agency (ESA) ɸ-lab. The purpose of the competition is to develop deep learning models to automatically produce sea ice charts including sea ice concentration, stage-of-development and floe size (form) information.

   You can access this dataset at:
   [https://data.dtu.dk/collections/AI4Arctic_Sea_Ice_Challenge_Dataset/6244065](https://data.dtu.dk/collections/AI4Arctic_Sea_Ice_Challenge_Dataset/6244065)

   Alternatively, you can use the ready-to-train data provided in the same collection.

   Citation:
   Buus-Hinkler, Jørgen; Wulf, Tore; Stokholm, Andreas Rønne; Korosov, Anton; Saldo, Roberto; Pedersen, Leif Toudal; et al. (2022). AI4Arctic Sea Ice Challenge Dataset. Technical University of Denmark. Collection. https://doi.org/10.11583/DTU.c.6244065.v2

## Data Acquisition

```bash
# Create a directory for the data
mkdir -p data/AI4Arctic

# Download the ready-to-train train dataset
wget -O data/AI4Arctic/train_data.zip https://data.dtu.dk/ndownloader/articles/21316608/versions/3

# Download the ready-to-train test dataset
wget -O data/AI4Arctic/test_data.zip https://data.dtu.dk/ndownloader/articles/21762830/versions/2

# Unzip the downloaded datasets
unzip data/AI4Arctic/train_data.zip -d data/AI4Arctic/train/
unzip data/AI4Arctic/test_data.zip -d data/AI4Arctic/test/

# Remove the zip files to save space
rm data/AI4Arctic/train_data.zip
rm data/AI4Arctic/test_data.zip
```
## How to run
Install Dependencies
```bash
pip install -r requirements.txt
```

The main entry point is main.py, which supports multiple models and fine-tuning strategies. Here are the basic usage patterns:
```bash
# Basic training with a specific model and strategy
python main.py --model prithvi_300 --finetuning-strategy full_finetune

# Evaluation only with a checkpoint
python main.py --model prithvi_100 --finetuning-strategy lora --mode evaluate --checkpoint path/to/model.ckpt
```
## Citation

If you use this code in your research, please cite our paper:

```bibtex
@article{Ice-FMBench,
  title={Ice-FMBench: A Foundation Model Benchmark for Sea Ice Type Segmentation},
  author={Samira Alkaee Taleghan, Morteza Karimzadeh, Andrew P. Barrett, Walter N. Meier, Farnoush Banaei-Kashani},
  journal={Journal Name},
  year={2025}
}
```