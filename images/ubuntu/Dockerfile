FROM ubuntu:22.04

ARG DEBIAN_FRONTEND=noninteractive

# Install base packages
RUN apt update && apt -y install apt-utils curl git gnupg2 && apt clean

# Install Docker
RUN echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian bookworm stable" | \
    tee /etc/apt/sources.list.d/docker.list
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | \
    gpg --dearmor -o /etc/apt/keyrings/docker.gpg
RUN apt update && apt -y install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin && apt clean

# Install & configure oh-my-zsh
ADD .zshrc $HOME/.zshrc
RUN apt update && apt -y install zsh && apt clean
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
