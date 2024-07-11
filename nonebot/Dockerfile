FROM python:3.12-slim
SHELL ["/bin/bash", "-c"]
RUN apt-get update && apt-get install fonts-noto-cjk fonts-noto-color-emoji

WORKDIR /app

COPY . /app

RUN cp fonts /usr/share/fonts/truetype/

ENV PATH="/root/.local/bin:$PATH"

RUN pip install pipx && python -m pipx ensurepath
RUN source ~/.bashrc && \
    pipx install pdm nb-cli && \
    pdm config venv.in_project false && pdm venv create --name nonebot && \
    pdm install --venv nonebot && \
    echo 'eval $(pdm venv activate nonebot)' >> ~/.bashrc && source ~/.bashrc
