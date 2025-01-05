FROM archlinux:base
# Install reflector
RUN pacman-key --init && \
    pacman -Syu --noconfirm && \
    pacman -Syy --noconfirm reflector
# Update the pacman mirror list
RUN reflector --verbose --latest 10 --save /etc/pacman.d/mirrorlis

RUN pacman -Syy --noconfirm extra/git core/ca-certificates core/bash core/openssh && \
    pacman --needed --noconfirm -S git core/python python-pip python-pipx libffi && \
    pacman -S --noconfirm arm-none-eabi-gcc avr-gcc avrdude dfu-programmer dfu-util && \
    pacman -S --noconfirm base-devel gcc wget zip avr-binutils avr-libc arm-none-eabi-binutils arm-none-eabi-newlib && \
    pacman -S --noconfirm extra/neovim extra/fd extra/unzip extra/lazygit extra/ripgrep core/less core/openssh && \
    git clone https://github.com/mizma/nvimrc.git /root/.config/nvim
RUN pipx install qmk && /root/.local/bin/qmk setup -y
COPY ./dotfiles/ /root/
CMD /usr/bin/bash

