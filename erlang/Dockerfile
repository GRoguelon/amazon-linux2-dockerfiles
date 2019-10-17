FROM amazonlinux:2

ENV LC_ALL en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8
ENV ERLANG_VERSION 22.0
ENV ERL_TOP /tmp/otp_src_${ERLANG_VERSION}

RUN yum install -y gcc perl m4 openssl-devel ncurses-devel unixODBC unixODBC-devel libxslt tar gzip make && \
    curl -Lo /tmp/otp_src_${ERLANG_VERSION}.tar.gz http://www.erlang.org/download/otp_src_${ERLANG_VERSION}.tar.gz && \
    tar -C /tmp -zxf /tmp/otp_src_${ERLANG_VERSION}.tar.gz && \
    cd $ERL_TOP && \
    ./configure --prefix=/opt/erlang/${ERLANG_VERSION} --without-wx --without-javac && \
    make -j$(nproc) && \
    make -j$(nproc) install

FROM amazonlinux:2

LABEL maintainer="Geoffrey Roguelon"

ENV LC_ALL en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8
ENV PATH /opt/erlang/22.0/bin:$PATH

RUN yum install -y unixODBC libxslt && \
    yum clean all

COPY --from=0 /opt/erlang /opt/erlang

CMD ["erl"]
