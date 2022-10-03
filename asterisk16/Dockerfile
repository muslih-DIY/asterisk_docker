FROM debian:buster

WORKDIR /usr/local/src

COPY asterisk-16.28.0.tar.gz ./
RUN  tar xzf asterisk-16.28.0.tar.gz 
RUN apt-get update && apt-get install -y procps 
RUN apt-get install -y \
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
    uuid-dev\
    odbcinst1debian2 libodbc1 odbcinst unixodbc libsqliteodbc odbc-postgresql && rm -rf /var/lib/apt/lists/*;
    # apt-get update && apt-get -y  install inotify-tools rsync
    # wget http://downloads.asterisk.org/pub/telephony/asterisk/asterisk-16.28.0.tar.gz ;\
   

WORKDIR asterisk-16.28.0

# RUN contrib/scripts/get_mp3_source.sh 
# RUN contrib/scripts/install_prereq install
RUN ./configure 
# RUN make menuselect
RUN make menuselect.makeopts
RUN menuselect/menuselect --disable BUILD_NATIVE --enable CORE-SOUNDS-EN-ALAW menuselect.makeopts
RUN make ;\
    make install ;\
    make progdocs ;\
    make samples ;\
    make config ;

