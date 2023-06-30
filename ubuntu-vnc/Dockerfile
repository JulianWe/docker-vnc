# docker run -it --rm -p 6080:80 -p 5900:5900

FROM ubuntu:latest

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y curl
RUN apt-get update && apt-get install -y nginx
RUN apt-get install npm -y
RUN apt-get install nodejs -y
RUN apt-get install vim -y
RUN apt-get install software-properties-common -y
RUN apt-get install lightdm -y

RUN apt-get install novnc -y
RUN apt-get install ubuntu-desktop -y
RUN apt-get install vanilla-gnome-desktop vanilla-gnome-default-settings -y  
RUN apt-get install lightdm -y
RUN apt-get install lxde -y --no-install-recommends software-properties-common 
RUN dpkg-reconfigure gdm3 

RUN add-apt-repository universe

RUN apt-get install python3 python3-pip build-essential -y
RUN pip install --upgrade pip setuptools wheel

COPY x11vnc.service /etc/systemd/system/
RUN systemctl enable x11vnc.service

RUN apt-get install supervisor -y
RUN apt-get install openssh-server -y
RUN apt-get install pwgen -y 
RUN apt-get install net-tools -y
RUN apt-get install lxde -y --no-install-recommends software-properties-common 
RUN apt-get install xvfb -y --no-install-recommends software-properties-common 
RUN apt-get install x11vnc -y --no-install-recommends software-properties-common 
RUN apt-get install gtk2-engines-murrine -y

RUN apt-get install libreoffice firefox -y
RUN apt-get install fonts-wqy-microhei -y
RUN apt-get install language-pack-zh-hant language-pack-gnome-zh-hant firefox-locale-zh-hant libreoffice-l10n-zh-tw -y

RUN apt-get install mesa-utils libgl1-mesa-dri -y
RUN apt-get install gnome-themes-standard gtk2-engines-pixbuf gtk2-engines-murrine pinta arc-theme -y --no-install-recommends software-properties-common  
RUN apt-get install dbus-x11 x11-utils -y
RUN apt-get install vlc flvstreamer ffmpeg -y
RUN apt-get autoclean -y
RUN apt-get autoremove -y

RUN rm -rf /var/lib/apt/lists/*

ADD default /etc/nginx/sites-enabled/
ADD requirements.txt /etc/
ADD startup.sh /
ADD /web/ /

RUN pip3 install setuptools wheel && pip install -r /etc/requirements.txt

RUN chown -R root:root /root
EXPOSE 80
WORKDIR /root
ENV HOME=/home/ubuntu \
    SHELL=/bin/bash
ENTRYPOINT ["/startup.sh"]