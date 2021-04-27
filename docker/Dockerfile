FROM amd64/ubuntu
ENV USER test
ENV HOME /home/${USER}
ENV SHELL /bin/bash
RUN useradd -m ${USER}
RUN gpasswd -a ${USER} sudo
RUN echo "${USER}:test123" | chpasswd

RUN apt update && apt upgrade && apt -y install sudo git
RUN apt -y --no-install-recommends install autoconf automake bash bison bzip2
RUN apt -y --no-install-recommends install diffutils file flex g++ gawk gcc-multilib
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections
RUN apt -y --no-install-recommends install gettext gperf groff-base libncurses-dev
RUN apt -y --no-install-recommends install libexpat1-dev libslang2 libssl-dev libtool
RUN apt -y --no-install-recommends install libxml-parser-perl make patch perl pkg-config
RUN apt -y --no-install-recommends install python sed shtool tar texinfo unzip zlib1g zlib1g-dev
RUN apt -y --no-install-recommends install lib32z1-dev lib32stdc++6 automake1.11
RUN dpkg --add-architecture i386 && apt update && apt -y install libelf-dev:i386 libelf1:i386

USER ${USER}
WORKDIR ${HOME}

RUN git clone https://github.com/RMerl/am-toolchains.git
RUN git clone https://github.com/RMerl/asuswrt-merlin.ng.git
RUN ln -s ~/am-toolchains/brcm-arm-sdk  ~/asuswrt-merlin.ng/release/src-rt-6.x.4708/toolchains
RUN echo "PATH=\$PATH:/opt/brcm-arm/bin" >> ~/.profile

USER root
RUN apt -y install xsltproc
RUN cd /home/${USER}; ln -s /home/${USER}/am-toolchains/brcm-arm-sdk/hndtools-arm-linux-2.6.36-uclibc-4.5.3 /opt/brcm-arm

USER ${USER}
