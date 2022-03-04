# yolo-butterfly

### 1. install requirements.txt in a Python>=3.7.0 environment, including PyTorch>=1.7.
```
$ git clone https://github.com/ultralytics/yolov5  # clone
$ cd yolov5  
$ pip install -r requirements.txt
```


### 2. Create labels by labelImg
```
$ pip3 install labelImg
$ labelImg
$ labelImg [IMAGE_PATH] [PRE-DEFINED CLASS FILE] 
```
eg. labelImg /PATH/Data/butterfly/Lycaenidae/Chilades_pandava /PATH/Data/butterfly/Lycaenidae/classes.txt 
PATH is a directory where you colned this yolo-butterfly repository


### 4. Copy images to dataset folder and Divide datset
Use partition_dataset.ipynb to split image data into three sets. (train, validation, and test)


### 5. modify data.yaml
'train' and 'val' should be a path of each datset txt files. 


### 6. Lets train!
```
$ cd yolov5
$ python train.py --img 640 --batch 4 --epochs 50 --data /PATH/dataset/data.yaml --cfg /PATH/yolov5/models/yolov5l.yaml --weights yolov5l.pt 
#use yolov5l weight pre-trainediwth COCO128
```


### 7. Visualize results 
```
$ tensorboard --logdir yolov5/runs/train
```
or
```
from utils.plots import plot_results
plot_results('/PATH/yolov5/runs/train/exp1/results.csv') 
```


### 8. Inference
```
$ python detect.py --weights /PATH/yolov5/runs/train/exp1/weights/best.pt --img 640 --conf 0.5 --source "/PATH/dataset/test/" --name exp1
```
It will be saved under /PATH/yolov5/runs/detect.
