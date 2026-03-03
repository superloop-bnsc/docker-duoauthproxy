FROM centos:7.9.2009

RUN sed -i -e 's/^mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-Base.repo
RUN sed -i -e 's/^#baseurl=http:\/\/mirror./baseurl=https:\/\/vault./g' /etc/yum.repos.d/CentOS-Base.repo


RUN \
    yum install -y \
      bash \
      curl \
      python \
      gcc \
      gmp-devel \
      libc-devel \
      libffi-devel \
      libgcc \
      openssl-devel \
      linux-headers \
      make \
      patch \
      perl \
      procps \
      py-setuptools \
      python-devel \
      tar \
      zlib-devel \
    && rm -fr /var/cache/yum && \
    useradd duo

ARG VERSION

# Build and install authproxy.
ADD https://dl.duosecurity.com/duoauthproxy-${VERSION}-src.tgz /root/
COPY build /root/
RUN /root/build
