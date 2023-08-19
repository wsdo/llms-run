FROM anibali/pytorch:1.13.0-cuda11.8-ubuntu22.04

# Set up time zone.
ENV TZ=UTC
RUN sudo ln -snf /usr/share/zoneinfo/$TZ /etc/localtime

# Install system libraries required by OpenCV.
RUN sudo apt-get update \
 && sudo apt-get install -y libgl1-mesa-glx libgtk2.0-0 libsm6 libxext6 \
 && sudo rm -rf /var/lib/apt/lists/*

# MAINTAINER
MAINTAINER starkwang starkwanglab@gmail.com

ENV DEBIAN_FRONTEND noninteractive

# CMD docker run执行
# RUN docker build执行

ADD node-v14.16.1-linux-x64.tar.xz /usr/local/src/

RUN apt-get update
RUN apt-get install nginx -y
RUN apt-get install vim -y
RUN apt-get install wget -y
RUN apt-get install curl -y
RUN apt-get install gzip -y
RUN apt-get install inetutils-ping -y
RUN apt-get install net-tools -y

# WORKDIR 指定工作目录
WORKDIR /home/

RUN ln -s /usr/local/src/node-v14.16.1-linux-x64/bin/node /usr/local/bin/node
RUN ln -s /usr/local/src/node-v14.16.1-linux-x64/bin/npm /usr/local/bin/npm


RUN apt-get -y install build-essential nghttp2 libnghttp2-dev libssl-dev git-lfs

RUN git clone https://huggingface.co/THUDM/chatglm2-6b

# EXPOSE 暴露 80 端口
EXPOSE 80
EXPOSE 8080

# 安装包
COPY . .
RUN pip install -r requirements.txt

CMD ["python3", "openai-api.py"]
