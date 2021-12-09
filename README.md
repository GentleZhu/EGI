# EGI
Source code for ["Transfer Learning of Graph Neural Networks with Ego-graph Information Maximization"](https://proceedings.neurips.cc/paper/2021/file/0dd6049f5fa537d41753be6d37859430-Paper.pdf), published in NeurIPS 2021.


If you find our paper useful, please consider cite the following paper.
```
@article{zhu2020transfer,
  title={Transfer learning of graph neural networks with ego-graph information maximization},
  author={Zhu, Qi and Yang, Carl and Xu, Yidan and Wang, Haonan and Zhang, Chao and Han, Jiawei},
  journal={arXiv preprint arXiv:2009.05204},
  year={2020}
}
```

## Requirements
Please use old version of DGL library (0.4.3) to run the original code. 
### CPU version
```
pip install dgl==0.4.3
```
### DGL GPU version (recommened)
Change your cuda version accordingly.
```
pip install dgl-cu101==0.4.3
```

## Model specifications
EGI model can be found under models/subgi.py, we call EGI as SubGI when code is developed. The default encoder arch is GIN as you will see in the code. To run the airport data, see example below
```
python run_airport.py --file-path=data/usa-airports.edgelist --label-path=data/labels-usa-airports.txt --n-dgi-epochs=100  --n-hidden=32 --self-loop --gpu=0 --n-layers=1 --dgi-lr=0.01 --model-id=2 --model-type=2
```

We also provide the code to run DGI on the dataset as below:
```
python run_airport.py --file-path=data/usa-airports.edgelist --label-path=data/labels-usa-airports.txt --n-dgi-epochs=100  --n-hidden=32 --self-loop --gpu=0 --n-layers=1 --dgi-lr=0.001 --model-id=2 --model-type=0
```

## Computer the EGI gap term
### from edgelist
```
python compute_bound_filepath.py --args.file-path=data/europe-aiports.edgelist --args.label-path=data/usa-aiports.edgelist
```
### from pickle file for synthetic experiment
```
python compute_bound_pickle.py --args.file-path=data/barabasi_small_graphs_full.pkl --args.label-path=data/forest_fire_graphs_full.pkl
```
