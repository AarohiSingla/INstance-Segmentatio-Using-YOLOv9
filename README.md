### Instance segmentation USing YOLOv9:

### Video tutorial: https://youtu.be/aVGdRZKe5dM

![as](https://github.com/AarohiSingla/INstance-Segmentatio-Using-YOLOv9/assets/60029146/5ae8dfc9-3f9d-4ee2-a648-739ad0bbee06)

1- Clone repo - git clone https://github.com/WongKinYiu/yolov9.git

2- cd to yolov9 folder

3- Install requirements:  pip install -r requirements.txt

4- Download yolov9 pretrained segmentation model:  https://github.com/WongKinYiu/yolov9/releases/download/v0.1/gelan-c-seg.pt

5- Place the downloaded weight file in yolov9 directory.

6- Make predictions using pretrained gelan model: 
python segment/predict.py --source test_img.jpg --img 640 --device 0 --weights gelan-c-seg.pt


# Custom model training
Download custom dataset: https://universe.roboflow.com/asit-xno9q/levelup/dataset/4

Create custom config file here: yolov9\models\segment  with this name (gelan-c-seg_custom.yaml) (make a copy of  gelan-c-seg.yaml)
Change the number of classes.

### train command:
python segment/train.py --workers 8 --device 0 --batch 32  --data data.yaml --img 640 --cfg models/segment/gelan-c-seg_custom.yaml --weights gelan-c-seg.pt --name gelan-c-seg --hyp hyp.scratch-high.yaml --no-overlap --epochs 100 --close-mosaic 10


### inference gelan models
python segment/predict.py --source ../1.jpg --img 640 --device 0 --weights runs/train-seg/gelan-c-seg/weights/best.pt

