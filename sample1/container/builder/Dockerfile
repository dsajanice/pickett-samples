FROM sample1:runner
MAINTAINER iansmith@igenous.io

##
## The objective here is to create our build tools. We end up re-downloading the
## build-essential and curl tools because these are not supposed to exist on the
## selma/runner container.
##
## The pickett side assumes that go is installed and the GOPATH and PATH set 
## correctly if you invoke a GoBuild in a container.
##

RUN DEBIAN_FRONTEND=noninteractive apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y build-essential pkg-config git mercurial curl 
RUN DEBIAN_FRONTEND=noninteractive apt-get upgrade -y

# Clean up APT
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

WORKDIR /opt
RUN hg clone -u release https://code.google.com/p/go
WORKDIR /opt/go/src
RUN ./all.bash

RUN ln -s /opt/go/bin/go /usr/bin/go

#
# These env vars are needed by various build-related activities. This does not
# include GOPATH, that's set in external.
#

ENV PKG_CONFIG_PATH /opt/build/lib/pkgconfig/
ENV LD_LIBRARY_PATH /opt/build/lib
ENV GOROOT /opt/go
