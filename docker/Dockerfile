# ROS2用のDockerfile

# Base Image
FORM ubuntu:18.04
# User Info
LABEL maintainer="Shinichi Inoue <inoue.shinichi.1800@gmail.com>"

#################################################################
# Preprocess
#################################################################
# Time Zone(Japan +9h)
ENV TZ JST-9
# インストール時のインタラクティブな設定をスキップ
ENV DEBIAN_FRONTEND=noninteractive


#################################################################
# Install libraries etc...
#################################################################
# ROS2のインストールに必要なパッケージのインストール
RUN apt update \
    && apt install -y --no-install-recommends \
        bash-completion \
        build-essential \
        curl \
        wget \
        vim \
        gedit \
        locales \
        git \
        eog \
        x11-apps \
        lsb-release \
        tmux \
        gnupg2
    && rm -rf /var/lib/apt/lists/*

# ROS2 Eloquentのインストール
RUN curl -Ls https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | apt-key add -
RUN sh -c 'echo "deb http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" > /etc/apt/sources.list.d/ros2-latest.list'
RUN apt update \
    && apt install -y ros-eloquent-desktop \
                    libpython3-dev \
                    python3-argcomplete \
                    python3-colcon-common-extentions \
                    python3-vcstool

# Python3系の更新 & インストール
RUN pip3 install --upgrade pip3
RUN pip3 install wheel setuptools
RUN pip3 install numpy \
                 matplotlib \
                 scipy \
                 pandas \
                 scikit-learn \
                 PIL

# Pytorchのインストール
RUN pip3 install torch==1.8.1+cpu torchvision==0.9.1+cpu torchaudio==0.8.1 -f https://download.pytorch.org/whl/torch_stable.html



# Turtlesimのインストール@ROS2
RUN apt install -y ros-eloquent-turtlesim \
                ros-eloquent-gazebo-ros-*