<div>
  <div align="center">
  
WalnutData
=======
    
  </div>

With the gradual maturity of UAV technology, it can provide extremely powerful support for smart agriculture and precise monitoring. Currently, there is no dataset related to green walnuts in the field of agricultural computer vision. Therefore, in order to promote the algorithm design in the field of agricultural computer vision, we used UAV to collect remote sensing data from 8 walnut sample plots. Considering that green walnuts have the characteristics of being affected by various lighting conditions and being occluded, we constructed a large-scale dataset with a higher fine-grained target feature - WalnutData. This dataset contains a total of 30,240 images and 7,062,080 instances, and there are 4 target categories: illuminated from the front and not occluded (A1), backlit and not occluded (A2), illuminated from the front and occluded (B1), and backlit and occluded (B2). We provide three types of labels: VOC, COCO, and YOLO, which are suitable for many currently mainstream object detection models. Then, we evaluated many mainstream algorithms on WalnutData and took these evaluation results as the baseline standard.The link to the paper of the WalnutData dataset: **https://doi.org/10.48550/arXiv.2502.20092**. 

Examples of the categories in WalnutData are shown in the following figure. (a) represents category A1, that is, the green walnuts are illuminated from the front and not occluded. (b) represents category A2, that is, the green walnuts are backlit and not occluded. (c) represents category B1, that is, the green walnuts are illuminated from the front and occluded. (d) represents category B2, that is, the green walnuts are backlit and occluded. 

  <p>
    <a href="https://github.com/1wuming/WalnutData/blob/WalnutData/README_zh.md" target="README_zh">
      <img width="100%" src="https://github.com/1wuming/WalnutData/blob/WalnutData/README_IMAGES/Category%20Examples%20of%20WalnutData.jpg" alt="WalnutData"></a>
  </p>

<div align="center">

[中文](https://github.com/1wuming/WalnutData/blob/WalnutData/README_zh.md) | [English](https://github.com/1wuming/WalnutData/blob/WalnutData/README_en.md) <br>
</div>

</div>


# 1. The download address of WalnutData
We provide three ways to obtain WalnutData (13.87G). ：
  - **IEEEDataPort**：https://ieee-dataport.org/documents/walnutdata-construction-green-walnut-dataset-based-uav-and-model-evaluation
  - **Hugging Face**:https://huggingface.co/datasets/nanmao/WalnutData/resolve/main/WalnutData.zip
  - **Baidu Netdisk**：https://pan.baidu.com/s/1ZQEr6YJW-V_cQ3sNrZKBEA?pwd=mt9m

  
# 2. Construction of the Dataset
We carried out data collection on 8 walnut sample plots between July 18 and September 14, 2024. All these sample plots are located in Yangbi County, Dali Bai Autonomous Prefecture, Yunnan Province, China. Additionally, in order to capture the changes in lighting conditions, we conducted the shooting between 9:00 and 19:00. The data collection equipment used uniformly was a DJI Matrice 300 RTK and a Zenmuse P1 (35mm F2.8) . The UAV took photos from a top-down angle (-90°) throughout the process according to the pre-planned flight route, and the flight path completely covered the scope of each sample plot. To reduce the impact of an excessively high flight altitude and too fast camera movement on the imaging quality, while ensuring flight safety, we set the flight speed between 1-3m/s and the flight altitude between 12-30m.

Since the resolution of the UAV aerial images (8192×5460 pixels) is too large, which is not conducive to the training of the model, in this study, the screened original images were all cut with a step size of 512. The resolution of the cut images is 1024×1024 pixels. After the processing of the above steps, the dataset of this study was finally formed, which consists of a total of 30,240 images.

The following table shows the detailed information of WalnutData.

|    Name   |  Number of Images | Number of Targets | Average Number of Targets per Image | Number of Large-Sized Targets | Number of Medium-Sized Targets | Number of Small-Sized Targets|
|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
|   Train  |     21167 |   495812   |     23.424    |     526   |  211669  |    283617    | 
|   Val  |     6048  |   139255   |     23.025    |     175   |  59371   |    79709     |  
|   Test  |     3025  |   71141    |     23.518    |     74    |  30047   |    41020     |

The following figure shows several examples of the dataset in WalnutData: 

<img src="https://github.com/1wuming/WalnutData/blob/WalnutData/README_IMAGES/Annotation%20Examples%20of%20WalnutData.jpg" alt="Annotation Examples WalnutData">

# 3. Dataset Analysis

## 3.1 Grayscale Value Analysis
The average grayscale values of the training set, validation set, and test set are 107.316, 108.048, and 107.544 respectively. The proportions of values lower than the middle grayscale value of 127.5 are 76.31%, 75.59%, and 75.81% respectively. This indicates that most of the green walnuts in WalnutData are in backlight conditions or are blocked by leaves in relatively dark places.

The following figure shows the distribution of the average grayscale values of WalnutData. 

![image](https://github.com/1wuming/WalnutData/blob/WalnutData/README_IMAGES/Grayscale%20Value%20Statistics.jpg)

## 3.2 Distribution of Category Instances in WalnutData
The proportions of the training set, validation set, and test set are 7:2:1, with the numbers of images being 21,167, 6,048, and 3,025 respectively. In addition, in the arrangement of the distribution of the number of categories, we have tried our best to ensure the similarity and balance of the distribution. The information on the distribution of category instances after the dataset is divided is shown in the following figure.  

![image](https://github.com/1wuming/WalnutData/blob/WalnutData/README_IMAGES/Instance%20Distribution%20Information%20After%20the%20Dataset%20Is%20Partitioned.jpg)

The following two figures show the distribution of the annotation boxes in the dataset:

<img src="https://github.com/1wuming/WalnutData/blob/WalnutData/README_IMAGES/labels_correlogram.jpg" alt="labels_correlogram" width="500"/>
<img src="https://github.com/1wuming/WalnutData/blob/WalnutData/README_IMAGES/labels.jpg" alt="labels" width="500"/>

# 4. Experimental Results

We evaluated some popular object detection models in recent years on WalnutData, and implemented one-stage and two-stage object detection algorithms using the ultralytics framework and the mmdetection framework respectively. The one-stage object detection algorithms include YOLOv3, YOLOv4, YOLOv5, DETR, etc.; the two-stage object detection algorithms include Fast R-CNN, Faster R-CNN, TridentNet, etc. In the following content, the evaluation results of each algorithm for various categories and instances of different sizes in WalnutData will be announced. All the experiments of the models in this study were carried out on 8 RTX 3090 servers or A800 servers, and the hyperparameters of the baseline models all used the default parameter values. In addition, the evaluation results of these baseline models will be provided as the benchmark values of WalnutData for researchers as a reference.

## 4.1 Experimental Results of WalnutData on One-Stage Object Detection Algorithms
The following table shows the evaluation of a series of mainstream algorithms on the validation set of WalnutData. 

|     Method         |     Para    |     GFLOPs     |     mAP50    |     mAP50:95    |     mAP50(A1)    |     mAP50(B1)    |     mAP50(B2)    |     mAP50(A2)    |     mAP50:95(A1)    |    mAP50:95(B1)   |   mAP50:95(B2)   |  mAP50:95(A2)   |
|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
|     YOLOv11-x      |     56.83M      |     194.4G     |      94.0       |     71.7    |  96.5 | 95.2 | 92.2 | 91.9 | 76.3 | 72.2 | 67.5 | 70.8 |
|     YOLOv11-l      |     25.28M      |     86.6G    |        91.7       |     68.0    | 95.2 | 93.3 | 89.4 | 88.9 | 73.5 | 68.5 | 63.2 | 66.8 |
|     YOLOv11-m      |     20.03M      |     67.7G    |        91.3       |     66.7    | 95.0 | 93.1 | 88.7 | 88.5 | 72.5 | 67.3 | 61.4 | 65.8    |
|     YOLOv11-s      |     9.41M      |     21.3G    |         84.7       |     58.7    | 91.3 | 88.0 | 80.5 | 79.2 | 66.7 | 59.8 | 52.0 | 56.0  |
|     YOLOv11-n      |     2.58M      |     6.3G      |        74.6       |     48.5    | 84.3 | 79.9 | 69.1 | 65.0 | 58.5 | 50.4 | 41.3 | 43.7  |
|     YOLOv10-x      |     31.59M      |     169.8G     |      94.4       |     72.6    |  96.7 | 95.5 | 92.6 | 92.6 | 77.1 | 72.8 | 68.5 | 71.9   |
|     YOLOv10-l      |     25.72M      |     126.3G    |       92.0       |     67.6    | 95.5 | 93.6 | 89.3 | 89.4 | 73.0 | 67.9 | 62.6 | 66.7    |
|     YOLOv10-b     |     20.41M      |     98.0G    |         90.9       |     65.9    |  94.8 | 93.0 | 88.1 | 87.8 | 71.7 | 66.5 | 60.7 | 64.6  |
|     YOLOv10-m     |     16.45M     |     63.4G    |          89.1     |       63.4  |    94.0 | 91.6 | 85.8 | 85.1 | 70.1 | 64.2 | 57.6 | 61.7 |
|     YOLOv10-s     |     8.03M      |     24.5G     |         86.3       |     59.9    |   92.1 | 89.2 | 82.5 | 81.6 | 67.5 | 60.6 | 53.6 | 58.0   |
|     YOLOv10-n     |     2.69M      |     8.2G    |           75.9       |     49.6    |   85.2 | 80.8 | 70.6 | 67.0 | 59.3 | 51.1 | 42.4 | 45.4   |
|     YOLOv9-e      |     -           |     -      |           93.8     |       70.6  |    96.8 | 95.1 | 91.3 | 92.0 | 75.8 | 71.1 | 65.7 | 70.0    |
|     YOLOv9-c      |     -          |     -     |             92.1   |         67.8    |  95.8 | 93.8 | 89.6 | 89.2 | 73.7 | 68.4 | 62.6 | 66.4  |
|     YOLOv9-m    |     -            |     -     |             89.7  |          64.1    |  94.3 | 92.0 | 86.5 | 85.8 | 70.9 | 64.8 | 58.3 | 62.3  |
|     YOLOv9-s      |     -          |     -     |             80.9       |     55.3    |  88.4 | 85.5 | 76.8 | 72.9 | 64.1 | 57.3 | 48.7 | 51.0  |
|     YOLOv9-t    |     -            |     -     |             72.2     |       47.3  |   82.7 | 78.5 | 66.6 | 61.0 | 57.7 | 50.0 | 40.1 | 41.4   |
|     YOLOv8-x      |     68.12M      |     257.4G    |        94.6       |     72.7    | 96.8 | 95.7 | 93.2 | 92.9 | 77.0 | 73.1 | 68.8 | 71.8  |
|     YOLOv8-l      |     43.60M      |     164.8G      |      93.6       |     70.6    |  96.2 | 95.0 | 91.8 | 91.5 | 75.4 | 71.1 | 66.3 | 69.6   |
|     YOLOv8-m      |     25.84M      |     78.7G     |        92.2       |     68.0    | 95.7 | 93.9 | 89.7 | 89.3 | 73.7 | 68.6 | 62.8 | 66.8    |
|     YOLOv8-s      |     11.12M      |     28.4G    |         86.2       |     59.7    | 92.2 | 89.4 | 82.1 | 81.1 | 67.3 | 60.8 | 53.3 | 57.3 |
|     YOLOv8-n     |     3.00M        |     8.1G    |          75.2    |        49.2    |  85.2 | 80.9 | 69.6 | 65.2 | 59.5 | 51.1 | 41.9 | 44.2  |
|     YOLOv7       |     -            |     -    |             67.0   |         40.1   |  80.1 | 74.0 | 61.6 | 52.3 | 51.1 | 41.6 | 33.9 | 33.8   |
|     YOLOv6-l      |     -            |     -     |           87.1      |      60.1   |    -     |    -     |     -      |    -  |     -   |    -   |    -     |    -   |
|     YOLOv6-m      |     -           |     -    |             83.7   |         56.9   |   -     |    -     |     -      |    -  |     -   |    -   |    -     |    -   |
|     YOLOv6-s      |     -            |     -    |            87.8  |          59.6    |    -     |    -     |     -      |    -  |     -   |    -   |    -     |    -   |
|     YOLOv6-n      |     -          |     -     |             74.2   |         47.8    |      -     |    -     |     -      |    -  |     -   |    -   |    -     |    -   |
|     YOLOv5-x    |     86.19M        |     203.8G     |       94.5       |     70.8    |  95.9 | 95.8 | 94.3 | 91.9 | 74.6 | 71.2 | 68.1 | 69.5   |
|     YOLOv5-l     |     46.12M         |     107.7G     |     93.3         |   68.4    |  94.9 | 94.7 | 93.4 | 90.1 | 72.5 | 68.8 | 65.5 | 66.9  |
|     YOLOv5-m    |     20.86M          |     47.9G     |      90.9        |    64.7    |  93.1 | 92.8 | 90.9 | 86.6 | 69.6 | 65.2 | 61.2 | 62.8   |
|     YOLOv5-s     |     7.02M         |     15.8G    |        84.5      |      57.0   | 89.0 | 87.9 | 84.3 | 76.9 | 63.9 | 58.2 | 52.7 | 53.4    |
|     YOLOv5-n      |     1.76M        |     4.1G      |       72.0       |     45.1    |  80.5 | 78.1 | 68.9 | 60.4 | 54.5 | 47.2 | 39.1 | 39.6    |
|     YOLOv4      |     -               |     -     |          57.3      |      31.3   |  74.0 | 54.7 | 49.8 | 40.6 | 44.2 | 32.7 | 23.7 | 24.6   |
|     YOLOv3      |     61.51M         |     154.6G    |       94.7       |     71.6    |  96.4 | 96.0 | 94.6 | 92.7 | 75.3 | 71.9 | 68.6 | 70.7   |
|     YOLOv3-SPP     |     62.56M      |     155.4G    |       95.1       |     71.4    |  96.4 | 96.1 | 94.7 | 93.0 | 74.9 | 71.5 | 68.3 | 70.9 |
|     YOLOv3-Tiny     |     8.67M     |     12.9G    |         66.2       |     38.0    |    73.9 | 71.7 | 64.9 | 54.1 | 46.9 | 39.2 | 33.0 | 33.0     |

Note: The units of the indicators such as mAP50:95, mAP50, mAP(A1), mAP(B1), mAP(B2), and mAP(A2) are all "%". 


|     Method         |     Backbone    |     Epoch    |     Batch    |     AP（%）    |     AP50（%）    |     AP75（%）    | AP-small（%）    |     AP-medium（%）    |     AP-large（%）    |     AR-small（%）    |     AR-medium（%）    |     AR-large（%）    |
|:-------------------:|:----------------:|:--------------:|:--------------:|:----------------:|:----------------:|:----------------:|:---------------------:|:----------------------:|:---------------------:|:---------------------:|:----------------------:|:---------------------:|
|     YOLOX-s     | CSPDarknet   | 300          | 4            | 45.4           | 72.8           | 52.9           |44.1                | 46.8                 | 37.3                | 64.1                | 64.3                 | 45.9                |
|     YOLOX-l    |  CSPDarknet   | 300            | 4            | 51.6           | 79.1           | 62.7           |50.1                | 53.3                 | 44.5                | 67.0                | 67.8                 | 55.6                |
|     YOLOX-x     |  CSPDarknet   | 300           | 4            | 54.9           | 82.7           | 67.5           |53.5                | 56.3                 | 52.7                | 68.4                | 68.4                 | 58.4                |
|     DETR      | ResNet50       | 150          | 8            | 14.1           | 34.7           | 8.0            |10.3                | 18.6                 | 32.4                | 24.5                | 39.6                 | 46.7                |
|     Deformable DETR | ResNet50        | 50           | 4            | 49.2           | 76.8           | 59.7           | 43.7                | 55.4                 | 64.7                | 59.4                | 69.5                 | 72.5                |
|     DINO-4scale      |   ResNet50       | 12            | 4           | 50.3           | 77.0           | 61.7           |47.5                | 53.5                 | 56.9                | 68.1                | 72.9                 | 72.8                |
|     Conditional DETR |   ResNet50    | 50           | 8            | 37.9           | 65.5           | 40.9           |32.3                | 44.5                 | 56.1                | 49.5                | 63.7                 | 68.0                |


## 4.2 Experimental Results of WalnutData on Two-Stage Object Detection Algorithms

The following table shows the evaluation of a series of mainstream algorithms on the validation set of WalnutData. 

|     Method         |     Backbone    |     Epoch    |     Batch    |     AP（%）    |     AP50（%）    |     AP75（%）    |     AP-small（%）    |     AP-medium（%）    |     AP-large（%）    |
|:-------------------:|:----------------:|:--------------:|:--------------:|:----------------:|:----------------:|:----------------:|:---------------------:|:----------------------:|:---------------------:|
|     Fast R-CNN| ResNet50       | 24           | 8            | 22.9           | 35.9           | 26.7           | 15.7                | 31.4                 | 54.5                |
|     Faster R-CNN| ResNet50             |24            | 8            | 51.5           | 79.7           | 62.2           | 45.6                | 58.2                 | 69.7                |
|     Cascade R-CNN| ResNet50          | 24             | 8            | 56.0           | 83.7           | 68.4           | 50.3                | 62.4                 | 72.6                |
|     Grid R-CNN| ResNet50             | 24           |8            | 53.8           | 80.4           | 66.1           | 48.2                | 60.2                 | 71.9                |
|     TridentNet| ResNet50            | 24           | 4            | 53.4           | 80.8           | 64.2           | 48.9                | 58.6                 | 69.9                |
|     Double head R-CNN| ResNet50          | 24            | 8            | 55.2           | 84.5           | 67.2           | 50.1                | 61.1                 | 69.6                |
|     Sparse R-CNN| ResNet50          | 36           | 8            | 45.3           | 68.8           | 55.8           | 40.6                | 50.9                 | 53.8                |
|     Fast R-CNN| ResNet101      | 24           | 8            | 24.5           | 37.7           | 28.9           | 16.8                | 33.7                 | 55.7                |
|     Faster R-CNN| ResNet101             | 24            | 8             | 56.3           | 84.1           | 68.9           | 49.8                | 63.7                 | 72.1                |
|     Cascade R-CNN| ResNet101           | 24           | 8            | 58.9           | 85.9           | 72.5           | 52.7                | 65.7                 | 74.5                |
|     Grid R-CNN| ResNet101        |24          | 8            | 57.5           | 83.1           | 70.9           | 51.2                | 64.9                 | 75.3                |
|     Sparse R-CNN| ResNet101    | 36           | 8            | 46.9           | 71.2           | 57.7           | 42.1                | 52.5                 | 59.9                |


# 5. Citation
```
@misc{wu2025walnutdatauavremotesensing, 
      title={WalnutData: A UAV Remote Sensing Dataset of Green Walnuts and Model Evaluation}, 
      author={Mingjie Wu and Chenggui Yang and Huihua Wang and Chen Xue and Yibo Wang and Haoyu Wang and Yansong Wang and Can Peng and Yuqi Han and Ruoyu Li and Lijun Yun and Zaiqing Chen and Songfan Shi and Luhao Fang and Shuyi Wan and Tingfeng Li and Shuangyao Liu and Haotian Feng},
      year={2025},
      eprint={2502.20092},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2502.20092}, 
}
```



