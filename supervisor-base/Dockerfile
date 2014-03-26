FROM blalor/centos

MAINTAINER Trevor R.H. Clarke <tclarke@ball.com> "https://github.com/tclarke"

# make sure the package repository is up to date and update ubuntu
RUN yum -y upgrade

# install supervisor to manage our processes
# the supervisor config file is more likely to change and is therefore added as a later step
# need to use pip to get v3.0 which is needed for includes in the conf file
RUN yum -y install python-pip
RUN pip install supervisor
# create directory for child images to store configuration in
RUN mkdir -p /etc/supervisord/conf.d
RUN rm -f /etc/supervisord.conf
ADD supervisord.conf /etc/supervisord.conf
