FROM archlinux:base
RUN pacman-key --init && \
    pacman -Syu --noconfirm && \
    pacman -S --noconfirm extra/git core/ca-certificates core/bash && \
    pacman --needed --noconfirm -S git core/python python-pip python-pipx libffi && \
    pacman -S --noconfirm arm-none-eabi-gcc avr-gcc avrdude dfu-programmer dfu-util && \
    pacman -S --noconfirm base-devel gcc wget zip avr-binutils avr-libc arm-none-eabi-binutils arm-none-eabi-newlib && \
    pacman -S --noconfirm extra/neovim extra/fd extra/unzip extra/lazygit extra/ripgrep && \
    git clone https://github.com/koma75/nvConfig.git /root/.config/nvim
RUN pipx install qmk && /root/.local/bin/qmk setup -y
COPY ./dotfiles/.bashrc /root/
COPY ./dotfiles/.ssh /root/
CMD /usr/bin/bash

