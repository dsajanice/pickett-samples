FROM phusion/baseimage:latest
MAINTAINER iansmith@igneous.io


# Set correct environment variables.
ENV HOME /root

# Regenerate SSH host keys. baseimage-docker does not contain any, so you
# have to do that yourself. You may also comment out this instruction; the
# init system will auto-generate one during boot.
RUN /etc/my_init.d/00_regen_ssh_host_keys.sh

# Use baseimage-docker's init system.
CMD ["/sbin/my_init"]

##
## The objective here is to get gotools installed, note go implies git these days
##

RUN DEBIAN_FRONTEND=noninteractive apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y golang git


# Clean up APT when done.
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

#make workdir homedir
WORKDIR /

## 
## the /sample2 is connected to the CodeVolume > MountedAt, the vendor dir is in the external
## directory and includes vendor libs
##
ENV GOPATH /vendor:/sample
