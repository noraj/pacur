FROM docker.io/centos:7
MAINTAINER Pacur <contact@pacur.org>

RUN yum -y install epel-release
RUN yum -y upgrade
RUN yum -y groupinstall 'Development Tools'
RUN yum -y install tar expect rpm-build rpm-sign openssl createrepo rsync make automake gcc wget zip git mercurial

RUN wget https://go.dev/dl/go1.18.1.linux-amd64.tar.gz
RUN echo "b3b815f47ababac13810fc6021eb73d65478e0b2db4b09d348eefad9581a2334 go1.18.1.linux-amd64.tar.gz" | sha256sum -c -
RUN tar -C /usr/local -xf go1.18.1.linux-amd64.tar.gz
RUN rm -f go1.18.1.linux-amd64.tar.gz

ENV GOPATH /go
ENV PATH /usr/local/go/bin:$PATH:/go/bin
ENV GO111MODULE on

RUN go install github.com/pacur/pacur@latest

ENTRYPOINT ["pacur"]
CMD ["build", "centos-7"]
