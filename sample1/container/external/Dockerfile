FROM sample1:builder
MAINTAINER iansmith@igneous.io

##
## The objective here is to create all 3rd party libaries and set our GOPATH.
##
## TRICKY: We set GOPATH to include the directory where our source code will
## TRICKY: be mounted by our Pickett.json.  
##

COPY update.sh /update.sh
RUN chmod +x /update.sh
ENV GOPATH /vendor:/sample1  

#install deps and then build the libraries for future reference
RUN /update.sh
