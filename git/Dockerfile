FROM ubuntu

ARG user=<username>
ARG grp=<groupname>
ARG uid=<userid in number>
ARG gid=<groupid in number>

RUN apt-get update
RUN apt-get install git -y
RUN apt-get install vim -y

RUN addgroup --gid $gid $user
RUN adduser -u $uid --gid $gid $user

RUN mkdir /practice
WORKDIR /practice

USER $user

RUN git config --global user.name "<git user name>"
#RUN git config --global user.email "<git email address>"

LABEL maintainer="<maintainer>" version="1.0"
