# DeepLog

PyTorch implements "DeepLog: Anomaly Detection and Diagnosis from System Logs through Deep Learning"

## Play on Colab

[https://colab.research.google.com/drive/1xWHovxTkysiPei68bTywqB2oCo6JelAU?usp=sharing](https://colab.research.google.com/drive/1xWHovxTkysiPei68bTywqB2oCo6JelAU?usp=sharing)

## Getting Started

1. Build environment

   ```sh
   python3 -m venv deeplog-venv
   cd deeplog-venv
   source bin/activate
   git clone https://github.com/nailo2c/deeplog.git
   cd deeplog
   pip install -r requirements.txt
   ```

2. Run local example

   We use open data `OpenStack` from logpai's loghub

   2.1. Preprocess

   ```python
   cd example/
   python3 preprocess.py
   ```

   2.2. Train

   `num-class` is count of `event_id_map`, where `event_id_map` is generated by `preprocess.py`. `num-candidates` is self-define, here we define `num-candidates` is `num-class*0.1`

   ```python
   python3 train.py --num-class 1143 --num-candidates 114 --epochs 35 --window-size 3 --local True
   ```

   2.3. Predict

   ```python
   python3 predict.py --threshold 25
   ```

3. Result

   | Accuracy  | 0.9430014 |
   |-----------|-----------|
   | Precision | 0.6497461 |
   | Recall    | 0.9275362 |
   | F1        | 0.7641791 |

4. Deactivate

   ```sh
   deactivate
   ```

## Folder Structure

+ This tree structure is generate by mac terminal tool `tree` & copy paste it to `README.md`.

   ```sh
   tree -I "__pycache__|tmp.*" >> tmp.txt
   ```

```sh
.
├── README.md
├── deeplog
│   ├── __init__.py
│   └── deeplog.py
├── example
│   ├── data
│   │   └── OpenStack
│   │       ├── anomaly_labels.txt
│   │       ├── openstack_abnormal.log
│   │       ├── openstack_normal1.log
│   │       └── openstack_normal2.log
│   ├── predict.py
│   ├── preprocess.py
│   └── train.py
└── requirements.txt
```
