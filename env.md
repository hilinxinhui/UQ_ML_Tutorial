# 环境配置

## 使用docker配置环境

```Shell
# 使用tensorflow docker环境
# 需要提前安装好docker和nvidia-container-toolkit
docker pull tensorflow/tensorflow:2.13.0-gpu-jupyter
docker run --gpus all -d -p 8889:8889 tensorflow/tensorflow:2.13.0-gpu-jupyter # 返回一个container id
docker cp UQ_ML_Tutorial/ <container_id>:/tf # 代码拷贝到docker环境中
docker exec -it <container_id> bash # 进入docker环境

# 在docker环境中安装依赖
python3 -m pip install --upgrade pip
pip install tf-models-official==2.11.6 numpy pandas matplotlib seaborn progressbar scikit-learn openpyxl ipython jupyter notebook

# 启动jupyter notebook
jupyter notebook --ip 0.0.0.0 --allow-root --port 8889 --no-browser

# 打包镜像
docker commit <container_id> <image_name>
# 保存镜像到文件
docker save -o <file_name> <image_name>
# 读取文件为镜像
docker load --input <file_name>
```

## 使用conda配置环境

```Shell
conda create -n tf python=3.8
conda activate tf
pip install tensorflow==2.11.0 tf-models-official
pip install numpy pandas matplotlib seaborn progressbar scikit-learn openpyxl ipython jupyter notebook
```
