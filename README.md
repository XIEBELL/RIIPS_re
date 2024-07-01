# RIIPS_re
替换python版本，或者使用conda
替换默认python python3版本
```
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.7 1

sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.7 1
```
装python工具
```
pip install opencv-python-headless -i https://pypi.tuna.tsinghua.edu.cn/simple
pip install "opencv-contrib-python-headless<4.3" -i https://pypi.tuna.tsinghua.edu.cn/simple

```
添加清华源
```
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/

3090用这个OK
pip install torch==1.9.1+cu111 torchvision==0.10.1+cu111 torchaudio==0.9.1 -f https://download.pytorch.org/whl/torch_stable.html
4090用这个
pip install torch==1.10.0+cu111 torchvision==0.11.0+cu111 torchaudio==0.10.0 -f https://download.pytorch.org/whl/torch_stable.html
```

## 安装BOT-SORT
```
pip3 install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
pip3 install tb-nightly setuptools==59.0.1  -i https://pypi.tuna.tsinghua.edu.cn/simple

python setup.py develop

pip install pycocotools cython cython_bbox faiss-gpu -i https://pypi.tuna.tsinghua.edu.cn/simple
```

复制一个环境到另外两个
```
conda create --name torchreid --clone botsort_env
conda create --name openmmlab --clone botsort_env
```
## 安装torchreid
```

pip3 install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple

python setup.py develop
```
## 安装openmmlab

```
#step 3
pip install -U openmim -i https://pypi.tuna.tsinghua.edu.cn/simple

mim install mmengine
mim install "mmcv==1.7.0"

mim install "mmdet==2.28.2"

#Build mmpose from source
git clone https://github.com/open-mmlab/mmpose.git -b v0.29.0 --depth 1
cd mmpose
修改requirement/poseval。txt
poseval@git+https://gitclone.com/github.com/svenkreiss/poseval.git

pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
pip install -v -e .
If you receive an mmcv AssertionError, please reinstall mmcv.

mim uninstall mmcv
mim install "mmcv==1.7.0"
```

## 替换python，conda略过



1.绑定阿里云盘,把SCENE_061下载到autodl-tmp

2.在/root/autodl-tmp/下创建文件夹：EmbedFeature，Pose，Detection，Tracking，Original

3.把下载好的压缩包移动并解压文件夹到/root/autodl-tmp/Original

4.提取每一帧：

sh scripts/extract_frame.sh 61

5.目标检测

sh scripts/detection.sh 61

6.特征提取

sh scripts/embedding.sh 61

7.姿态估计

sh scripts/pose.sh 61

8.协同跟踪

source .venv/bin/activate

sh scripts/tracking.sh 61

9.生成结果

python3 tools/generate_submission.py
