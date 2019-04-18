FROM nvidia/cuda:10.1-cudnn7-runtime

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        curl \
        git && \
    rm -rf /var/lib/apt/lists/*

RUN curl -o ~/miniconda.sh -O  https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh  && \
    chmod +x ~/miniconda.sh && \
    ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    /opt/conda/bin/conda install -y \
        numpy \
        pyyaml \
        scipy \
        ipython \
        scikit-learn \
        pandas \
        lightgbm \
        notebook \
        tqdm && \
    /opt/conda/bin/conda install xgboost imageio -c conda-forge && \
    /opt/conda/bin/conda install -y pytorch torchvision cudatoolkit=10.0 -c pytorch && \
    /opt/conda/bin/conda clean -ya && \
    /opt/conda/bin/pip install git+https://github.com/wpwei/pretrained-models.pytorch.git@vision_bug_fix && \
    /opt/conda/bin/pip install git+https://github.com/BorealisAI/advertorch.git

ENV PATH /opt/conda/bin:$PATH



        