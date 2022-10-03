FROM debian:buster

WORKDIR /usr/local/src

COPY asterisk-18.14.0.tar.gz ./
RUN  tar -xzf asterisk-18.14.0.tar.gz 
RUN apt-get update && apt-get install -y procps 
RUN apt-get install -y gcc \
    g++ \
    git \
    patch \
    libedit-dev \
    curl \
    wget \
    make \
    libnewt-dev \
    libssl-dev \
    libncurses5-dev \
    subversion  \
    sqlite3 \
    libsqlite3-dev \
    build-essential \
    libjansson-dev \
    libxml2-dev  \
    uuid-dev  rsync net-tools vim \
	
    odbcinst1debian2 libodbc1 odbcinst unixodbc libsqliteodbc odbc-postgresql;
    # apt-get update && apt-get -y  install inotify-tools rsync
    # wget http://downloads.asterisk.org/pub/telephony/asterisk/asterisk-16.28.0.tar.gz ;\
   

WORKDIR asterisk-18.14.0

# RUN contrib/scripts/get_mp3_source.sh 
ENV DEBIAN_FRONTEND=noninteractive
RUN contrib/scripts/install_prereq install && rm -rf /var/lib/apt/lists/*
RUN ./configure --with-jansson-bundled
# RUN make menuselect
RUN make menuselect.makeopts ; \
	menuselect/menuselect --disable BUILD_NATIVE --enable CORE-SOUNDS-EN-ALAW menuselect.makeopts
RUN make && make all && make install ; \
     make samples ;\
     make config ;

