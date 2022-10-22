FROM --platform=linux/amd64 nvidia/cuda:11.6.1-cudnn8-runtime-ubuntu20.04

RUN apt-get update \
    #
    # install conda
    && apt-get install -y --no-install-recommends \
        curl \
    && curl -o ~/miniconda.sh -O https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh \
    && chmod +x ~/miniconda.sh \
    && ~/miniconda.sh -b -p /opt/conda \
    #
    # install libs
    && /opt/conda/bin/conda install -y \
        numpy \
        scipy \
        pandas \
        lightgbm \
        matplotlib \
        seaborn \
        numba \
        tqdm \
    && /opt/conda/bin/conda install -y -c conda-forge \
        xgboost \
        imageio \
        scikit-learn \
        cudatoolkit=11.6 \
        pytorch-lightning \
        networkx \
    && /opt/conda/bin/conda install -y -c pytorch \
        pytorch \
        torchvision \
        torchaudio \
    #
    # clean up
    && /opt/conda/bin/conda clean -ya \
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/*

ENV PATH /opt/conda/bin:$PATH



