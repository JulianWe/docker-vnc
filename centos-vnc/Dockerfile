FROM centos:centos7

# Install the appropriate software
RUN yum -y update; yum clean all
RUN yum -y install epel-release; yum clean all
RUN yum -y install x11vnc firefox xorg-x11-server-Xvfb xorg-x11-twm tigervnc-server xterm xorg-x11-font dejavu-sans-fonts dejavu-serif-fonts xdotool; yum clean all

# Add the xstartup file into the image
ADD ./xstartup /

RUN mkdir /.vnc


RUN echo "abcdefg" > /.vnc/passwd
#RUN x11vnc -storepasswd "abcdefg" /.vnc/passwd

#RUN x11vnc -passwdfile /.vnc/passwd -display :1

#RUN x11vnc -ssl -passwdfile /.vnc/passwd -display :0 




#RUN  \cp -f ./xstartup /.vnc/.
#RUN chmod -v +x /.vnc/xstartup
#RUN sed -i '/\/etc\/X11\/xinit\/xinitrc-common/a [ -x /usr/bin/firefox ] && /usr/bin/firefox &' /etc/X11/xinit/xinitrc

EXPOSE 5901

#CMD    ["vncserver", "-fg" ]
# ENTRYPOINT ["vncserver", "-fg" ]


ENTRYPOINT ["/bin/bash"]