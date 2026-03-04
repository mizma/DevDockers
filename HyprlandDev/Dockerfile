FROM archlinux:base
# Install reflector
RUN pacman-key --init && \
    pacman -Syu --noconfirm && \
    pacman -Syy --noconfirm reflector
# Update the pacman mirror list
RUN reflector --verbose --latest 10 --save /etc/pacman.d/mirrorlis

# ───────────────────────────────────────────────
# 1. Basic preparation + add a non-root build user
# ───────────────────────────────────────────────
RUN pacman -Syu --noconfirm \
    && pacman -S --noconfirm --needed \
        base-devel \
        git \
    && useradd -m -s /bin/bash builder \
    && echo "builder ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/builder-nopasswd \
    && chmod 0440 /etc/sudoers.d/builder-nopasswd

# ───────────────────────────────────────────────
# 2. Install yay (as the builder user)
# ───────────────────────────────────────────────
USER builder
WORKDIR /home/builder

RUN git clone https://aur.archlinux.org/yay.git \
    && cd yay \
    && makepkg -si --noconfirm --needed \
    && cd .. \
    && rm -rf yay

USER root

RUN pacman -Syy --noconfirm extra/git core/make extra/cmake ninja core/ca-certificates core/gcc core/bash core/less && \
    pacman -S --noconfirm meson libxcb xcb-proto xcb-util xcb-util-keysyms libxfixes libx11 libxcomposite libxrender libxcursor pixman wayland-protocols && \
    pacman -S --noconfirm cairo pango libxkbcommon xcb-util-wm xorg-xwayland libinput libliftoff libdisplay-info cpio tomlplusplus && \
    git clone https://github.com/mizma/nvimrc.git /root/.config/nvim
USER builder
RUN yay -S --noconfirm hyprlang-git hyprcursor-git hyprwayland-scanner-git hyprwire-git xcb-util-errors hyprutils-git glaze hyprgraphics-git aquamarine-git re2 hyprland-qtutils-git muparser && \
    yay -S --noconfirm extra/neovim extra/fd extra/unzip extra/lazygit extra/ripgrep
USER root
WORKDIR /root
RUN git config --global --add safe.directory /root/Hyprland
RUN git config --global --add safe.directory /home
COPY ./dotfiles/.bashrc /root/

ENV CMAKE_EXPORT_COMPILE_COMMANDS=1
CMD /usr/bin/bash
