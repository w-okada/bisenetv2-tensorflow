This repository is forked from https://github.com/MaybeShewill-CV/bisenetv2-tensorflow/

# Pourpose of this repository

- generate arbitrary input size model
- retrain more easily 



# generate arbitrary input size model
I strongly recommend this process in docker container.

```
docker pull tensorflow/tensorflow:1.15.4-gpu-py3
docker run --rm --gpus all -v /home/<path_to_working_folder>/:/work  -ti tensorflow/tensorflow:1.15.4-gpu-py3
```
## CityPass
Not yet

## CelebAMask
Downloaded the pretrained model from
[here](https://www.dropbox.com/sh/0iisy23j4j6d1hj/AABm3fho2glNA7TWnvD7kK2oa?dl=0) into `./checkpoint`

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

### Demo
![image](https://user-images.githubusercontent.com/48346627/97803282-822e3e80-1c8c-11eb-8635-74d937e5a8f6.png)


https://flect-lab-web.s3-us-west-2.amazonaws.com/P01_wokers/t08_bisenetv2-celebamask/index.html


### Demo repository

https://github.com/w-okada/image-analyze-workers



# retrain more easily
Not yet ...

