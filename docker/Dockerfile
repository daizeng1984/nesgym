# Mostly grabbed from this repo https://github.com/paulsuda/jupyter-gym-vnc
# build: sudo docker build -t test:nesgym .
# run: sudo nvidia-docker run -it -p 5900:5900 -v ~/Workspace/:/root/Workspace test:nesgym
#      then run your python app
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
COPY "./xsession_start.sh" "/opt/xsession_start.sh"

RUN chmod +x "/opt/docker_start.sh" "/opt/xsession_start.sh"

CMD ["/opt/docker_start.sh"]
