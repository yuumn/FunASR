ARG FUNASR_BASE_IMAGE=registry.cn-hangzhou.aliyuncs.com/funasr_repo/funasr
ARG FUNASR_BASE_TAG=funasr-runtime-sdk-gpu-0.2.1
FROM ${FUNASR_BASE_IMAGE}:${FUNASR_BASE_TAG}

ARG APP_DIR=/workspace/FunASR
WORKDIR ${APP_DIR}
COPY . .

RUN export https_proxy=http://10.7.4.2:3128 && \
    export http_proxy=http://10.7.4.2:3128 && \
    apt update && apt-get update && apt install -y ffmpeg && \
    pip install gunicorn && \
    pip install flask && \
    pip install openai && \
    pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118 && \
    unset https_proxy && \
    unset http_proxy

WORKDIR ${APP_DIR}

CMD ["/bin/bash"]