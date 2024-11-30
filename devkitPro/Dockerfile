FROM archlinux:base

# Install reflector
RUN pacman-key --init && \
    pacman -Syu --noconfirm && \
    pacman -S --noconfirm reflector
# Update the pacman mirror list
RUN reflector --verbose --latest 10 --save /etc/pacman.d/mirrorlis

ENV DEVKITPRO=/opt/devkitpro
ENV DEVKITARM=/opt/devkitpro/devkitARM
ENV DEVKITPPC=/opt/devkitpro/devkitPPC
ADD https://pkg.devkitpro.org/devkitpro-keyring.pkg.tar.xz /root/
RUN pacman-key --recv BC26F752D25B92CE272E0F44F7FD5492264BB9D0 --keyserver keyserver.ubuntu.com && \
    pacman-key --lsign BC26F752D25B92CE272E0F44F7FD5492264BB9D0 && \
    pacman -U --noconfirm /root/devkitpro-keyring.pkg.tar.xz
RUN echo "[dkp-libs]" >> /etc/pacman.conf && \
    echo "Server = https://pkg.devkitpro.org/packages" >> /etc/pacman.conf && \
    echo "[dkp-linux]" >> /etc/pacman.conf && \
    echo "Server = https://pkg.devkitpro.org/packages/linux/\$arch/" >> /etc/pacman.conf
RUN pacman -Syu --noconfirm && \
    pacman -S --noconfirm extra/git core/make extra/cmake core/ca-certificates core/gcc core/bash which && \
    pacman -S --noconfirm core/python extra/nodejs extra/npm extra/clang && \
    pacman -S --noconfirm switch-dev dkp-linux/devkitARM && \
    pacman -S --noconfirm extra/neovim extra/fd extra/unzip extra/lazygit extra/ripgrep core/less && \
    git clone https://github.com/mizma/nvimrc.git /root/.config/nvim
COPY ./dotfiles/.bashrc /root/

# Following groups can be installed for convenience
# - gp32-dev
# - gp2x-dev
# - gba-dev
# - nds-dev
# - 3ds-dev
# - gamecube-dev
# - wii-dev
# - wiiu-dev
# - switch-dev

CMD /usr/bin/bash
