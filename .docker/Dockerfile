FROM ubuntu:latest
RUN apt update && \
    apt install -y curl wget git gnupg gnupg-agent zsh sudo && \
    useradd -u 1000 -d /home/ttsuzuki -m -s /bin/zsh ttsuzuki && \
    echo "ttsuzuki:ttsuzuki" | chpasswd && adduser ttsuzuki sudo && \
    chown -R ttsuzuki:ttsuzuki /home/ttsuzuki && \
    echo 'ttsuzuki ALL=(ALL) NOPASSWD: ALL' | sudo EDITOR='tee -a' visudo && \
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add

WORKDIR /home/ttsuzuki
ENV HOME /home/ttsuzuki

RUN gpg --keyserver hkp://pool.sks-keyservers.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB && \
    curl -sSL https://get.rvm.io | bash -s stable --ruby --auto-dotfiles && \
    echo progress-bar >> ~/.curlrc && \
    /bin/bash -l -c "source ~/.rvm/scripts/rvm" && \
    /bin/bash -l -c "gem update --system" && \
    /bin/bash -l -c "gem install rails pry bundler pg nokogiri" && \
    rvm install 2.6.1 && \
    rvm use 2.6.1 --default && \
    which ruby && \
    which rails
