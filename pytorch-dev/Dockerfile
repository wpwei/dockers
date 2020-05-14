FROM wpwei/pytorch:latest

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Install apt and install packages
RUN apt-get update \
    && apt-get -y install --no-install-recommends apt-utils 2>&1 \
    #
    # Verify git, process tools, lsb-release (common in install instructions for CLIs) installed
    && apt-get -y install git iproute2 procps lsb-release \
    #
    # install dev libs
    && /opt/conda/bin/conda install -y \
        ipython \
        jupyter \
        notebook \
        ipywidgets \
    && /opt/conda/bin/conda install -y flake8 -c anaconda \
    && /opt/conda/bin/conda install -y yapf tensorboard jupyterlab -c conda-forge \
    #
    # Create a non-root user
    && groupadd --gid $USER_GID $USERNAME \
    && useradd -s /bin/bash --uid $USER_UID --gid $USER_GID -m $USERNAME \
    # Add sudo support for the non-root user
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME\
    && chmod 0440 /etc/sudoers.d/$USERNAME \
    #
    # Clean up
    && /opt/conda/bin/conda clean -ya \
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/*
    
    # set locale for VSCode debugger
    ENV LC_ALL C