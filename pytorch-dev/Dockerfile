FROM wpwei/pytorch:latest

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        git && \
    rm -rf /var/lib/apt/lists/*

RUN /opt/conda/bin/conda install -y \
        ipython \
        jupyter \
        notebook \
        ipywidgets && \
    /opt/conda/bin/conda install -y flake8 -c anaconda && \
    /opt/conda/bin/conda install -y yapf tensorboard -c conda-forge && \
    /opt/conda/bin/conda clean -ya && \
    /opt/conda/bin/pip install pretrainedmodels pytorch-lightning



        