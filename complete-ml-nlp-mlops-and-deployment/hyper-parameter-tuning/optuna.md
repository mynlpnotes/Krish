# Optuna

* Better than gridsearch and randomsearch cv
* Works on all frameworks like pytorch, tensorflow, sklearn etc
* pip install optuna
* Define a objective function
*

    <figure><img src="../../.gitbook/assets/image (13) (1).png" alt=""><figcaption></figcaption></figure>
* Tree\_method = gpu\_hist is for executing on gpu
* Trail.suggest\_loguniform 🡪 suggest alpha from this range
* In case we have multiple gpu, then we can pass gpu id also
*

    <figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>
* !NVIDIA-SMI 🡪 to get the GPU details list
* CUDA 🡪 driver program which helps to run program on GPU
* Param for each trial
*

    <figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>
* Optuna.visualization.plot\_optimization\_history(find\_param)
*

    <figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>
* Optuna.visualizatin.plot\_slice(find\_param)
*

    <figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>
