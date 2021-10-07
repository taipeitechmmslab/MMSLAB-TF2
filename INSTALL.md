# 1. Windows

## 1.1. Virtualenv

#### 1.1.1. 安裝virtualenv虛擬機： 

```bash
pip install virtualenv
```



#### 1.1.2. 創建新的虛擬環境

```bash
virtualenv -p python ./tf2 
```



#### 1.1.3. 進入虛擬環境

```bash
cd tf2\Scripts 
activate 
```



## 1.2. TensorFlow

#### 1.2.1. 升級pip版本

```bash
pip install --upgrade pip 
```



#### 1.2.2. 安裝TensorFlow

**TensorFlow CPU版本**：

```bash
pip install tensorflow==2.6.0
```



**TensorFlow GPU版本**：

1. 安裝顯示卡驅動器(450.x 以上版本)。[驅動程式](https://www.nvidia.com/download/index.aspx?lang=en-us)
2. 安裝 TensorFlow 支援 CUDA® 11.2 (TensorFlow 2.5.0 以上版本)。[CUDA](https://developer.nvidia.com/cuda-toolkit-archive)
3. 下載cuDNN SDK 8.1.0並將其解壓縮至`C:\tools\cuda`。[cuDNN](https://developer.nvidia.com/rdp/cudnn-archive)

4. 設定環境變數

   ```bash
   C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2\bin
   C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2\extras\CUPTI\lib64
   C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2\include
   C:\tools\cuda\bin
   ```

安裝TensorFlow-GPU

```bash
pip install tensorflow-gpu==2.6.0
```



#### 1.2.3. TensorFlow Test

測試：

```bash
python -c "import tensorflow as tf;print(tf.reduce_sum(tf.random.normal([1000, 1000])))"
```

輸出：

```bash
2021-10-07 23:14:08.671984: I tensorflow/core/platform/cpu_feature_guard.cc:142] This TensorFlow binary is optimized with oneAPI Deep Neural Network Library (oneDNN) to use the following CPU instructions in performance-critical operations:  AVX AVX2
To enable them in other operations, rebuild TensorFlow with the appropriate compiler flags.
2021-10-07 23:14:09.502332: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1510] Created device /job:localhost/replica:0/task:0/device:GPU:0 with 8963 MB memory:  -> device: 0, name: GeForce RTX 2080 Ti, pci bus id: 0000:26:00.0, compute capability: 7.5
tf.Tensor(1267.9038, shape=(), dtype=float32)
```



如果出現以下錯誤訊息：

```bash
2021-07-07 00:07:20.567760: W tensorflow/stream_executor/platform/default/dso_loader.cc:64] Could not load dynamic library 'cusolver64_11.dll'; dlerror: cusolver64_11.dll not found
```

將`C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.0\bin\cusolver64_10.dll`改成`C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.0\bin\cusolver64_11.dll`



# 2. Ubuntu

## 2.1. Virtualenv

#### 2.1.1. 安裝Virtualenv虛擬機

```bash
sudo apt install virtualenv
```



#### 2.1.2. 創建新的虛擬環境

```bash
virtualenv -p python3 ./tf2
```



#### 2.1.3. 進入虛擬環境

```bash
source tf2/bin/activate  
```



## 2.2. TensorFlow

#### 2.2.1. 升級pip版本

```bash
pip install --upgrade pip
```



#### 2.2.2. 安裝TensorFlow

**TensorFlow CPU版本**：

```bash
pip install tensorflow==2.6.0
```



**TensorFlow GPU版本**：

安裝CUDA

```bash
# Add NVIDIA package repositories
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/cuda-ubuntu1804.pin
sudo mv cuda-ubuntu1804.pin /etc/apt/preferences.d/cuda-repository-pin-600
sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub
sudo add-apt-repository "deb https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/ /"
sudo apt-get update

wget http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1804/x86_64/nvidia-machine-learning-repo-ubuntu1804_1.0.0-1_amd64.deb

sudo apt install ./nvidia-machine-learning-repo-ubuntu1804_1.0.0-1_amd64.deb
sudo apt-get update

wget https://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1804/x86_64/libnvinfer7_7.1.3-1+cuda11.0_amd64.deb
sudo apt install ./libnvinfer7_7.1.3-1+cuda11.0_amd64.deb
sudo apt-get update

# Install development and runtime libraries (~4GB)
sudo apt-get install --no-install-recommends \
    cuda-11-0 \
    libcudnn8=8.0.4.30-1+cuda11.0  \
    libcudnn8-dev=8.0.4.30-1+cuda11.0

# Reboot. Check that GPUs are visible using the command: nvidia-smi

# Install TensorRT. Requires that libcudnn8 is installed above.
sudo apt-get install -y --no-install-recommends libnvinfer7=7.1.3-1+cuda11.0 \
    libnvinfer-dev=7.1.3-1+cuda11.0 \
    libnvinfer-plugin7=7.1.3-1+cuda11.0
```

安裝TensorFlow-GPU

```bash
pip install tensorflow-gpu==2.6.0
```

