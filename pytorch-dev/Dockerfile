FROM wpwei/pytorch:latest

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        git \
        sudo \
    && rm -rf /var/lib/apt/lists/*

RUN /opt/conda/bin/conda install -y \
        ipython \
        jupyter \
        notebook \
        ipywidgets \
    && /opt/conda/bin/conda install -y flake8 -c anaconda \
    && /opt/conda/bin/conda install -y yapf tensorboard -c conda-forge \
    && /opt/conda/bin/conda clean -ya \
    && /opt/conda/bin/pip install pretrainedmodels pytorch-lightning

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME