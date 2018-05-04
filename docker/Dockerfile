# docker run -it \
#    --net host \ # may as well YOLO
#    --cpuset-cpus 0 \ # control the cpu
#    --memory 512mb \ # max memory it can use
#    -v /tmp/.X11-unix:/tmp/.X11-unix \ # mount the X11 socket
#    -e DISPLAY=unix$DISPLAY \ # pass the display
#    -v $HOME/Downloads:/root/Downloads \ # optional, but nice
#    -v $HOME/.config/google-chrome/:/data \ # if you want to save state
#    --device /dev/snd \ # so we have sound
#    --name chrome \
#    jess/chrome
FROM ufoym/deepo

RUN apt-get update

RUN apt-get install -y freeglut3 libglu1 libopenal1
# Install open ai gym requirements and X11 stuff
RUN apt-get update \
    && apt-get install -y \
        libav-tools \
        python-pyglet \
        python-opengl \
        libpq-dev \
        libjpeg-dev \
        libboost-all-dev \
        libsdl2-dev \
        curl \
        cmake \
        swig \
        wget \
        unzip \
        git \
        xvfb \
        x11vnc \
        ratpoison \
        xterm \
        python-tk \
        fceux \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /root/.cache/pip/

RUN pip3 install gym

ENV PATH=$PATH:/usr/games

# Xvnc
EXPOSE 5900

COPY "./docker_start.sh" "/opt/docker_start.sh"


CMD ["/opt/docker_start.sh"]


