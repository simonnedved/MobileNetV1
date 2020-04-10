# Tensorflow-Mobilenet

1. Clone this repo  
```
$ git clone https://github.com/ZH-Lee/Tensorflow-Mobilenet.git
```
2. You will need a cifar10 dataset before train your model
```
$ wget http://www.cs.toronto.edu/~kriz/cifar-10-python.tar.gz
```
3. Into your repo and mkdir
```
$ cd Tensorflow-Mobilenet
$ mkdir cifar
then unzip you cifar10 dataset into cifar
$ mkdir ckpt (for saved model)

```
After step mentioned above, your repo will looks like this:  
```
  Mobilnet:
          cifar (your data)
          ckpt (saved model ckpt)
          train.py
          freeze_graph.py
          mobilenet.py
          train.py
```
## Train your model  
You are allowed to use command line to start training:
```
      The agrs are description below:
        --lr            learing_rate from begin, and it will decay by 0.99
        --batch_size    a mini_batch size depend on your GPU memory, a appropriate batch size is needed, not too larget or too small
        --epochs        the total epoch your model trained
        --load_pretrain whether load a pretrain weights for your model or not
        --pretrain_path the path of your pretrain_path, only by setting 'load_pretrain' be true, you can use this pretrain weight
```
Here are two ways to train model, the first is to load pre_train model that i train on my Mac.In this way, you are expected to download pre_train model
```
$ wget https://github.com/ZH-Lee/Tensorflow-Mobilenet/releases/download/Mobilenetv1-0.7688/Mobilenet-0.768.zip
```
and then put this ckpt.zip into your ckpt dir in your repo.
next...
```
$ python3 train.py --lr 1e-3 --batch_size 16 --epochs 20 --load_pretrain 1
```

The second ways is to train your model from scratch
```
$ python3 train.py --lr 1e-3 --batch_size 16 --epochs 20 --load_pretrain 0
```
## Experiment
Some hyperparameters i used to train my pre_train weights are as below:
First train:
```
lr                = 0.001
batch_size        = 16
data_aug          = False
epochs            = 10
step per epochs   = 10k
load_pretrain     = False
```
it will got test acc 0.7+
then 
```
lr                = 1e-6
batch_size        = 16
data_aug          = False
epochs            = 10
step per epochs   = 10k
load_pretrain     = True
```
and finally, got:
```
train acc         = 0.9+
train loss        = 0.0+
test acc          = 0.76+
```


