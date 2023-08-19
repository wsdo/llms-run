FROM anibali/pytorch:1.13.0-cuda11.8-ubuntu22.04

# Set up time zone.
ENV TZ=UTC
RUN sudo ln -snf /usr/share/zoneinfo/$TZ /etc/localtime


# MAINTAINER
MAINTAINER starkwang starkwanglab@gmail.com

ENV DEBIAN_FRONTEND noninteractive

# CMD docker run执行
# RUN docker build执行

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

RUN apt-get -y install build-essential nghttp2 libnghttp2-dev libssl-dev git-lfs

RUN git clone https://huggingface.co/THUDM/chatglm2-6b

# EXPOSE 暴露 80 端口
EXPOSE 80
EXPOSE 8080

# 安装包
COPY . .
RUN pip install -r requirements.txt

CMD ["python3", "openai-api.py"]
