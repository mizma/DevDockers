FROM archlinux:base
RUN pacman-key --init && \
    pacman -Syu --noconfirm && \
    pacman -S --noconfirm extra/git core/make extra/cmake core/ca-certificates core/gcc core/bash && \
    pacman -S --noconfirm extra/arm-none-eabi-gcc extra/arm-none-eabi-newlib && \
    pacman -S --noconfirm core/python extra/nodejs extra/npm extra/clang && \
    pacman -S --noconfirm extra/neovim extra/fd extra/unzip extra/lazygit extra/ripgrep && \
    git clone https://github.com/koma75/nvConfig.git /root/.config/nvim
RUN git clone https://github.com/raspberrypi/pico-sdk.git && cd pico-sdk && git submodule update --init
COPY ./dotfiles/.bashrc /root/

ENV PICO_SDK_PATH=/pico-sdk
ENV CMAKE_EXPORT_COMPILE_COMMANDS=1
ENV GP2040_BOARDCONFIG=pico
CMD /usr/bin/bash
