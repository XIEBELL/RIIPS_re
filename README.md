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
pip install opencv-python install "opencv-python-headless<4.3"
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
pip install torch==1.11.0+cu113 torchvision==0.12.0+cu113 torchaudio==0.11.0 --extra-index-url https://download.pytorch.org/whl/cu113

```
下载四个包：
```
git clone https://github.com/riips/AIC24_Track1_YACHIYO_RIIPS.git
git clone https://github.com/NirAharon/BoT-SORT.git
git clone https://gitclone.com/github.com/KaiyangZhou/deep-person-reid.git

```
## 安装BOT-SORT
```
pip3 install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
pip install tb-nightly
pip install pycocotools cython cython_bbox faiss-gpu -i https://pypi.tuna.tsinghua.edu.cn/simple
pip install setuptools==59.5.0

pip3 install setuptools==59.0.1  -i https://pypi.tuna.tsinghua.edu.cn/simple

python setup.py develop

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
1


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


lanyun-gpu

scene 61-64 3090 reid 70% 掉线，准备下载后重配 7/2/9：43
19863729336
A6.


scene 65 4090 Det 100%   7/2/17.50 关机，余额70
19218403844
A6.

scene 66-68 3090 det 7/3/9：43
66:
det 100% emb 100% 下载完，已关机
68:
det 100% emb 100% 下载完，已关机
67:
det 100% emb 100% 下载完，已关机


scene 69 70 4090 
69 det 100% emb 100%报错修改y2=y1  下载完，已关机

70 det 100% emb 100%  下载完，已关机 



15031873509
A6.

姜戈
1.
19232703368
2.
19253030534
3.
19253031224
4.
19253032246
5.
19252405170
6.
19232706458
7.
17758792031
8.
13122569971
9.
18621586913
10.
15697764239

