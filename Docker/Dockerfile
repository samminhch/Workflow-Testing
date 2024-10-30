FROM ubuntu:22.04 as development

SHELL ["/bin/bash", "-c"]
RUN sed -r -i 's,http://(.*).ubuntu.com,http://mirror.us-tx.kamatera.com,' /etc/apt/sources.list

RUN apt-get update && apt-get upgrade && apt-get --no-install-recommends -y install \
    curl git zsh software-properties-common && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

RUN add-apt-repository ppa:neovim-ppa/unstable -y && \
    apt-get update && apt-get upgrade && apt-get --no-install-recommends -y install \
    nala libtree-sitter-dev ripgrep python3-venv npm neovim &&\
    apt-get clean && rm -rf /var/lib/apt/lists/* && \
    curl -sS https://starship.rs/install.sh | sh -s -- -y &> /dev/null

RUN echo "alias apt='nala'" >> /root/.bash_aliases && \
    echo 'eval "$(starship init bash)"' >> /root/.bashrc && \
    echo "Complete!"
