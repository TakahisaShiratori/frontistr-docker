FROM ubuntu:16.04

ADD FrontISTR_V46.tar.gz /opt/FrontISTR_4.6/
ADD REVOCAP_Refiner-1.1.04.tar.gz /opt/
ADD Makefile.am /opt/FrontISTR_4.6/ 
ADD Makefile.conf /opt/FrontISTR_4.6/

RUN apt update; \
    apt upgrade -y; \
    apt install -y build-essential gfortran; \
    apt install -y openmpi-bin libopenmpi-dev; \
    apt install -y libtrilinos-ml-dev; \
    apt install -y libtrilinos-aztecoo-dev libtrilinos-zoltan-dev; \
    apt install -y libopenblas-dev libmumps-dev libmetis-dev; \
    cd /opt/REVOCAP_Refiner-1.1.04; \
    make; \
    cd /opt/FrontISTR_4.6; \
    ./setup.sh -p --with-tools --with-refiner --with-metis --with-mumps --with-lapack --with-ml; \
    make; \
    make install; \
    groupadd -r frontistr && useradd -r -g frontistr frontistr; \
    mkdir /home/frontistr; \
    chown frontistr /home/frontistr; \
    chgrp frontistr /home/frontistr

USER frontistr
WORKDIR /home/frontistr
ENV PATH ${PATH}:/opt/FrontISTR_4.6/bin
CMD ["fistr1"]
