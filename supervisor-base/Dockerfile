FROM blalor/centos

MAINTAINER Trevor R.H. Clarke <tclarke@ball.com> "https://github.com/tclarke"

# make sure the package repository is up to date and update ubuntu
RUN yum -y upgrade

# install supervisor to manage our processes
# the supervisor config file is more likely to change and is therefore added as a later step

RUN yum -y install supervisor
# create directory for child images to store configuration in
RUN mkdir -p /etc/supervisor/conf.d

ADD supervisor.conf /etc/supervisor.conf
