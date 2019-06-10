FROM tensorflow/tensorflow:nightly-gpu-py3

MAINTAINER Xiaotian Wu <wuxiaotiankevin@gmail.com>

# git
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y git

# reproduce kernels
RUN pip install tqdm && \
    pip install imageio && \
    pip install opencv-python && \
    pip install scikit-learn && \
    pip install scikit-image && \
    pip install keras && \
    pip install pandas && \
    pip install seaborn

RUN apt update && apt install -y libsm6 libxext6 libxrender1 && \
    pip install git+https://github.com/rcmalli/keras-vggface.git

# try new ideas
RUN pip install keras-facenet && \
    pip install mira

RUN pip install cmake && \
    pip install face_recognition
