# TensorFlow 2.0 YOLO-V3

這個專案實現了TensorFlow2.0 YOLO-V3物件偵測。

GitHub: https://github.com/KUASWoodyLIN/TF2-Yolo3

## Usage

- Requirements
    - [Numpy](http://www.numpy.org/)
    
    - [OpenCV](https://opencv.org/)
    
    - [Matplotlib](https://matplotlib.org/)
    
    - [TensorFlow >= 2.0](https://www.tensorflow.org/versions/r2.0/api_docs/python/tf)
    
    - [TensorFlow Datasets](https://www.tensorflow.org/datasets/)
    
    - [TensorFlow addons](https://github.com/tensorflow/addons)

- DarkNet weights 轉換到 TensorFlow weights
    ```bash
    python convert.py
    ```

- YOLO-V3訓練
    ```bash
    python train.py
    ```

- YOLO-V3多尺度訓練(multi scale training)
    ```bash
    python train-multi-scale.py
    ```

- YOLO-V3測試
    ```bash
    python test.py
    ```



- TensorBoard觀察訓練紀錄
    ```bash
    tensorboard --logdir logs_yolo
    ```

## Results

Predict by YOLO v3 original weights

![100 Iteratives](https://raw.githubusercontent.com/KUASWoodyLIN/TF2-Yolo3/master/output_images/output_results.png)
## References

- https://github.com/pjreddie/darknet
	- YOLO-V3原作者程式碼(DarkNet)
- https://github.com/qqwweee/keras-yolo3
	- 網路模型
- https://github.com/zzh8829/yolov3-tf2
	- 損失函數
	- 資料預處理
- https://github.com/allanzelener/YAD2K
	- DarkNet到Keras網路模型轉換
