FROM ubuntu:16.04

ADD FrontISTR_V46.tar.gz /root/FrontISTR_4.6/
ADD REVOCAP_Refiner-1.1.04.tar.gz /root/
ADD Makefile.am /root/FrontISTR_4.6/ 
ADD Makefile.conf /root/FrontISTR_4.6/

RUN apt update
RUN apt upgrade -y
RUN apt install -y build-essential gfortran
RUN apt install -y openmpi-bin libopenmpi-dev
RUN apt install -y libtrilinos-ml-dev
RUN apt install -y libtrilinos-aztecoo-dev libtrilinos-zoltan-dev
RUN apt install -y libopenblas-dev libmumps-dev libmetis-dev
RUN cd /root/REVOCAP_Refiner-1.1.04; make
RUN cd /root/FrontISTR_4.6; \
    ./setup.sh -p --with-tools --with-refiner --with-metis --with-mumps --with-lapack --with-ml; \
    make; \
    make install
ENV PATH ${PATH}:/root/FrontISTR/bin
