FROM ubuntu:latest

ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y curl
RUN apt-get update && apt-get install -y nginx
RUN apt-get install software-properties-common -y
RUN apt-get install novnc -y
RUN apt-get install ubuntu-desktop -y
RUN apt-get install vanilla-gnome-desktop vanilla-gnome-default-settings -y  
RUN apt-get install lightdm -y
RUN apt-get install lxde -y --no-install-recommends software-properties-common 
RUN apt-get install libreoffice firefox -y

# Install git, supervisor , VNC, & X11 packages
RUN set -ex; \
    apt-get update; \
    apt-get install -y \
      bash \
      fluxbox \
      git \
      net-tools \
      novnc \
      supervisor \
      x11vnc --no-install-recommends software-properties-common \
      xterm \
      xvfb

# Setup demo environment variables
ENV HOME=/root \
    DEBIAN_FRONTEND=noninteractive \
    LANG=en_US.UTF-8 \
    LANGUAGE=en_US.UTF-8 \
    LC_ALL=C.UTF-8 \
    DISPLAY=:0.0 \
    DISPLAY_WIDTH=1024 \
    DISPLAY_HEIGHT=768 \
    RUN_XTERM=yes \
    RUN_FLUXBOX=yes


COPY . /app
CMD ["/app/entrypoint.sh"]
EXPOSE 8080
