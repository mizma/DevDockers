FROM archlinux:base
# Install reflector
RUN pacman-key --init && \
    pacman -Syu --noconfirm && \
    pacman -S --noconfirm reflector
# Update the pacman mirror list
RUN reflector --verbose --latest 10 --save /etc/pacman.d/mirrorlis

RUN pacman -S --noconfirm extra/git core/make extra/cmake core/ca-certificates core/gcc core/bash && \
    pacman -S --noconfirm extra/arm-none-eabi-gcc extra/arm-none-eabi-newlib && \
    pacman -S --noconfirm core/python extra/nodejs-lts-iron extra/npm extra/clang && \
    pacman -S --noconfirm extra/neovim extra/fd extra/unzip extra/lazygit extra/ripgrep && \
    git clone https://github.com/koma75/nvConfig.git /root/.config/nvim
RUN git clone https://github.com/raspberrypi/pico-sdk.git && \
    cd pico-sdk && \
    git fetch --tags && \
    git checkout 1.5.1 && \
    git submodule update --init
RUN git config --global --add safe.directory /root/GP2040-ce
COPY ./dotfiles/.bashrc /root/

ENV PICO_SDK_PATH=/pico-sdk
ENV CMAKE_EXPORT_COMPILE_COMMANDS=1
ENV GP2040_BOARDCONFIG=Pico
CMD /usr/bin/bash
