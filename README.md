# Yolo7_gpu
This contains the necessary files and links to run yolov7 on gpu in ubunut 22.04

Ubuntu:

Prerequisites:
    • Anaconda 
    • Python (pip)

    • Create a conda environment.
        ◦ conda create venv
        ◦ conda activate venv
        - pip3 install -r requirements.txt
        - download the pretrained weights: https://github.com/WongkinYiu/yolov7/release/download/v0.1/yolov7.pt
    
    - Do the below outside the conda environment
    • Clone the YOLOV7 repository from GitHub. 
        ◦ git clone https://github.com/WongKinYiu/yolov7.git
        ◦ change directory to this cloned repository.

    • Install the necessary packages from the requirements.txt file.
    • pip3 install -r requirements.txt


    • Do these steps if you want to execute in GPU,
    • Install CUDA from https://developer.nvidia.com/cuda-downloads.
    • If the installed CUDA version is 11.x, install pytorch using following command : pip install torch==1.11.0+cu113 torchvision==0.12.0+cu113 torchaudio==0.11.0 --extra-index-url https://download.pytorch.org/whl/cu113
    • If CUDA version is different, check with https://pytorch.org/get-started/locally/ to install compatible version of PyTorch.
    • In GPU mode, quantization of weights happens from FP32 to FP16. Hence, sometimes the model returns no predictions. So, We should specify not to perform quantization. Change Line #31 in detect.py file in the cloned repository to : half = False

    - problem may arise when there is already package related to nvidia. follow the steps to resolve the issue
    • apt list --installed | grep
    • sudo apt remove --purge nvidia-driver-535 nvidia-kernel-source-535 nvidia-kernel-common-535 nvidia-compute-utils-535 nvidia-utils-535 nvidia-firmware-535-535.171.04 xserver-xorg-video-nvidia-535 libnvidia-cfg1-535 libnvidia-compute-535 libnvidia-decode-535 
    libnvidia-encode-535 libnvidia-fbc1-535 libnvidia-gl-535 libnvidia-extra-535 libnvidia-common-535
    • reboot
    
    • Run the command
      python3 detect.py --weights yolov7.pt --conf 0.25 --img-size 640 --source inference/images/horses.jpg
