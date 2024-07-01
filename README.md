# RIIPS_re
安装BOT-SORT
pip3 install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
python3 setup.py develop
 pycocotools cython 

替换默认python python3版本

sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.7 1

sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.7 1

pip install "opencv-contrib-python-headless<4.3" -i https://pypi.tuna.tsinghua.edu.cn/simple

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
