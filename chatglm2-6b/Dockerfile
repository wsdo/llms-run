# FROM pytorch/pytorch:latest
FROM itxishu/agi:v6

# WORKDIR 指定工作目录
WORKDIR /home/

# 安装包
COPY openai-api.py openai-api.py
COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt


# EXPOSE 暴露 80 端口
EXPOSE 80
EXPOSE 7000

#CMD ["python3", "openai-api.py"]
