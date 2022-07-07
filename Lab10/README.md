# TF2-VAE
GitHub: https://github.com/KUASWoodyLIN/TF2-VAE

## Usage

- Requirements
    - [Numpy](http://www.numpy.org/)
    - [TensorFlow >= 2.0](https://www.tensorflow.org/versions/r2.0/api_docs/python/tf)
    - [TensorFlow Datasets](https://www.tensorflow.org/datasets/)

- Training VAE
    ```bash
    python train.py
    ```

- Test VAE
    ```bash
    python test.py
    ```
    
- TensorBoard
    ```bash
    tensorboard --logdir logs_vae
    ```

## Results
Results Images
![Results Images](images/output.png)

TensorBoard Output
![Tensorboard Output](images/Tensorboard.png)

## References
[Auto-Encoding Variational Bayes](https://arxiv.org/abs/1312.6114)
