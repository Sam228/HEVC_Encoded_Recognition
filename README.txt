The FDDB face dataset originally has annotations in ellipse notation.
To work better with yolov5, darknet annotation format is followed which
uses bounding boxes. To do this, a script was used from the following 
repository: 
https://github.com/abars/YoloKerasFaceDetection
Following the README.md file in that repo, the following steps need to be
performed:
Create dataset
Download fddb dataset (FDDB-folds and originalPics folder) and put in the dataset/fddb folder.
http://vis-www.cs.umass.edu/fddb/

Create dataset/fddb/FDDB-folds/annotations_darknet folder for darknet.
python annotation_fddb_darknet.py

This will create FDDB image annotations in bounding box format at:
YoloKerasFaceDetection/dataset/fddb/FDDB-folds/annotations_darknet

As per darknet format, the images and annotations should be in the same folder
and have the same name with the image extension being .jpg (in this case) and
the annotation extension being .txt
Copy all of the images into this folder so that all images and annotations
from the FDDB dataset are present. I moved them to the path:
hevc_data/darknet_annotations

Clone yolov5 if you don't have it already:
https://github.com/ultralytics/yolov5/

Place the hevc_data file to the root of yolov5.

I created the training and validation lists and the corresponding .yaml
Now, the fddb_face.yaml can be used to train with yolov5
using the command from yolov5 root:
python train.py --epochs 120 --data hevc_data/fddb_face.yaml --weights yolov5s.pt

