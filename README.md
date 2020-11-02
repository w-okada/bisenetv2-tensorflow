This repository is forked from https://github.com/MaybeShewill-CV/bisenetv2-tensorflow/

# Pourpose of this repository

- generate arbitrary input size model
- retrain more easily 



# generate arbitrary input size model

## CityPass
Not yet

## CelebAMask
Downloaded the pretrained model from
[here](https://www.dropbox.com/sh/0iisy23j4j6d1hj/AABm3fho2glNA7TWnvD7kK2oa?dl=0)

(1) create frozen model
```
$ export PYTHONPATH=$PYTHONPATH:`pwd`
$ pip install PyYAML
$ python3 tools/celebamask_hq/freeze_celebamaskhq_bisenetv2_model.py \
    --weights_path checkpoint/celebamaskhq.ckpt \
    --frozen_pb_file_path ./checkpoint/bisenetv2_celebamask_frozen.pb \
    --optimized_pb_file_path ./checkpoint/bisenetv2_celebamask_optimized.pb

```
\* In my environment, PyYAML version is 5.3.1

(2) convert to tensorflowjs
```
$ pip install tensorflowjs
$ tensorflowjs_converter --input_format tf_frozen_model \
    --output_node_names final_output \
    checkpoint/bisenetv2_celebamask_optimized.pb \
    webmodel

```
\* In my environment, tensorflowjs version is 2.7.0



# retrain more easily
Not yet ...

