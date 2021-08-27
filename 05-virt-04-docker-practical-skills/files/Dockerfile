FROM archlinux:latest

RUN pacman -Sy && \
pacman -S --noconfirm community/ponysay

ENTRYPOINT ["/usr/bin/ponysay"]
CMD ["Hey, netology”]