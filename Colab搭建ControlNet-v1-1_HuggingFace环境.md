# Colab搭建ControlNet-v1-1_HuggingFace环境
## Git地址
https://github.com/glt3953/ControlNet-v1-1_HuggingFace
## 扩展阅读
https://www.uisdc.com/stable-diffusion-2
## 相关网站
https://huggingface.co/spaces/hysts/ControlNet-v1-1
https://replicate.com/jagilley
https://promptomania.com/
https://www.urania.ai/top-sd-artists
https://stableres.info/
https://civitai.com/
## Colab示例
https://colab.research.google.com/drive/1Sq3eMl5FtdtQZjNELeyi0CzjYNregHX5#scrollTo=S6G1afsrjJJd
## 搭建流程
1. 安装Git环境
```
%pip install gitpython
```
2. 拉取代码并进入目录
```
import git

git.Repo.clone_from('https://github.com/glt3953/ControlNet-v1-1_HuggingFace.git', '/content/repo/ControlNet-v1-1')

%cd /content/repo/ControlNet-v1-1
%ls
```
3. 安装依赖库
```
!pip install -r requirements.txt
```
4. 配置 ngrok 环境
```
!wget https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip
!unzip ngrok-stable-linux-amd64.zip
#获取token https://dashboard.ngrok.com/get-started/your-authtoken
#验证token
!./ngrok authtoken 2PuPonHwFQpdeht3WZFgMlQDRuw_2YkcaMrbuG5pjg9jTzkT5
```
5. 使用 ngrok 映射到Colab端口运行代码
```
import subprocess
ngrok_process = subprocess.Popen('./ngrok http 7860', shell=True)  
#映射的地址在https://dashboard.ngrok.com/tunnels/agents 中查询

!python app.py
```
映射的地址在https://dashboard.ngrok.com/tunnels/agents 中查询
## 模型分类
### Depth - 根据人物轮廓画图
python gradio_depth.py
模型文件：control_v11f1p_sd15_depth
### Normalbae - 房间布局画图
python gradio_normalbae.py
模型文件：control_v11p_sd15_normalbae.pth
### Canny - 精细化创作
python gradio_canny.py
模型文件：control_v11p_sd15_canny.pth
### MLSD - 室内设计
python gradio_mlsd.py
模型文件：control_v11p_sd15_mlsd.pth

### Scribble - 涂鸦创作
#### To test synthesized scribbles
python gradio_scribble.py
#### To test hand-drawn scribbles in an interactive demo
python gradio_interactive.py
模型文件：control_v11p_sd15_scribble.pth
### SoftEdge - 处理人像
python gradio_softedge.py
模型文件：control_v11p_sd15_softedge.pth
### Seg - 建筑设计
python gradio_seg.py
模型文件：control_v11p_sd15_seg.pth
### Openpose - 根据动作创作
模型文件: control_v11p_sd15_openpose.pth
python gradio_openpose.py
### Lineart - 线稿创作
模型文件：control_v11p_sd15_lineart.pth
python gradio_lineart.py
### Lineart Anime - 动漫线稿创作
模型文件：control_v11p_sd15s2_lineart_anime.pth
python gradio_lineart_anime.py