# 1. WalnutData 下载地址
我们提供了两种方式来获取WalnutData：
  - **IEEEDataPort**：https://ieee-dataport.org/documents/walnutdata-construction-green-walnut-dataset-based-uav-and-model-evaluation

  - **百度网盘**：
  
# 2. 数据集构建
我们分别在2024年7月18日至9月14日之间对8块核桃样本地进行数据采集，这些样本地均处于中国云南省大理白族自治州漾濞县。另外，为了获取光照情况的变化，我们在9点至19点之间进行拍摄。数据采集设备统一使用DJI Matrice 300 RTK无人机和Zenmuse P1（35mm F2.8）镜头，无人机全程按照预先规划的航线进行从上往下的角度（-90°）拍摄，飞行路径完全涵盖每块样本地的范围。为了减少飞行高度过高与相机运动过快对成像质量的影响，我们在保证飞行安全的情况下，将飞行速度设置在1-3m/s之间，飞行高度设置在12-30m之间。

由于无人机航拍图像分辨率（8192×5460像素）过大，不利于模型的训练，因此本研究将筛选后的原始图像均按照步长为512进行图像切割，切割后的图像分辨率均为1024×1024像素。经过上述步骤的处理，最终形成了本研究的数据集，共30240张图像。


|           |     Scenario    |     Resolution    |     FPS     |     Duration       |     Size        |     Weather      |     The number of objects    |     Description                                                 |
|-----------|-----------------|-------------------|-------------|--------------------|-----------------|------------------|------------------------------|-----------------------------------------------------------------|
|     1     |     a           |     1480×684      |     17.6    |     126 seconds    |     270.7 Mb    |     Sunny        |     Multiple Objects         |     Daylight, mountains, and plains                             |
|     2     |     a           |     1480×684      |     17.7    |     85 seconds     |     227.5 Mb    |     Sunny        |     No Objects               |     Evening, mountains, and plains                              |
|     3     |     a           |     1480×684      |     17.2    |     109 seconds    |     30.2 Mb     |     Sunny        |     Multiple Objects         |     Night, mountains, and plains                                |
|     4     |     a           |     1480×684      |     13.8    |     79 seconds     |     184.1 Mb    |     Sunny        |     No Objects               |     Evening, mountains, and plains                              |
|     5     |     a           |     776×452       |     18.6    |     113 seconds    |     75.3 Mb     |     Sunny        |     No Objects               |     Daylight, mountains, and plains                             |
|     6     |     a           |     1480×684      |     17.9    |     82 seconds     |     9.7 Mb      |     Sunny        |     Single Object            |     Night, mountains, and plains                                |
|     7     |     b           |     1480×684      |     29.9    |     115 seconds    |     496.2 Mb    |     Sunny        |     Multiple Objects         |     Daylight, mountains, and plains                             |
|     8     |     b           |     1480×684      |     28      |     82 seconds     |     314.4 Mb    |     Sunny        |     No Objects               |     Daylight, Evening, Night, mountains, and   plains           |
|     9     |     b           |     1480×684      |     29.9    |     101 seconds    |     477.4 Mb    |     Sunny        |     Single Object            |     Daylight, mountains, and plains                             |
|     10    |     b           |     1480×684      |     26.5    |     83 seconds     |     43.4 Mb     |     Sunny        |     Single Object            |     Night, mountains, and plains                                |
|     11    |     c           |     1480×684      |     18.5    |     195 seconds    |     258.4 Mb    |     Sunny        |     Multiple Objects         |     Daylight, Night, mountains, and plains                      |
|     12    |     c           |     1480×684      |     21.2    |     190 seconds    |     423.3 Mb    |     Sunny        |     Single Object            |     Daylight, Evening, Night, mountains, and   plains           |
|     13    |     d           |     1480×684      |     9.99    |     133 seconds    |     145.9 Mb    |     Sunny        |     Single Object            |     Daylight, Evening, Night, mountains, lakes,   and plains    |
|     14    |     d           |     1480×684      |     15.7    |     122 seconds    |     169.2 Mb    |     Sunny        |     Multiple Objects         |     Daylight, Evening, Night, mountains, lakes,   and plains    |
|     15    |     d           |     1480×684      |     11.1    |     125 seconds    |     136.5 Mb    |     Sunny        |     No Objects               |     Daylight, Evening, Night, mountains, lakes,   and plains    |
|     16    |     e           |     1280×720      |     30      |     148 seconds    |     348 Mb      |     Sunny        |     Multiple Objects         |     Daylight, mountains, and lakes                              |
|     17    |     e           |     1280×720      |     30      |     97 secnds      |     130.2 Mb    |     Sunny        |     Multiple Objects         |     Night, mountains, and lakes                                 |
|     18    |     e           |     1280×720      |     30      |     89 seconds     |     92 Mb       |     Sunny        |     Multiple Objects         |     Evening, mountains, and lakes                               |
|     19    |     f           |     1280×720      |     24.6    |     60 seconds     |     342.8 Mb    |     Rainy&Fog    |     Multiple Objects         |     Daylight, mountains, lakes, and plains                      |
|     20    |     f           |     1280×720      |     23.7    |     29 seconds     |     20.2 Mb     |     Rainy&Fog    |     Multiple Objects         |      Evening, Night, mountains, lakes, and plains               |
|     21    |     f           |     1280×720      |     10.6    |     57 seconds     |     6.7 Mb      |     Rainy&Fog    |     Multiple Objects         |     Night, mountains, lakes, and plains                         |
|     22    |     f           |     1280×721      |     10.6    |     36 seconds     |     28.1 Mb     |     Rainy&Fog    |     Multiple Objects         |     Evening, mountains, lakes, and plains                       |
|     23    |     g           |     1280×722      |     10.2    |     99 seconds     |     206 Mb      |     Sunny        |     Multiple Objects         |     Daylight, plains                                            |
|     24    |     g           |     1280×723      |     10.5    |     27 seconds     |     21.8 Mb     |     Sunny        |     Multiple Objects         |     Night, plains                                               |
|     25    |     g           |     1280×724      |     9.3     |     61 seconds     |     92 Mb       |     Sunny        |     Multiple Objects         |     Evening, plains                                             |
|     26    |     h           |     1280×724      |     24.7    |     40 seconds     |     251.1 Mb    |     Snow         |     Multiple Objects         |     Daylight, mountains, and plains                             |
|     27    |     h           |     1280×724      |     26      |     33 seconds     |     143.4 Mb    |     Snow         |     Multiple Objects         |     Night, mountains, and plains                                |
|     28    |     h           |     1280×724      |     25.3    |     49 seconds     |     183.6 Mb    |     Snow         |     Multiple Objects         |     Evening, mountains, and plains                              |


## 2.1 多样化场景
我们搭建了八个具有不同地形、不同植被的多种规模森林场景。

![8个不同地形的森林场景，包含平原、山脉、湖泊和河流。](https://user-images.githubusercontent.com/51520993/230010235-ca6fe6c3-9369-4fdc-bfcc-a4be02af4138.png)


## 2.2 多种天气
M<sup>4</sup>SFWD 不仅模拟了晴天场景，还模拟了雨雾天和雪天的场景。

![多样化气象条件，包含晴天、雨&雾天和雪天。](https://user-images.githubusercontent.com/51520993/230010663-3901daad-b3ad-4c18-ae02-9f77812deb2b.png)

## 2.3 多个时间
M<sup>4</sup>SFWD 考虑了一天中不同时间点（白天，傍晚和黑夜）的多模态森林火灾图像。

![image](https://user-images.githubusercontent.com/51520993/230017256-dd94a59a-7448-499b-a93e-e35d6536b5dd.png)


## 2.4 不同数量的火灾目标
在多种地形、多种气象条件和多个时间点的多模态森林场景下，我们设置了无目标、单个目标和多个目标三种火灾目标数量情况，旨在全面评估模拟多模态森林火灾数据集在目标检测算法的性能表现。

![image](https://user-images.githubusercontent.com/51520993/230016997-8110d8a7-2cc4-4a0f-8f34-b3b1282ee55a.png)


# 3. 数据集的详细信息

下表为数据集的图像和注释框在不同天气和一天中不同时间的分布。


|     Multimodal scenarios    |     Number of images    |     fire    |     smoke    |     Number of annotation boxes    |     Average number of instances boxes per image    |
|-----------------------------|-------------------------|-------------|--------------|-----------------------------------|----------------------------------------------------|
|     Sunny                   |     3292                |     8423    |     7095     |     15518                         |     4.7                                            |
|     Snowy                   |     312                 |     772     |     547      |     1319                          |     4.2                                            |
|     Rainy & Fog             |     370                 |     432     |     494      |     926                           |     2.5                                            |
|     Daytime                 |     2209                |     4684    |     3807     |     8491                          |     3.8                                            |
|     Evening                 |     560                 |     2052    |     1581     |     3633                          |     6.5                                            |
|     Night                   |     1205                |     2891    |     2748     |     5639                          |     4.7                                            |


下表为所有注释框的尺寸分布

|     class    |     small boxes    |     medium boxes    |     large boxes    |     total    |
|--------------|--------------------|---------------------|--------------------|--------------|
|     fire     |     4848           |     4114            |     665            |     9627     |
|     smoke    |     1883           |     2037            |     4216           |     8136     |
|     all      |     6731           |     6151            |     4881           |     17763    |


下图为数据集中注释框的分布情况

![image](https://user-images.githubusercontent.com/51520993/230016724-060d4f17-3e00-4416-a3ca-bf73fa230b58.png)
![image](https://user-images.githubusercontent.com/51520993/230016663-57becf5c-fc60-42d2-b2b0-3dc55af5cf13.png)
![image](https://user-images.githubusercontent.com/51520993/230016547-1f1c81db-013c-4608-9b6e-366c93c157de.png)




# 4. 实验结果

## 4.1 M<sup>4</sup>SFWD 在单阶段目标检测算法的实验结果

|     Model         |     #Param.    |     Flops     |     Weight Size    |     AP50:95    |     AP50    |     APFire    |     APSmoke    |     Precision    |     Recall    |     F1-socre    |
|-------------------|----------------|---------------|--------------------|----------------|-------------|---------------|----------------|------------------|---------------|-----------------|
|     YOLOv8m       |     25.9M      |     78.9G     |     52Mb           |     51.2       |     87.3    |     88.7      |     86         |     83.7         |     86.9      |     85.3        |
|     YOLOv8l       |     43.7M      |     165.2G    |     87.7Mb         |     51.6       |     86.8    |     88.9      |     84.8       |     84.6         |     80.1      |     82.3        |
|     YOLOv8x       |     68.2M      |     258.1G    |     136.7Mb        |     47.3       |     87.1    |     88.5      |     85.8       |     84.4         |     80.2      |     82.2        |
|     YOLOv7        |     36.5M      |     103.2G    |     74.8Mb         |     48.5       |     87.5    |     88.7      |     86.2       |     85.3         |     80.5      |     82.8        |
|     YOLOv7-X      |     70.8M      |     188G      |     142.1Mb        |     47.3       |     87.1    |     88.5      |     85.8       |     84.4         |     80.2      |     82.2        |
|     YOLOv6-M      |     34.9M      |     85.8G     |     74.9Mb         |     44.5       |     83.4    |     84.2      |     82.6       |     83.8         |     80.7      |     82.2        |
|     YOLOv6-L      |     59.5M      |     150.7G    |     117.6Mb        |     48.8       |     86.3    |     87.2      |     85.4       |     84.2         |     79.8      |     81.9        |
|     YOLOv6-M6     |     79.6M      |     379.5G    |     72.51Mb        |     43.7       |     82.9    |     82        |     85.1       |     82.6         |     80        |     81.3        |
|     YOLOv6-L6     |     140.4M     |     673.4G    |     268.4Mb        |     46.3       |     83.3    |     83.9      |     82.6       |     83.6         |     79.7      |     81.6        |
|     YOLOv5m       |     21.2M      |     49.0G     |     42.2Mb         |     45.6       |     87.1    |     88.1      |     86         |     86.6         |     81.5      |     84.0        |
|     YOLOv5l       |     46.5M      |     109.1G    |     92.8Mb         |     45.9       |     86.7    |     87.9      |     85.4       |     85.2         |     81.6      |     83.4        |
|     YOLOv5x       |     86.7M      |     205.7G    |     173.1Mb        |     45.7       |     86.3    |     87.3      |     85.3       |     84.6         |     82.3      |     83.4        |
|     YOLOv4        |     -          |     59.6G     |     256Mb          |     -          |     75.3    |     75.7      |     74.8       |     66           |     73        |     69.3        |
|     YOLOv4-CSP    |     -          |     50.3G     |     210.3Mb        |     -          |     81.5    |     83.8      |     79.3       |     78           |     80        |     79.0        |
|     YOLOv3        |     -          |     65.3G     |     246.3Mb        |     -          |     82.3    |     82.6      |     82         |     83           |     77        |     79.9        |
|     YOLOv3-spp    |     -          |     65.7G     |     250.5Mb        |     -          |     82.1    |     82.3      |     81.8       |     83           |     78        |     80.4        |


## 4.2 在双阶段目标检测算法的实验结果

|     Model                    |     Image Size    |     Weight Size    |     AP50:95    |     AP50    |
|------------------------------|-------------------|--------------------|----------------|-------------|
|     Faster R-CNN R50-DC5     |     640           |     1300Mb         |     38.6       |     78.9    |
|     Faster R-CNN R50-FPN     |     640           |     333.3Mb        |     42.1       |     82.7    |
|     Faster R-CNN R50-C4      |     416           |     257.5Mb        |     24.8       |     59.8    |
|     Faster R-CNN R101-C4     |     416           |     422Mb          |     26.9       |     60      |
|     Faster R-CNN R101-DC5    |     416           |     1400Mb         |     25.3       |     57.8    |
|     Faster R-CNN R101-FPN    |     416           |     365.2Mb        |     35.9       |     76.1    |
|     RPN R50                  |     416           |     103.5Mb        |     25.4       |     55.8    |
|     Fast R-CNN  R50-FPN      |     416           |     318.7Mb        |     28.5       |     59.8    |

## 4.3 M<sup>4</sup>SFWD 在轻量级目标检测算法的实验结果

|     Model          |     #Param.    |     Flops    |     Weight Size    |     AP50:95    |     AP50    |     APFire    |     APSmoke    |     Precision    |     Recall    |     F1-socre    |
|--------------------|----------------|--------------|--------------------|----------------|-------------|---------------|----------------|------------------|---------------|-----------------|
|     YOLOv8n        |     3.2M       |     8.7G     |     6.3Mb          |     49.5       |     86.4    |     87.1      |     85.7       |     83.2         |     81.2      |     82.2        |
|     YOLOv8s        |     11.2M      |     28.6G    |     22.5Mb         |     50.3       |     86.4    |     87.9      |     85         |     83.1         |     81.4      |     82.2        |
|     YOLOv6-N       |     4.7M       |     11.4G    |     10.0Mb         |     42         |     82.2    |     82.9      |     81.5       |     83.3         |     78.8      |     81.0        |
|     YOLOv6-S       |     18.5M      |     45.3G    |     10.2Mb         |     44.4       |     84.1    |     85        |     83.2       |     83.9         |     80.3      |     82.1        |
|     YOLOv6-N6      |     10.4M      |     49.8G    |     21.83Mb        |     42.1       |     82.1    |     82.8      |     81.3       |     83.7         |     78.9      |     81.2        |
|     YOLOv6-S6      |     41.4M      |     198G     |     85.84Mb        |     43.2       |     83.1    |     83.8      |     82.5       |     83.6         |     79.4      |     81.4        |
|     YOLOv5n        |     1.9M       |     4.5G     |     3.8Mb          |     40.1       |     84.9    |     86.1      |     83.7       |     84.3         |     79.1      |     81.6        |
|     YOLOv5s        |     7.2M       |     16.5G    |     14.4Mb         |     43.7       |     86.4    |     87.9      |     84.9       |     83.7         |     80.9      |     82.3        |
|     YOLOv4-tiny    |     -          |     6.8G     |     23.5Mb         |     -          |     64.5    |     51.9      |     77.1       |     80           |     58        |     67.2        |
|     YOLOv3-tiny    |     -          |     5.4G     |     34.7Mb         |     -          |     71.7    |     69.6      |     73.9       |     76           |     72        |     73.9        |

