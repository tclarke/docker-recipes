FROM tclarke/supervisor

MAINTAINER Trevor R.H. Clarke <tclarke@ball.com> "https://github.com/tclarke"

RUN yum install -y Django Django-south python-sqlite python-pip
RUN pip install celery django-celery

RUN mkdir -p /var/www/django

ADD 10-django.supervisord.conf /etc/supervisord/conf.d/

# we'll have problems running django manage.py without a LANG set
ENV LANG en_US

EXPOSE 9123
