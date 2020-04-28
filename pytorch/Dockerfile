FROM nvidia/cuda:10.1-cudnn7-runtime

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
        tqdm \
    && /opt/conda/bin/conda install -y -c conda-forge \
        xgboost \
        imageio \
        scikit-learn \
        tornado \
    && /opt/conda/bin/conda install -y -c pytorch \
        pytorch \
        torchvision \
        cudatoolkit=10.1 \
    && /opt/conda/bin/pip install \
        pretrainedmodels \
        pytorch-lightning \
        simpy \
    #
    # clean up
    && /opt/conda/bin/conda clean -ya \
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/*

ENV PATH /opt/conda/bin:$PATH



